# QueryConfig

调用QueryConfig接口查询接口配置。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|QueryConfig|系统规定参数，取值：QueryConfig。 |
|ClusterId|String|是|mse-09k1q11\*\*\*\*|集群ID。 |
|ConfigType|String|是|TEXT|配置格式，包括TEXT、JSON、XML、HTML等。 |
|InstanceId|String|是|mse\_prepaid\_public\_cn-st2212\*\*\*\*|实例ID。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |数据概览。 |
|AutopurgePurgeInterval|String|none|保留字段。 |
|AutopurgeSnapRetainCount|String|none|保留字段。 |
|ClusterName|String|name|集群名称 |
|ConfigAuthEnabled|Boolean|true|配置是否生效，取值如下：

 -   `true`：生效
-   `false`：未生效 |
|ConfigAuthSupported|Boolean|true|配置是否支持，取值如下：

 -   `true`：支持
-   `false`：不支持 |
|InitLimit|String|100|实例最长连接时间，单位：秒。 |
|JuteMaxbuffer|String|1|每个节点最大数据量，默认是1M，单位：字节。 |
|JvmFlagsCustom|String|none|自定义JVM参数。 |
|MCPEnabled|Boolean|true|MCP是否生效，取值如下：

 -   `true`：生效
-   `false`：不生效 |
|MCPSupported|Boolean|true|MCP是否支持，取值如下：

 -   `true`：支持
-   `false`：不支持 |
|MaxClientCnxns|String|0|单个客户端与单台服务器之间的连接数。

 如果设置为0，表示不作任何限制。 |
|OpenSuperAcl|Boolean|true|超级权限开关，取值如下：

 -   `true`：打开
-   `false`：关闭 |
|PassWord|String|password|用户密码。 |
|RestartFlag|Boolean|true|重启配置，取值如下：

 -   `true`：重启成功。
-   `false`：重启失败。 |
|SyncLimit|String|10|实例连接超时时间，单位：秒。 |
|TickTime|String|2000|ZooKeeper引擎中的一个时间单元，默认为2000毫秒。 |
|UserName|String|name|用户名称。 |
|ErrorCode|String|mse-100-100|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|8BD1E58D-0755-42AC-A599-E6B55112EC53|请求ID。 |
|Success|String|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=QueryConfig
&ClusterId=mse-09k1q11****
&ConfigType=TEXT
&InstanceId=mse_prepaid_public_cn-st2212****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<QueryConfigResponse>
  <Message>请求处理成功</Message>
  <RequestId>8BD1E58D-0755-42AC-A599-E6B55112EC53</RequestId>
  <Data>
        <MCPEnabled>true</MCPEnabled>
        <MaxClientCnxns>0</MaxClientCnxns>
        <UserName>name</UserName>
        <OpenSuperAcl>true</OpenSuperAcl>
        <TickTime>2000</TickTime>
        <AutopurgeSnapRetainCount>none</AutopurgeSnapRetainCount>
        <PassWord>password</PassWord>
        <InitLimit>100</InitLimit>
        <ConfigAuthEnabled>true</ConfigAuthEnabled>
        <JvmFlagsCustom>none</JvmFlagsCustom>
        <RestartFlag>true</RestartFlag>
        <AutopurgePurgeInterval>none</AutopurgePurgeInterval>
        <JuteMaxbuffer>1</JuteMaxbuffer>
        <MCPSupported>true</MCPSupported>
        <ClusterName>name</ClusterName>
        <ConfigAuthSupported>true</ConfigAuthSupported>
        <SyncLimit>10</SyncLimit>
  </Data>
  <ErrorCode>mse-100-100</ErrorCode>
  <Success>true</Success>
</QueryConfigResponse>
```

`JSON`格式

```
{
    "Message": "请求处理成功",
    "RequestId": "8BD1E58D-0755-42AC-A599-E6B55112EC53",
    "Data": {
        "MCPEnabled": true,
        "MaxClientCnxns": 0,
        "UserName": "name",
        "OpenSuperAcl": true,
        "TickTime": 2000,
        "AutopurgeSnapRetainCount": "none",
        "PassWord": "password",
        "InitLimit": 100,
        "ConfigAuthEnabled": true,
        "JvmFlagsCustom": "none",
        "RestartFlag": true,
        "AutopurgePurgeInterval": "none",
        "JuteMaxbuffer": 1,
        "MCPSupported": true,
        "ClusterName": "name",
        "ConfigAuthSupported": true,
        "SyncLimit": 10
    },
    "ErrorCode": "mse-100-100",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

