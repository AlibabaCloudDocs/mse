# UpdateEngineNamespace

调用UpdateEngineNamespace接口，更新引擎命名空间。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=UpdateEngineNamespace&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateEngineNamespace|系统规定参数，取值：UpdateEngineNamespace。 |
|Id|String|是|33ff74b6-d21e-4f9b-91a8-bc1ea4ef\*\*\*\*|命名空间ID。 |
|Name|String|是|name|集群名称。 |
|ServiceCount|Integer|是|3|活跃服务数。 |
|Desc|String|否|public|集群描述。 |
|ClusterId|String|否|mse-09k1q11\*\*\*\*|集群ID。 |
|InstanceId|String|否|mse-cn-st21ri2\*\*\*\*|实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |数据概览。 |
|ConfigCount|Integer|1|配额数量。 |
|Namespace|String|public|命名空间。 |
|NamespaceDesc|String|mytest|命名空间描述。 |
|NamespaceShowName|String|mytestshowname|命名空间描述名称。 |
|Quota|Integer|1|配额。 |
|Type|Integer|1|命名空间类型，取值如下：

 -   `0`：全局配置
-   `1`：默认命名空间
-   `2`：自定义命名空间 |
|ErrorCode|String|mse-100-000|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|4E9FDCFE-0738-493B-B801-82BDFBCB\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=UpdateEngineNamespace
&Id=33ff74b6-d21e-4f9b-91a8-bc1ea4ef****
&Name=name
&ServiceCount=3
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateEngineNamespaceResponse>
  <RequestId>4E9FDCFE-0738-493B-B801-82BDFBCB****</RequestId>
  <Message>请求处理成功</Message>
  <Data>
        <Type>1</Type>
        <Quota>1</Quota>
        <ConfigCount>1</ConfigCount>
        <NamespaceShowName>mytestshowname</NamespaceShowName>
        <NamespaceDesc>mytest</NamespaceDesc>
        <Namespace>public</Namespace>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</UpdateEngineNamespaceResponse>
```

`JSON`格式

```
{
    "RequestId": "4E9FDCFE-0738-493B-B801-82BDFBCB****",
    "Message": "请求处理成功",
    "Data": {
        "Type": 1,
        "Quota": 1,
        "ConfigCount": 1,
        "NamespaceShowName": "mytestshowname",
        "NamespaceDesc": "mytest",
        "Namespace": "public"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

