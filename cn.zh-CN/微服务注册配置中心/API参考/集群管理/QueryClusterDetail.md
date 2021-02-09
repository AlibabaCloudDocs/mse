# QueryClusterDetail

调用QueryClusterDetail接口查询集群详情。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|QueryClusterDetail|系统规定参数，取值：QueryClusterDetail。 |
|InstanceId|String|否|mse-cn-st21ri2\*\*\*\*|实例ID。 |
|OrderId|String|否|20576750143\*\*\*\*|订单ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |数据概览。 |
|AclEntryList|String|\[\]|白名单列表。 |
|AclId|String|acl-bp17020kiqvzutwwj\*\*\*\*|白名单ID。 |
|AppVersion|String|1.2.1|APP版本。 |
|ClusterAliasName|String|mse-7413\*\*\*\*|集群别名。 |
|ClusterName|String|mse-bc1a29b0-160230875\*\*\*\*|集群名称。 |
|ClusterType|String|Nacos-Ans|集群类型，包括ZooKeeper、Nacos-Ans和Eureka。 |
|Cpu|Integer|1|CPU数量。 |
|CreateTime|String|2020-07-31 11:36:08|集群创建时间。 |
|DiskCapacity|Long|60|磁盘容量，单位：G。 |
|DiskType|String|alicloud-disk-ssd-multi-zone|磁盘类型。 |
|HealthStatus|String|RESTART\_SUCCESS|集群健康状态。 |
|InitCostTime|Long|98408|集群创建耗时，单位：ms。 |
|InitStatus|String|RESTART\_SUCCESS|集群创建状态。 |
|InstanceCount|Integer|3|集群实例数。 |
|InstanceId|String|mse-cn-st21ri2\*\*\*\*|实例ID。 |
|InstanceModels|Array of InstanceModel| |实例列表。 |
|HealthStatus|String|Running|实例健康状态。 |
|InternetIp|String|47.98.XX.XX|公网IP。 |
|Ip|String|10.12.XX.XX|实例IP。 |
|PodName|String|mse-7413\*\*\*\*-159616656\*\*\*\*-reg-center-0-0|Pod名称。 |
|Role|String|Peer|角色。 |
|SingleTunnelVip|String|192.168.XX.XX|单线程IP。 |
|InternetAddress|String|47.98.XX.XX|公网地址。 |
|InternetDomain|String|mse-7413\*\*\*\*-p.eureka.mse.aliyuncs.com|公网域名。 |
|InternetPort|String|8761|私网端口。 |
|IntranetAddress|String|192.168.XX.XX|私网地址。 |
|IntranetDomain|String|mse-7413\*\*\*\*-eureka.mse.aliyuncs.com|私网域名。 |
|IntranetPort|String|8761|私网端口。 |
|MemoryCapacity|Long|2|内存大小，单位：G。 |
|PayInfo|String|按量付费|付费类型，包括包年包月和按量付费类型。 |
|PubNetworkFlow|String|3|公网带宽，单位：Mbps。

 取值范围：0~5000，其中0表示不接入公网。 |
