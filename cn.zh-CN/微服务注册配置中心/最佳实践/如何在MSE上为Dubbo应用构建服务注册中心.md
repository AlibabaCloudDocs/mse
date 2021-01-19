---
keyword: [微服务, 服务发现]
---

# 如何在MSE上为Dubbo应用构建服务注册中心

本文以包含服务提供者和服务消费者的Dubbo微服务应用为例，让您快速体验如何在MSE上构建ZooKeeper、Eureka和Nacos等服务注册中心，实现应用的服务注册与发现，以及消费者对提供者的调用。

## 准备工作

在开始开发前，请确保您已经完成以下工作：

-   [开通MSE集群托管](https://www.aliyun.com/product/mse)。
-   下载[Maven](https://aliware-images.oss-cn-hangzhou.aliyuncs.com/EDAS/App-develop/apache-maven-3.6.0-bin.tar.gz)并设置环境变量。
-   [创建命名空间](/cn.zh-CN/微服务注册配置中心/Nacos/管理命名空间.md)。

    本文使用默认命名空间**Public**。


## 在MSE上创建服务注册中心

本文以在MSE构建Nacos为例。

**说明：**

-   如果您需要的注册中心为ZooKeeper，具体操作请参见[购买并构建ZooKeeper引擎](/cn.zh-CN/快速入门/微服务注册配置中心/购买并构建ZooKeeper引擎.md)。
-   如果您需要的注册中心为Eureka，具体操作请参见[购买并构建Eureka引擎](/cn.zh-CN/快速入门/微服务注册配置中心/购买并构建Eureka引擎.md)。

1.  进入MSE实例创建页面。

    -   未开通MSE集群托管
        1.  登录[MSE产品页](https://www.aliyun.com/product/mse)。
        2.  在MSE产品页单击**超值资源包**。
        3.  选择您需要创建的MSE实例，例如**ZooKeeper**、**Eureka**和**Nacos**。

            进入MSE实例创建及购买页面。

    -   已开通MSE集群托管
        1.  登录[MSE管理控制台](https://mse.console.aliyun.com)。
        2.  在左侧导航栏选择**注册配置中心** \> **实例列表**。
        3.  在实例列表页面单击**创建实例**。
2.  设置**付费模式**。

    在MSE购买页面选择付费模式。

    MSE有预付费（包年包月）和按量付费（按小时）两种模式，如果您的服务注册中心使用时间在一个月以上，建议采用更加优惠的预付费（包年包月）模式。

3.  设置实例**地域和可用区**。

    选择您MSE实例所在地域。

    **说明：** 目前MSE现已开放了**华东1（杭州）**、**华东2（上海）**、**华北2（北京）**、**华南1（深圳）**、**华北3（张家口）**、**华南5（呼和浩特）**、**西南1（成都）**、**中国（香港）**、**新加坡**、**美国（弗吉尼亚）**、**俄罗斯（莫斯科）**、**美国（硅谷）**地域。

4.  配置引擎基本信息。

    ![Nacos引擎](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5724229061/p176072.png)

    配置基本参数如下：

    |参数|描述|
    |--|--|
    |**引擎类型**|选择**Nacos**。 |
    |**引擎版本**|MSE Nacos支持两种引擎版本，**1.1.3**和**1.2.1**。推荐使用**1.2.1**。

**说明：** 目前仅1.2.1版本支持配置中心，1.1.3不包含配置中心功能。 |
    |**引擎规格**|MSE实例规格有四种规格，**1核2G**、**2核4G**、**4核8G**和**8核16G**。

请您根据实际情况选择合适的组件规格，关于组件的评估方法，请参见[微服务注册配置中心实例能力评估](/cn.zh-CN/产品定价/微服务注册配置中心/微服务注册配置中心实例能力评估.md)。 |
    |**集群节点数**|选择集群内的节点数，即一个集群需要多少台上述规格的节点组成。

**说明：** 强烈建议Nacos集群规模最小3个节点，否则无法保障高可用。 |

5.  单击**立即购买**。

    创建完成后，如果所创建的Nacos状态为**运行中**，表示Nacos创建完成。

    ![在MSE创建Nacos完成](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6776076951/p69536.png)

    其中访问列对应的**mse.XX.nacos.mse.aliyuncs.com**为Nacos访问地址。


## 创建服务提供者

在本地创建一个提供者应用工程，添加依赖，配置服务注册与发现，并将注册中心指定为Nacos。

1.  创建Maven项目并引入依赖。

    1.  使用IDE（如IntelliJ IDEA或Eclipse）创建一个Maven项目。

    2.  在**pom.xml**文件中添加dubbo、dubbo-registry-nacos和nacos-client依赖。

        ```
        <dependencies>
            <dependency>
                <groupId>org.apache.dubbo</groupId>
                <artifactId>dubbo</artifactId>
                <version>2.7.3</version>
            </dependency>
            <dependency>
                <groupId>com.alibaba.nacos</groupId>
                <artifactId>nacos-client</artifactId>
                <version>1.1.1</version>
            </dependency>
        </dependencies>            
        ```

2.  开发Dubbo服务提供者。

    Dubbo中服务都是以接口的形式提供的。

    1.  在src/main/java工程路径下创建一个**package**，命名为com.alibaba.edas。

    2.  在com.alibaba.edas下创建一个接口（interface）**IHelloService**，里面包含一个**SayHello**方法。

        ```
        package com.alibaba.edas;
        
        public interface IHelloService {
           String sayHello(String str);
        }                                
        ```

    3.  在com.alibaba.edas下创建一个类**IHelloServiceImpl**，实现此接口。

        ```
        package com.alibaba.edas;
        
        public class IHelloServiceImpl implements IHelloService {
        public String sayHello(String str) {
            return "hello " + str;
            }
        }                          
        ```

3.  配置Dubbo服务。

    1.  在src/main/resources路径下创建**provider.xml**文件并打开。

    2.  在**provider.xml**中，添加Spring相关的XML Namespace（xmlns）和XML Schema Instance（xmlns:xsi），以及Dubbo相关的Namespace（xmlns:dubbo）和Scheme Instance（xsi:schemaLocation）。

        ```
        <beans xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xmlns:dubbo="http://dubbo.apache.org/schema/dubbo"
        xmlns="http://www.springframework.org/schema/beans"
        xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-4.3.xsd
        http://dubbo.apache.org/schema/dubbo http://dubbo.apache.org/schema/dubbo/dubbo.xsd">                   
        ```

    3.  在**provider.xml**中将接口和实现类暴露成Dubbo服务。

        ```
        <dubbo:application name="demo-provider"/>
        
        <dubbo:protocol name="dubbo" port="28082"/>
        
        <dubbo:service interface="com.alibaba.edas.IHelloService" ref="helloService"/>
        
        <bean id="helloService" class="com.alibaba.edas.IHelloServiceImpl"/>                                
        ```

    4.  在**provider.xml**中将注册中心指定为本地启动的Nacos Server。

        ```
        <dubbo:registry address="nacos://mse.XX.nacos.mse.aliyuncs.com:8848" />                                
        ```

        其中`mse.XX.nacos.mse.aliyuncs.com`为在MSE上传创建的Nacos的外网访问地址，如下图所示。

        ![在MSE创建Nacos完成](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6776076951/p69536.png)

        **说明：** 如果您使用的服务注册中心是MSE的Zookeeper，那么您需要将本步骤的注册中心代码换成Zookeeper相应的代码，具体代码详情请参见[MSE微服务注册配置中心使用说明](/cn.zh-CN/快速入门/微服务注册配置中心/MSE微服务注册配置中心使用说明.md)。

4.  启动服务。

    1.  在com.alibaba.edas中创建类**Provider**，并按下面的代码在Provider的main函数中加载Spring Context，将配置好的Dubbo服务暴露。

        ```
        package com.alibaba.edas;
        
        import org.springframework.context.support.ClassPathXmlApplicationContext;
        
        public class Provider {
            public static void main(String[] args) throws Exception {
                ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext(new String[] {"provider.xml"});
                context.start();
                System.in.read();
            }
        }                
        ```

    2.  执行Provider的main函数，启动服务。

5.  验证结果。

    1.  登录[MSE注册中心控制台](https://mse.console.aliyun.com)。

    2.  在左侧导航树中单击**实例列表**，并在实例列表页单击已创建的MSE实例。

    3.  设置MSE引擎访问白名单。

        如果没有填写任何IP地址及掩码，表示允许所有地址均可访问该实例。本文以无白名单为例。

    4.  在实例详情页面的左侧导航树，单击**服务管理**。

        如果在服务管理列表中存在Provider服务，表示该服务注册成功。

        ![SpringCloud应用使用mse创建的nacos服务注册成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6776076951/p69681.png)


## 创建服务消费者

在本地创建一个消费者应用工程，添加依赖，添加订阅服务的配置。

1.  创建Maven项目并引入依赖。

    1.  使用IDE（如IntelliJ IDEA或Eclipse）创建一个Maven项目。

    2.  在**pom.xml**文件中添加dubbo、dubbo-registry-nacos和nacos-client依赖。

        ```
        <dependencies>
            <dependency>
                <groupId>org.apache.dubbo</groupId>
                <artifactId>dubbo</artifactId>
                <version>2.7.3</version>
            </dependency>
            <dependency>
                <groupId>com.alibaba.nacos</groupId>
                <artifactId>nacos-client</artifactId>
                <version>1.1.1</version>
            </dependency>
        </dependencies>            
        ```


## 结果验证

执行`curl http://localhost:8080/sayHello/EDAS`，如果结果返回`Hello, EDAS`，表示Consumer与Provider业务调用成功。

```
`curl http://localhost:8080/sayHello/EDAS`

`Hello, EDAS`            
```

