# QueryMonitor

调用QueryMonitor接口查询监控信息。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|QueryMonitor|系统规定参数，取值：QueryMonitor。 |
|EndTime|Long|是|20210208|监控结束时间。 |
|InstanceId|String|是|mse-cn-\*\*\*\*|实例ID。 |
|MonitorType|String|是|TPS|监控类型如下：

 -   服务数
-   服务提供者数
-   写接口的平均请求耗时
-   读接口的平均请求耗时
-   TPS
-   QPS |
|StartTime|Long|是|20200207|监控开始时间。 |
|Step|Long|是|7|数据点间隔，单位：s。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|String|6|数据概览。 |
|ErrorCode|String|mse-100-000|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|ADDD8AB7-8D1C-4697-A83E-410D2607\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=QueryMonitor
&EndTime=20210208
&InstanceId=mse-cn-****
&MonitorType=TPS
&StartTime=20200207
&Step=7
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<QueryMonitorResponse>
  <RequestId>ADDD8AB7-8D1C-4697-A83E-410D2607****</RequestId>
  <Message>请求处理成功</Message>
  <Data>6</Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</QueryMonitorResponse>
```

`JSON`格式

```
{
    "RequestId": "ADDD8AB7-8D1C-4697-A83E-410D2607****",
    "Message": "请求处理成功",
    "Data": 6,
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