|RegionId|String|cn-hangzhou|地域ID。 |
|VpcId|String|vpc-bp1hcg467ekqsv0zr\*\*\*\*|VPC ID。 |
|ErrorCode|String|mse-100-000|错误码。 |
|Message|String|请求处理成功|信息。 |
|RequestId|String|9515ACA4-E94D-440D-989E-C379FCED\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=QueryClusterDetail
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<QueryClusterDetailResponse>
  <RequestId>E7744898-AF7E-4FBC-9123-EAF01CFA****</RequestId>
  <Message>请求处理成功</Message>
  <Data>
        <InternetAddress>47.98.XX.XX</InternetAddress>
        <AclEntryList>[]</AclEntryList>
        <Cpu>1</Cpu>
        <InternetPort>8761</InternetPort>
        <IntranetPort>8761</IntranetPort>
        <AppVersion>1.9.3</AppVersion>
        <DiskType>alicloud-disk-ssd-multi-zone</DiskType>
        <PayInfo>按量付费</PayInfo>
        <InitCostTime>98408</InitCostTime>
        <ClusterName>mse-74131be0-159616656****</ClusterName>
        <IntranetDomain>mse-7413****-eureka.mse.aliyuncs.com</IntranetDomain>
        <ClusterId>mse-7413****</ClusterId>
        <InstanceId>mse-cn-st21ri2****</InstanceId>
        <InternetDomain>mse-7413****-p.eureka.mse.aliyuncs.com</InternetDomain>
        <CreateTime>2020-07-31 11:36:08</CreateTime>
        <AclId>acl-bp17020kiqvzutwwj****</AclId>
        <HealthStatus>RESTART_SUCCESS</HealthStatus>
        <ClusterType>Eureka</ClusterType>
        <MemoryCapacity>2</MemoryCapacity>
        <ClusterAliasName>mse-7413****</ClusterAliasName>
        <InstanceModels>
              <Role>Peer</Role>
              <PodName>mse-7413****-159616656****-reg-center-0-0</PodName>
              <InternetIp>47.98.XX.XX</InternetIp>
              <InstanceId>mse-cn-st21ri2****</InstanceId>
              <ClusterId>mse-7413****</ClusterId>
              <SingleTunnelVip>192.168.XX.XX</SingleTunnelVip>
              <Ip>10.12.XX.XX</Ip>
              <HealthStatus>Running</HealthStatus>
              <InstanceType>xxx</InstanceType>
              <Vip>XXX</Vip>
              <ZkClientPort>2181</ZkClientPort>
        </InstanceModels>
        <InstanceCount>3</InstanceCount>
        <IntranetAddress>192.168.XX.XX</IntranetAddress>
        <DiskCapacity>60</DiskCapacity>
        <VpcId>vpc-bp1hcg467ekqsv0zr****</VpcId>
        <PubNetworkFlow>3</PubNetworkFlow>
        <RegionId>cn-hangzhou</RegionId>
        <InitStatus>RESTART_SUCCESS</InitStatus>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</QueryClusterDetailResponse>
```

`JSON`格式

```
{
    "RequestId": "E7744898-AF7E-4FBC-9123-EAF01CFA****",
    "Message": "请求处理成功",
    "Data": {
        "InternetAddress": "47.98.XX.XX",
        "AclEntryList": "[]",
        "Cpu": 1,
        "InternetPort": 8761,
        "IntranetPort": 8761,
        "AppVersion": "1.9.3",
        "DiskType": "alicloud-disk-ssd-multi-zone",
        "PayInfo": "按量付费",
        "InitCostTime": 98408,
        "ClusterName": "mse-74131be0-159616656****",
        "IntranetDomain": "mse-7413****-eureka.mse.aliyuncs.com",
        "ClusterId": "mse-7413****",
        "InstanceId": "mse-cn-st21ri2****",
        "InternetDomain": "mse-7413****-p.eureka.mse.aliyuncs.com",
        "CreateTime": "2020-07-31 11:36:08",
        "AclId": "acl-bp17020kiqvzutwwj****",
        "HealthStatus": "RESTART_SUCCESS",
        "ClusterType": "Eureka",
        "MemoryCapacity": 2,
        "ClusterAliasName": "mse-7413****",
        "InstanceModels": {
            "Role": "Peer",
            "PodName": "mse-7413****-159616656****-reg-center-0-0",
            "InternetIp": "47.98.XX.XX",
            "InstanceId": "mse-cn-st21ri2****",
            "ClusterId": "mse-7413****",
            "SingleTunnelVip": "192.168.XX.XX",
            "Ip": "10.12.XX.XX",
            "HealthStatus": "Running",
            "InstanceType": "xxx",
            "Vip": "XXX",
            "ZkClientPort": 2181
        },
        "InstanceCount": 3,
        "IntranetAddress": "192.168.XX.XX",
        "DiskCapacity": 60,
        "VpcId": "vpc-bp1hcg467ekqsv0zr****",
        "PubNetworkFlow": 3,
        "RegionId": "cn-hangzhou",
        "InitStatus": "RESTART_SUCCESS"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

