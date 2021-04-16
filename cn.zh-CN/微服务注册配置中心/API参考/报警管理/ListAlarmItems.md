# ListAlarmItems

调用ListAlarmItems接口获取报警列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=ListAlarmItems&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAlarmItems|系统规定参数，取值：ListAlarmItems。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of AlarmItem| |数据概览。 |
|AlarmCode|String|MIN\_SINGLE\_CONNECTIONS\_ZOOKEEPER|报警响应码。 |
|AlarmDesc|String|单机最小链接数|报警规则描述。 |
|ClusterType|String|ZooKeeper|集群类型。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|10|每页展示实例数。 |
|RequestId|String|AF21683A-29C7-4853-AC0F-B5ADEE4D\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|TotalCount|Integer|7|实例总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAlarmItems
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListAlarmItemsResponse>
  <HttpCode>202</HttpCode>
  <TotalCount>7</TotalCount>
  <PageSize>10</PageSize>
  <Message>请求处理成功</Message>
  <RequestId>AF21683A-29C7-4853-AC0F-B5ADEE4D****</RequestId>
  <PageNumber>1</PageNumber>
  <Data>
        <AlarmDesc>单机最小链接数</AlarmDesc>
        <AlarmCode>MIN_SINGLE_CONNECTIONS_ZOOKEEPER</AlarmCode>
        <ClusterType>ZooKeeper</ClusterType>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListAlarmItemsResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "TotalCount": 7,
    "PageSize": 10,
    "Message": "请求处理成功",
    "RequestId": "AF21683A-29C7-4853-AC0F-B5ADEE4D****",
    "PageNumber": 1,
    "Data": {
        "AlarmDesc": "单机最小链接数",
        "AlarmCode": "MIN_SINGLE_CONNECTIONS_ZOOKEEPER",
        "ClusterType": "ZooKeeper"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

