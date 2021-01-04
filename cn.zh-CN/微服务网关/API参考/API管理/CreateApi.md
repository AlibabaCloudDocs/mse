# CreateApi

调用CreateApi创建API。

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /v1/gateway/{gatewayId}/api 
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
| |Object|Body|否| |API相关参数。 |
|aliasName|String|Body|否|DOCtest|API别名，最多支持16字符。 |
|attachedServices|Array of Long|Body|否|1|API关联服务ID。 |
|basePath|String|Body|否|/order/query|API的访问路径。 |
|description|String|Body|否|DOCtest|API的描述信息。 |
|name|String|Body|否|DOCtest|API名称，仅限字母、数字和下划线（\_），最多支持64个字符，必须以字母开头。 |
|status|Long|Body|否|3|API运行状态，取值如下：

 -   **0**：未发布
-   **1**：未发布，编辑中
-   **2**：发布中
-   **3**：已发布
-   **4**：已发布，编辑中
-   **5**：回收中 |
|gatewayId|Long|Path|否|70|API所属网关ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|code|Long|200|状态码。 |
|data|Map| |返回数据。 |
|message|String|success|错误信息。 |

## 示例

请求示例

```
POST /v1/gateway/70/api HTTP/1.1 
 {
	"data":{
		"aliasName":"DOCtest",
		"attachedServices":"[ 1 ]",
		"basePath":"/order/query",
		"name":"DOCtest",
		"description":"DOCtest",
		"status":"3"
	}
}
```

正常返回示例

`XML` 格式

```
<CreateApiResponse>
  <code>200</code>
  <message>success</message>
</CreateApiResponse>
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

