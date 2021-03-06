---
keyword: [微服务测试, 流量测试, 智能测试, 流量录制]
---

# 智能流量测试Spring Cloud服务

智能流量测试功能通过对微服务应用接口的流量录制，并自动生成对应的自动化回归测试用例和服务压测场景，帮助您轻松完成模拟真实请求进行服务压测和零编码成本的接口自动化回归。本文介绍如何录制Spring Cloud服务的流量和如何将录制流量自动化生成服务压测场景。

在使用智能流量测试前，请确保您的应用已接入MSE治理中心。具体操作，请参见[微服务治理中心入门概述]()。

在微服务测试过程中，开发人员很难编写应用的API测试，通常期望能通过页面操作，快速生成应用的API测试用例和性能测试用例。流量测试功能可以帮助您低成本低门槛的进行应用的API流量录制，并支持多条流量的压测参数和压测场景自动化生成，帮助您轻松完成自动化测试和性能测试场景编写。

## 录制自动化回归应用的流量

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **智能流量测试**。

3.  在顶部菜单栏选择**地域**，然后在**应用名**文本框中输入应用名称，单击![搜索](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9107870261/p272701.png)图标。

4.  在应用列表中单击目标应用**操作**列的**自动化回归录制**。

5.  在**录制流量**对话框中选择路径，然后单击**确认**。

6.  在**录制记录**页面，您可查看当前流量信息，包括应用名、流量入口、机器、录制时间等。

    ![录制流量记录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0207870261/p272633.png)

    当前流量正在**录制中**，您可在**录制记录**页面执行以下操作：

    -   单击目标录制流量**操作**列下的**详情**，可在**流量详情**面板中查看请求信息、响应信息等。
    -   单击目标录制流量**操作**列下的**删除**，可删除该流量数据。
7.  在**录制记录**页面单击左上角**保存场景**，在**保存操作场景**对话框中输入场景名，单击**确定**。

    当前流量录制结果会自动保存至管理页面，请参见[管理流量录制场景](#section_coq_7l0_qvy)。

8.  在**录制记录**页面单击左上角**结束录制**。

    自动返回**智能流量测试**页面。


## 录制服务压测应用的流量

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **智能流量测试**。

3.  在顶部菜单栏选择**地域**，然后在**应用名**文本框中输入应用名称，单击![搜索](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9107870261/p272701.png)图标。

4.  在应用列表中单击目标应用**操作**列的**服务压测录制**。

5.  在**录制的请求路径**对话框中选择路径，然后单击**确认**。

6.  在**录制记录**页面，您可查看当前流量信息，包括应用名、流量入口、机器、录制时间等。

    ![录制流量记录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0207870261/p272633.png)

    当前流量正在**录制中**，您可在**录制记录**页面执行以下操作：

    -   单击目标录制流量**操作**列下的**详情**，可在**流量详情**面板中查看请求信息、响应信息等。
    -   单击目标录制流量**操作**列下的**删除**，可删除该流量数据。
7.  在**录制记录**页面单击左上角**保存场景**，在**保存操作场景**对话框中输入场景名，单击**确定**。

    当前流量录制结果会自动保存至管理页面，请参见[管理流量录制场景](#section_coq_7l0_qvy)。

8.  在**录制记录**页面单击左上角**结束录制**。

    自动返回**智能流量测试**页面。


## 管理流量录制场景

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **智能流量测试**。

3.  在顶部菜单栏选择**地域**，然后在**应用名**文本框中输入应用名称，单击![搜索](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9107870261/p272701.png)图标。

4.  在应用列表中单击目标应用**操作**列的**管理**。

5.  在**流量管理**页面，您可查看保存的流量信息，包括流量场景、场景类别等。

    ![流量管理](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0207870261/p272638.png)

    您可在**流量管理**页面执行以下操作：

    -   单击目标流量**操作**列下的**详情**，可在**场景对应流量列表**面板中查看流量数据。
    -   单击目标流量**操作**列下的**删除**，可删除该流量数据。

## 生成服务压测场景

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **智能流量测试**。

3.  在顶部菜单栏选择**地域**，然后在**应用名**文本框中输入应用名称，单击![搜索](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9107870261/p272701.png)图标。

4.  在应用列表中单击目标应用**操作**列的**管理**。

5.  在**流量管理**页面，选中流量场景，单击**生成服务压测场景**，在**生成压测场景**对话框中单击**确认**。

    ![生成服务压测场景](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0207870261/p272698.png)

    控制台自动跳转至服务压测**场景详情**页面。

6.  在服务压测**场景详情**面板中单击**编辑场景**。

    关于服务压测配置的相关内容，请参见[压测Spring Cloud服务](/cn.zh-CN/微服务治理/Spring Cloud服务治理/微服务测试/压测Spring Cloud服务.md)。

7.  在**场景配置**页签的配置文件区域可选择上传或下载文件。

    ![上传和下载场景文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0207870261/p272699.png)

    -   单击**上传文件**，可上传更新后的参数文件。
    -   单击![下载图标](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0207870261/p272700.png)图标，可下载参数文件进行查看和编辑。

## 生成自动化回归场景

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **智能流量测试**。

3.  在顶部菜单栏选择**地域**，然后在**应用名**文本框中输入应用名称，单击![搜索](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9107870261/p272701.png)图标。

4.  在应用列表中单击目标应用**操作**列的**管理**。

5.  在**流量管理**页面，选中需要生产压测的场景，单击**批量生成自动化回归用例**，在**生成自动化回归场景**对话框中单击**确认**。

    ![生成自动化回归场景](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3280452261/p279278.png)

    自动生成对应的自动化回归测试用例，控制台自动跳转至服务**自动化回归（用例管理）**页面。

6.  在**用例来源**下拉框中选择**智能流量测试**，单击目标自动化回归用例**操作**列下方的**详情**。

7.  在**用例详情**页面，选择**步骤配置**页签，单击展开图标。

    关于服务自动化回归测试用例的相关内容，请参见[自动化回归Spring Cloud服务测试用例](/cn.zh-CN/微服务治理/Spring Cloud服务治理/微服务测试/自动化回归Spring Cloud服务测试用例.md)。

8.  在**步骤配置**中单击**断言（选填）**页签，查看和修改用例断言内容。

9.  单击右侧的**断言规则配置**，您可在**断言规则配置**面板中配置断言规则。


**说明：** 测试用例可以直接执行回归测试或者加入用例集进行回归测试。相关内容，请参见[自动化回归Spring Cloud测试用例集](/cn.zh-CN/微服务治理/Spring Cloud服务治理/微服务测试/自动化回归Spring Cloud测试用例集.md)。

## 微服务测试用户交流群

如果您在微服务引擎MSE使用微服务测试过程中有任何疑问，欢迎您使用钉钉扫描下方的二维码或搜索钉钉群号31180380加入钉钉群进行反馈。

![微服务测试交流群](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9780389061/p181621.png)

