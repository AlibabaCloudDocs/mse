# CreateAuthTicket

调用CreateAuthTicket创建凭证。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /v1/auth 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
| |Object|Body|否| |凭证相关参数。 |
|comment|String|Body|否|doctest|凭证的备注信息，多用于标识凭证的作用。 |
|gatewayId|Long|Body|否|70|凭证所属网关ID。 |
|name|String|Body|否|JWTtest|凭证名称，仅限字母、数字和下划线（\_），最长16个字符，必须以字母开头。 |
|ticketType|String|Body|否|JWT|凭证类型，目前支持以下两种类型：

 -   **JWT**
-   **JWT-SIGNER** |
|duration|Long|Body|否|30|凭证有效期，支持设置**短期**和**长期**。

 -   **短期**：包含30、180和365天，或任意时间。
-   **长期**：3年。 |
|jwtSignatureTypeEnum|String|Body|否|RS256|当**ticketType**为**JWT\_SIGNER**类型时，所选择的签名算法，取值如下：

 -   RS256
-   RS384
-   RS512
-   HS256
-   HS512
-   HS384 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|返回码。 |
|data|Map| |创建凭证返回的详细信息。 |
|message|String|success|返回信息。 |

## 示例

请求示例

```
POST /v1/auth HTTP/1.1 
 {
	"data":{
		"name":"JWTtest",
		"validDuration":"30",
		"comment":"doctest",
		"ticketType":"JWT",
		"gatewayId":"70"
	}
}
```

正常返回示例

`XML` 格式

```
<CreateAuthTicketResponse>
  <code>200</code>
  <message>success</message>
</CreateAuthTicketResponse>
```

`JSON` 格式

```
{
    "code": "200",
    "message": "success"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/microgw)查看更多错误码。

