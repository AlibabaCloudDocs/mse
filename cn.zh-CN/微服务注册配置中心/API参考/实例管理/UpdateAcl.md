# UpdateAcl

调用UpdateAcl接口修改白名单。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateAcl|系统规定参数，取值：UpdateAcl。 |
|AclEntryList|String|是|192.168.0.0/XX,192.168.0.0/XX|白名单列表。 |
|InstanceId|String|是|mse-cn-78v1l83\*\*\*\*|实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ErrorCode|String|mse-100-100|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|7466566F-F30F-4A29-965D-3E0AF21D\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateAcl
&AclEntryList=192.168.0.0/XX,192.168.0.0/XX
&InstanceId=mse-cn-78v1l83****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateAclResponse>
  <Message>请求处理成功</Message>
  <RequestId>7466566F-F30F-4A29-965D-3E0AF21D****</RequestId>
  <ErrorCode>mse-100-100</ErrorCode>
  <Success>true</Success>
</UpdateAclResponse>
```

`JSON`格式

```
{
    "Message": "请求处理成功",
    "RequestId": "7466566F-F30F-4A29-965D-3E0AF21D****",
    "ErrorCode": "mse-100-100",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

