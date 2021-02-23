---
keyword: [微服务, 服务发现]
---

# MSE微服务注册配置中心使用说明

为了方便您更好的使用MSE，您可以预先了解MSE实例创建时的注意事项、Spring Could应用和Dubbo应用开发时的服务注册中心配置代码等。

## 创建实例

在创建MSE实例过程中，配置网络类型、地域和公网宽带时需要注意以下事项：

-   网络类型
    -   专有网络：MSE实例创建过程中所选择VPC须与应用所在的ECS的VPC一致。
    -   公网网络：如果您的应用有公网访问需求，那么需要设置白名单，格式为ECS 公网 IP 地址/32，具体操作请参见[设置白名单](/cn.zh-CN/微服务注册配置中心/Nacos/设置白名单.md)。
-   地域

    如果您应用选择专有网络，那么MSE实例创建过程中所选地域须与应用所在的ECS地域一致。

-   公网宽带

    如果您的应用有公网访问需求，那么购买时您需要设置公网带宽。只有公网带宽大于0时，才会生成公网域名。


![MSE服务购买示例图](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3781309951/p95857.png)

## 注册中心的使用

MSE支持Nacos、Eureka和Zookeeper等多种服务注册中心供您的Spring Cloud和Dubbo应用使用。

**Nacos**

-   Spring Cloud应用使用MSE的Nacos注册中心

    ```
    spring.application.name=service-provider
    server.port=18081
    spring.cloud.nacos.discovery.server-addr=mse.XX.nacos.mse.aliyuncs.com:8848
    #其中mse.XX.nacos.mse.aliyuncs.com为MSE上创建的Nacos实例的外网访问地址。
    #如果要使用自己创建的命名空间可以使用下面的配置。
    #spring.cloud.nacos.discovery.namespace=11a8ca4c-xxx-xxx-xxx-6aad4dab92a9
    ```

-   Dubbo应用使用MSE的Nacos注册中心
    -   通过xml方式

        ```
        <dubbo:application name="demo-provider"/>
        <dubbo:protocol name="dubbo" port="28082" />
        <dubbo:service interface="com.alibaba.dubbo.api.IHelloService" ref="helloService"/>
        <bean id="helloService" class="com.alibaba.dubbo.service.impl.IHelloServiceImpl"/>
        <dubbo:registry address="nacos://mse-XX-p.nacos-ans.mse.aliyuncs.com:8848"/>
        #其中mse.XX.nacos.mse.aliyuncs.com为MSE上创建的Nacos实例的外网访问地址。
        #如果要使用自己创建的命名空间可以使用下面的配置。
        #<dubbo:registry address="nacos://mse-XX.nacos-ans.mse.aliyuncs.com:8848?namespace=d5cbb70a5-xxx-xxx-84c1-d43479ae0932"/>
        ```

    -   通过properties方式

        ```
        dubbo.application.name=dubbo-consumer-demo
        server.port=8080
        dubbo.registry.address=nacos://mse-XX-p.nacos-ans.mse.aliyuncs.com:8848
        #其中mse.XX.nacos.mse.aliyuncs.com为MSE上创建的Nacos实例的外网访问地址。
        #如果要使用自己创建的命名空间可以使用下面的配置。
        dubbo.registry.parameters.namespace=5cbb70a5-xxx-xxx-xxx-d43479ae0932
        ```

        ```
        <dubbo:application name="demo-provider"/>
          <dubbo:protocol name="dubbo" port="28082" />
           <dubbo:service interface="com.alibaba.dubbo.api.IHelloService" ref="helloService"/>
           <bean id="helloService" class="com.alibaba.dubbo.service.impl.IHelloServiceImpl"/>
           <dubbo:registry address="nacos://mse-XX-p.nacos-ans.mse.aliyuncs.com:8848"/>
        ```


**ZooKeeper**

-   Spring Cloud应用使用MSE的Zookeeper注册中心

    ```
    spring:
      application:
        name: demo-provider
      cloud:
        zookeeper:
          connect-string: mse-XX-p.nacos-ans.mse.aliyuncs.com:2181
          discovery:
            enabled: true
    ```

-   Dubbo应用使用MSE的Zookeeper注册中心

    ```
    <dubbo:registry address="zookeeper://mse-XX-p.nacos-ans.mse.aliyuncs.com:2181" />
    ```


**Eureka**

Spring Cloud应用使用MSE的Eureka注册中心

```
server:
  port: 8080
spring:
  application:
    name: demo-provider
eureka:
  client:
    serviceUrl:
      defaultZone: http://mse-XXX-p.eureka.mse.aliyuncs.com:8761/eureka
  instance:
    prefer-ip-address: true
```

## 排查Nacos注册中心异常

在使用MSE的Nacos注册中心时，如果遇到异常，那么您可以查看注册中心客户端日志，其路径为`${user.home}/logs/nacos/naming.log`。

