# UpdateCluster

调用UpdateCluster接口修改集群信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=UpdateCluster&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateCluster|系统规定参数，取值：UpdateCluster。 |
|ClusterAliasName|String|是|cluster-1|集群别名。 |
|InstanceId|String|是|mse-cn-78v1l83\*\*\*\*|实例ID。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ErrorCode|String|mse-100-100|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|5B170A0D-2C5D-4CF8-B808-03966B86\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateCluster
&ClusterAliasName=cluster-1
&InstanceId=mse-cn-78v1l83****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateClusterResponse>
  <Message>请求处理成功</Message>
  <RequestId>5B170A0D-2C5D-4CF8-B808-03966B86****</RequestId>
  <ErrorCode>mse-100-100</ErrorCode>
  <Success>true</Success>
</UpdateClusterResponse>
```

`JSON`格式

```
{
    "Message": "请求处理成功",
    "RequestId": "5B170A0D-2C5D-4CF8-B808-03966B86****",
    "ErrorCode": "mse-100-100",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

