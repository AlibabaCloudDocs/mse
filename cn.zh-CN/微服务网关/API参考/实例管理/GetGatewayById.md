# GetGatewayById

调用GetGatewayById查询网关详情。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
GET /v1/gateway/{gatewayId} 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|gatewayId|Long|Path|否|70|网关ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|返回码。 |
|data|Array of data| |查询网关性情返回的详细信息。 |
|armsInfo|object| |ARMS相关参数。 |
|appId|String|1|应用ID。 |
|appName|String|doctest|应用名称。 |
|description|String|doctest|应用描述。 |
|licenseKey|String|iioe7\*\*\*\*@a0bcdaec2\*\*\*\*\*\*\*\*|应用的License Key。 |
|autoCreateSlb|Boolean|true|是否新建SLB，取值如下：

 -   **true**：新建SLB。
-   **false**：选择已有SLB。 |
|basePath|String|/abc|基本路径。 |
|creationDateTime|String|2020-10-29 21:16:11|网关创建时间。 |
|edasNamespaceId|String|test|EDAS命名空间。 |
|gatewayType|String|Zuul|网关引擎类型，目前支持**Zuul**、**Kong**和**Spring Cloud Gateway**三种引擎类型。 |
|id|Long|1|网关ID。 |
|name|String|doctest|网关名称。 |
|podCidr|String|2|网关节点数量，目前支持设置为1~100个节点，强烈建议不少于2个节点。 |
|region|String|cn-shenzhen|网关所在地域。 |
|regionName|String|shenzhen|网关所在地域名称。 |
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
|message|String|success|返回信息。 |

## 示例

请求示例

```
GET /v1/gateway/{gatewayId} HTTP/1.1 
 {
	"gatewayId":"70"
}
```

正常返回示例

`XML` 格式

```
<GetGatewayByIdResponse>
  <code>200</code>
  <data>
        <replica>2</replica>
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
              <licenseKey>iioe7****@a0bcdaec2********</licenseKey>
              <appName>doctest</appName>
              <appId>1</appId>
              <description>doctest</description>
        </armsInfo>
        <autoCreateSlb>true</autoCreateSlb>
        <edasNamespaceId>test</edasNamespaceId>
        <name>doctest	</name>
        <id>1</id>
        <podCidr>2</podCidr>
        <region>cn-shenzhen</region>
        <creationDateTime>2020-10-29 21:16:11</creationDateTime>
        <status>2</status>
  </data>
  <message>success</message>
</GetGatewayByIdResponse>
```

`JSON` 格式

```
{
    "code": "200",
    "data": [
        {
            "replica": "2",
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
                "licenseKey": "iioe7****@a0bcdaec2********",
                "appName": "doctest",
                "appId": "1",
                "description": "doctest"
            },
            "autoCreateSlb": "true",
            "edasNamespaceId": "test",
            "name": "doctest\t",
            "id": "1",
            "podCidr": "2",
            "region": "cn-shenzhen",
            "creationDateTime": "2020-10-29 21:16:11",
            "status": "2"
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

