# UpdateConfig

调用UpdateConfig接口更新配置。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=UpdateConfig&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateConfig|系统规定参数。取值：UpdateConfig。 |
|AutopurgePurgeInterval|String|是|none|保留字段。 |
|AutopurgeSnapRetainCount|String|是|none|保留字段。 |
|ClusterId|String|是|mse-09k1q11\*\*\*\*|集群ID。 |
|ConfigType|String|是|TEXT|配置格式，包括TEXT、JSON、XML、HTML等。 |
|InitLimit|String|是|100|实例最长连接时间，单位：秒。 |
|JuteMaxbuffer|String|是|1|每个节点最大数据量，默认是1M，单位：字节。 |
|MaxClientCnxns|String|是|0|单个客户端与单台服务器之间的连接数。

 如果设置为0，表示不作任何限制。 |
|OpenSuperAcl|String|是|true|超级权限开关，取值如下：

 -   `true`：打开
-   `false`：关闭 |
|SyncLimit|String|是|10|实例连接超时时间，单位：秒。 |
|TickTime|String|是|2000|ZooKeeper引擎中的一个时间单元，默认为2000毫秒。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |
|UserName|String|否|name|用户名称。 |
|PassWord|String|否|password|用户密码。 |
|ConfigAuthEnabled|Boolean|否|true|配置是否生效，取值如下：

 -   `true`：生效
-   `false`：未生效 |
|MCPEnabled|Boolean|否|true|MCP是否生效，取值如下：

 -   `true`：生效
-   `false`：不生效 |
|InstanceId|String|否|mse\_prepaid\_public\_cn-st2212\*\*\*\*|实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ErrorCode|String|mse-100-100|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|8BD1E58D-0755-42AC-A599-E6B55112\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateConfig
&AutopurgePurgeInterval=none
&AutopurgeSnapRetainCount=none
&ClusterId=mse-09k1q11****
&ConfigType=TEXT
&InitLimit=100
&JuteMaxbuffer=1
&MaxClientCnxns=0
&OpenSuperAcl=true
&SyncLimit=10
&TickTime=2000
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateConfigResponse>
  <RequestId>CB889254-0C8B-49B2-8465-4CDAB08A****</RequestId>
  <Message>请求处理成功</Message>
  <ErrorCode>mse-100-100</ErrorCode>
  <Success>true</Success>
</UpdateConfigResponse>
```

`JSON`格式

```
{
    "RequestId": "CB889254-0C8B-49B2-8465-4CDAB08A****",
    "Message": "请求处理成功",
    "ErrorCode": "mse-100-100",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

