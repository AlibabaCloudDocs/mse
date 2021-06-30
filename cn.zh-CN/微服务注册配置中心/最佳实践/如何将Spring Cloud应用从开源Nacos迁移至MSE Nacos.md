# 如何将Spring Cloud应用从开源Nacos迁移至MSE Nacos

MSE提供托管版Nacos引擎，包含比开源Nacos更强大和稳定的功能，能帮助您免去运维Nacos集群的烦恼，更加聚焦业务本身的实现，同时MSE也提供专业版的Nacos专家支持。本文介绍如何将Spring Cloud应用从开源Nacos无缝迁移至MSE。

[创建Nacos引擎](/cn.zh-CN/快速入门/微服务注册配置中心/创建Nacos引擎.md)

**说明：**

-   如果您的集群只需要在VPC内访问，那么只需要开通**专有网络**。
-   如果您的集群需要被其他VPC访问，那么您需要开通**公网网络**。公网访问地址需要配置白名单，配置内容置空表示能被任意的地址访问。相关操作，请参见[设置白名单](/cn.zh-CN/微服务注册配置中心/Nacos/设置白名单.md)。

**说明：** 为了更好地说明完整的场景，以部署在阿里云ACK集群上的一组应用为背景信息进行说明。如果您已充分了解注册中心迁移的场景，请参见[迁移方案](#section_7mk_5ay_95u)。

**最开始的业务形态**

假设在ACK集群中，部署了Nacos Server和Consumer应用，通过注册中心去获取Provider服务的地址，并通过访问/user/rest这个URL，返回服务提供者的端口号。

![服务调用](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1604033261/p282240.png)

首先，在阿里云ACK集群中，部署Consumer、Provider和Nacos Server应用。具体操作，请参见[创建无状态工作负载Deployment](/cn.zh-CN/Kubernetes集群用户指南/应用/工作负载/创建无状态工作负载Deployment.md)。

![部署服务](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2604033261/p282621.png)

然后，配置阿里云ACK集群的服务。

![配置服务](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2604033261/p282720.png)

-   Consumer服务属于LoadBalancer类型，通过SLB，可以直接访问Consumer服务。
-   Nacos服务属于LoadBalancer类型，通过SLB，可以访问开源Nacos控制台。
-   Nacos Server服务属于NodePort类型，配置好后，Consumer应用和Provider应用可以通过`[http://nacos-server:8848/](http://eureka-server:8761/eureka/)`访问Nacos Server服务。

最后，验证服务调用成功，并登录开源Nacos控制台可查看服务注册详情。

![nacos控制台](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9137033261/p282730.png)

**模拟迁移过程**

部署一个Consumer-new应用，注册到MSE上的Nacos，Consumer-new应用与Consumer应用使用了两个不同的标签。事实上，Consumer-new应用除了将开源Nacos的地址修改为Mse Nacos地址外，没有任何其他修改。

![部署consumer-new](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2604033261/p282623.png)

同样，在阿里云ACK集群中配置一个负载均衡服务访问Consumer-new应用。

**遇到的问题**

Consumer-new应用无法调用Provider服务，MSE Nacos可以查询到Consumer-new应用节点，但开源Nacos上查询不到，原因是开源Nacos并没有注册。

在实际业务中，如果新应用无法访问原有注册中心的应用，就无法顺利地完成注册中心的迁移，特别是应用规模比较大，调用链路比较复杂的时候，这个问题就更加明显，所以要先将应用迁移至MSE。

## 迁移方案

MSE基于Java Agent技术，您只需要接入MSE，就能享受微服务的功能，无需修改任何代码和配置。



1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏单击**集群**，然后在**集群列表**页面单击目标集群名称。

3.  在集群详情页面左侧导航栏选择**应用** \> **微服务治理**。

4.  在**微服务治理**页面单击**安装**。

    ![安装mse pilot](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0877023261/p281860.png)

5.  在**安装**对话框中单击**确定**。


1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/#/msc/k8s)。

2.  在左侧导航栏选择**微服务治理中心** \> **K8s集群列表**。

3.  在**K8s集群列表**页面搜索框列表中选择**集群名称**或**集群ID**，然后输入相应的关键字，单击![搜索图标](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9480080261/p272716.png)图标。

4.  单击目标集群**操作**列的**管理**。

5.  在**集群详情**页面命名空间列表区域，单击目标命名空间**操作**列下的**开启微服务治理**。


1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏单击**集群**，然后在**集群列表**页面单击目标集群名称。

3.  在集群详情页面左侧导航栏选择**工作负载** \> **无状态**，选择**命名空间**。

4.  在目标应用右侧单击**编辑**。

5.  在**编辑**页面的**环境变量**区域单击**新增**，添加以下两条环境变量。

    ![开启Nacos迁移](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4757133261/p281925.png)

    新增环境变量说明如下：

    |类型|**变量名称**|**变量/变量引用**|
    |--|--------|-----------|
    |自定义|enable\_multi\_nacos|true**说明：** 表明需要开启Nacos多注册订阅功能。 |
    |自定义|additional\_nacos\_address|nacos-server:8848**说明：** 除指定的注册中心之外的Nacos Server的地址。 |

    如果您的Nacos注册中心使用了命名空间，可以在环境变量中通过additional\_nacos\_namespace这个配置，例如additional\_nacos\_namespace=b5e92c40-6e0b-4c24-a5b0-ee326159de80。


**说明：** 在实际迁移过程中，建议在创建新应用时就开启MSE并配置好环境变量，避免出现多次重启。

## 结果验证

1.  登录开源Nacos Server控制台。

2.  在左侧导航栏选择**服务管理** \> **服务列表**，可以看到服务已经成功注册，且在详情中可以查询该服务的详情。


将应用进行扩容或缩容，验证服务注册的实时性。例如在本文示例中，将Consumer-new服务扩容到4个，可以发现，服务注册和注销的时效性都是实时的。

![服务扩缩容](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9137033261/p282653.png)

在本文示例中，通过Consumer-new服务调用Provider服务，在浏览器中输入http://Consumer-new服务的外部端点地址/user/rest，显示服务调用成功。

![服务调用成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9137033261/p282426.png)

## 更多通用配置

**配置更多的Nacos参数**

如果additional\_nacos\_address和additional\_nacos\_namespace这两个配置参数不能满足您对Nacos Properties的配置需求，您希望能配置更多的Nacos properties参数，可以通过以下方式配置：

```
additional_nacos_properties=com.alibaba.nacos.naming.log.filename=/home/admin&com.alibaba.nacos.naming.log.level=warn
```

**说明：** 其中additional\_nacos\_properties为配置参数，com.alibaba.nacos.naming.log.filename=/home/admin和com.alibaba.nacos.naming.log.level=warn为配置变量值，通过连接（&）符号分隔。如果您还想配置更多的值，使用连接（&）符号连接即可。

**只注册不订阅/只订阅不注册**

-   如果您想实现只订阅不注册，则添加以下参数：

    ```
    additional_nacos_properties=subscribeOnly=true
    ```

-   如果您想实现只注册不订阅，则添加以下参数：

    ```
    additional_nacos_properties=registerOnly=true
    ```


