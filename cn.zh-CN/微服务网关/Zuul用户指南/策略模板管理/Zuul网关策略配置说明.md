# Zuul网关策略配置说明

Zuul类型网关支持路由、负载均衡、限流和鉴权等多种策略，为了帮助您更好的配置策略，本文对各种策略的配置进行说明。

## 路由-Zuul

路由配置兼容开源的Spring Cloud Netflix Zuul。更多信息，请参见[Router and Filter: Zuul](https://cloud.spring.io/spring-cloud-netflix/multi/multi__router_and_filter_zuul.html)。

## 负载均衡-Ribbon

负载均衡的配置兼容开源的Spring Cloud Netflix Ribbon。更多信息，请参见[Working with load balancers](https://github.com/Netflix/ribbon/wiki/Working-with-load-balancers)。

**说明：** 如果您已自建注册中心，例如Eureka，可以在控制台添加注册中心。具体操作，请参见[新建服务来源](/cn.zh-CN/微服务网关/Spring Cloud Gateway用户指南/服务来源管理/新建服务来源.md)。当注册中心中Server列表（格式为`IP:Port`）发生变更时，自动发布到网关生效。

## 限流-Sentinel

限流的配置部分兼容开源社区版Sentinel。目前只支持单机版限流，具体的配置解释如下：

```
sentinel:
  rules:
    - name: rule1
      path:
        - pattern: /bbbb
      count: 200
      interval: 10
    burst: 5
```

## 鉴权-JWT

使用JWT对Client请求鉴权时，请先在控制台创建凭证。具体操作，请参见[新建凭证](/cn.zh-CN/微服务网关/Spring Cloud Gateway用户指南/凭证管理/新建凭证.md)。生成鉴权策略需要使用的Client Token和Server Key，并将Client Token授予信任的服务调用方。

JWT配置除JWT根配置外，有providers和rules两个子节点。providers表示有哪些鉴权实体，rules表示如何判断某次请求需要进行鉴权。为了帮助您理解，下面以一个配置示例从鉴权的流程来解释两个配置的含义。

```
rules: // 表示匹配规则的合集。
    - match: // 表示一个匹配规则。
          path: /greeting // 具体匹配的路径，与Zuul中的path属性含义和判断方式相同。
      requires: // 表示匹配之后需要哪些鉴权实体实施鉴权。
          providerName: ticket_name // 鉴权实体的名字，与providers中的唯一名称对应，如果providers中不存在该名称的鉴权实体，直接判定鉴权失败，请求被block。

providers: // 表示鉴权实体的集合。
    ticketName: // 表示一个鉴权实体，名称唯一，与rules/requires/providerName对应。
      issuer: http://alibabacloud.com // JWT Client Token和Server Key的发布方，默认为alibabacloud。
      localJwks: PUBLIC-KEY // Server Key，通过控制台凭证管理生成，可以从控制台凭证详情中直接复制过来。
      fromHeaders: // 获取Client Token的Http Header属性，列表类型，如果为空，默认以Authorization:Bearer XXX形式获取。
        - jwt-assertion
        - jwt1-assertion
      fromParams: // 获取Client Token的Http Query Param属性，列表类型，如果为空，默认从access_token获取。
        - jwt_token
```

