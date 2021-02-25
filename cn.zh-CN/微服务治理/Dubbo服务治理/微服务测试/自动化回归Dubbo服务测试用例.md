---
keyword: [微服务, 测试用例, 自动化回归]
---

# 自动化回归Dubbo服务测试用例

自动化回归平台基于服务契约信息快速编排被测服务、管理自动化测试用例，帮助您高效管理、回归业务测试场景，完成业务快速验证和交付。

在使用服务测试前，请确保您的应用已接入MSE治理中心。具体操作，请参见[MSE微服务治理入门概述]()。

## 创建Dubbo测试用例

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **自动化回归**。

3.  在顶部菜单栏选择**地域**，然后单击**新建用例**。

4.  在**新建用例**页面单击测试步骤中间空白处或右侧的![下拉箭头](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0389155061/p182521.png)，然后设置相关参数信息。

    ![创建Dubbo测试用例](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9589155061/p182577.png)

    |参数|描述|
    |--|--|
    |**用例名称**|自定义测试用例名称。|
    |**步骤名称**|自定义测试步骤名称。|
    |**应用**|选择需要测试的应用。|
    |**框架类型**|选择**Dubbo**框架。|
    |**服务**|选择应用的服务。|
    |**方法**|选择服务的方法|
    |**基本信息**|支持JSON格式的参数输入方式。其中默认入参为\[\]。关于Dubbo服务的方法参数类型及配置方式，请参见[Dubbo参考示例](#section_04m_its_sag)。 |
    |**断言（选填）**|输入**检查对象**和**检查内容**，选择**检查条件**。|
    |**出参提取（选填）**|输入**出参名**和**解析表达式**。|

5.  单击右侧的**访问一次**，弹出**单步骤调试结果**，查看此次请求入参和请求出参。

6.  单击**出参提取助手**，弹出**出参提取助手**对话框，再单击需要提取的出参名，复制该参数。

7.  在**断言（选填）**下方的**检查对象**中粘贴所复制的参数，选择**检查条件**，输入**检查内容**。

8.  在**出参提取（选填）**下方的**出参提取表达式**中粘贴所复制的参数，并自定义**出参名**。

9.  单击右上方的**保存配置**即可。

    您可在用例列表中查看创建的测试用例。


## 创建多步骤串联的测试用例

**说明：** 一个测试用例可以包含多个测试步骤，当后序的测试步骤依赖前序的测试步骤的输出时，需要使用参数传递。

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **自动化回归**。

3.  在顶部菜单栏选中**地域**，单击目标用例右侧**操作**列的**详情**。

4.  在**用例详情**页面单击右侧的**访问一次**，弹出**单步骤调试结果**，查看此次请求入参和出参。

5.  单击**出参提取助手**，弹出**出参提取助手**窗口，选择需要提取的出参参数进行复制。

6.  在**出参提取（选填）**下方的**出参提取表达式**中粘贴所选择的出参表达式，并自定义**出参名**。

7.  单击**+添加下一步**增加多个测试步骤。

8.  在该测试步骤的**基本信息**区域下方的**JSON格式化**中输入引用变量名$\{XXX\}。

    **说明：** XXX为前序步骤的**出参提取**中设置的**出参名**，需要用$\{ \}格式进行引用。

9.  单击右上方的**保存配置**，再单击**执行用例**。


## 执行测试用例

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **自动化回归**。

3.  在顶部菜单栏选中**地域**。

4.  您可选择以下两种方式执行测试用例。

    -   在**用例列表**页面，单击目标用例右侧**操作**列的**执行**。
    -   在**用例列表**页面，单击目标用例右侧**操作**列的**详情**，在**用例详情**页面单击**立即执行**。

        ![执行测试用例](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0389155061/p182563.png)

    您可在**执行历史**页签中查看详细执行结果。


## 相关操作

您还可以执行以下操作管理测试用例。

-   复制测试用例：在**自动化回归**列表页面，单击**操作**列的**复制**，可生成一条新的测试用例。
-   删除测试用例：在**自动化回归**列表页面，单击**操作**列的**删除**，可删除该测试用例。

## Dubbo参考示例

|方法|参数类型填写方式|参数填写方式|
|--|--------|------|
|String sayHello\(String name\);|\["java.lang.String"\]|\["hello, dubbo"\]|
|String helloBean\(HelloBean helloBean\);|\["com.alibaba.dubbo.api.DemoService"\]|\[\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\}\]|
|String helloBean\(HelloBean helloBean1, HelloBean helloBean2\);|\["com.alibaba.dubbo.api.DemoService","com.alibaba.pts.dubbo.api.DemoService"\]|\[\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\},\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\}\]|
|String helloMap\(Map helloMap\);|\["java.util.Map"\]|\[\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\}\]|
|String helloMap\(Map helloMap1, Map helloMap2\);|\["java.util.Map", "java.util.Map"\]|\[\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\},\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\}\]|
|String helloList\(List helloList\);|\["java.util.List"\]|\[\[1\]\]|
|String helloList\(List helloList1, List helloList2\);|\["java.util.List","java.util.List"\]|\[\[1\],\[1,2\]\]|
|String helloString\(String helloString\);|\["java.lang.String"\]|\[\[1\],\[1,2\],\[1,3\]\]|
|String helloString\(String helloString1, String helloString2\);|\["java.lang.String","java.lang.String"\]|\["hello, dubbo", "hello, dubbo"\]|
|String helloInt\(int helloInt\);|\["int"\]|\["hello, dubbo", "hello, dubbo"\]|
|String helloInt\(int helloInt1, int helloInt2\);|\["int","int"\]|\["1","2"\]|
|String helloBoolean\(boolean helloBoolean\);|\["boolean"\]|\["true"\]|
|String helloBoolean\(boolean helloBoolean1, boolean helloBoolean2\);|\["boolean","boolean"\]|\["true","false"\]|
|String helloVoid\(\);|\[\]|\[\]|

## 微服务测试用户交流群

如果您在微服务引擎MSE使用微服务测试过程中有任何疑问，欢迎您使用钉钉扫描下方的二维码或搜索钉钉群号31180380加入钉钉群进行反馈。

![微服务测试交流群](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9780389061/p181621.png)

