# CreateEngineNamespace

调用CreateEngineNamespace接口，创建引擎命名空间。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateEngineNamespace|系统规定参数，取值：CreateEngineNamespace。 |
|Name|String|是|name|集群名称。 |
|ClusterId|String|否|mse-98s\*\*\*\*|集群ID。 |
|Desc|String|否|public|集群描述。 |
|InstanceId|String|否|mse-cn-st21ri2\*\*\*\*|实例ID。 |
|ServiceCount|Integer|否|3|集群服务数。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ClusterId|String|mse-892k\*\*\*\*|集群ID。 |
|Data|Struct| |数据概览。 |
|ConfigCount|Integer|1|配置数量。 |
|Namespace|String|DEFAULT|命名空间。 |
|NamespaceDesc|String|mytest|命名空间描述。 |
|NamespaceShowName|String|public|命名空间描述名称。 |
|Quota|Integer|1|配额。 |
|ServiceCount|Integer|3|活跃服务数。 |
|Type|Integer|1|命名空间类型，取值如下：

 -   `0`：全局配置
-   `1`：默认命名空间
-   `2`：自定义命名空间 |
|ErrorCode|String|mse-100-000|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|F6092602-C357-4750-89D9-E572FBEA\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateEngineNamespace
&Name=name
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateEngineNamespaceResponse>
  <RequestId>F6092602-C357-4750-89D9-E572FBEA****</RequestId>
  <Message>请求处理成功</Message>
  <ClusterId>mse-892k****</ClusterId>
  <Data>
        <Type>1</Type>
        <Quota>1</Quota>
        <ConfigCount>1</ConfigCount>
        <NamespaceShowName>public</NamespaceShowName>
        <ServiceCount>3</ServiceCount>
        <NamespaceDesc>mytest</NamespaceDesc>
        <Namespace>DEFAULT</Namespace>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</CreateEngineNamespaceResponse>
```

`JSON`格式

```
{
    "RequestId": "F6092602-C357-4750-89D9-E572FBEA****",
    "Message": "请求处理成功",
    "ClusterId": "mse-892k****",
    "Data": {
        "Type": 1,
        "Quota": 1,
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

