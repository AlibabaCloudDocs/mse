---
keyword: [微服务, 测试用例, 自动化回归, 脚本化]
---

# 自动化回归Spring Cloud服务的脚本化编排

自动化回归脚本化编排支持将测试用例的UI编排转换成脚本化编排，还可以将测试用例加入用例集后，在用例集中将加入的所有用例导出成JSON格式的脚本文件，然后使用本地编辑器对脚本进行修改后再导入到当前用例集或其他用例集中，方便您对用例进行迁移和管理。

-   在使用服务测试前，请确保您的应用已接入MSE治理中心。具体操作，请参见[微服务治理中心入门概述]()。

-   [创建Spring Cloud测试用例](/cn.zh-CN/微服务治理/Spring Cloud服务治理/微服务测试/自动化回归Spring Cloud服务测试用例.md)。


## 操作步骤



1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **自动化回归（用例管理）**。

3.  在顶部菜单栏选择地域，然后单击目标用例**操作**列下方的**详情**。

4.  在**用例详情**页面右侧单击/图标，切换到脚本模式；单击UI，切换到UI模式。

    关于用例管理的脚本参数说明，请参见[用例管理脚本模式参数说明](#section_1j3_cow_t8q)。

    ![脚本和UI模式切换](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8790784261/p289678.png)

    **说明：** 脚本模式下，不可进行**访问一次**的调试和**保存配置**等操作，请切换到UI模式进行。


1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **自动化回归（用例集）**。

3.  在顶部菜单栏选择地域，然后单击目标用例**操作**列下方的**详情**。

4.  在**用例集详情**页面右侧单击**导出脚本**，在**导出脚本**对话框中单击**导出**。

    关于用例集管理的脚本参数说明，请参见[用例集管理脚本参数说明](#section_wvu_u20_g5s)。

    ![自动化回归用例集导出脚本](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8790784261/p289685.png)

    成功导出JSON格式的脚本文件。

5.  使用本地编辑器对脚本进行修改，然后在**用例集详情**页面右侧单击**导入脚本**，在**导入脚本**对话框中选择**相同用例**执行的操作，并单击**上传文件**，选择并上传本地的脚本文件，然后单击**导入**。

    ![自动化回归用例集导入脚本](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8790784261/p289682.png)

    **相同用例**是指该用例集下相同名称的用例，执行的操作说明如下：

    -   **终止导入**：此次操作选中的所有用例都不会被同步到目标微服务空间。
    -   **跳过**：跳过重复的用例，继续克隆其他用例。
    -   **覆盖**：用此次选择的用例覆盖目标微服务空间中已有的相同用例。

## 用例管理脚本模式参数说明

自动化回归功能支持将UI模式切换成脚本模式修改测试用例，再将脚本模式切换到UI模式进行调试和保存，脚本中有关请求的基础信息解析为测试步骤的API。

脚本模式相关的字段解析说明如下。

|脚本字段|字段解析|
|----|----|
|info.namespaceId|微服务空间。|
|info.regionId|地域。|
|info.schema|脚本版本号。|
|item\[\]|表示多个测试步骤。|
|item\[0\].name|测试步骤的名称。|
|item\[0\].request.method|请求方法。|
|regionId|地域，支持Spring Cloud和Dubbo服务。|
|appId|应用ID，支持Spring Cloud和Dubbo服务。|
|appName|应用名称，支持Spring Cloud和Dubbo服务。|
|serviceType|服务类型，支持Spring Cloud和Dubbo服务。|
|serviceName|服务名称，支持Spring Cloud和Dubbo服务。|
|methodName|方法名称，支持Spring Cloud和Dubbo服务。|
|methodTypes|方法类型，仅支持Dubbo服务。|
|group|组别，仅支持Dubbo服务。|
|version|版本号，仅支持Dubbo服务。|
|method|请求方法，仅支持Spring Cloud服务。|
|uri|请求路径，仅支持Spring Cloud服务。|
|item\[0\].request.body|参数基本信息。|
|contentType|根据框架类型和ContentType区分，其中mode有urlencoded和raw两种模式：-   `"mode":"urlencoded"`：当框架类型为Spring Cloud服务时，可选此模式。入参信息填在对应的`urlencoded`中，以`key`和`value`的方式传入，例如：

    ```
"urlencoded":[  
               {                          
               "key":"aa",            
               "value":"11"
                }    
             ]
    ```

-   `"mode":"raw"`：Spring Cloud服务可选此模式，Dubbo仅支持此类型，入参信息填在对应`raw`中，以字符串方式传入，例如：

    ```
"raw":"[\"11234\"]"
    ``` |
|mode|
|urlencoded|
|raw|
|item\[0\].request.header|请求头。|
|key|请求头的Key，仅支持Spring Cloud服务。|
|value|请求头对应的Value值，仅支持Spring Cloud服务。|
|item\[0\].request.checkpoints|断言。|
|point|检查对象，为`${}`括起来的`JsonPath`，例如`${response.name}`。|
|checkers.operate|检查条件。|
|checkers.expect|检查内容，即预期值。|
|item\[0\].request.exports|出参提取。|
|key|出参提取的出参名。|
|value|对应的出参提取表达式，为`${}`括起来的`JsonPath`。|

**说明：**

-   脚本中的info信息仅做展示，转换成UI模式时以实际页面选择为准。
-   JSON脚本中，配置`item[0] item[1] item[2]……`表示有多个测试步骤。
-   从脚本模式转换成UI模式时，将对脚本格式和`request.method`中的内容进行正确性校验，若不正确，则不允许转换。其中`request.method.method`为Spring Cloud框架类型基本信息中的请求方法，支持GET、POST、PUT和DELETE。

其中`request.body.contentType`支持以下7种类型。

|contentType|描述|
|-----------|--|
|`application/x-www-form-urlencoded`|对应`mode`为`urlencoded`。|
|`application/json`|对应`mode`为`raw`。|
|`text/plain`|
|`application/javascript`|
|`text/html`|
|`text/xml`|
|`application/xml`|

**说明：** Dubbo服务仅支持`contentType=application/json`，`mode=raw`的模式。

其中`request.checkpoints.checkers.operate`检查条件枚举如下。

|checkers.operate|描述|
|----------------|--|
|EQUAL\_NUMERIC|等于（数字）|
|NOT\_EQUAL\_NUMERIC|不等于（数字）|
|GREATER\_OR\_EQUAL\_NUMERIC|大于等于（数字）|
|LESS\_OR\_EQUAL\_NUMERIC|小于等于（数字）|
|GREATER\_NUMERIC|大于（数字）|
|LESS\_NUMERIC|小于（数字）|
|EQUAL\_STRING|等于（字符串、区分大小写）|
|NOT\_EQUAL\_STRING|不等于（字符串、区分大小写）|
|EQUAL\_STRING\_IGNORE|等于（字符串、不区分大小写）|
|NOT\_EQUAL\_STRING\_IGNORE|不等于（字符串、不区分大小写）|
|CONTAIN\_STRING|包含（字符串）|
|NOT\_CONTAIN\_STRING|不包含（字符串）|
|TIME\_EARLY|时间早于|
|TIME\_LATE|时间晚于|
|IS\_NULL|为空，表示没有该字段。**说明：** `checkers.operate`为该字段时，无需设置`checkers.expect`。 |
|IS\_NOT\_NULL|不为空，表示有该字段。**说明：** `checkers.operate`为该字段时，无需设置`checkers.expect`。 |
|JSON\_CONTAIN|JSON对象中包含此值|
|JSON\_NOT\_CONTAIN|JSON对象中不包含此值|
|JSON\_ARRAY\_NULL|JSON数组是否为空数组|
|JSON\_ARRAY\_NOT\_NULL|JSON数组是否为非空数组|
|JSON\_ARRAY\_SIZE\_EQUAL|JSON数组长度等于|
|JSON\_ARRAY\_SIZE\_GREATER|JSON数组长度大于|
|JSON\_ARRAY\_SIZE\_GREATER\_OR\_EQUAL|JSON数组长度大于等于|
|JSON\_ARRAY\_SIZE\_LESS|JSON数组长度小于|
|JSON\_ARRAY\_SIZE\_LESS\_OR\_EQUAL|JSON数组长度小于等于|
|IS\_JSON\_OBJECT|是否为JSON对象类型**说明：** `checkers.operate`为该字段时，无需设置`checkers.expect`。 |
|IS\_JSON\_ARRAY|是否为JSON数组类型**说明：** `checkers.operate`为该字段时，无需设置`checkers.expect`。 |
|REGEX\_COMPARE|正则表达式|

## 用例集管理脚本参数说明

自动化回归用例集功能支持将加入用例集中的所有用例导出成脚本，然后使用本地用编辑器对脚本进行修改后导入到当前用例集或其他用例集中。

导出的脚本文件为JSON格式，字段解析和测试用例的脚本模式相比多了一层`item`，内容如下：

|脚本字段|字段解析|
|----|----|
|info.namespaceId|微服务空间|
|info.regionId|地域|
|info.schema|脚本版本号|
|item\[\]|多个测试用例|
|item\[0\].name|测试用例的名称|
|item\[0\].item\[0\].name|第1个用例的第一个步骤的名称|
|item\[0\].item\[1\].name|第1个用例的第二个步骤的名称|

**说明：**

-   脚本中的info信息仅做展示，导入脚本时以实际页面选择为准。
-   JSON脚本中，配置`item[0] item[1] item[2]……`表示有多个测试用例。
-   导入脚本时将对脚本格式和`request.method`中的内容进行正确性校验。若导入失败，则返回导入的总数、成功数、失败数和具体的失败原因。
-   用例集下相同名称的用例将被识别为相同用例。若遇到相同用例时，可选择导入规则为终止导入、跳过或覆盖。

