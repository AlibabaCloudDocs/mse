# ListEngineNamespaces

调用ListEngineNamespaces接口获取引擎命名空间列表信息。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListEngineNamespaces|系统规定参数，取值：ListEngineNamespaces。 |
|InstanceId|String|否|mse-cn-st21ri2\*\*\*\*|实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of Namespace| |数据概览。 |
|ConfigCount|Integer|1|配额数量。 |
|Namespace|String|DEFAULT|命名空间。 |
|NamespaceDesc|String|mytest|命名空间描述。 |
|NamespaceShowName|String|public|命名空间名称。 |
|Quota|Integer|200|配额。 |
|ServiceCount|String|3|活跃服务数。 |
|Type|Integer|0|命名空间类型，取值如下：

 -   `0`：全局配置
-   `1`：默认命名空间
-   `2`：自定义命名空间 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|10|每页展示实例数。 |
|RequestId|String|062D13C5-DEA3-4921-8918-C49A0F1B\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|TotalCount|Integer|7|实例总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListEngineNamespaces
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListEngineNamespacesResponse>
  <HttpCode>202</HttpCode>
  <TotalCount>7</TotalCount>
  <PageSize>10</PageSize>
  <Message>请求处理成功</Message>
  <RequestId>062D13C5-DEA3-4921-8918-C49A0F1B****</RequestId>
  <PageNumber>1</PageNumber>
  <Data>
        <Type>0</Type>
        <Quota>200</Quota>
        <ConfigCount>1</ConfigCount>
        <NamespaceShowName>public</NamespaceShowName>
        <ServiceCount>3</ServiceCount>
        <NamespaceDesc>mytest</NamespaceDesc>
        <Namespace>DEFAULT</Namespace>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListEngineNamespacesResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "TotalCount": 7,
    "PageSize": 10,
    "Message": "请求处理成功",
    "RequestId": "062D13C5-DEA3-4921-8918-C49A0F1B****",
    "PageNumber": 1,
    "Data": {
        "Type": 0,
        "Quota": 200,
        "ConfigCount": 1,
        "NamespaceShowName": "public",
        "ServiceCount": 3,
        "NamespaceDesc": "mytest",
        "Namespace": "DEFAULT"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

