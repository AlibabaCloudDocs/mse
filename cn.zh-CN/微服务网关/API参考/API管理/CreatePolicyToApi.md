# CreatePolicyToApi

调用CreatePolicyToApi为指定API创建策略。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /v1/api/{apiId}/policy 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|apiId|Long|Path|否|69|API唯一ID。 |
| |Object|Body|否| |策略相关参数。 |
|creationDateTime|String|Body|否|2020-08-14 15:28:43|策略创建时间。 |
|direction|String|Body|否|INBOUND|策略的作用方向。取值如下：

 -   **OUTBOUND**：出方向
-   **INBOUND**：入方向 |
|policyAliasName|String|Body|否|route|策略别名。 |
|policyContent|String|Body|否|zuul:\\n|策略内容。 |
|policyGroup|String|Body|否|zuul|策略所属策略组。 |
|policyId|Long|Body|否|1|策略ID。 |
|policyName|String|Body|否|route|策略名称。 |
|priority|Long|Body|否|0|策略优先级，0和正整数，数字越大优先级越高。 |
|scope|String|Body|否|REQUEST|策略作用范围。取值如下：

 -   **REQUEST**：请求处理
-   **RESPONSE**：响应处理
-   **BACKEND**：后端处理
-   **EXCEPTION**：异常处理 |
|status|Boolean|Body|否|true|策略状态。取值如下：

 -   **true**：启用策略
-   **false**：不启用策略 |
|type|Long|Body|否|0|策略类型。由策略组类型、策略code和网关类型三个参数确定策略类型。

 例：ZUUL\(PolicyGroupEnum.ROUTE, "ZUUL", 0, GatewayType.ZUUL\) |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|状态码。 |
|data|Map| |返回数据。 |
|message|String|success|错误信息。 |

## 示例

请求示例

```
POST /v1/api/69/policy HTTP/1.1 
 {
	"data":{
		"policyId":"1",
		"policyName":"route",
		"scope":"REQUEST",
		"policyAliasName":"route",
		"policyGroup":"zuul",
		"priority":"0",
		"type":"0",
		"policyContent":"zuul:\\n",
		"creationDateTime":"2020-08-14 15:28:43",
		"direction":"INBOUND",
		"status":"true"
	}
}
```

正常返回示例

`XML` 格式

```
<CreatePolicyToApiResponse>
  <code>200</code>
  <message>success</message>
</CreatePolicyToApiResponse>
```

`JSON` 格式

```
{
    "code": "200",
    "message": "success"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|param\_error|The param is must be in ...| |
|403|ACCESS\_FORBIDEN|The param is must be in ...| |

访问[错误中心](https://error-center.aliyun.com/status/product/microgw)查看更多错误码。

