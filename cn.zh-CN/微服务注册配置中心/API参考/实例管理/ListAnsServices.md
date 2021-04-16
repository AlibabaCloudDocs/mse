# ListAnsServices

调用ListAnsServices接口查看服务详情。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=ListAnsServices&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAnsServices|系统规定参数，取值：ListAnsServices。 |
|ClusterId|String|是|mse-09k1q11\*\*\*\*|集群ID。 |
|PageNum|Integer|是|1|页码。 |
|PageSize|Integer|是|10|每页展示实例数。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |
|ServiceName|String|否|name|服务名称。 |
|GroupName|String|否|name|联系人组名称。 |
|HasIpCount|String|否|1|服务IP计数。 |
|InstanceId|String|否|mse-cn-st21v5\*\*\*\*|实例ID。 |
|NamespaceId|String|否|12233\*\*\*\*|命名空间ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of SimpleNacosAnsService| |数据概览。 |
|ClusterCount|Integer|1|集群总数。 |
|GroupName|String|name|联系人组名称。 |
|HealthyInstanceCount|Integer|1|健康心跳总数。 |
|IpCount|Integer|1|IP总数。 |
|Name|String|name|服务名称。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|10|每页展示实例数。 |
|RequestId|String|52BA6DA6-A702-4362-A32F-DFF79655\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|TotalCount|Integer|7|实例总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAnsServices
&ClusterId=mse-09k1q11****
&PageNum=1
&PageSize=10
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListAnsServicesResponse>
  <HttpCode>202</HttpCode>
  <TotalCount>7</TotalCount>
  <PageSize>10</PageSize>
  <Message>请求处理成功</Message>
  <RequestId>52BA6DA6-A702-4362-A32F-DFF79655****</RequestId>
  <PageNumber>1</PageNumber>
  <Data>
        <GroupName>name</GroupName>
        <IpCount>1</IpCount>
        <HealthyInstanceCount>1</HealthyInstanceCount>
        <ClusterCount>1</ClusterCount>
        <Name>name</Name>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListAnsServicesResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "TotalCount": 7,
    "PageSize": 10,
    "Message": "请求处理成功",
    "RequestId": "52BA6DA6-A702-4362-A32F-DFF79655****",
    "PageNumber": 1,
    "Data": {
        "GroupName": "name",
        "IpCount": 1,
        "HealthyInstanceCount": 1,
        "ClusterCount": 1,
        "Name": "name"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

