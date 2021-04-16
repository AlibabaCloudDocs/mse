# DeleteCluster

调用DeleteCluster接口释放集群。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=DeleteCluster&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteCluster|系统规定参数，取值：DeleteCluster。 |
|InstanceId|String|是|mse-cn-6ja1rgl\*\*\*\*|实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|3369AD10-F1A6-4E6F-B99E-20F51826\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteCluster
&InstanceId=mse-cn-6ja1rgl****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DeleteClusterResponse>
  <HttpCode>202</HttpCode>
  <RequestId>3369AD10-F1A6-4E6F-B99E-20F51826****</RequestId>
  <Message>请求处理成功</Message>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</DeleteClusterResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "RequestId": "3369AD10-F1A6-4E6F-B99E-20F51826****",
    "Message": "请求处理成功",
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

