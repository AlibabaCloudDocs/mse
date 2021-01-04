# FindApisByPaging

调用FindApisByPaging批量查询API。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
GET /v1/gateway/{gatewayId}/api 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|gatewayId|Long|Path|否|70|API所属网关的ID。 |
|pageNumber|Long|Query|否|2|页码。 |
|pageSize|Long|Query|否|10|每页显示的API数量，可设置为**5**、**10**和**20**。 |
|status|String|Query|否|3|API运行状态。取值如下：

 -   **0**：未发布
-   **1**：未发布，编辑中
-   **2**：发布中
-   **3**：已发布
-   **4**：已发布，编辑中
-   **5**：回收中 |
|name|String|Query|否|Doctest|API名称。 |
|aliasName|String|Query|否|Doctest|API别名。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|状态码。 |
|data|object| |返回数据。 |
|list|Array of data| |查询得到的API列表。 |
|aliasName|String|Doctest|API别名。 |
|attachedServices|Array of attachedServices| |API关联服务的详细信息。 |
|aliasName|String|DoctestService|服务别名。 |
|creationDateTime|String|2020-09-22 20:09:05|服务创建时间。 |
|description|String|Doctest|服务描述信息。 |
|id|Long|0|无需填写。 |
|isAutoRefresh|Boolean|true|是否自动刷新后端节点。取值如下：

 -   **true**：根据节点变化自动刷新。
-   **false**：不自动刷新。 |
|isHealth|Boolean|0|服务健康状态。取值如下：

 -   **0**：健康
-   **1**：不健康 |
|name|String|DoctestService|服务名称，仅限字母、数字和下划线（\_），最多64个字符，必须以字母开头。 |
|registryId|String|1|注册中心ID。 |
|serviceEnds|Array of serviceEnds| |服务列表。 |
|creationDateTime|String|2020-09-22 20:09:05|服务创建时间。 |
|id|Long|0|无需填写。 |
|ipAddress|String|192.168.0.124|服务的后端节点IP。 |
|port|String|8080|服务的后端节点端口。 |
|serviceId|Long|1|服务ID。 |
|status|Long|0|服务状态。取值如下：

 -   **0**：健康
-   **1**：不健康 |
|updateDateTime|String|2020-09-25 20:09:05|服务最近更新时间。 |
|serviceNameInRegistry|String|DoctestService|服务注册到注册中心的服务名称。 |
|sourceType|Long|0|服务来源。取值如下：

 -   **0**：注册中心
-   **1**：其他 |
|updateDateTime|String|2020-09-25 20:09:05|服务最近更新时间。 |
|basePath|String|/order/query|API访问路径。 |
|creationDateTime|String|2020-09-22 20:09:05|API创建时间。 |
|description|String|doctest|API描述信息。 |
|id|Long|1|API唯一ID。 |
|name|String|DOCtest|API名称。 |
|owneredPolicies|Array of owneredPolicies| |API所属策略的详细信息。 |
|apiId|Long|1|API唯一ID。 |
|apiName|String|DOCtest|API名称。 |
|creationDateTime|String|2020-08-14 15:30:53|策略创建时间。 |
|direction|String|INBOUND|策略的作用方向。取值如下：

 -   **INBOUND**：入方向
-   **OUTBOUND**：出方向 |
|id|Long|0|无需填写。 |
|policyAliasName|String|route|策略别名。 |
|policyContent|String|route|策略备注信息。 |
|policyGroup|String|route|策略组。 |
|policyId|String|1|策略ID。 |
|policyName|String|route|策略名称。 |
|priority|Long|0|策略优先级，0和正整数，数字越大优先级越高。 |
|scope|String|REQUEST|策略作用范围。取值如下：

 -   **REQUEST**：请求处理
-   **RESPONSE**：响应处理
-   **BACKEND**：后端处理
-   **EXCEPTION**：异常处理 |
|status|Boolean|true|策略状态。取值如下：

 -   **true**：启用策略
-   **false**：不启用策略 |
|type|Long|0|策略类型。由策略组类型、策略code和网关类型三个参数确定策略类型。

 例：ZUUL\(PolicyGroupEnum.ROUTE, "ZUUL", 0, GatewayType.ZUUL\) |
|updateDateTime|String|2020-09-24 10:51:45|策略更新时间。 |
|publishedGateway|object| |API所属网关的详细信息。 |
|armsInfo|String|0|是否安装ARMS商业化。取值如下：

 -   **0**：已安装
