# UpdateZnode

调用UpdateZnode接口更新Zookeeper数据节点。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateZnode|系统规定参数，取值：UpdateZnode。 |
|ClusterId|String|是|mse-09k1q11\*\*\*\*|集群ID。 |
|Data|String|是|data|节点数据。 |
|Path|String|是|/zookeeper|节点路径。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ErrorCode|String|mse-100-000|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|316F5F64-F73D-42DC-8632-01E308B6\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateZnode
&ClusterId=mse-09k1q11****
&Data=data
&Path=/zookeeper
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateZnodeResponse>
  <RequestId>316F5F64-F73D-42DC-8632-01E308B6****</RequestId>
  <Message>请求处理成功</Message>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</UpdateZnodeResponse>
```

`JSON`格式

```
{
    "RequestId": "316F5F64-F73D-42DC-8632-01E308B6****",
    "Message": "请求处理成功",
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

