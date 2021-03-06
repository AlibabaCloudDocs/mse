# DeleteNacosService

调用DeleteNacosService接口删除Nacos实例详情。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=DeleteNacosService&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteNacosService|系统规定参数。取值：**DeleteNacosService**。 |
|InstanceId|String|是|mse-cn-123456|实例ID。 |
|ServiceName|String|是|hello\_service|服务名称。 |
|GroupName|String|是|DEFAULT\_GROUP|分组名称。 |
|NamespaceId|String|否|9e78a671-4b9b-4dd4-99c1-0\*\*\*\*|命名空间ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|HttpStatusCode|Integer|200|HTTP状态码。 |
|RequestId|String|9e78a671-4b9b-4dd4-99c1-0b9da87d3dec|请求ID。 |
|Message|String|请求成功|返回信息。 |
|Code|Integer|200|响应码。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|Data|String|ok|删除结果。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteNacosService
&InstanceId=mse-cn-123456
&ServiceName=hello_service
&GroupName=DEFAULT_GROUP
&NamespaceId=9e78a671-4b9b-4dd4-99c1-0****
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DeleteNacosServiceResponse>
    <HttpStatusCode>200</HttpStatusCode>
    <RequestId>9e78a671-4b9b-4dd4-99c1-0b9da87d3dec</RequestId>
    <Message>请求成功</Message>
    <Code>200</Code>
    <Success>true</Success>
    <Data>ok</Data>
</DeleteNacosServiceResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "HttpStatusCode" : 200,
  "RequestId" : "9e78a671-4b9b-4dd4-99c1-0b9da87d3dec",
  "Message" : "请求成功",
  "Code" : 200,
  "Success" : true,
  "Data" : "ok"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

