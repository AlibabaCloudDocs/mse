---
keyword: [微服务, 服务治理]
---

# 压测Dubbo服务

在日常开发中，开发人员或测试人员需要评估服务的性能是否符合预期，避免因功能迭代导致服务性能下降而引发故障。服务压测功能可以让您低成本地评估服务性能，做到1分钟创建压测场景，5分钟获取性能指标。

在使用服务测试前，请确保您的应用已接入MSE治理中心。具体操作，请参见[MSE微服务治理入门概述]()。

在大促活动中，应该准备多少实例资源才能满足大促吞吐量的要求，降低因大促活动带来的访问量暴增进而引发系统宕机的风险。此时需要合理地评估服务性能，避免流量冲击引发的故障，并降低运营使用成本。

## 视频教程



## 操作步骤

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **服务压测**。

3.  在顶部菜单栏选择**地域**，然后单击**创建场景**。

4.  在**创建场景**面板中设置**场景配置**和**压力配置**相关参数，然后单击**确定**。

    ![dubbo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8346152161/p181904.png)

    **场景配置**相关参数说明如下。

    |参数|描述|
    |--|--|
    |**场景名称**|压测场景名称，例如test-dubbo。|
    |**应用**|选择需要压测的应用。|
    |**框架类型**|选择**Dubbo**框架。|
    |**服务**|选择应用的服务。|
    |**方法**|选择服务的方法。|
    |**参数模式**|选择请求参数输入模式。    -   参数填写：填写参数内容。关于参数填写格式，请参见[Dubbo参考示例](#dubbo)和[参数文件URL](#section_lz2_xgk_r22)。
    -   参数文件路径：填写参数文件地址。参数文件路径必须支持公网可访问。 |
    |**超时时间（毫秒）**|设置超时时间，单位：毫秒。|
    |**直连服务**|开启后选择**服务地址**，可直接连接该服务。|
    |**打印日志**|开启可自动打印日志信息，但会影响到服务压测性能，建议正常压测时关闭。|

    **压力配置**页签相关参数说明如下。

    |参数|描述|
    |--|--|
    |**压测模式**|压测模式有两种：并发模式（虚拟用户模式）、TPS模式（Transaction Per Second，吞吐量模式）。    -   **并发模式**：指虚拟并发用户数，从业务角度，也可以理解为同时在线的用户数。
    -   **TPS模式**：指系统每秒处理的事务数量。 |
    |**流量模型**|流量模型包括固定压力、阶梯压力和脉冲压力。    -   **固定压力**：以配置的固定并发值进行施压，并可设置预热时长。
    -   **阶梯压力**：设置最大值、最小值、预热时间等信息，在预热递增期间，从最小值开始按照阶梯逐步递增，达到最大并发后按照最大并发持续施压。不可指定循环次数。
    -   **脉冲压力**：设置峰值、谷值以及持续时间等信息，施压流量以峰值、峰谷的锯齿波的形式进行施压。 |
    |**压测时长（分钟）**|指压测总时长，公测期间最大压测时长60分钟。|
    |**预热时长（分钟）**|施压前的预热时间，若设置为0，则表示无需预热。|


## 执行结果

压测场景创建成功后，您可查看**服务压测**列表查看相关信息，包括**平均TPS**、**平均响应时间**、**错误率**等。

您可在压测场景**详情**页面选择**重启**、**停止**或**编辑场景**，也可执行**删除**等操作。

## 查看压测报告

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **服务压测**。

3.  在服务压测列表中单击**操作**列的**详情**，查看**场景配置**和**运行记录**。

4.  在**运行记录**区域单击**操作**列的**详情**，查看实时性能数据。

    ![压测场景性能数据](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8582815061/p181995.png)

    **说明：** **性能数据**是每10秒的所有施压机数据统计，具体根据压测总时间长度会有所变化。单击图上方的图例，可以显示或隐藏某些数据曲线。

    |参数|说明|
    |--|--|
    |**总请求数**|整个压测过程中，共发起的请求个数。|
    |**平均TPS**|压测周期内，所有压力机发出的平均TPS值，TPS=调用总次数/总运行时间。|
    |**平均RT（ms）**|所有压力机发出平均响应时间。|
    |**最小RT（ms）**|所有压力机中最小的一次响应时间。|
    |**最大RT（ms）**|所有压力机中最大的一次响应时间。|
    |**错误请求数**|所有压力机中错误请求数之和。|
    |**错误率**|所有压力机中的平均错误率。|
    |**TP80（ms）**|所有压力机中80分位（P80）的平均值。|
    |**TP95（ms）**|所有压力机中95分位（P95）的平均值。|
    |**TP99（ms）**|所有压力机中99分位（P99）的平均值。|

5.  单击**下载日志**，可获取压测过程中的日志。


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

## 参数文件URL：提供一个公网可下载的文件地址

平台会把该参数文件分发到每一个施压机，应用每一次调用参数就在该文件中按顺序读取一行。文件里面也支持动态函数参数。

参数文件填写格式如下：

-   方法参数类型：填写的内容是一个字符串类型的JSON数组，数组的每一位代表对应位置的参数类型。除了Java基本类型，其余类型需要填写完整的类路径。
-   方法参数：填写的内容是一个字符串类型的JSON数组，数组的每一位代表对应位置的参数。

|方法|参数类型填写方式|参数文件内容填写格式|
|--|--------|----------|
|String sayHello\(String name\);|\["java.lang.String"\]|\["hello, dubbo"\]

\["hello, dubbo"\]

\["hello, dubbo"\] |
|String helloList\(List helloList\);|\["java.util.List"\]|\[\[1\]\]

\[\[1\]\]

\[\[1\]\] |
|String helloList\(List helloList1, List helloList2\);|\["java.util.List","java.util.List"\]|\[\[1\],\[1,2\]\]

\[\[1\],\[1,2\]\]

\[\[1\],\[1,2\]\] |

## 微服务测试用户交流群

如果您在微服务引擎MSE使用微服务测试过程中有任何疑问，欢迎您使用钉钉扫描下方的二维码或搜索钉钉群号31180380加入钉钉群进行反馈。

![微服务测试交流群](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9780389061/p181621.png)

