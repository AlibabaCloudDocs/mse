# GetApiDetail

调用GetApiDetail查询API详情。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
GET /v1/api/{apiId} 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|apiId|Long|Path|否|68|API唯一ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|状态码。 |
|data|Array of data| |返回数据。 |
|aliasName|String|DOCtest|API别名。 |
|attachedServices|Array of attachedServices| |API关联服务的详细信息。 |
|aliasName|String|DOCtestService|服务别名。 |
|creationDateTime|String|2020-09-23 11:08:17|服务创建时间。 |
|description|String|DoctestService|服务的描述信息。 |
|id|Long|0|无需填写。 |
|isAutoRefresh|Boolean|Yes|节点是否自动刷新，取值如下：

 -   **Yes**：自动刷新，根据后端节点变化而变化。
-   **False**：不自动刷新，保持初始后端节点。 |
|isHealth|Boolean|0|服务的健康状态。取值如下：

 -   **0**：健康
-   **1**：不健康 |
|name|String|DOCtestService|服务名称。 |
|registryId|String|1|服务注册的注册中心ID。 |
|serviceEnds|Array of serviceEnds| |服务列表。 |
|creationDateTime|String|2020-09-23 11:08:17|服务创建时间。 |
|id|Long|0|无需填写。 |
|ipAddress|String|192.168.0.125|服务的后端节点IP。 |
|port|String|8080|服务的后端节点端口。 |
|serviceId|Long|1|服务ID。 |
|status|Long|0|服务的健康状态。取值如下：

 -   **0**：健康
-   **1**：不健康 |
|updateDateTime|String|2020-09-25 11:08:17|服务的更新时间。 |
|serviceNameInRegistry|String|DoctestService|服务注册到注册中心的名称。 |
|sourceType|Long|0|服务来源。取值如下：

 -   **0**：注册中心
-   **1**：其他 |
|updateDateTime|String|2020-09-25 11:08:17|API的更新时间。 |
|basePath|String|/order/query|API的访问路径。 |
|creationDateTime|String|2020-09-23 11:08:17|API的创建时间。 |
|description|String|DOCtest|API的描述信息。 |
|id|Long|0|无需填写。 |
|name|String|DOCtest|API名称。 |
|owneredPolicies|Array of owneredPolicies| |所属API的策略详细信息。 |
|apiId|Long|68|API唯一ID。 |
|apiName|String|DOCtest|API名称。 |
|creationDateTime|String|2020-09-23 11:24:00|策略创建时间。 |
|direction|String|DOCtest|策略的描述信息。 |
|id|Long|0|无需填写 |
|policyAliasName|String|route|策略别名。 |
|policyContent|String|zuul:\\n|策略内容。 |
|policyGroup|String|zuul|策略所属策略组。 |
|policyId|String|1|策略ID。 |
|policyName|String|route|策略名称。 |
|priority|Long|0|策略优先级，0和正整数，数字越大优先级越高。 |
|scope|String|response|策略作用范围。取值如下：

 -   **REQUEST**：请求处理
-   **RESPONSE**：响应处理
-   **BACKEND**：后端处理
-   **EXCEPTION**：异常处理 |
|status|Boolean|true|策略状态。取值如下：

 -   **true**：启用策略
-   **false**：不启用策略 |
|type|Long|0|策略类型。由策略组类型、策略code和网关类型三个参数确定策略类型。

 例：ZUUL\(PolicyGroupEnum.ROUTE, "ZUUL", 0, GatewayType.ZUUL\) |
|updateDateTime|String|2020-09-25 11:24:00|策略的更新时间。 |
|publishedGateway|object| |API所属网关的详细信息。 |
|armsInfo|String|0|是否安装了ARMS商业版。取值如下：

 -   **0**：已安装
-   **1**：未安装 |
|autoCreateSlb|Boolean|true|是否新建SLB，取值如下：

 -   **true**：新建SLB。
