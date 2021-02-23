# （不推荐）自建Nacos服务注册中心

本地开发的Spring Cloud应用或者Dubbo应用，除了可以使用MSE作为服务注册管理中心，也可以自建Nacos。本文以Provider和Conumser微服务应用Demo为例，指导您如何在单机上自建Nacos服务注册中心，并为应用提供服务注册功能。

-   已安装yum。
-   执行应用程序前，请确保您Nacos注册中心的访问端口（如8848）已添加至您的安全组。
-   下载的微服务应用Demo应用包：
    -   [Provider](https://aliware-images.oss-cn-hangzhou.aliyuncs.com/SAE/eureka-service-provider.zip?spm=a2c4g.11186623.2.17.73289506P2lAoA&file=eureka-service-provider.zip)
    -   [Conumser](https://aliware-images.oss-cn-hangzhou.aliyuncs.com/SAE/eureka-service-consumer.zip)

某创业公司现在有微服务众多应用，期望使用自建Nacos注册中心。

本文以Demo中的Provider和Consumer微服务应用为例，介绍如何在单机上自建Nacos服务注册中心；如果集群部署请参考[集群部署说明](https://nacos.io/zh-cn/docs/cluster-mode-quick-start.html)。

**说明：** 服务注册中心使用优先级：MSE的Nacos服务注册中心\>自建Nacos。不推荐使用自建Nacos，与MSE的Nacos服务注册中心相比，自建Nacos不仅需要购买各种搭建所需的资源，还需要投入人力进行维护，耗费资源，增加运维成本。

## 步骤一：环境准备

Nacos依赖Java环境来运行。如果您是从代码开始构建并运行Nacos，请确保是在以下版本环境中安装使用。

-   64 bit OS，支持Linux/Unix/Mac/Windows，推荐选用Linux/Unix/Mac。
-   64 bit JDK 1.8及以上版本。

1.  查询可安装的JDK。

    ```
    yum -y list java*
    ```

2.  安装JDK。

    ```
    yum install -y java-latest-openjdk-devel.x86_64
    ```

3.  配置JAVA\_HOME。

    ```
    export JAVA_HOME=jdk-install-dir
    
    export PATH=$JAVA_HOME/bin:$PATH
    ```


## 步骤二：Nacos安装

1.  下载Nacos。

    ```
    wget https://github.com/alibaba/nacos/releases/download/1.1.3/nacos-server-1.1.3.zip
    ```

2.  解压Nacos并进入nacos/bin文件。

    ```
    unzip nacos-server-1.1.3.zip
    cd nacos/bin
    ```

    **说明：** 如果服务器上没有Unzip工具，请执行`yum install unzip`，并在安装后键入Y。

    ![解压Nacos](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9616401161/p64903.png)

3.  启动Nacos。

    ```
    sh startup.sh -m standalone
    ```

    ![启动Nacos](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9616401161/p64904.png)


## 步骤三：服务注册与发现

Nacos启动后，提供了服务注册发现功能，需要在应用侧指定服务注册中心。在应用程序执行后，系统会依据所设服务注册中心，自动进行服务注册与发现。

**说明：** 执行应用程序前，请确保您Nacos注册中心的访问端口（如8848）已添加至您的安全组。

1.  在服务应用侧指定注册中心，并运行应用Provider和Consumer。

    打开`src\main\resources`路径下的文件`application.properties`，指定Nacos Server的IP地址。

    -   Provider

        修改前：

        ```
        spring.application.name=service-provider
        server.port=18081
        eureka.client.serviceUrl.defaultZone=http://127.0.0.1:8761/eureka/                            
        ```

        修改后

        ```
        spring.application.name=service-provider
        server.port=18081
        spring.cloud.nacos.discovery.server-addr=IP地址:8848                            
        ```

    -   Consumer

        修改前

        ```
        spring.application.name=service-consumer
        server.port=18082
        eureka.client.serviceUrl.defaultZone=http://127.0.0.1:8761/eureka/                            
        ```

        修改后

        ```
        spring.application.name=service-consumer
        server.port=18082
        spring.cloud.nacos.discovery.server-addr=IP地址:8848                            
        ```

2.  服务验证。

    -   Linux/Unix/Mac系统

        ```
        curl -X GET 'http://IP地址:8848/nacos/v1/ns/instance/list?serviceName=service-provider'
        ```

        `service-provider`为服务名。`IP地址:8848`为安装Nacos的主机IP地址。

        服务发现成功。

        ![SAE产品自建Nacos提供注册中心之Provider服务发现成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9616401161/p65846.png)

    -   Windows系统

        在浏览器中输入`http://c:18082/echo-rest/{自定义变量}`或`http://127.0.0.1:18082/echo-feign/{自定义变量}`。

        当出现类似下图页面表示服务注册、发现成功。

        ![SAE产品自建Nacos提供注册中心](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9616401161/p65298.png)

        `127.0.0.1：18082`为运行Provider和Consumer的主机IP地址和访问端口。


