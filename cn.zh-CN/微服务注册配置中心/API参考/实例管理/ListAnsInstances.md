# ListAnsInstances

调用ListAnsInstances接口查看实例详情。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAnsInstances|系统规定参数。取值：ListAnsInstances。 |
|PageNum|Integer|是|1|页码。 |
|PageSize|Integer|是|10|每页展示实例数。 |
|ServiceName|String|是|name|服务名称。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |
|ClusterId|String|否|mse-09k1q11\*\*\*\*|集群ID。 |
|GroupName|String|否|test|联系人组名称。 |
|NamespaceId|String|否|12233\*\*\*\*|命名空间ID。 |
|ClusterName|String|否|mse-7413\*\*\*\*|集群别名。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of NacosAnsInstance| |数据概览。 |
|App|String|app|应用名。 |
|ClusterName|String|DEFAULT|集群名称。 |
|DatumKey|String|30.5.XX.XX:unknown:DEFAULT|基准键。 |
|DefaultKey|String|30.5.XX.XX:unknown|缺省键。 |
|Enabled|Boolean|true|生效状态，取值如下：

 -   `true`：生效。
-   `false`：不生效。 |
|Ephemeral|Boolean|true|临时节点，取值如下：

 -   `true`：获取成功。
-   `false`：获取失败。 |
|FailCount|Integer|0|失败计数。 |
|Healthy|Boolean|true|实例健康状态，取值如下：

 -   `true`：实例健康。
-   `false`：实例不健康。 |
|InstanceHeartBeatInterval|Integer|5000|实例心跳间隔，单位：秒。 |
|InstanceHeartBeatTimeOut|Integer|15000|实例心跳超时。 |
|InstanceId|String|30.5.XX.XX\#0\#DEFAULT\#DEFAULT\_GROUP@@consumers:com.alibaba.edas.IHelloService|实例ID。 |
|Ip|String|30.5.XX.XX|公网IP。 |
|IpDeleteTimeout|Integer|30000|IP删除超时。 |
|LastBeat|Long|20201010|最近一次的心跳时间。 |
|Marked|Boolean|true|标记，取值如下：

 -   `true`：标记成功。
-   `false`：标记失败。 |
|Metadata|Map|\[int\]|元数据。 |
|OkCount|Integer|0|成功计数。 |
|Port|Integer|8080|端口号 |
|ServiceName|String|DEFAULT\_GROUP@@consumers:com.alibaba.edas.IHelloService::|服务名称。 |
|Weight|Integer|1|权重。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|10|每页展示实例数。 |
|RequestId|String|52BA6DA6-A702-4362-A32F-DFF79655\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|TotalCount|Integer|7|实例总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAnsInstances
&PageNum=1
&PageSize=10
&ServiceName=name
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListAnsInstancesResponse>
  <HttpCode>202</HttpCode>
  <TotalCount>7</TotalCount>
  <PageSize>10</PageSize>
  <Message>请求处理成功</Message>
  <RequestId>52BA6DA6-A702-4362-A32F-DFF79655****</RequestId>
  <PageNumber>1</PageNumber>
  <Data>
        <App>app</App>
        <InstanceId>30.5.XX.XX#0#DEFAULT#DEFAULT_GROUP@@consumers:com.alibaba.edas.IHelloService</InstanceId>
        <Ip>30.5.XX.XX</Ip>
        <Port>8080</Port>
        <Metadata>[int]</Metadata>
        <Enabled>true</Enabled>
        <Weight>1</Weight>
        <DatumKey>30.5.XX.XX:unknown:DEFAULT</DatumKey>
        <OkCount>0</OkCount>
        <ServiceName>DEFAULT_GROUP@@consumers:com.alibaba.edas.IHelloService::</ServiceName>
        <FailCount>0</FailCount>
        <ClusterName>DEFAULT</ClusterName>
        <LastBeat>20201010</LastBeat>
        <DefaultKey>30.5.XX.XX:unknown</DefaultKey>
        <InstanceHeartBeatTimeOut>15000</InstanceHeartBeatTimeOut>
        <Ephemeral>true</Ephemeral>
        <IpDeleteTimeout>30000</IpDeleteTimeout>
        <Marked>true</Marked>
        <Healthy>true</Healthy>
        <InstanceHeartBeatInterval>5000</InstanceHeartBeatInterval>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListAnsInstancesResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "TotalCount": 7,
    "PageSize": 10,
    "Message": "请求处理成功",
    "RequestId": "52BA6DA6-A702-4362-A32F-DFF79655****",
    "PageNumber": 1,
    "Data": {
        "App": "app",
        "InstanceId": "30.5.XX.XX#0#DEFAULT#DEFAULT_GROUP@@consumers:com.alibaba.edas.IHelloService",
        "Ip": "30.5.XX.XX",
        "Port": 8080,
        "Metadata": "[int]",
        "Enabled": true,
        "Weight": 1,
        "DatumKey": "30.5.XX.XX:unknown:DEFAULT",
        "OkCount": 0,
        "ServiceName": "DEFAULT_GROUP@@consumers:com.alibaba.edas.IHelloService::",
        "FailCount": 0,
        "ClusterName": "DEFAULT",
        "LastBeat": 20201010,
        "DefaultKey": "30.5.XX.XX:unknown",
        "InstanceHeartBeatTimeOut": 15000,
        "Ephemeral": true,
        "IpDeleteTimeout": 30000,
        "Marked": true,
        "Healthy": true,
        "InstanceHeartBeatInterval": 5000
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

