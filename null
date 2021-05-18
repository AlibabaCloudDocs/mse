# Kong网关策略配置说明

微服务网关的Kong类型网关完全兼容开源Kong网关的所有策略，如路由、负载均衡、流量控制、安全和日志策略等。为了帮助您更好的配置策略，本文对各种策略的配置进行说明。

## 路由-KONG\_ROUTE

每个路由都与一个服务关联，一个服务可能具有多个与其关联的路由。路由策略中定义规则以匹配客户端请求，匹配到路由策略的请求都将被转发到其关联的服务。

此处仅介绍KONG\_ROUTE策略的关键属性，更多关于KONG\_ROUTE策略的介绍，请参见[Route Object](https://docs.konghq.com/2.1.x/admin-api/#route-object)。

|属性|描述|
|--|--|
|name|路由的名称。|
|protocols|允许的协议列表，默认值为HTTP和HTTPS。|
|methods|允许的HTTP请求方法，默认值为GET和POST。|
|hosts|匹配的域名列表。|
|paths|配的路径列表。|
|headers|匹配的请求头列表。|
|service|关联的服务。|

## 负载均衡-KONG\_LOADBALANCE

通过此策略可以实现多个请求的负载均衡处理。

此处仅介绍KONG\_LOADBALANCE策略的关键属性，更多关于KONG\_LOADBALANCE策略属性介绍，请参见[Upstream Object](https://docs.konghq.com/2.1.x/admin-api/#upstream-object)。

|属性|描述|
|--|--|
|services.name|服务名。|
|services.host|服务所在IP地址或者域名，也可已设置为关联服务的服务名称。|
|upstreams.name|设置为关联服务的服务名称。|

## 安全-KONG\_CORS

通过此策略可以实现将跨域资源共享添加到路由。

此处仅介绍KONG\_CORS策略的关键属性，更多关于KONG\_CORS策略属性介绍，请参见[CORS](https://docs.konghq.com/hub/kong-inc/cors/)。

|属性|描述|
|--|--|
|name|插件名称，固定为cors。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.origins|允许的域列表，如果允许所有来源，此属性配置为通配符（\*）。|
|config.methods|允许的HTTP请求方式，默认为GET和POST。|
|config.headers|允许的请求头。|

## 安全-KONG\_IP\_RESTRICTION

通过此策略可以实现允许或拒绝IP地址对路由的访问，支持IPv4和IPv6网段。

此处仅介绍KONG\_IP\_RESTRICTION策略的关键属性，更多关于KONG\_IP\_RESTRICTION策略属性介绍，请参见[IP Restriction](https://docs.konghq.com/hub/kong-inc/ip-restriction/)。

|属性|描述|
|--|--|
|name|插件名称，固定为ip-restriction。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.allow|允许访问的IP或者网段。**说明：** 允许属性和拒绝属性两者至少配置一项。 |
|config.deny|拒绝访问的IP或者网段。**说明：** 允许属性和拒绝属性两者至少配置一项。 |

## 流量控制-KONG\_PROXY\_CACHE

通过此策略实现反向代理缓存，根据配置的响应码、内容类型和请求方法来缓存响应实体。缓存实体将存储一段可配置的时间，在此之后。对同一资源的请求将重新获取并存储。

此处仅介绍KONG\_PROXY\_CACHE策略的关键属性，更多关于KONG\_PROXY\_CACHE策略属性介绍，请参见[Proxy Cache](https://docs.konghq.com/hub/kong-inc/proxy-cache/)。

|属性|描述|
|--|--|
|name|插件名称，固定为proxy-cache。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|enabled|是否启用proxy-cache插件，默认为true。|
|config.response\_code|可缓存的上游响应状态码，默认值200、302和404。|
|config.request\_methed|可缓存的下游请求方式，默认值为GET和POST。|
|config.content\_type|可缓存的上游响应内容类型，默认值test/plain。|
|config.cache\_ttl|以秒为单位的缓存实体时间，默认值500。|
|config.strategy|支持缓存实体的备份数据存储，固定为memory。|

## 流量控制-KONG\_REQUEST\_SIZE\_LIMIT

通过此策略实现阻止请求主体大于配置阈值的请求。

此处仅介绍KONG\_REQUEST\_SIZE\_LIMIT策略的关键属性，更多关于KONG\_REQUEST\_SIZE\_LIMIT策略属性介绍，请参见[Request Size Limiting](https://docs.konghq.com/hub/kong-inc/request-size-limiting/)。

|属性|描述|
|--|--|
|name|插件名称，固定为request-size-limiting。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.allowed\_payload\_size|允许的请求主体最大值（以兆字节为单位），默认为128。|
|config.size\_unit|单位，默认值为megabytes，可设置为bytes、kilobytes和megabytes。|

## 流量控制-KONG\_RATE\_LIMIT

通过该策略实现限制在配置的时间内可以发出的HTTP请求数量。

此处仅介绍KONG\_RATE\_LIMIT策略的关键属性，更多关于KONG\_RATE\_LIMIT策略属性介绍，请参见[Rate Limiting](https://docs.konghq.com/hub/kong-inc/rate-limiting/)。

|属性|描述|
|--|--|
|name|插件名称，固定为rate-limiting。|
|service|插件作用的目标，可以是route、service或者cosumer，此策略以service为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.second|每秒可以发出的HTTP请求数。**说明：** 每秒请求数或者每小时请求数至少设置一个。 |
|config.hour|每小时可以发出的HTTP请求数。**说明：** 每秒请求数或者每小时请求数至少设置一个。 |

## 流量控制-KONG\_RESPONSE\_RATE\_LIMIT

通过该策略实现根据上游服务响应头设置自定义限速对象，来限制在配置的时间内可以发出的HTTP请求数量。

此处仅介绍KONG\_RESPONSE\_RATE\_LIMIT策略的关键属性，更多关于KONG\_RESPONSE\_RATE\_LIMIT策略属性介绍，请参见[Response Rate Limiting](https://docs.konghq.com/hub/kong-inc/response-ratelimiting/)。

|属性|描述|
|--|--|
|name|插件名称，固定为response-ratelimiting。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.limits.\{limit\_name\}|根据上游服务返回的响应头设置的自定义对象列表，在\{limit\_name\}占位符中设置名称。|
|config.limits.\{limit\_name\}.minute|每分钟可以发出的HTTP请求数。|

## 流量控制-KONG\_REQUEST\_TERMINATION

通过该策略实现使用指定的状态码和消息终止请求。

此处仅介绍KONG\_REQUEST\_TERMINATION策略的关键属性，更多关于KONG\_REQUEST\_TERMINATION策略属性介绍，请参见[Request Termination](https://docs.konghq.com/hub/kong-inc/request-termination/)。

|属性|描述|
|--|--|
|name|插件名称，固定为request-termination。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.status\_code|发送的状态码，默认值为403。|
|config.message|发送的信息。|

## 监控-KONG\_DATADOG

通过该策略实现服务数据路由到本地代理。

此处仅介绍KONG\_DATADOG策略的关键属性，更多关于KONG\_DATADOG策略属性介绍，请参见[Datadog](https://docs.konghq.com/hub/kong-inc/datadog/#metrics)。

|属性|描述|
|--|--|
|name|插件名称，固定为datadog。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.host|数据发送到的IP地址或主机名。|
|config.port|数据发送到的服务器端口。|

## 监控-KONG\_ZIPKIN

通过该策略实现分布式跟踪HTTP请求的范围，并将范围上报给Zipkin服务器。

此处仅介绍KONG\_ZIPKIN策略的关键属性，更多关于KONG\_ZIPKIN策略属性介绍，请参见[Zipkin](https://docs.konghq.com/hub/kong-inc/zipkin/)。

|属性|描述|
|--|--|
|name|插件名称，固定为zipkin。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.http\_endpoint|Zipkin服务器上传路径。|
|config.traceid\_byte\_count|每个请求的traceid字节长度。|

## 协议-KONG\_CERTIFICATE

通过该策略解密进入流量的HTTPS，并添加访问上游流量的HTTPS信任证书。

此处仅介绍KONG\_CERTIFICATE策略的关键属性，更多关于KONG\_CERTIFICATE策略属性介绍，请参见[Certificate Object](https://docs.konghq.com/2.1.x/admin-api/#certificate-object)。

|属性|描述|
|--|--|
|certificates.cert|用于解密进入流量的HTTPS的公共证书。|
|certificates.key|用于解密进入流量的HTTPS的私钥。|
|ca\_certificates.cert|添加访问上游流量的HTTPS的信任证书。|

## 编辑-KONG\_CORRELATION\_ID

通过该策略实现通过HTTP header传输的唯一ID关联请求和响应。

此处仅介绍KONG\_CORRELATION\_ID策略的关键属性，更多关于KONG\_CORRELATION\_ID策略属性介绍，请参见[Correlation ID](https://docs.konghq.com/hub/kong-inc/correlation-id/)。

|属性|描述|
|--|--|
|name|插件名称，固定为correlation-id。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.header\_name|HTTP header名称。|

## 编辑-KONG\_REQUEST\_TRANSFORMER

通过该策略实现请求在到达上游服务器之前进行转换。这些转换可以是简单的替换，也可以是复杂的转换，通过使用正则表达式匹配请求的各个部分，将匹配的字符串保存到变量中，然后使用模板将这些字符串替换为转换后的请求。

此处仅介绍KONG\_REQUEST\_TRANSFORMER策略的关键属性，更多关于KONG\_REQUEST\_TRANSFORMER策略属性介绍，请参见[Request Transformer](https://docs.konghq.com/hub/kong-inc/request-transformer/)。

|属性|描述|
|--|--|
|name|插件名称，固定为request-transformer。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.remove.headers|HTTP header名称列表，取消设置具有指定名称的字符串。|
|config.replace.body|成对取值的字符串，用新值替换旧值。|

## 编辑-KONG\_RESPONSE\_TRANSFORMER

通过该策略实现在响应返回客户端之前，将上游服务器发送的响应进行转换。

此处仅介绍KONG\_RESPONSE\_TRANSFORMER策略的关键属性，更多关于KONG\_RESPONSE\_TRANSFORMER策略属性介绍，请参见[Response Transformer](https://docs.konghq.com/hub/kong-inc/response-transformer/)。

|属性|描述|
|--|--|
|name|插件名称，固定为response-transformer。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.remove.headers|HTTP header名称列表，取消设置具有指定名称的字符串。|
|config.add.json|成对取值的字符串，当该属性不存在时，将给定值添加到字符串。|

## 日志-KONG\_HTTPLOG

通过该策略实现将请求和响应日志发送到HTTP服务器。

此处仅介绍KONG\_HTTPLOG策略的关键属性，更多关于KONG\_HTTPLOG策略属性介绍，请参见[HTTP Log](https://docs.konghq.com/hub/kong-inc/http-log/)。

|属性|描述|
|--|--|
|name|插件名称，固定为http-log。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.http\_endpoint|请求和响应日志需要发送到的HTTP端点。|

## 日志-KONG\_LOGGLY

通过该策略实现将请求和响应日志发送到Loggly服务器。

此处仅介绍KONG\_LOGGLY策略的关键属性，更多关于KONG\_LOGGLY策略属性介绍，请参见[Loggly](https://docs.konghq.com/hub/kong-inc/loggly/)。

|属性|描述|
|--|--|
|name|插件名称，固定为loggly。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.host|Loggly服务器的IP地址或主机名。|
|config.key|Loggly客户令牌。|

## 日志-KONG\_STATSD

通过该策略实现将请求和响应日志发送到StatsD服务器。

此处仅介绍KONG\_STATSD策略的关键属性，更多关于KONG\_STATSD策略属性介绍，请参见[StatsD](https://docs.konghq.com/hub/kong-inc/statsd/)。

|属性|描述|
|--|--|
|name|插件名称，固定为statsd。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.host|StatsD服务器的IP地址或主机名。|

## 日志-KONG\_TCPLOG

通过该策略实现将请求和响应日志发送到TCP服务器。

此处仅介绍KONG\_TCPLOG策略的关键属性，更多关于KONG\_TCPLOG策略属性介绍，请参见[TCP Log](https://docs.konghq.com/hub/kong-inc/tcp-log/)。

|属性|描述|
|--|--|
|name|插件名称，固定为tcp-log。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.host|TCP服务器的IP地址或主机名。|

## 日志-KONG\_UPDLOG

通过该策略实现将请求和响应日志发送到UDP服务器。

此处仅介绍KONG\_UPDLOG策略的关键属性，更多关于KONG\_UPDLOG策略属性介绍，请参见[UDP Log](https://docs.konghq.com/hub/kong-inc/udp-log/)。

|属性|描述|
|--|--|
|name|插件名称，固定为udp-log。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.host|UDP服务器的IP地址或主机名。|

## 鉴权-KONG\_JWT

通过该策略实现验证请求是否包含JWT Token，只有通过验证的请求，才会转发到上游服务。

此处仅介绍KONG\_JWT策略的关键属性，更多关于KONG\_JWT策略属性介绍，请参见[JWT](https://docs.konghq.com/hub/kong-inc/jwt/)。

|属性|描述|
|--|--|
|name|插件名称，固定为jwt。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|consumer.rsa\_public\_key|如果algorithm设置为RS256时，该参数用于验证Token签名的公共密钥。|
|consumer.algorithm|用于验证Token签名的算法，默认值为RS256，可设置为RS256、RS384、RS512、HS256、HS384和HS512。|

## 鉴权-KONG\_BASIC

通过该策略根据添加用户名和密码实现基本身份验证。

此处仅介绍KONG\_BASIC策略的关键属性，更多关于KONG\_BASIC策略属性介绍，请参见[Basic Authentication](https://docs.konghq.com/hub/kong-inc/basic-auth/)。

|属性|描述|
|--|--|
|name|插件名称，固定为basic-auth。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|basicauth\_credentials.username|用户名。|
|basicauth\_credentials.password|密码。|

## 鉴权-KONG\_KEY

通过该策略根据添加密钥实现身份验证。

此处仅介绍KONG\_KEY策略的关键属性，更多关于KONG\_KEY策略属性介绍，请参见[Key Authentication](https://docs.konghq.com/hub/kong-inc/key-auth/)。

|属性|描述|
|--|--|
|name|插件名称，固定为key-auth。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|keyauth\_credentials.key|设置唯一的key验证客户端，如果未设置，自动生成。|

## 鉴权-KONG\_LDAP

通过该策略根据添加LDAP信息实现绑定身份验证。

此处仅介绍KONG\_LDAP策略的关键属性，更多关于KONG\_LDAP策略属性介绍，请参见[LDAP Authentication](https://docs.konghq.com/hub/kong-inc/ldap-auth/)。

|属性|描述|
|--|--|
|name|插件名称，固定为ldap-auth。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|config.ldap\_host|LDAP服务器ID或者域名。|
|config.ldap\_port|LDAP服务器端口。|

## 鉴权-KONG\_HMAC

通过该策略根据添加HMAC签名身份验证，以建立传入请求的完成性。

此处仅介绍KONG\_HMAC策略的关键属性，更多关于KONG\_HMAC策略属性介绍，请参见[HMAC Authentication](https://docs.konghq.com/hub/kong-inc/hmac-auth/)。

|属性|描述|
|--|--|
|name|插件名称，固定为hmac-auth。|
|route|插件作用的目标，可以是route、service或者cosumer，此策略以route为例。如果不指定目标，则视为全局生效，作用到每个请求。 |
|hmacauth\_credentials.username|在HMAC签名验证中使用的用户名。|

