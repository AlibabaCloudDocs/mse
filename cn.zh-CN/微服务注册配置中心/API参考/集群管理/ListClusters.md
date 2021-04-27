# ListClusters

调用ListClusters接口查询集群列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=ListClusters&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListClusters|系统规定参数，取值：ListClusters。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |
|PageNum|Integer|是|1|页码。 |
|PageSize|Integer|是|10|每页展示集群数。 |
|ClusterAliasName|String|否|cluster|集群名字，支持模糊匹配。 |
|RegionId|String|是|cn-hangzhou|集群所在地域，MSE支持的地域，请参见[开服地域](https://help.aliyun.com/document_detail/210784.html)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|HttpCode|String|202|HTTP状态码。 |
|TotalCount|Integer|7|实例总数。 |
|RequestId|String|69AD2AA7-DB47-449B-941B-B14409DF\*\*\*\*|请求ID。 |
|Message|String|请求处理成功|信息。 |
|PageSize|Integer|10|每页展示实例数。 |
|PageNumber|Integer|1|页码。 |
|Data|Array of ClusterForListModel| |数据概览。 |
|EndDate|String|2021-08-01 00:00:00|集群截止时间。 |
|IntranetDomain|String|mse-7413\*\*\*\*-eureka.mse.aliyuncs.com|私网域名。 |
|InternetDomain|String|mse-7413\*\*\*\*-p.eureka.mse.aliyuncs.com|公网域名。 |
|CreateTime|String|2020-07-31 11:36:08|集群创建时间。 |
|ChargeType|String|按量付费|付费模式，包括包年包月和按量付费。 |
|IntranetAddress|String|192.168.XX.XX|私网地址。 |
|InstanceId|String|mse-cn-st21ri2\*\*\*\*|实例ID。 |
|InternetAddress|String|47.98.XX.XX|公网地址。 |
|ClusterAliasName|String|mse-7413\*\*\*\*|集群别名。 |
|ClusterType|String|Eureka|集群类型，包括ZooKeeper、Nacos-Ans和Eureka。 |
|InitStatus|String|RESTART\_SUCCESS|初始化状态。 |
|AppVersion|String|1.9.3|APP版本。 |
|ErrorCode|String|mse-100-000|错误码。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListClusters
&RequestPars={}
&PageNum=1
&PageSize=10
&ClusterAliasName=cluster
&RegionId=cn-hangzhou
&公共请求参数
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<ListClustersResponse>
    <HttpCode>202</HttpCode>
    <TotalCount>7</TotalCount>
    <RequestId>69AD2AA7-DB47-449B-941B-B14409DF****</RequestId>
    <Message>请求处理成功</Message>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <Data>
        <EndDate>2021-08-01 00:00:00</EndDate>
        <IntranetDomain>mse-7413****-eureka.mse.aliyuncs.com</IntranetDomain>
        <InternetDomain>mse-7413****-p.eureka.mse.aliyuncs.com</InternetDomain>
        <CreateTime>2020-07-31 11:36:08</CreateTime>
        <ChargeType>按量付费</ChargeType>
        <IntranetAddress>192.168.XX.XX</IntranetAddress>
        <InstanceId>mse-cn-st21ri2****</InstanceId>
        <InternetAddress>47.98.XX.XX</InternetAddress>
        <ClusterAliasName>mse-7413****</ClusterAliasName>
        <ClusterType>Eureka</ClusterType>
        <InitStatus>RESTART_SUCCESS</InitStatus>
        <AppVersion>1.9.3</AppVersion>
    </Data>
    <ErrorCode>mse-100-000</ErrorCode>
    <Success>true</Success>
</ListClustersResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "HttpCode" : 202,
  "TotalCount" : 7,
  "RequestId" : "69AD2AA7-DB47-449B-941B-B14409DF****",
  "Message" : "请求处理成功",
  "PageSize" : 10,
  "PageNumber" : 1,
  "Data" : {
    "EndDate" : "2021-08-01 00:00:00",
    "IntranetDomain" : "mse-7413****-eureka.mse.aliyuncs.com",
    "InternetDomain" : "mse-7413****-p.eureka.mse.aliyuncs.com",
    "CreateTime" : "2020-07-31 11:36:08",
    "ChargeType" : "按量付费",
    "IntranetAddress" : "192.168.XX.XX",
    "InstanceId" : "mse-cn-st21ri2****",
    "InternetAddress" : "47.98.XX.XX",
    "ClusterAliasName" : "mse-7413****",
    "ClusterType" : "Eureka",
    "InitStatus" : "RESTART_SUCCESS",
    "AppVersion" : "1.9.3"
  },
  "ErrorCode" : "mse-100-000",
  "Success" : true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

