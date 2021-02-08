# DeleteAlarmRule

调用DeleteAlarmRule接口删除报警规则。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteAlarmRule|系统规定参数，取值：DeleteAlarmRule。 |
|AlarmRuleId|String|是|393\*\*\*\*|报警规则ID。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|56D9E600-6348-4260-B35F-583413F\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteAlarmRule
&AlarmRuleId=393****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DeleteAlarmRuleResponse>
  <HttpCode>202</HttpCode>
  <RequestId>56D9E600-6348-4260-B35F-583413F****</RequestId>
  <Message>请求处理成功</Message>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</DeleteAlarmRuleResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "RequestId": "56D9E600-6348-4260-B35F-583413F****",
    "Message": "请求处理成功",
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

