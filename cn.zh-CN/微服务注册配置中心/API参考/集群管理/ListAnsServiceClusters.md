# ListAnsServiceClusters

调用ListAnsServiceClusters接口查看集群服务详情。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAnsServiceClusters|系统规定参数，取值：ListAnsServiceClusters。 |
|PageNum|Integer|是|1|页码。 |
|PageSize|Integer|是|10|每页展示实例数。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |
|ClusterId|String|否|mse-09k1q110q01|集群ID。 |
|ServiceName|String|否|test|服务名称。 |
|GroupName|String|否|test|联系人组名称。 |
|NamespaceId|String|否|12233\*\*\*\*|命名空间ID。 |
|ClusterName|String|否|mse-7413\*\*\*\*|集群别名。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |数据概览。 |
|Clusters|Array of NacosAnsCluster| |集群信息。 |
|DefaultCheckPort|Integer|80|默认检查端口。 |
|DefaultPort|Integer|80|默认端口。 |
|HealthCheckerType|String|心跳上报|健康检查类型。 |
|Metadata|Map|111|元数据。 |
|Name|String|test|名称。 |
|ServiceName|String|DEFAULT\_GROUP@@consumers:com.alibaba.edas.IHelloService::|服务名。 |
|UseIPPort4Check|Boolean|true|开启IP校验。 |
|GroupName|String|DEFAULT\_GROUP|联系人组名称。 |
|Metadata|Map|111|元数据。 |
|Name|String|DEFAULT|名称。 |
|ProtectThreshold|Float|0|保护阈值。 |
|SelectorType|String|none|选举模式。 |
|ErrorCode|String|mse-100-000|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|52BA6DA6-A702-4362-A32F-DFF79655\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAnsServiceClusters
&PageNum=1
&PageSize=10
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListAnsServiceClustersResponse>
  <Message>请求处理成功</Message>
  <RequestId>52BA6DA6-A702-4362-A32F-DFF79655****</RequestId>
  <Data>
        <GroupName>DEFAULT_GROUP</GroupName>
        <SelectorType>none</SelectorType>
        <Metadata>111</Metadata>
        <ProtectThreshold>0</ProtectThreshold>
        <Name>DEFAULT</Name>
        <Clusters>
              <UseIPPort4Check>true</UseIPPort4Check>
              <DefaultCheckPort>80</DefaultCheckPort>
              <ServiceName>DEFAULT_GROUP@@consumers:com.alibaba.edas.IHelloService::</ServiceName>
              <Metadata>111</Metadata>
              <HealthCheckerType>心跳上报</HealthCheckerType>
              <DefaultPort>80</DefaultPort>
              <Name>test</Name>
        </Clusters>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListAnsServiceClustersResponse>
```

`JSON`格式

```
{
    "Message": "请求处理成功",
    "RequestId": "52BA6DA6-A702-4362-A32F-DFF79655****",
    "Data": {
        "GroupName": "DEFAULT_GROUP",
        "SelectorType": "none",
        "Metadata": 111,
        "ProtectThreshold": 0,
        "Name": "DEFAULT",
        "Clusters": {
            "UseIPPort4Check": true,
            "DefaultCheckPort": 80,
            "ServiceName": "DEFAULT_GROUP@@consumers:com.alibaba.edas.IHelloService::",
            "Metadata": 111,
            "HealthCheckerType": "心跳上报",
            "DefaultPort": 80,
            "Name": "test"
        }
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

