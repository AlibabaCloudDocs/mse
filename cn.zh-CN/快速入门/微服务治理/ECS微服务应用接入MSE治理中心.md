# ECS微服务应用接入MSE治理中心

您可以将部署在ECS以及非阿里云虚拟机等部署环境的应用接入MSE治理中心，使用MSE提供的一系列服务治理能力，大幅提升线上微服务的稳定性和开发效率。

-   已创建ECS实例，详情请参见[创建方式导航](/cn.zh-CN/实例/创建实例/创建方式导航.md)。
-   已安装JDK并配置环境变量，详情请参见[Java Downloads](https://www.oracle.com/downloads/)。

## 接入流程

将ECS中的应用接入MSE治理中心包含以下步骤：

-   [下载MSE Agent](#section_il5_w4o_fki)
-   [安装MSE Agent](#section_nio_xc6_54v)
-   [验证应用已接入MSE](#section_wfq_ohg_8zr)

## 下载MSE Agent

1.  登录[ECS管理控制台](https://ecs.console.aliyun.com)。

2.  在左侧导航栏选择**实例与镜像** \> **实例**。

3.  在顶部菜单栏左上角，选择**地域**。

4.  在**实例列表**页面，搜索需要连接的实例，单击该实例对应**操作**列下的**远程连接**。

5.  在弹出的**远程连接与命令**对话框中，选择相应的链接方式进行登录，详情请参见[连接方式概述ECS远程连接操作指南](/cn.zh-CN/实例/连接实例/连接方式概述.md)。

6.  下载MSE Agent。

    以上海Region为例，通过Shell脚本方式下载MSE Agent。

    -   公网脚本地址：

        ```
        wget -O- http://mse-shanghai.oss-cn-shanghai.aliyuncs.com/install.sh | sh
        ```

    -   VPC脚本地址（公网脚本地址无法下载时使用VPC脚本地址下载）：

        ```
        wget -O- http://mse-shanghai.oss-cn-shanghai-internal.aliyuncs.com/install.sh | sh
        ```

    MSE Agent下载成功。


## 安装MSE Agent

MSE Agent下载成功后需要进行解压和安装。

1.  将MseAgent.zip中的所有文件解压到任意目录中。

    ```
    unzip MseAgent -d /{user.workspace}/
    ```

    **说明：** “\{user.workspace\}”是示例路径，请根据具体环境替换为正确的路径。

2.  在应用启动参数上添加AppName以及LicenseKey参数。

    ```
    -javaagent:/{user.workspace}/MseAgent/mse-bootstrap-1.7.0-SNAPSHOT.jar
    -Dmse.licenseKey=<yourLicenseKey>     #<yourLicenseKey>系统为您自动生成的LicenseKey，请勿泄露。
    -Dmse.appName=<yourAppName>           #<yourAppName>自定义应用名称。
    -Dmse.enable=true
    ```

    **说明：** 安装java agent需要确保对应节点，至少预留300 M内存。


## 验证应用已接入MSE

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **应用列表**。

3.  在顶部菜单栏左上角，选择**地域**。

4.  在**应用列表**页面查看您的应用是否已接入MSE。


完成上述步骤后，您就为部署在ECS以及非阿里云虚拟机等部署环境的应用开启了MSE微服务治理能力。登录[MSE治理中心控制台](https://mse.console.aliyun.com/#/msc/home)，即可使用MSE微服务治理对您的Spring Cloud和Dubbo应用进行服务治理，详情请参见[使用指引](/cn.zh-CN/.md)。