-   **1**：未安装 |
|autoCreateSlb|Boolean|true|是否新建SLB，取值如下：

 -   **true**：新建SLB。
-   **false**：选择已有SLB。 |
|basePath|String|/abc|网关的根目录。 |
|creationDateTime|String|2020-08-14 15:30:53|网关创建时间。 |
|edasNamespaceId|String|test|EDAS命名空间。 |
|gatewayType|String|ZUUL|网关引擎类型，目前支持**ZUUL**、**Kong**和**Spring Cloud Gateway**三种引擎类型。 |
|id|Long|0|无需填写。 |
|name|String|doctest|网关名称。 |
|podCidr|String|2|网关节点数量，目前支持设置为1~100个节点，强烈建议节点数不要少于2。如果是单节点，一旦出现问题，整个系统就存在瘫痪的风险。 |
|region|String|cn-shenzhen|网关所在地域。 |
|regionName|String|shenzhen|网关所在地域名称。 |
|replica|Long|2|集群节点数。 |
|runtimeOn|String|ECS|后端服务运行平台。取值如下：

 -   **ACK**：网关运行在ACK集群。
-   **ECS**：网关运行在ECS集群。 |
|securityGroup|String|sg-wz9ba0uq29fqfs6e\*\*\*\*|选定VPC下的安全组。 |
|slb|String|lb-wz95esf4jd3khmy96\*\*\*\*|SLB实例。 |
|slbAccessAddr|String|192.168.0.1|SLB实例的IP地址。 |
|status|String|2|网关状态。取值如下：

 -   **0**：创建中
-   **2**：运行中
-   **4**：缩容中
-   **6**：扩容中
-   **8**：回收中
-   **9**：欠费停服中
-   **10**：重启中 |
|vpc|String|doctest-vpc（vpc-wz9ssjxyeitqu5umq\*\*\*\*）|专有网络VPC。 |
|vswitch|String|doctest-switch（vsw-wz93whpnyx9z62iwe\*\*\*\*）|选定VPC下的虚拟交换机。 |
|status|String|3|API运行状态。取值如下：

 -   **0**：未发布
-   **1**：未发布，编辑中
-   **2**：发布中
-   **3**：已发布
-   **4**：已发布，编辑中
-   **5**：回收中 |
|updateDateTime|String|2020-09-26 20:09:05|API更新时间。 |
|totalCount|Long|2|符合查询条件的API数量。 |
|message|String|success|错误信息。 |

## 示例

请求示例

```
GET /v1/gateway/70/api HTTP/1.1 
 {
	"aliasName":"Doctest",
	"pageNumber":"2",
	"name":"Doctest",
	"pageSize":"10",
	"status":"3"
}
```

正常返回示例

`XML` 格式

```
<FindApisByPagingResponse>
  <code>200</code>
  <data>
        <list>
              <aliasName>Doctest</aliasName>
              <attachedServices>
                    <aliasName>DoctestService</aliasName>
                    <serviceEnds>
                          <port>8080</port>
                          <ipAddress>192.168.0.124</ipAddress>
                          <id>0</id>
                          <serviceId>1</serviceId>
                          <updateDateTime>2020-09-25 20:09:05</updateDateTime>
                          <creationDateTime>2020-09-22 20:09:05</creationDateTime>
                          <status>0</status>
                    </serviceEnds>
                    <sourceType>0</sourceType>
                    <isHealth>0</isHealth>
                    <name>DoctestService</name>
                    <description>Doctest</description>
                    <registryId>1</registryId>
                    <id>0</id>
                    <serviceNameInRegistry>DoctestService</serviceNameInRegistry>
                    <updateDateTime>2020-09-25 20:09:05</updateDateTime>
                    <isAutoRefresh>true</isAutoRefresh>
                    <creationDateTime>2020-09-22 20:09:05</creationDateTime>
              </attachedServices>
              <basePath>/order/query</basePath>
              <name>DOCtest</name>
              <description>doctest</description>
              <id>1</id>
              <publishedGateway>
                    <replica>2</replica>
                    <regionName>shenzhen</regionName>
                    <slb>lb-wz95esf4jd3khmy96****	</slb>
                    <vpc>doctest-vpc（vpc-wz9ssjxyeitqu5umq****）</vpc>
                    <runtimeOn>ECS</runtimeOn>
                    <securityGroup>sg-wz9ba0uq29fqfs6e****	</securityGroup>
                    <slbAccessAddr>192.168.0.1</slbAccessAddr>
                    <vswitch>doctest-switch（vsw-wz93whpnyx9z62iwe****）	</vswitch>
                    <gatewayType>ZUUL</gatewayType>
                    <basePath>/abc</basePath>
                    <armsInfo>0</armsInfo>
                    <autoCreateSlb>true</autoCreateSlb>
                    <edasNamespaceId>test</edasNamespaceId>
                    <name>doctest</name>
                    <id>0</id>
                    <podCidr>2</podCidr>
                    <region>cn-shenzhen</region>
                    <creationDateTime>2020-08-14 15:30:53</creationDateTime>
                    <status>2</status>
              </publishedGateway>
              <owneredPolicies>
                    <apiName>DOCtest</apiName>
                    <policyName>route</policyName>
                    <policyAliasName>route</policyAliasName>
                    <policyGroup>route</policyGroup>
                    <priority>0</priority>
                    <type>0</type>
                    <policyContent>route</policyContent>
                    <policyId>1</policyId>
                    <scope>REQUEST</scope>
                    <id>0</id>
                    <updateDateTime>2020-09-24 10:51:45	</updateDateTime>
                    <apiId>1</apiId>
                    <creationDateTime>2020-08-14 15:30:53</creationDateTime>
                    <direction>INBOUND</direction>
                    <status>true</status>
              </owneredPolicies>
              <updateDateTime>2020-09-26 20:09:05</updateDateTime>
              <creationDateTime>2020-09-22 20:09:05</creationDateTime>
              <status>3</status>
        </list>
        <totalCount>2</totalCount>
  </data>
  <message>success</message>
</FindApisByPagingResponse>
```

