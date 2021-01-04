# FindGateways

调用FindGateways查询网关。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
GET /v1/gateway 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|gatewayUniqueId|String|Query|否|70|需要查询的网关ID。 |
|name|String|Query|否|Test|网关名称。 |
|region|String|Query|否|cn-hangzhou|网关所在地域。 |
|gatewayTypes|String|Query|否|Zuul|网关引擎类型，目前包含**Zuul**、**Kong**和**Spring Cloud Gateway** 3种类型。 |
|status|String|Query|否|2|网关状态。取值如下：

 -   **0**：创建中
-   **2**：运行中
-   **4**：缩容中
-   **6**：扩容中
-   **8**：回收中
-   **9**：欠费停服中
-   **10**：重启中 |
|pageNumber|String|Query|否|2|页码。 |
|pageSize|String|Query|否|10|每页显示的网关数量，包含**5**、**10**和**20**。 |
|namespace|String|Query|否|none|命名空间。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|返回码。 |
|data|object| |查询网关返回的详细信息。 |
|list|Array of data| |网关列表。 |
|armsInfo|object| |ARMS商业版信息。 |
|appId|String|gg01myzq\*\*\*\*|ARMS应用ID。 |
|appName|String|ahas-1670\*\*\*\*-cn-hangzhou|ARMS应用APP名称。 |
|description|String|doctest|网关描述。 |
|licenseKey|String|gg01myzq\*\*\*\*|ARMS应用许可密钥。 |
|autoCreateSlb|Boolean|true|是否新建SLB。取值如下：

 -   **true**：新建SLB。
-   **false**：选择已有SLB。 |
|basePath|String|/abc|基本路径。 |
|creationDateTime|String|2020-09-22 20:29:45|网关创建时间。 |
|edasNamespaceId|String|test|EDAS命名空间。 |
|gatewayType|String|Zuul|网关引擎类型，目前支持**ZUUL**、**Kong**和**Spring Cloud Gateway**三种引擎类型。 |
|id|Long|1|网关ID。 |
|name|String|doctest|网关名称。 |
|podCidr|String|2|网关节点数量。 |
|region|String|cn-shenzhen|网关所属地域。 |
|regionName|String|shenzhen|网关所属地域名称。 |
|replica|Long|1|集群节点数。 |
|runtimeOn|String|ECS|后端服务运行平台。取值如下：

 -   **ACK**：网关运行在ACK集群。
-   **ECS**：网关运行在ECS集群。 |
|securityGroup|String|sg-wz9ba0uq29fqfs6e\*\*\*\*|选定VPC下的安全组。 |
|slb|String|lb-wz95esf4jd3khmy96\*\*\*\*|SLB实例。 |
|slbAccessAddr|String|http://10.0.0.8:80|SLB访问地址。 |
|status|String|运行中|网关状态。取值如下：

 -   **0**：创建中
-   **2**：运行中
-   **4**：缩容中
-   **6**：扩容中
-   **8**：回收中
-   **9**：欠费停服中
-   **10**：重启中 |
|vpc|String|doctest-vpc（vpc-wz9ssjxyeitqu5umq\*\*\*\*）|专有网络VPC。 |
|vswitch|String|doctest-switch（vsw-wz93whpnyx9z62iwe\*\*\*\*）|选定VPC下的虚拟交换机。 |
|totalCount|Long|3|符合查询条件的网关数量。 |
|message|String|success|返回信息。 |

## 示例

请求示例

```
GET /v1/gateway HTTP/1.1 
 {
    "pageNumber":"2",
    "gatewayTypes":"Zuul",
    "name":"Test",
    "pageSize":"10",
    "region":"cn-hangzhou",
    "gatewayUniqueId":"70"
}
```

正常返回示例

`XML` 格式

```
<FindGatewaysResponse>
  <code>200</code>
  <data>
        <list>
              <replica>1</replica>
              <regionName>shenzhen</regionName>
              <slb>lb-wz95esf4jd3khmy96****</slb>
              <vpc>doctest-vpc（vpc-wz9ssjxyeitqu5umq****）</vpc>
              <runtimeOn>ECS</runtimeOn>
              <securityGroup>sg-wz9ba0uq29fqfs6e****</securityGroup>
              <slbAccessAddr>http://10.0.0.8:80</slbAccessAddr>
              <vswitch>doctest-switch（vsw-wz93whpnyx9z62iwe****）</vswitch>
              <gatewayType>Zuul</gatewayType>
              <basePath>/abc</basePath>
              <armsInfo>
                    <licenseKey>gg01myzq****</licenseKey>
                    <appName>ahas-1670****-cn-hangzhou</appName>
                    <appId>gg01myzq****</appId>
                    <description>doctest</description>
              </armsInfo>
              <autoCreateSlb>true</autoCreateSlb>
              <edasNamespaceId>test</edasNamespaceId>
              <name>doctest</name>
              <id>1</id>
              <podCidr>2</podCidr>
              <region>cn-shenzhen</region>
              <creationDateTime>2020-09-22 20:29:45</creationDateTime>
              <status>运行中</status>
        </list>
        <totalCount>3</totalCount>
  </data>
  <message>success</message>
</FindGatewaysResponse>
```

`JSON` 格式

```
{
    "code": "200",
    "data": {
        "list": [
            {
                "replica": "1",
                "regionName": "shenzhen",
                "slb": "lb-wz95esf4jd3khmy96****",
                "vpc": "doctest-vpc（vpc-wz9ssjxyeitqu5umq****）",
                "runtimeOn": "ECS",
                "securityGroup": "sg-wz9ba0uq29fqfs6e****",
                "slbAccessAddr": "http://10.0.0.8:80",
                "vswitch": "doctest-switch（vsw-wz93whpnyx9z62iwe****）",
                "gatewayType": "Zuul",
                "basePath": "/abc",
                "armsInfo": {
                    "licenseKey": "gg01myzq****",
                    "appName": "ahas-1670****-cn-hangzhou",
                    "appId": "gg01myzq****",
                    "description": "doctest"
                },
                "autoCreateSlb": "true",
                "edasNamespaceId": "test",
                "name": "doctest",
                "id": "1",
                "podCidr": "2",
                "region": "cn-shenzhen",
                "creationDateTime": "2020-09-22 20:29:45",
                "status": "运行中"
            }
        ],
        "totalCount": "3"
    },
    "message": "success"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/microgw)查看更多错误码。

