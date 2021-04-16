# QueryClusterSpecification

调用QueryClusterSpecification接口查询集群规格。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=QueryClusterSpecification&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|QueryClusterSpecification|系统规定参数，取值：QueryClusterSpecification。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|Integer|200|返回值。 |
|Data|Array of Data| |数据概览。 |
|ClusterSpecificationName|String|MSE\_SC\_1\_2\_200\_c|引擎规格，取值如下：

 -   `MSE_SC_1_2_200_c`：1核2G
-   `MSE_SC_2_4_200_c`：2核4G
-   `MSE_SC_4_8_200_c`：4核8G
-   `MSE_SC_8_16_200_c`：8核16G |
|CpuCapacity|String|1|CPU容量。 |
|DiskCapacity|String|60|磁盘容量，单位：G。 |
|InstanceCount|String|1|实例数量。 |
|MaxCon|String|3000|最大连接数。 |
|MaxTps|String|5000|最大TPS。 |
|MemoryCapacity|String|2|内存大小，单位：G。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|EE5C32A1-BC0E-4B79-817C-103E4EDF\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=QueryClusterSpecification
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<QueryClusterSpecificationResponse>
  <Message>请求处理成功</Message>
  <RequestId>EE5C32A1-BC0E-4B79-817C-103E4EDF****</RequestId>
  <HttpStatusCode>200</HttpStatusCode>
  <Data>
        <MaxTps>5000</MaxTps>
        <CpuCapacity>1</CpuCapacity>
        <InstanceCount>1</InstanceCount>
        <DiskCapacity>60</DiskCapacity>
        <ClusterSpecificationName>MSE_SC_1_2_200_c</ClusterSpecificationName>
        <MemoryCapacity>2</MemoryCapacity>
        <MaxCon>3000</MaxCon>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Code>200</Code>
  <Success>true</Success>
</QueryClusterSpecificationResponse>
```

`JSON`格式

```
{
    "Message": "请求处理成功",
    "RequestId": "EE5C32A1-BC0E-4B79-817C-103E4EDF****",
    "HttpStatusCode": 200,
    "Data": {
        "MaxTps": 5000,
        "CpuCapacity": 1,
        "InstanceCount": 1,
        "DiskCapacity": 60,
        "ClusterSpecificationName": "MSE_SC_1_2_200_c",
        "MemoryCapacity": 2,
        "MaxCon": 3000
    },
    "ErrorCode": "mse-100-000",
    "Code": 200,
    "Success": true
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|NoPermission|You are not authorized to perform this operation.|没有权限操作|
|500|InternalError|An error occurred while processing your request.|服务端异常|

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

