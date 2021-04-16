# CreateCluster

调用CreateCluster接口创建一个集群。

请确保在使用该接口前，已充分了解MSE（Microservice Engine）产品的收费方式和价格，请参见[价格说明](https://help.aliyun.com/document_detail/139842.html)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=mse&api=CreateCluster&type=RPC&version=2019-05-31)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateCluster|系统规定参数，取值：CreateCluster。 |
|ClusterSpecification|String|是|MSE\_SC\_2\_4\_200\_c|引擎规格，取值如下：

 -   `MSE_SC_1_2_200_c`：1核2G
-   `MSE_SC_2_4_200_c`：2核4G
-   `MSE_SC_4_8_200_c`：4核8G
-   `MSE_SC_8_16_200_c`：8核16G |
|PubNetworkFlow|String|是|0|公网带宽，单位：Mbps。

 取值范围：0~5000，其中0表示不接入公网。 |
|DiskType|String|是|alicloud-disk-ssd-multi-zone|磁盘类型。 |
|NetType|String|是|privatenet|网络类型，取值如下：

 -   `privatenet`：表示专有网络。
-   `pubnet`：表示公网。 |
|ClusterVersion|String|是|NACOS\_ANS\_1\_1\_3|集群版本，取值如下：

 -   `ZooKeeper_3_4_14`：表示ZooKeeper 3.4.14版本。
-   `ZooKeeper_3_5_5`：表示ZooKeeper 3.5.5版本。
-   `NACOS_ANS_1_1_3`：表示Nacos 1.1.3版本。
-   `NACOS_ANS_1_2_1`：表示Nacos 1.2.1版本。
-   `EUREKA_1_9_3`：表示Eureka 1.9.3版本。 |
|InstanceCount|Integer|是|3|实例数，范围限制：1~9个。 |
|ClusterType|String|是|Nacos-Ans|集群类型，包括ZooKeeper、Nacos-Ans和Eureka。 |
|Region|String|是|cn-hangzhou|集群所在地域，包括但不限于如下地域：

 -   `cn-hangzhou`：杭州
-   `cn-beijing`：北京
-   `cn-shanghai`：上海
-   `cn-zhangjiakou`：张家口
-   `cn-shenzhen`：深圳 |
|PubSlbSpecification|String|否|slb.s1.small|公网SLB规格，取值如下：

 -   `slb.s1.small`
-   `slb.s3.medium`

更多信息，请参见[实例概述](https://help.aliyun.com/document_detail/85931.html)。 |
|VpcId|String|否|vpc-bp1t50e045b5g7i3p\*\*\*\*|VPC ID。 |
|VSwitchId|String|否|vsw-bp17opt4v18sto39k\*\*\*\*|交换机ID。 |
|PrivateSlbSpecification|String|否|slb.s1.small|私网SLB规格，取值如下：

 -   `slb.s1.small`
-   `slb.s3.medium`

更多信息，请参见[实例概述](https://help.aliyun.com/document_detail/85931.html)。 |
|ConnectionType|String|否|公网网络|网络连接类型，包括专有网络和公网网络类型。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |
|DiskCapacity|Integer|否|1250|磁盘容量。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ErrorCode|String|mse-100-000|错误码。 |
|InstanceId|String|mse-cn-st21ri2\*\*\*\*|实例ID。 |
|Message|String|请求处理成功|信息。 |
|OrderId|String|20574710974\*\*\*\*|订单ID。 |
|RequestId|String|dc63-465d-8ef5-20dc18af\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateCluster
&ClusterSpecification=MSE_SC_2_4_200_c
&PubNetworkFlow=0
&DiskType=alicloud-disk-ssd-multi-zone
&NetType=privatenet
&ClusterVersion=NACOS_ANS_1_1_3
&InstanceCount=3
&ClusterType=Nacos-Ans
&Region=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateClusterResponse>
  <RequestId>dc63-465d-8ef5-20dc18af****</RequestId>
  <Message>请求处理成功</Message>
  <InstanceId>mse-cn-st21ri2****</InstanceId>
  <ErrorCode>mse-100-000</ErrorCode>
  <OrderId>20574710974****</OrderId>
  <Success>true</Success>
</CreateClusterResponse>
```

`JSON`格式

```
{
    "RequestId": "dc63-465d-8ef5-20dc18af****",
    "Message": "请求处理成功",
    "InstanceId": "mse-cn-st21ri2****",
    "ErrorCode": "mse-100-000",
    "OrderId": "20574710974****",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

