# QueryZnodeDetail

调用QueryZnodeDetail接口查询ZooKeeper数据节点信息。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|QueryZnodeDetail|系统规定参数，取值：QueryZnodeDetail。 |
|ClusterId|String|是|mse-09k1q11\*\*\*\*|集群ID。 |
|Path|String|是|/zookeeper|节点路径。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |数据概览。 |
|Data|String|cluster|节点数据。 |
|Dir|Boolean|true|节点列表信息，取值如下：

 -   `true`：信息返回成功。
-   `false`：信息返回失败。 |
|Name|String|zookeeper|节点名称。 |
|Path|String|/zookeeper|节点路径。 |
|ErrorCode|String|mse-100-000|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|58E06A0A-BD2C-47A0-99C2-B100F353\*\*\*\*|请求ID。 |
|Success|String|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=QueryZnodeDetail
&ClusterId=mse-09k1q11****
&Path=/zookeeper
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<QueryZnodeDetailResponse>
  <Message>请求处理成功</Message>
  <RequestId>58E06A0A-BD2C-47A0-99C2-B100F353****</RequestId>
  <Data>
        <Path>/zookeeper</Path>
        <Data>cluster</Data>
        <Dir>true</Dir>
        <Name>zookeeper</Name>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</QueryZnodeDetailResponse>
```

`JSON`格式

```
{
    "Message": "请求处理成功",
    "RequestId": "58E06A0A-BD2C-47A0-99C2-B100F353****",
    "Data": {
        "Path": "/zookeeper",
        "Data": "cluster",
        "Dir": true,
        "Name": "zookeeper"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

