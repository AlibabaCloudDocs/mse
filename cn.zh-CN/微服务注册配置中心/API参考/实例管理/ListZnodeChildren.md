# ListZnodeChildren

调用ListZnodeChildren接口查看ZooKeeper集群列表详情。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListZnodeChildren|系统规定参数，取值：ListZnodeChildren。 |
|ClusterId|String|是|mse-09k1q11\*\*\*\*|集群ID。 |
|Path|String|是|/zookeeper|节点路径。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of ZnodeModel| |数据概览 |
|Data|String|cluster|节点数据。 |
|Dir|Boolean|true|节点列表信息，取值如下：

 -   `true`：信息返回成功。
-   `false`：信息返回失败。 |
|Name|String|mse-bc1a29b0-160230875\*\*\*\*-reg-center-0-1|节点名称。 |
|Path|String|/zookeeper|节点路径。 |
|ErrorCode|String|mse-100-000|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|BDB6CE0B-9CAF-41B5-9FEA-E08BE8E2\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListZnodeChildren
&ClusterId=mse-09k1q11****
&Path=/zookeeper
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListZnodeChildrenResponse>
  <Message>请求处理成功</Message>
  <RequestId>BDB6CE0B-9CAF-41B5-9FEA-E08BE8E2****</RequestId>
  <Data>
        <Path>/zookeeper</Path>
        <Data>cluster</Data>
        <Dir>true</Dir>
        <Name>mse-bc1a29b0-160230875****-reg-center-0-1</Name>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListZnodeChildrenResponse>
```

`JSON`格式

```
{
    "Message": "请求处理成功",
    "RequestId": "BDB6CE0B-9CAF-41B5-9FEA-E08BE8E2****",
    "Data": {
        "Path": "/zookeeper",
        "Data": "cluster",
        "Dir": true,
        "Name": "mse-bc1a29b0-160230875****-reg-center-0-1"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