`JSON` 格式

```
{
    "code": "200",
    "data": {
        "list": [
            {
                "aliasName": "Doctest",
                "attachedServices": [
                    {
                        "aliasName": "DoctestService",
                        "serviceEnds": [
                            {
                                "port": "8080",
                                "ipAddress": "192.168.0.124",
                                "id": "0",
                                "serviceId": "1",
                                "updateDateTime": "2020-09-25 20:09:05",
                                "creationDateTime": "2020-09-22 20:09:05",
                                "status": "0"
                            }
                        ],
                        "sourceType": "0",
                        "isHealth": "0",
                        "name": "DoctestService",
                        "description": "Doctest",
                        "registryId": "1",
                        "id": "0",
                        "serviceNameInRegistry": "DoctestService",
                        "updateDateTime": "2020-09-25 20:09:05",
                        "isAutoRefresh": "true",
                        "creationDateTime": "2020-09-22 20:09:05"
                    }
                ],
                "basePath": "/order/query",
                "name": "DOCtest",
                "description": "doctest",
                "id": "1",
                "publishedGateway": {
                    "replica": "2",
                    "regionName": "shenzhen",
                    "slb": "lb-wz95esf4jd3khmy96****\t",
                    "vpc": "doctest-vpc（vpc-wz9ssjxyeitqu5umq****）",
                    "runtimeOn": "ECS",
                    "securityGroup": "sg-wz9ba0uq29fqfs6e****\t",
                    "slbAccessAddr": "192.168.0.1",
                    "vswitch": "doctest-switch（vsw-wz93whpnyx9z62iwe****）\t",
                    "gatewayType": "ZUUL",
                    "basePath": "/abc",
                    "armsInfo": "0",
                    "autoCreateSlb": "true",
                    "edasNamespaceId": "test",
                    "name": "doctest",
                    "id": "0",
                    "podCidr": "2",
                    "region": "cn-shenzhen",
                    "creationDateTime": "2020-08-14 15:30:53",
                    "status": "2"
                },
                "owneredPolicies": [
                    {
                        "apiName": "DOCtest",
                        "policyName": "route",
                        "policyAliasName": "route",
                        "policyGroup": "route",
                        "priority": "0",
                        "type": "0",
                        "policyContent": "route",
                        "policyId": "1",
                        "scope": "REQUEST",
                        "id": "0",
                        "updateDateTime": "2020-09-24 10:51:45\t",
                        "apiId": "1",
                        "creationDateTime": "2020-08-14 15:30:53",
                        "direction": "INBOUND",
                        "status": "true"
                    }
                ],
                "updateDateTime": "2020-09-26 20:09:05",
                "creationDateTime": "2020-09-22 20:09:05",
                "status": "3"
            }
        ],
        "totalCount": "2"
    },
    "message": "success"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|param\_error|The param is must be in ...| |
|403|ACCESS\_FORBIDEN|The param is must be in ...| |

访问[错误中心](https://error-center.aliyun.com/status/product/microgw)查看更多错误码。

