# GetPolicyOwnedByApi

调用GetPolicyOwnedByApi查询API所属的策略。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
GET /v1/api/{apiId}/policy 
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
|scopes|Map| |返回策略相关数据。 |
| |Array| |返回数据。 |
|apiId|Long|68|策略所属API的唯一ID。 |
|apiName|String|Doctest|API名称。 |
|creationDateTime|String|2020-08-14 15:30:53|策略创建时间。 |
|direction|String|INBOUND|策略的作用方向。取值如下：

 **INBOUND**：入方向

 **OUTBOUND**：出方向 |
|id|Long|0|无需填写。 |
|policyAliasName|String|route|策略别名。 |
|policyContent|String|zuul:\\route:\\n|策略内容。 |
|policyGroup|String|zuul|策略组。 |
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
|message|String|success|返回信息。 |

## 示例

请求示例

```
GET /v1/api/{apiId}/policy HTTP/1.1 
 {
	"apiId":"68"
}
```

正常返回示例

`XML` 格式

```
<GetPolicyOwnedByApiResponse>
  <code>200</code>
  <data>
        <scopes>
              <key>
                    <apiName>Doctest</apiName>
                    <policyName>route</policyName>
                    <policyAliasName>route</policyAliasName>
                    <policyGroup>zuul</policyGroup>
                    <priority>0</priority>
                    <type>0</type>
                    <policyContent>zuul:\route:\n</policyContent>
                    <policyId>1</policyId>
                    <scope>REQUEST</scope>
                    <id>0</id>
                    <updateDateTime>2020-09-24 10:51:45</updateDateTime>
                    <apiId>68</apiId>
                    <creationDateTime>2020-08-14 15:30:53</creationDateTime>
                    <direction>INBOUND</direction>
                    <status>true</status>
              </key>
        </scopes>
  </data>
  <message>success</message>
</GetPolicyOwnedByApiResponse>
```

`JSON` 格式

```
{
    "code": "200",
    "data": [
        {
            "scopes": {
                "key": [
                    {
                        "apiName": "Doctest",
                        "policyName": "route",
                        "policyAliasName": "route",
                        "policyGroup": "zuul",
                        "priority": "0",
                        "type": "0",
                        "policyContent": "zuul:\\route:\\n",
                        "policyId": "1",
                        "scope": "REQUEST",
                        "id": "0",
                        "updateDateTime": "2020-09-24 10:51:45",
                        "apiId": "68",
                        "creationDateTime": "2020-08-14 15:30:53",
                        "direction": "INBOUND",
                        "status": "true"
                    }
                ]
            }
        }
    ],
    "message": "success"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/microgw)查看更多错误码。

