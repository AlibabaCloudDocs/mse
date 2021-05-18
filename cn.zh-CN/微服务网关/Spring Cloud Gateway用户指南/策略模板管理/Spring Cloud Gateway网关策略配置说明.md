# Spring Cloud Gateway网关策略配置说明

微服务网关的Spring Cloud Gateway类型网关完全兼容开源Spring Cloud Gateway网关的所有策略，如路由、插件、客户端、熔断、负载均衡和限流等。为了帮助您更好地配置策略，本文对该网关的各种策略配置进行说明。

## 路由-SCG\_ROUTE

Spring Cloud Gateway将路由作为Spring WebFlux基础架构的一部分进行匹配。Spring Cloud Gateway包括许多内置的路由谓词。所有这些谓词都与HTTP请求的不同属性匹配。您可以将多个路由谓词与逻辑and语句结合使用。

此处仅介绍SCG\_ROUTE策略的关键属性，更多关于SCG\_ROUTE策略的介绍，请参见[Route Predicate Factories](https://docs.spring.io/spring-cloud-gateway/docs/2.2.5.RELEASE/reference/html/#gateway-request-predicates-factories)。

|属性|描述|
|--|--|
|routes|动态路由前缀。|
|id|服务ID。|
|uri|访问路径URL。|
|order|加载规则。|
|predicates|断言。|
|filters|插件。|

## 插件-SCG\_DEFAULT\_FILTER

您可使用该策略添加过滤器并将其应用于所有路由。

此处仅介绍SCG\_DEFAULT\_FILTER策略的关键属性，更多关于SCG\_DEFAULT\_FILTER策略的介绍，请参见[Default Filters](https://docs.spring.io/spring-cloud-gateway/docs/2.2.5.RELEASE/reference/html/#default-filters)。

|属性|描述|
|--|--|
|gateway|DEFAULT\_FILTER前缀。|
|default-filters|配置默认过滤器。|

## 插件-SCG\_FILTER\_OPTIONS

该策略为原始响应添加了一系列起安全作用的响应头，如果您想修改这些Header的值，那么就需要使用这些Headers对应的后缀。

此处仅介绍SCG\_FILTER\_OPTIONS策略的关键属性，更多关于SCG\_FILTER\_OPTIONS策略的介绍，请参见[The SecureHeaders Factory](https://docs.spring.io/spring-cloud-gateway/docs/2.2.5.RELEASE/reference/html/#the-secureheaders-gatewayfilter-factory)。

|属性|描述|
|--|--|
|secure-headers|FILTER\_OPTIONS策略前缀。|
|content-type-options|如果从script或stylesheet读入的文件的MIME类型与指定MIME类型不匹配，不允许读取该文件。用于防止XSS等跨站脚本攻击。|
|download-options|用于放置用户下载文件。|
|request-rate-limiter|限制用户访问速率。|

## 安全-SCG\_CORS

您可以配置网关以控制CORS行为。全局CORS配置是URL模式到[CorsConfiguration](https://docs.spring.io/spring/docs/5.0.x/javadoc-api/org/springframework/web/cors/CorsConfiguration.html)的映射。

此处仅介绍SCG\_CORS策略的关键属性，更多关于SCG\_CORS策略属性介绍，请参见[CORS Configuration](https://docs.spring.io/spring-cloud-gateway/docs/2.2.5.RELEASE/reference/html/#cors-configuration)。

|属性|描述|
|--|--|
|globalcors|CORS策略前缀。|
|cors-configurations|CORS策略属性配置。|
|allowedOrigins|允许跨域的源（网站域名/IP），设置\*为全部。|
|allowedMethods|允许跨域的method，默认为GET和OPTIONS，设置\*为全部。|

## 客户端-SCG\_HTTP\_CLIENT

您可以使用该策略为网关配置一组可以信任的已知证书。

此处仅介绍SCG\_HTTP\_CLIENT策略的关键属性，更多关于SCG\_HTTP\_CLIENT策略属性介绍，请参见[TSL and SSL](https://docs.spring.io/spring-cloud-gateway/docs/2.2.5.RELEASE/reference/html/#tls-and-ssl)。

|属性|描述|
|--|--|
|httpclient|HTTP\_CLIENT策略前缀。|
|trustedX509Certificates|配置可信的X509证书。|

## 熔断-SCG\_HYSTRIX

您可以使用该策略为路由设置熔断策略。

此处仅介绍SCG\_HYSTRIX策略的关键属性，更多关于SCG\_HYSTRIX策略属性介绍，请参见[The Hystrix Factory](https://docs.spring.io/spring-cloud-gateway/docs/2.2.5.RELEASE/reference/html/#hystrix)。

|属性|描述|
|--|--|
|hystrix|HYSTRIX策略前缀。|
|timeoutInMilliseconds|超时时间，默认10000，单位：ms。|

## 限流-SCG\_REDIS\_RATE\_LIMITER

该策略基于[Stripe](https://stripe.com/blog/rate-limiters)工作，需要使用Spring Boot启动器，限制用户访问请求速率。

此处仅介绍SCG\_REDIS\_RATE\_LIMITER策略的关键属性，更多关于SCG\_REDIS\_RATE\_LIMITER策略属性介绍，请参见[The Redis](https://docs.spring.io/spring-cloud-gateway/docs/2.2.5.RELEASE/reference/html/#the-redis-ratelimiter)。

|属性|描述|
|--|--|
|redis\_rate\_limiter|REDIS\_RATE\_LIMITER策略前缀。|
|burst-capacity-header|允许用户每秒钟内执行的最大请求数。当此值设置为零时表示阻止所有请求。|
|remaining-header|剩余消息固定头部。|
|replenish-rate-header|允许用户每秒发送的请求数。|
|requested-tokens-header|允许用户每个请求从存储桶中提取的令牌数。|

## 负载均衡-SCG\_RIBBON

Ribbon策略是客户端负载平衡器，可让您对HTTP和TCP客户端的行为进行控制。

此处仅介绍SCG\_RIBBON策略的关键属性，更多关于SCG\_RIBBON策略属性介绍，请参见[Working with load balancers](https://github.com/Netflix/ribbon/wiki/Working-with-load-balancers?spm=a2c4g.11186623.2.16.3fd678c0sqm0jd)。

|属性|描述|
|--|--|
|ribbon|RIBBON策略前缀。|
|NIWSServerListClassName|ServerList接口实现类。|
|listOfServers|服务后端节点。|
|ConnectTimeout|建立连接所用的时间，默认1000，单位：ms。|
|ReadTimeout|建立连接后从服务器读取到可用资源所用的时间，默认3000，单位：ms。|
|MaxTotalHttpConnections|最大HTTP连接数，默认500。|
|MaxConnectionsPerHost|每个host连接数，默认100。|

