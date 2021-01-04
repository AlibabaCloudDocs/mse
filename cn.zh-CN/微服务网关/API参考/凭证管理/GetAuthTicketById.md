# GetAuthTicketById

调用GetAuthTicketById查询凭证详情。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
GET /v1/auth/{ticketId} 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|ticketId|Long|Path|否|1|凭证ID。 |
|cookie|Map|Header|否| |请求头。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|返回码。 |
|data|Array of data| |查询凭证详情返回的详细信息。 |
|clientToken|String|eyJhbGciOiJSUzUx\*\*\*\*|凭证的Client Token值，可在控制台**凭证详情**页面查看。 |
|comment|String|Doctest|凭证备注信息。 |
|id|Long|0|无需设置。 |
|name|String|JWTtest|凭证名称。 |
|serverKey|String|\{"kty":"RSA","kid":"9c901c45-0ef0-4bda-a4e2-8307012c\*\*\*\*"\}|凭证的Server Key值，可在控制台**凭证详情**页面查看。 |
|ticketType|String|JWT|凭证类型，目前支持**JWT**和**JWT-SIGNER**两种类型。 |
|validEndTime|String|2020-07-23 11:12:28|凭证到期时间。 |
|validStartTime|String|2020-06-23 11:12:28|凭证创建时间。 |
|message|String|success|返回信息。 |

## 示例

请求示例

```
GET /v1/auth/{ticketId} HTTP/1.1 
 {
	"ticketId":"1"
}
```

正常返回示例

`XML` 格式

```
<GetAuthTicketByIdResponse>
  <code>200</code>
  <data>
        <validEndTime>2020-07-23 11:12:28</validEndTime>
        <validStartTime>2020-06-23 11:12:28</validStartTime>
        <clientToken>eyJhbGciOiJSUzUx****</clientToken>
        <serverKey>{"kty":"RSA","kid":"9c901c45-0ef0-4bda-a4e2-8307012c****"}</serverKey>
        <name>JWTtest</name>
        <comment>Doctest</comment>
        <ticketType>JWT</ticketType>
        <id>1</id>
  </data>
  <message>success</message>
</GetAuthTicketByIdResponse>
```

`JSON` 格式

```
{
    "code": "200",
    "data": [
        {
            "validEndTime": "2020-07-23 11:12:28",
            "validStartTime": "2020-06-23 11:12:28",
            "clientToken": "eyJhbGciOiJSUzUx****",
            "serverKey": "{\"kty\":\"RSA\",\"kid\":\"9c901c45-0ef0-4bda-a4e2-8307012c****\"}",
            "name": "JWTtest",
            "comment": "Doctest",
            "ticketType": "JWT",
            "id": "1"
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

