# ListClusters

调用ListClusters接口查询集群列表。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListClusters|系统规定参数，取值：ListClusters。 |
|PageNum|Integer|是|1|页码。 |
|PageSize|Integer|是|10|每页展示集群数。 |
|RegionId|String|是|cn-hangzhou|集群所在地域，包括但不限于如下地域：

 -   `cn-hangzhou`：杭州
-   `cn-beijing`：北京
-   `cn-shanghai`：上海
-   `cn-zhangjiakou`：张家口
-   `cn-shenzhen`：深圳 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |
|ClusterAliasName|String|否|cluster|集群名字，支持模糊匹配。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of ClusterForListModel| |数据概览。 |
|AppVersion|String|1.9.3|APP版本。 |
|ChargeType|String|按量付费|付费模式，包括包年包月和按量付费。 |
|ClusterAliasName|String|mse-7413\*\*\*\*|集群别名。 |
|ClusterType|String|Eureka|集群类型，包括ZooKeeper、Nacos-Ans和Eureka。 |
|CreateTime|String|2020-07-31 11:36:08|集群创建时间。 |
|EndDate|String|2021-08-01 00:00:00|集群截止时间。 |
|InitStatus|String|RESTART\_SUCCESS|初始化状态。 |
|InstanceId|String|mse-cn-st21ri2\*\*\*\*|实例ID。 |
|InternetAddress|String|47.98.XX.XX|公网地址。 |
|InternetDomain|String|mse-7413\*\*\*\*-p.eureka.mse.aliyuncs.com|公网域名。 |
|IntranetAddress|String|192.168.XX.XX|私网地址。 |
|IntranetDomain|String|mse-7413\*\*\*\*-eureka.mse.aliyuncs.com|私网域名。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|10|每页展示实例数。 |
|RequestId|String|69AD2AA7-DB47-449B-941B-B14409DF\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|TotalCount|Integer|7|实例总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListClusters
&PageNum=1
&PageSize=10
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListClusterResopnse>
  <HttpCode>202</HttpCode>
  <TotalCount>7</TotalCount>
  <PageSize>10</PageSize>
  <Message>请求处理成功</Message>
  <RequestId>69AD2AA7-DB47-449B-941B-B14409DF****</RequestId>
  <PageNumber>1</PageNumber>
  <Data>
        <AppVersion>1.9.3</AppVersion>
        <ClusterAliasName>mse-7413****</ClusterAliasName>
        <IntranetAddress>192.168.XX.XX</IntranetAddress>
        <InternetAddress>47.98.XX.XX</InternetAddress>
        <InstanceId>mse-cn-st21ri2****</InstanceId>
        <ChargeType>按量付费</ChargeType>
        <InternetDomain>mse-7413****-p.eureka.mse.aliyuncs.com</InternetDomain>
        <CreateTime>2020-07-31 11:36:08</CreateTime>
        <ClusterType>Eureka</ClusterType>
        <InitStatus>RESTART_SUCCESS</InitStatus>
        <IntranetDomain>mse-7413****-eureka.mse.aliyuncs.com</IntranetDomain>
        <EndDate>2021-08-01 00:00:00</EndDate>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListClusterResopnse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "TotalCount": 7,
    "PageSize": 10,
    "Message": "请求处理成功",
    "RequestId": "69AD2AA7-DB47-449B-941B-B14409DF****",
    "PageNumber": 1,
    "Data": {
        "AppVersion": "1.9.3",
        "ClusterAliasName": "mse-7413****",
        "IntranetAddress": "192.168.XX.XX",
        "InternetAddress": "47.98.XX.XX",
        "InstanceId": "mse-cn-st21ri2****",
        "ChargeType": "按量付费",
        "InternetDomain": "mse-7413****-p.eureka.mse.aliyuncs.com",
        "CreateTime": "2020-07-31 11:36:08",
        "ClusterType": "Eureka",
        "InitStatus": "RESTART_SUCCESS",
        "IntranetDomain": "mse-7413****-eureka.mse.aliyuncs.com",
        "EndDate": "2021-08-01 00:00:00"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