-   **false**：选择已有SLB。 |
|basePath|String|/abc|网关的根路径。 |
|creationDateTime|String|2020-09-22 20:09:05|网关创建时间。 |
|edasNamespaceId|String|test|EDAS命名空间。 |
|gatewayType|String|ZUUL|网关引擎类型，目前支持**ZUUL**、**Kong**和**Spring Cloud Gateway**三种引擎类型。 |
|id|Long|0|无需填写。 |
|name|String|doctest|网关名称。 |
|podCidr|String|2|网关节点数量，支持1~100个节点，强烈建议节点数不要少于2。如果是单节点，一旦出现问题，整个系统就存在瘫痪的风险。 |
|region|String|cn-shenzhen|网关所在地域。 |
|regionName|String|shenzhen|地域名称。 |
|replica|Long|2|集群节点数。 |
|runtimeOn|String|ECS|后端服务运行平台。取值如下：

 -   **ACK**：网关运行在ACK集群。
-   **ECS**：网关运行在ECS集群。 |
|securityGroup|String|sg-wz9ba0uq29fqfs6e\*\*\*\*|选定VPC下的安全组。 |
|slb|String|lb-wz95esf4jd3khmy96\*\*\*\*|SLB实例。 |
|slbAccessAddr|String|http://10.0.0.8:80|SLB访问地址。 |
|status|String|2|网关状态。取值如下：

 -   **0**：创建中
-   **2**：运行中
-   **4**：缩容中
-   **6**：扩容中
-   **8**：回收中
-   **9**：欠费停服中
-   **10**：重启中 |
|vpc|String|doctest-vpc（vpc-wz9ssjxyeitqu5umq\*\*\*\*）|微服务所在的专有网络VPC。 |
|vswitch|String|doctest-switch（vsw-wz93whpnyx9z62iwe\*\*\*\*）|选定VPC下的虚拟交换机。 |
|status|String|3|API状态。取值如下：

 -   **0**：未发布
-   **1**；未发布，编辑中
-   **2**：发布中
-   **3**：已发布
-   **4**：已发布，编辑中
-   **5**：回收中 |
|updateDateTime|String|2020-09-25 20:09:05|API更新时间。 |
|message|String|success|错误信息。 |

## 示例

请求示例

```
GET /v1/api/{apiId} HTTP/1.1 
 {
	"apiId":"68"
}
```

正常返回示例

`XML` 格式

```
<GetApiDetailResponse>
  <code>200</code>
  <data>
        <aliasName>DOCtest</aliasName>
        <attachedServices>
              <aliasName>DOCtestService</aliasName>
              <serviceEnds>
                    <port>8080</port>
                    <ipAddress>192.168.0.125</ipAddress>
                    <id>0</id>
                    <serviceId>1</serviceId>
                    <updateDateTime>2020-09-25 11:08:17</updateDateTime>
                    <creationDateTime>2020-09-23 11:08:17</creationDateTime>
                    <status>0</status>
              </serviceEnds>
              <sourceType>0</sourceType>
              <isHealth>0</isHealth>
              <name>DOCtestService</name>
              <description>DoctestService</description>
              <registryId>1</registryId>
              <id>0</id>
              <serviceNameInRegistry>DoctestService</serviceNameInRegistry>
              <updateDateTime>2020-09-25 11:08:17</updateDateTime>
              <isAutoRefresh>Yes</isAutoRefresh>
              <creationDateTime>2020-09-23 11:08:17</creationDateTime>
        </attachedServices>
        <basePath>/order/query</basePath>
        <name>DOCtest</name>
        <description>DOCtest</description>
        <id>0</id>
        <publishedGateway>
              <replica>2</replica>
              <regionName>shenzhen</regionName>
              <slb>lb-wz95esf4jd3khmy96****</slb>
              <vpc>doctest-vpc（vpc-wz9ssjxyeitqu5umq****）</vpc>
              <runtimeOn>ECS</runtimeOn>
              <securityGroup>sg-wz9ba0uq29fqfs6e****</securityGroup>
              <slbAccessAddr>http://10.0.0.8:80</slbAccessAddr>
              <vswitch>doctest-switch（vsw-wz93whpnyx9z62iwe****）</vswitch>
              <gatewayType>ZUUL</gatewayType>
              <basePath>/abc</basePath>
              <armsInfo>0</armsInfo>
              <autoCreateSlb>true</autoCreateSlb>
              <edasNamespaceId>test</edasNamespaceId>
              <name>doctest	</name>
              <id>0</id>
              <podCidr>2</podCidr>
              <region>cn-shenzhen</region>
              <creationDateTime>2020-09-22 20:09:05</creationDateTime>
              <status>2</status>
        </publishedGateway>
        <owneredPolicies>
              <apiName>DOCtest</apiName>
              <policyName>route</policyName>
              <policyAliasName>route</policyAliasName>
              <policyGroup>zuul</policyGroup>
              <priority>0</priority>
              <type>0</type>
              <policyContent>zuul:\n</policyContent>
              <policyId>1</policyId>
              <scope>response</scope>
              <id>0</id>
              <updateDateTime>2020-09-25 11:24:00</updateDateTime>
              <apiId>68</apiId>
              <creationDateTime>2020-09-23 11:24:00</creationDateTime>
              <direction>DOCtest</direction>
              <status>true</status>
        </owneredPolicies>
        <updateDateTime>2020-09-25 20:09:05</updateDateTime>
        <creationDateTime>2020-09-23 11:08:17</creationDateTime>
        <status>3</status>
  </data>
  <message>success</message>
</GetApiDetailResponse>
```

