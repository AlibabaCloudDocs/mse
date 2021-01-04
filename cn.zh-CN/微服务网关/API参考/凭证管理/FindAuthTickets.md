# FindAuthTickets

调用FindAuthTickets查询凭证。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
GET /v1/auth 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|gatewayId|Long|Query|否|70|配置所属的网关ID。 |
|name|String|Query|否|JWTtest|凭证名称。 |
|pageNumber|Long|Query|否|2|页码。 |
|pageSize|Long|Query|否|10|每页显示凭证数量，包含**5**、**10**和**20**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|返回码。 |
|data|object| |查询凭证返回的详细信息。 |
|list|Array of list| |凭证列表。 |
|clientToken|String|eyJhbGciOiJSUzUx\*\*\*\*|凭证的Client Token，可在控制台**凭证详情**页面查看。 |
|comment|String|Doctest|凭证的备注信息。 |
|id|Long|58|凭证ID。 |
|name|String|JWTtest|凭证名称。 |
|serverKey|String|\{"kty":"RSA","kid":"9c901c45-0ef0-4bda-a4e2-8307012c\*\*\*\*"\}|凭证的Server Key，可在控制台**凭证详情**页面查看。 |
|ticketType|String|JWT|凭证类型，包含**JWT**和**JWT-SIGNER**。

 -   **JWT**：该类型的凭证会直接生成Client Token。
-   **JWT-SIGNER**：该类型的凭证则是生成Client Key，使用者再根据Client Key去生成Client Token。 |
|validEndTime|String|2020-11-22|凭证有效期。 |
|validStartTime|String|2020-10-22|凭证的创建时间，即凭证的生效时间。 |
|totalCount|Long|2|符合查询条件的凭证数量。 |
|message|String|success|错误信息，仅错误时返回错误信息。 |

## 示例

请求示例

```
GET /v1/auth HTTP/1.1 
 {
	"pageNumber":"2",
	"name":"JWTtest",
	"pageSize":"10",
	"gatewayId":"70"
}
```

正常返回示例

`XML` 格式

```
<FindAuthTicketsResponse>
  <code>200</code>
  <data>
        <list>
              <validEndTime>2020-11-22</validEndTime>
              <validStartTime>2020-10-22</validStartTime>
              <clientToken>eyJhbGciOiJSUzUx****</clientToken>
              <serverKey>{"kty":"RSA","kid":"9c901c45-0ef0-4bda-a4e2-8307012c****"}</serverKey>
              <name>JWTtest</name>
              <comment>Doctest</comment>
              <ticketType>JWT</ticketType>
              <id>58</id>
        </list>
        <totalCount>2</totalCount>
  </data>
  <message>success</message>
</FindAuthTicketsResponse>
```

`JSON` 格式

```
{
    "code": "200",
    "data": {
        "list": [
            {
                "validEndTime": "2020-11-22",
                "validStartTime": "2020-10-22",
                "clientToken": "eyJhbGciOiJSUzUx****",
                "serverKey": "{\"kty\":\"RSA\",\"kid\":\"9c901c45-0ef0-4bda-a4e2-8307012c****\"}",
                "name": "JWTtest",
                "comment": "Doctest",
                "ticketType": "JWT",
                "id": "58"
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

