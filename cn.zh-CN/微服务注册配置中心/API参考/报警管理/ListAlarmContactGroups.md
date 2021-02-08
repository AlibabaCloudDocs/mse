# ListAlarmContactGroups

调用ListAlarmContactGroups接口，获取报警联系人分组列表。

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAlarmContactGroups|系统规定参数，取值：ListAlarmContactGroups。 |
|PageNum|Integer|是|1|页码。 |
|PageSize|Integer|是|10|每页展示实例数。 |
|RequestPars|String|否|\{\}|扩展请求参数，JSON格式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Array of AlarmContactGroupModel| |数据概览。 |
|ContactGroupId|String|7434|报警联系人分组ID。 |
|ContactGroupName|String|test-123|联系人分组名称。 |
|ErrorCode|String|mse-100-000|错误码。 |
|HttpCode|String|202|HTTP状态码。 |
|Message|String|请求处理成功|信息。 |
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|10|每页展示实例数。 |
|RequestId|String|25EA0A83-9007-4E87-808C-637BE1A\*\*\*\*|请求ID。 |
|Success|Boolean|true|请求结果，取值如下：

 -   `true`：请求成功。
-   `false`：请求失败。 |
|TotalCount|Integer|12|实例总数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAlarmContactGroups
&PageNum=1
&PageSize=10
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListAlarmContactGroupsResponse>
  <HttpCode>202</HttpCode>
  <TotalCount>12</TotalCount>
  <PageSize>10</PageSize>
  <Message>请求处理成功</Message>
  <RequestId>25EA0A83-9007-4E87-808C-637BE1A****</RequestId>
  <PageNumber>1</PageNumber>
  <Data>
        <ContactGroupId>7434</ContactGroupId>
        <ContactGroupName>test-123</ContactGroupName>
  </Data>
  <ErrorCode>mse-100-000</ErrorCode>
  <Success>true</Success>
</ListAlarmContactGroupsResponse>
```

`JSON`格式

```
{
    "HttpCode": 202,
    "TotalCount": 12,
    "PageSize": 10,
    "Message": "请求处理成功",
    "RequestId": "25EA0A83-9007-4E87-808C-637BE1A****",
    "PageNumber": 1,
    "Data": {
        "ContactGroupId": 7434,
        "ContactGroupName": "test-123"
    },
    "ErrorCode": "mse-100-000",
    "Success": true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/mse)查看更多错误码。

