# ListEurekaInstances

调用ListEurekaInstances接口查看Eureka实例详情。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListEurekaInstances|系统规定参数，取值：ListEurekaInstances。 |
|PageNum|Integer|是|1|页码。 |
|PageSize|Integer|是|10|每页展示实例数。 |
|ServiceName|String|是|name|服务名称。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |
|ClusterId|String|否|mse-09k1q11\*\*\*\*|集群ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of EurekaInstance| |数据概览。 |
|App|String|CONTACTINFO|应用名。 |
|DurationInSecs|Integer|90|实例超时时间。

 超过这个时间后，服务默认不可用，将会被删除。 |
|HomePageUrl|String|http://30.5.XX.XX:8091/|主页地址。 |
|HostName|String|30.5.XX.XX|主机名。 |
|InstanceId|String|L-PC1A6A28-\*\*\*\*.hz.ali.com:contactinfo:8091|实例ID。 |
|IpAddr|String|30.5.XX.XX|IP地址。 |
|LastDirtyTimestamp|Long|20201009115543|实例属性最后更新的时间。 |
|LastUpdatedTimestamp|Long|20201010071203|最近一次心跳时间。 |
|Metadata|Map|\[string\]|元数据。 |
|Port|Integer|8091|服务端口。 |
|RenewalIntervalInSecs|Integer|10|心跳执行器在续约过程中超时后再次执行续约的最大延迟倍数。

 默认最大延迟倍数为10。 |
|SecurePort|Integer|443|安全端口。 |
|Status|String|1/1|服务提供者数量，健康实例数/总实例数。 |
|VipAddress|String|contactinfo|VIP地址。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|10|每页展示实例数。 |
|RequestId|String|316F5F64-F73D-42DC-8632-01E308B6\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|TotalCount|Integer|7|实例总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListEurekaInstances
&PageNum=1
&PageSize=10
&ServiceName=name
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListEurekaInstancesResponse>
  <HttpCode>202</HttpCode>
  <TotalCount>7</TotalCount>
  <PageSize>10</PageSize>
  <Message>请求处理成功</Message>
  <RequestId>316F5F64-F73D-42DC-8632-01E308B6****</RequestId>
  <PageNumber>1</PageNumber>
  <Data>
        <Status>1/1</Status>
        <App>CONTACTINFO</App>
        <RenewalIntervalInSecs>10</RenewalIntervalInSecs>
        <SecurePort>443</SecurePort>
        <IpAddr>30.5.XX.XX</IpAddr>
        <InstanceId>L-PC1A6A28-****.hz.ali.com:contactinfo:8091</InstanceId>
        <DurationInSecs>90</DurationInSecs>
        <VipAddress>contactinfo</VipAddress>
        <LastUpdatedTimestamp>20201010071203</LastUpdatedTimestamp>
        <Port>8091</Port>
        <Metadata>[string]</Metadata>
        <LastDirtyTimestamp>20201009115543</LastDirtyTimestamp>
        <HomePageUrl>http://30.5.XX.XX:8091/</HomePageUrl>
        <HostName>30.5.XX.XX</HostName>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListEurekaInstancesResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "TotalCount": 7,
    "PageSize": 10,
    "Message": "请求处理成功",
    "RequestId": "316F5F64-F73D-42DC-8632-01E308B6****",
    "PageNumber": 1,
    "Data": {
        "Status": "1/1",
        "App": "CONTACTINFO",
        "RenewalIntervalInSecs": 10,
        "SecurePort": 443,
        "IpAddr": "30.5.XX.XX",
        "InstanceId": "L-PC1A6A28-****.hz.ali.com:contactinfo:8091",
        "DurationInSecs": 90,
        "VipAddress": "contactinfo",
        "LastUpdatedTimestamp": 20201010071203,
        "Port": 8091,
        "Metadata": "[string]",
        "LastDirtyTimestamp": 20201009115543,
        "HomePageUrl": "http://30.5.XX.XX:8091/",
        "HostName": "30.5.XX.XX"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

