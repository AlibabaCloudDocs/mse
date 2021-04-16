# ListEurekaServices

调用ListEurekaServices接口查看Eureka服务详情。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=ListEurekaServices&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListEurekaServices|系统规定参数，取值：ListEurekaServices。 |
|ClusterId|String|是|mse-09k1q11\*\*\*\*|集群ID。 |
|PageNum|Integer|是|1|页码。 |
|PageSize|Integer|是|10|每页展示实例数。 |
|RegionId|String|是|cn-hangzhou|地域ID。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of SimpleService| |数据概览。 |
|InstancesId|List|mse-cn-st21ri2\*\*\*\*|实例ID。 |
|Name|String|CONTACTINFO|服务名称。 |
|UpStatus|String|1/1|服务提供者数量，健康实例数/总实例数。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|10|每页展示实例数。 |
|RequestId|String|316F5F64-F73D-42DC-8632-01E308B6\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|TotalCount|Integer|7|实例总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListEurekaServices
&ClusterId=mse-09k1q11****
&PageNum=1
&PageSize=10
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListEurekaServicesResponse>
  <HttpCode>202</HttpCode>
  <TotalCount>7</TotalCount>
  <PageSize>10</PageSize>
  <Message>请求处理成功</Message>
  <RequestId>316F5F64-F73D-42DC-8632-01E308B6****</RequestId>
  <PageNumber>1</PageNumber>
  <Data>
        <UpStatus>1/1</UpStatus>
        <Name>CONTACTINFO</Name>
        <InstancesId>mse-cn-st21ri2****</InstancesId>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListEurekaServicesResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "TotalCount": 7,
    "PageSize": 10,
    "Message": "请求处理成功",
    "RequestId": "316F5F64-F73D-42DC-8632-01E308B6****",
    "PageNumber": 1,
    "Data": {
        "UpStatus": "1/1",
        "Name": "CONTACTINFO",
        "InstancesId": "mse-cn-st21ri2****"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

