# DeleteGateway

调用DeleteGateway删除网关。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
DELETE /v1/gateway/{gatewayId} 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|gatewayId|Long|Path|否|70|需要删除的网关ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|返回码。 |
|data|Map| |删除网关返回的详细信息。 |
|message|String|success|返回信息。 |

## 示例

请求示例

```
DELETE /v1/gateway/{gatewayId} HTTP/1.1 
 {
	"gatewayId":"70"
}
```

正常返回示例

`XML` 格式

```
<DeleteGatewayResponse>
  <code>200</code>
  <message>success</message>
</DeleteGatewayResponse>
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

