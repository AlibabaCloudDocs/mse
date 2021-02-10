# DeleteZnode

调用DeleteZnode接口释放Zookeeper数据节点。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteZnode|系统规定参数，取值：DeleteZnode。 |
|ClusterId|String|是|mse-09k1q11\*\*\*\*|集群ID。 |
|Path|String|是|/zookeeper|节点路径。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |数据概览。 |
|Data|String|cluster|节点数据列表。 |
|Dir|Boolean|true|节点列表信息，取值如下：

 -   `true`：信息返回成功。
-   `false`：信息返回失败。 |
|Name|String|mse-bc1a29b0-160230875\*\*\*\*-reg-center-0-1|节点名称。 |
|Path|String|/|节点路径。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|200|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|DC34E4A3-5F1C-4E40-86EA-02EDF967\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteZnode
&ClusterId=mse-09k1q11****
&Path=/zookeeper
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DeleteZnodeResponse>
  <HttpCode>200</HttpCode>
  <RequestId>DC34E4A3-5F1C-4E40-86EA-02EDF967****</RequestId>
  <Message>请求处理成功</Message>
  <Data>
        <Path>/</Path>
        <Data>cluster</Data>
        <Dir>true</Dir>
        <Name>mse-bc1a29b0-160230875****-reg-center-0-1</Name>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</DeleteZnodeResponse>
```

`JSON`格式

```
{
    "HttpCode": 200,
    "RequestId": "DC34E4A3-5F1C-4E40-86EA-02EDF967****",
    "Message": "请求处理成功",
    "Data": {
        "Path": "/",
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