`JSON` 格式

```
{
    "code": "200",
    "data": [
        {
            "aliasName": "DOCtest",
            "attachedServices": [
                {
                    "aliasName": "DOCtestService",
                    "serviceEnds": [
                        {
                            "port": "8080",
                            "ipAddress": "192.168.0.125",
                            "id": "0",
                            "serviceId": "1",
                            "updateDateTime": "2020-09-25 11:08:17",
                            "creationDateTime": "2020-09-23 11:08:17",
                            "status": "0"
                        }
                    ],
                    "sourceType": "0",
                    "isHealth": "0",
                    "name": "DOCtestService",
                    "description": "DoctestService",
                    "registryId": "1",
                    "id": "0",
                    "serviceNameInRegistry": "DoctestService",
                    "updateDateTime": "2020-09-25 11:08:17",
                    "isAutoRefresh": "Yes",
                    "creationDateTime": "2020-09-23 11:08:17"
                }
            ],
            "basePath": "/order/query",
            "name": "DOCtest",
            "description": "DOCtest",
            "id": "0",
            "publishedGateway": {
                "replica": "2",
                "regionName": "shenzhen",
                "slb": "lb-wz95esf4jd3khmy96****",
                "vpc": "doctest-vpc（vpc-wz9ssjxyeitqu5umq****）",
                "runtimeOn": "ECS",
                "securityGroup": "sg-wz9ba0uq29fqfs6e****",
                "slbAccessAddr": "http://10.0.0.8:80",
                "vswitch": "doctest-switch（vsw-wz93whpnyx9z62iwe****）",
                "gatewayType": "ZUUL",
                "basePath": "/abc",
                "armsInfo": "0",
                "autoCreateSlb": "true",
                "edasNamespaceId": "test",
                "name": "doctest\t",
                "id": "0",
                "podCidr": "2",
                "region": "cn-shenzhen",
                "creationDateTime": "2020-09-22 20:09:05",
                "status": "2"
            },
            "owneredPolicies": [
                {
                    "apiName": "DOCtest",
                    "policyName": "route",
                    "policyAliasName": "route",
                    "policyGroup": "zuul",
                    "priority": "0",
                    "type": "0",
                    "policyContent": "zuul:\\n",
                    "policyId": "1",
                    "scope": "response",
                    "id": "0",
                    "updateDateTime": "2020-09-25 11:24:00",
                    "apiId": "68",
                    "creationDateTime": "2020-09-23 11:24:00",
                    "direction": "DOCtest",
                    "status": "true"
                }
            ],
            "updateDateTime": "2020-09-25 20:09:05",
            "creationDateTime": "2020-09-23 11:08:17",
            "status": "3"
        }
    ],
    "message": "success"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|param\_error|The param is must be in ...| |
|403|ACCESS\_FORBIDEN|The param is must be in ...| |

访问[错误中心](https://error-center.aliyun.com/status/product/microgw)查看更多错误码。

