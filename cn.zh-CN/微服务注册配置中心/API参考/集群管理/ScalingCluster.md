# ScalingCluster

调用ScalingCluster接口伸缩集群。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ScalingCluster|系统规定参数，取值：ScalingCluster。 |
|ClusterSpecification|String|是|MSE\_SC\_2\_4\_200\_c|引擎规格，取值如下：

 -   `MSE_SC_1_2_200_c`：1核2G
-   `MSE_SC_2_4_200_c`：2核4G
-   `MSE_SC_4_8_200_c`：4核8G
-   `MSE_SC_8_16_200_c`：8核16G |
|InstanceCount|Integer|是|3|实例数，范围限制：1~9个。 |
|InstanceId|String|是|mse-cn-st21ri2\*\*\*\*|实例ID。 |
|Cpu|Integer|否|1|CPU数量。 |
|MemoryCapacity|Long|否|2|内存大小，单位：G。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ErrorCode|String|mse-100-000|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|A73AC37C-C617-4E3A-8049-372CF49C\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ScalingCluster
&ClusterSpecification=MSE_SC_2_4_200_c
&InstanceCount=3
&InstanceId=mse-cn-st21ri2****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ScalingClusterResponse>
  <Message>请求处理成功</Message>
  <RequestId>A73AC37C-C617-4E3A-8049-372CF49C****</RequestId>
  <ClusterId>mse-7413****</ClusterId>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ScalingClusterResponse>
```

`JSON`格式

```
{
    "Message": "请求处理成功",
    "RequestId": "A73AC37C-C617-4E3A-8049-372CF49C****",
    "ClusterId": "mse-7413****",
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

