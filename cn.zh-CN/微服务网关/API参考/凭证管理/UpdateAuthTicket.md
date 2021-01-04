# UpdateAuthTicket

调用UpdateAuthTicket更新凭证。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
PUT /v1/auth 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
| |Object|Body|否| |凭证相关参数。 |
|comment|String|Body|否|Doctest|凭证备注信息。 |
|id|Long|Body|否|1|凭证ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|返回码。 |
|data|Map| |更新凭证返回的详细信息。 |
|message|String|success|返回信息。 |

## 示例

请求示例

```
PUT /v1/auth HTTP/1.1 
 {
	"comment":"Doctest",
	"id":"1"
}
```

正常返回示例

`XML` 格式

```
<UpdateAuthTicketResponse>
  <code>200</code>
  <message>success</message>
</UpdateAuthTicketResponse>
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

