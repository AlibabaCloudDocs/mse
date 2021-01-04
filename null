---
keyword: [本地联调, 使用本地注册中心]
---

# 使用Cloud Toolkit实现微服务的端云互联

您可以在IntelliJ IDEA中使用Cloud Toolkit的端云互联功能实现本地和云上应用的相互调用，提升开发效率。

在使用Cloud Toolkit实现端云互联前，请完成以下工作：

-   2020.9.1及以上版本的Cloud Toolkit能够基于本地工程的项目（Project）和模块（Module）粒度配置端云互联，如果想使用配置粒度功能，请将Cloud Toolkit升级到2020.9.1及以上版本。

    **说明：** 如果Cloud Toolkit已经是2020.9.1版本，但没有配置粒度选项，请您卸载再重新安装Cloud Toolkit插件。

-   使用一台可使用SSH登录的ECS，用于建立端云互联通道。具体操作，请参见[通过控制台使用ECS实例（快捷版）云服务器ECS快速入门](/cn.zh-CN/快速入门/通过控制台使用ECS实例（快捷版）.md)。

    **说明：**

    -   请确保该ECS实例和需要互联的应用在同一个VPC内。
    -   SSH通道需要使用密码方式登录，暂不支持使用密钥对登录。

## 使用限制

端云互联目前支持Java应用，而且不同Java微服务框架还有以下限制：

**说明：** 由于技术框架限制，暂不支持Eureka类型的注册中心。

|微服务框架|使用限制|
|-----|----|
|Spring Cloud|如果使用Nacos进行配置管理，请确保Spring Cloud为Spring CloudEdgware及以上版本。|
|Dubbo|-   Dubbo 2.7.2及以上版本
-   依赖的服务注册及发现组件版本：
    -   dubbo-nacos-registry 2.7.2及以上版本
    -   edas-dubbo-extension 2.0.2及以上版本 |
|HSF|无|

## 步骤一：安装Cloud Toolkit

1.  启动IntelliJ IDEA。

2.  在IntelliJ IDEA中安装插件。

    -   **macOS系统**： 在顶部菜单栏选择**IntelliJ IDEA** \> **Preference...**，在**Preference**配置页面左边导航栏单击**Plugins**，搜索Alibaba Cloud Toolkit，并单击**Install**安装。

        ![在IntelliJ IDEA中安装插件—mac](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9395552061/p133847.png)

    -   **Windows系统**：在顶部菜单栏选择**File** \> **Settings**，在**Settings**页面的左侧导航栏单击**Plugins**，搜索Alibaba Cloud Toolkit，并单击**Install**安装。

        ![在IntelliJ IDEA中安装插件—windows](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9395552061/p133851.png)

3.  在IntelliJ IDEA中插件安装成功后，重启IntelliJ IDEA，您可以在工具栏看到Alibaba Cloud Toolkit的图标（![Alibaba Cloud Toolkit图标](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9067688951/p133853.png)）。


## 步骤二：配置阿里云账号

在安装完Alibaba Cloud Toolkit后，您需使用AccessKey ID和AccessKey Secret来配置阿里云的账号。

1.  启动IntelliJ IDEA。

2.  在顶部菜单栏中选择**Tools** \> **Alibaba Cloud** \> **Preferences...**。

3.  在Settings对话框中选择**Alibaba Cloud Toolkit** \> **Accounts**。

4.  在**Accounts**对话框中设置**AccessKey ID**和**AccessKey Secret**，然后单击**OK**。

    ![Accounts](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0495552061/p133860.png)

    关于阿里云账号说明如下：

    -   如果您已经注册过阿里云账号，在**Accounts**对话框中单击**Get existing AK/SK**，进入阿里云登录页面。用已有账号登录后，跳转至安全信息管理页面，获取**AccessKey ID**和**AccessKey Secret**。
    -   如果您还没有阿里云账号，在**Accounts**对话框中单击**Sign up**，进入阿里云账号注册页面，注册账号。注册完成后按照上述方式获取**AccessKey ID**和**AccessKey Secret**。

## 步骤三：配置端云互联

1.  启动IntelliJ IDEA。

2.  在顶部菜单栏中选择**Tools** \> **Alibaba Cloud** \> **Preferences...。**

3.  在Settings对话框中选择**Alibaba Cloud Toolkit** \> **Microservice** \> **Microservice**。

4.  在**Microservice**对话框中配置端云互联相关参数。

    ![MSE端云互联配置](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9455978061/p205068.png)

    |参数|描述|
    |--|--|
    |**配置粒度**|本地工程需要使用端云互联功能的粒度，包含项目和模块。    -   项目：当前工程使用统一的端云互联配置。适用于单模块工程或模块间无配置差异的多模块工程。
    -   模块：当前工程包含多个模块，其中仅某个模块需要使用端云互联或不同模块的端云互联配置需求不同。如果需要为不同模块配置端云互联，选择具体模块，完成各自的端云互联配置。 |
    |**端云互联**|选中**端云互联**，启用端云互联功能。启用端云互联功能后，本地应用默认注册到云端注册中心并订阅云端注册中心的服务，本地应用中的服务可以和云端服务相互调用。

如果仅需要调用云端服务，不希望云端服务调用本地服务，可以选中**只订阅云端服务，不注册本地服务**。 |
    |**产品**|选择**微服务引擎（MSE）**。|
    |**区域**|选择云端注册中心应用的所在地域。|
    |**实例**|选择MSE托管的注册中心类型和实例名称。|
    |**命名空间**|当实例的注册配置中心类型选择Nacos集群时，需选择实例的命名空间。|
    |**SpringCloud服务端口**|如果是Spring Cloud应用，则需在**SpringCloud服务端口**文本框内添加该应用的服务端口，其他类型应用不需要填写。|
    |**代理**|选择代理机。关于代理配置的相关内容，请参见[配置代理]()。|
    |**初始化代理...**|初始化SSH代理机，配置SSH规则使得端云互联生效。**说明：** 如果代理列表中最后一级SSH代理非root账号，则会提示您提供root权限来进行配置，配置完成后即可正常使用。若您不希望插件帮您配置，也可手动配置代理，关于手动初始化代理的相关操作，请参见[手动初始化代理](手动初始化代理)。 |
    |**高级配置**|选中**自动关闭启动提示**，可设置应用启动提示间隔时长，单位毫秒。|
    |**一键诊断**|端云互联过程中，如果遇到问题，可以单击**一键诊断**，排查etrans通道启动异常和服务连接不通等问题。 |

5.  先单击**Apply**，然后单击**OK**。


## 步骤四：启动本地应用进行端云互联

启动本地应用，如果当前状态处于端云互联状态，那么会有如下提示：

![启动本地应用进行端云互联](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1790652061/p66859.png)

并且，在启动应用之后会启动一个etrans的进程：

![启动etrans的进程](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1790652061/p66860.png)

## 更多信息

在使用Cloud Toolkit实现端云互联时，如果遇到相关问题，请参见[端云互联问题]()。

