# ListAlarmRules

调用ListAlarmRules接口获取告警规则清单。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=ListAlarmRules&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAlarmRules|系统规定参数，取值：ListAlarmRules。 |
|AlarmMseType|String|是|none|报警类型，多余参数。 |
|PageNum|Integer|是|1|页码。 |
|PageSize|Integer|是|10|每页展示实例数。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of AlarmRuleModel| |数据概览。 |
|AlarmName|String|test|报警名称。 |
|AlarmRuleDetail|String|报警规则：最近2分钟 集群服务数 总和小于等于1.0时触发报警！ 报警集群：mse-bc1a29b0-160230875\*\*\*\* 通知方式\(SMS=短信,DING\_ROBOT=钉钉,EMAIL=邮件\)：\[SMS\] 通知联系人分组：\["test"\]|报警规则的详细信息。 |
|AlarmRuleId|String|393\*\*\*\*|报警规则ID。 |
|AlarmStatus|String|RUNNING|报警状态，取值如下：

 -   RUNNING：运行成功。
-   ERROR：运行失败。 |
|CreateTime|String|2021-02-08 15:30:27|报警规则创建时间。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|10|每页展示实例数。 |
|RequestId|String|54973C90-F379-4372-9AA5-053A3F7\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|TotalCount|Integer|12|实例总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAlarmRules
&AlarmMseType=1
&PageNum=1
&PageSize=10
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListAlarmRulesResponse>
  <HttpCode>202</HttpCode>
  <TotalCount>12</TotalCount>
  <PageSize>10</PageSize>
  <Message>请求处理成功</Message>
  <RequestId>54973C90-F379-4372-9AA5-053A3F7****</RequestId>
  <PageNumber>1</PageNumber>
  <Data>
        <AlarmRuleId>393****</AlarmRuleId>
        <AlarmName>test</AlarmName>
        <AlarmRuleDetail>报警规则：最近2分钟 集群服务数 总和小于等于1.0时触发报警！ 报警集群：mse-bc1a29b0-160230875**** 通知方式(SMS=短信,DING_ROBOT=钉钉,EMAIL=邮件)：[SMS] 通知联系人分组：["test"]</AlarmRuleDetail>
        <CreateTime>2021-02-08 15:30:27</CreateTime>
        <AlarmStatus>RUNNING</AlarmStatus>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListAlarmRulesResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "TotalCount": 12,
    "PageSize": 10,
    "Message": "请求处理成功",
    "RequestId": "54973C90-F379-4372-9AA5-053A3F7****",
    "PageNumber": 1,
    "Data": {
        "AlarmRuleId": "393****",
        "AlarmName": "test",
        "AlarmRuleDetail": "报警规则：最近2分钟 集群服务数 总和小于等于1.0时触发报警！ 报警集群：mse-bc1a29b0-160230875**** 通知方式(SMS=短信,DING_ROBOT=钉钉,EMAIL=邮件)：[SMS] 通知联系人分组：[\"test\"]",
        "CreateTime": "2021-02-08 15:30:27",
        "AlarmStatus": "RUNNING"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

