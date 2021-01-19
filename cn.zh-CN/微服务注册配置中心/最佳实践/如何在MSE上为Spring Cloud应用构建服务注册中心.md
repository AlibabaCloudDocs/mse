---
keyword: [微服务, 服务发现]
---

# 如何在MSE上为Spring Cloud应用构建服务注册中心

本文以包含服务提供者和服务消费者的Spring Cloud微服务应用为例，让您快速体验如何在MSE上构建ZooKeeper、Eureka和Nacos等服务注册中心，实现应用的服务注册与发现，以及消费者对提供者的调用。

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
        2.  选择您需要创建的MSE实例，例如**ZooKeeper**、**Eureka**和**Nacos**。

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

在本地创建服务提供者应用工程，添加依赖，开启服务注册与发现功能，并将注册中心指定为Nacos Server。

1.  创建Maven工程，命名为**nacos-service-provider**。

2.  在**pom.xml**文件中添加依赖。

    以Spring Boot 2.1.4.RELEASE和Spring Cloud Greenwich.SR1为例，依赖如下：

    ```
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.4.RELEASE</version>
        <relativePath/>
    </parent>
    
    <dependencies>
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
            <version>2.1.1.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
    
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>Greenwich.SR1</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>                  
    ```

    示例中使用的版本为Spring Cloud Greenwich，对应Spring Cloud Alibaba版本为2.1.1.RELEASE。

    -   如果使用Spring Cloud Finchley版本，对应Spring Cloud Alibaba版本为2.0.1.RELEASE。
    -   如果使用Spring Cloud Edgware版本，对应Spring Cloud Alibaba版本为1.5.1.RELEASE。
    **说明：** Spring Cloud Edgware版本的生命周期已结束，不推荐使用这个版本开发应用。

3.  在src\\main\\java工程路径下创建名为com.aliware.edas的**Package**。

4.  在com.aliware.edas中创建服务提供者的启动类**ProviderApplication**，并添加如下代码。

    ```
    package com.aliware.edas;
    
    import org.springframework.boot.SpringApplication;
    import org.springframework.boot.autoconfigure.SpringBootApplication;
    import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
    
    @SpringBootApplication
        @EnableDiscoveryClient
        public class ProviderApplication {
    
            public static void main(String[] args) {
                SpringApplication.run(ProviderApplication.class, args);
            }
        }             
    ```

    **说明：** 其中`@EnableDiscoveryClient`注解表明此应用需开启服务注册与发现功能。

5.  在com.aliware.edas中创建**EchoController**，指定URL mapping 为 \{/echo/\{String\}\}，指定HTTP方法为GET，方法参数从URL路径中获得，回显收到的参数。

    ```
    package com.aliware.edas;
    
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestMethod;
    import org.springframework.web.bind.annotation.RestController;
    
    @RestController
    public class EchoController {
       @RequestMapping(value = "/echo/{string}", method = RequestMethod.GET)
        public String echo(@PathVariable String string) {
           return string;
          }
    }              
    ```

6.  在src\\main\\resources工程路径下创建文件application.properties，在application.properties中添加如下配置，并指定Nacos Server的访问地址。

    ```
    spring.application.name=service-provider
    server.port=18081
    spring.cloud.nacos.discovery.server-addr=mse.XX.nacos.mse.aliyuncs.com:8848               
    ```

    其中mse.XX.nacos.mse.aliyuncs.com为在MSE上传创建的Nacos的外网访问地址，如下图所示。

    ![在MSE创建Nacos完成1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9996481951/p95994.png)

    **说明：** 如果您使用的服务注册中心为MSE的Zookeeper或者Eureka，那么您需要将本步骤的注册中心代码换成Zookeeper或者Eureka相应的代码，具体详情请参见[MSE集群托管使用说明](/cn.zh-CN/快速入门/微服务注册配置中心/MSE微服务注册配置中心使用说明.md)。

7.  验证结果。

    1.  执行**nacos-service-provider**中**ProviderApplication**的**main**函数，启动应用。

    2.  登录[MSE注册中心控制台](https://mse.console.aliyun.com)。

    3.  在左侧导航树中单击**实例列表**，并在实例列表页单击已创建的MSE实例。

    4.  设置MSE引擎访问白名单。

        如果没有填写任何IP地址及掩码，表示允许所有地址均可访问该实例。本文以无白名单为例。

    5.  在实例详情页面的左侧导航树，单击**服务管理**。

        如果在服务管理列表中存在所Provider服务表示，该服务注册成功。

        ![SpringCloud应用使用mse创建的nacos服务注册成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6776076951/p69681.png)


## 创建服务消费者

本内容除介绍服务注册的功能，还将介绍Nacos服务发现与RestTemplate和FeignClient两个客户端如何配合使用。

1.  创建Maven工程，命名为**nacos-service-consumer**。

2.  在**pom.xml**中添加依赖。

    ```
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.4.RELEASE</version>
        <relativePath/>
    </parent>
    
    <dependencies>
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
            <version>2.1.1.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-openfeign</artifactId>
        </dependency>
    </dependencies>
    
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>Greenwich.SR1</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>        
    ```

3.  在src\\main\\java工程路径下创建名为com.aliware.edas的**Package**。

4.  在com.aliware.edas中配置RestTemplate和FeignClient。

    1.  在com.aliware.edas中创建一个接口类**EchoService**，添加`@FeignClient`注解，并配置对应的HTTP URL地址及HTTP方法。

        ```
        package com.aliware.edas;
        
        import org.springframework.cloud.openfeign.FeignClient;
        import org.springframework.web.bind.annotation.PathVariable;
        import org.springframework.web.bind.annotation.RequestMapping;
        import org.springframework.web.bind.annotation.RequestMethod;
        
        @FeignClient(name = "service-provider")
        public interface EchoService {
            @RequestMapping(value = "/echo/{str}", method = RequestMethod.GET)
            String echo(@PathVariable("str") String str);
        }                   
        ```

    2.  在com.aliware.edas中创建启动类**ConsumerApplication**并添加相关配置。

        -   使用`@EnableDiscoveryClient`注解启用服务注册与发现。
        -   使用`@EnableFeignClients`注解激活FeignClient。
        -   添加`@LoadBalanced`注解将RestTemplate与服务发现集成。
        ```
        package com.aliware.edas;
        
        import org.springframework.boot.SpringApplication;
        import org.springframework.boot.autoconfigure.SpringBootApplication;
        import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
        import org.springframework.cloud.client.loadbalancer.LoadBalanced;
        import org.springframework.cloud.openfeign.EnableFeignClients;
        import org.springframework.context.annotation.Bean;
        import org.springframework.web.client.RestTemplate;
        
        @SpringBootApplication
        @EnableDiscoveryClient
        @EnableFeignClients
        public class ConsumerApplication {
        
            @LoadBalanced
            @Bean
            public RestTemplate restTemplate() {
                return new RestTemplate();
            }
        
            public static void main(String[] args) {
                SpringApplication.run(ConsumerApplication.class, args);
            }
        }
        ```

5.  在com.aliware.edas中创建类**TestController**，以演示和验证服务发现功能。

    ```
    package com.aliware.edas;
    
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.PathVariable;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestMethod;
    import org.springframework.web.bind.annotation.RestController;
    import org.springframework.web.client.RestTemplate;
    
    @RestController
    public class TestController {
    
    @Autowired
    private RestTemplate restTemplate;
    @Autowired
    private EchoService echoService;
    
    @RequestMapping(value = "/echo-rest/{str}", method = RequestMethod.GET)
    public String rest(@PathVariable String str) {
          return restTemplate.getForObject("http://service-provider/echo/" + str,
                        String.class);
            }
    
          @RequestMapping(value = "/echo-feign/{str}", method = RequestMethod.GET)
          public String feign(@PathVariable String str) {
                return echoService.echo(str);
            }
    
        }           
    ```

6.  在src\\main\\resources工程路径下创建文件**application.properties**，在**application.properties**中添加如下配置，指定Nacos Server的地址。

    ```
    spring.application.name=service-consumer
    server.port=18082
    spring.cloud.nacos.discovery.server-addr=mse.XX.nacos.mse.aliyuncs.com:8848
    ```

    其中`mse.XX.nacos.mse.aliyuncs.com`为在MSE上传创建的Nacos的外网访地址，如下图所示。

    ![在MSE创建Nacos完成](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6776076951/p69536.png)

    **说明：** 如果您使用的服务注册中心为MSE的Zookeeper或者Eureka，那么您需要将本步骤的注册中心代码换成Zookeeper或者Eureka相应的代码，具体详情请参见[MSE使用说明](/cn.zh-CN/快速入门/微服务注册配置中心/MSE微服务注册配置中心使用说明.md)。

7.  验证结果。

    1.  执行**nacos-service-consumer**中**ConsumerApplication**的**main**函数，启动应用。

    2.  登录[MSE注册中心控制台](https://mse.console.aliyun.com)。

    3.  在左侧导航树中单击**实例列表**，并在实例列表页单击已创建的MSE实例。

    4.  设置MSE引擎访问白名单。

        如果没有填写任何IP地址及掩码，表示允许所有地址均可访问该实例。本文以无白名单为例。

    5.  在实例详情页面的左侧导航树单击**服务管理**。

        如果在服务管理列表中存在所Consumer服务表示，该服务注册成功。

        ![SpringCloud应用使用mse创建的nacos服务注册成功-consumer](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9996481951/p69682.png)


## 本地测试

在本地测试消费者对提供者的服务调用结果。

-   Linux/Unix/Mac系统：运行以下命令。

    ```
    curl http://127.0.0.1:18082/echo-rest/rest-rest
    curl http://127.0.0.1:18082/echo-feign/feign-rest
    ```

-   Windows系统：在浏览器中输入http://127.0.0.1:18082/echo-rest/rest-rest和http://127.0.0.1:18082/echo-feign/feign-rest。

本示例以Windows系统为例。

![Spring Cloud微服务应用是使用MSE调用成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0007481951/p69683.png)

## 常见问题

-   本地开发的Spring Cloud微服务应用，其服务注册中心为MSE上创建的Nacos，应用运行后，在MSE服务管理页面看不到服务信息，如何处理？

    您需要对您的应用访问进行白名单配置，具体请参见[设置白名单](/cn.zh-CN/微服务注册配置中心/Nacos/设置白名单.md)。

    MSE默认设置为127.0.0.1/32，表示禁止所有地址的访问。

-   支持哪些Spring Cloud版本？

    -   Spring Cloud Greenwich对应的Spring Cloud Alibaba版本为2.1.1.RELEASE。
    -   Spring Cloud Finchley对应的Spring Cloud Alibaba版本为 2.0.1.RELEASE。
    -   Spring Cloud Edgware对应的 Spring Cloud Alibaba版本为1.5.1.RELEASE。
    **说明：** Spring Cloud Edgware版本的生命周期已结束，不推荐使用这个版本开发应用。


