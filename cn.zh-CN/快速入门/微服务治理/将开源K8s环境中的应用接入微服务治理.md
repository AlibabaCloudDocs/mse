# 将开源K8s环境中的应用接入微服务治理

借助MSE微服务治理，您无需修改任何代码就可以为开源K8s环境中的Dubbo和Spring Cloud应用提供无侵入的微服务治理能力，包含无损下线、离群实例摘除、服务查询、服务鉴权、服务测试和金丝雀发布，大幅提升线上微服务的稳定性和开发效率。本文将帮助您将开源K8s环境中的应用接入MSE微服务治理。

-   [安装Helm](https://helm.sh/docs/intro/install/)。
-   确保您的Kubernetes api-server组件为1.10及以上版本。
-   确保您的集群连通公网。

## 步骤一：安装mse-pilot

MSE微服务治理目前仅支持无状态（Deployment）的应用接入。

1.  执行以下`wget`命令下载mse-pilot安装包。

    ```
     wget 'https://edas-public.oss-cn-hangzhou.aliyuncs.com/mse/mse-pilot-unmanaged.zip' -O mse-pilot-unmanaged.zip
    ```

2.  执行以下命令解压mse-pilot安装包。

    ```
    unzip mse-pilot-unmanaged.zip                        
    ```

3.  执行以下命令安装mse-pilot。

    **说明：** 请确保执行命令之前，您已经将~/.kube/config文件内容替换成需要接入MSE微服务治理的K8s集群的配置。

    ```
    kubectl create namespace mse-pilot
    helm install mse-pilot ./mse-pilot-unmanaged --namespace mse-pilot                        
    ```


## 步骤二：获取Licensekey

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **应用列表**。

3.  在**应用列表**页面顶部选择**华东1（杭州）**地域，单击**应用接入**。

    **说明：** 开源K8s环境中的应用默认接入**华东1（杭州）**地域，因此您需在**华东1（杭州）**地域获取License Key。

4.  在**接入方式**页面的**环境类型**区域单击**ECS集群**，然后在**第2步 安装 MSE Agent**区域复制LicenseKey。

    ![获取LicenseKey](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4262458061/p203783.png)


## 步骤三：修改应用的YAML文件

1.  执行以下命令查看目标无状态（Deployment）应用的配置。

    ```
    ### 查看指定无状态（Deployment）类型应用的配置
    kubectl get deployment {deployment名称} -o yaml                            
    ```

    **说明：** 若您不清楚`{deployment名称}`，请先执行以下命令查看所有无状态（Deployment）应用，在执行结果中找到目标无状态（Deployment）应用，再查看目标无状态（Deployment）应用的配置。

    ```
    ### 查看所有无状态（Deployment）类型应用的配置
    kubectl get deployments --all-namespace                
    ```

2.  启动编辑目标无状态（Deployment）应用的YAML文件。

    ```
    kubectl edit deployment {Deployment名称} -o yaml                        
    ```

3.  在YAML文件中的spec -\> template -\> metadata -\> annotations层级下加入以下内容。

    ```
    msePilotAutoEnable: "on"
    msePilotLicenseKey: xxx
    msePilotCreateAppName: xxx                           
    ```

    **说明：** 请将`xxx`分别替换成您的LicenseKey和应用名称，应用名暂不支持中文。

4.  保存配置后，应用将自动重启，以上配置生效。

    2~5分钟后，若您的应用出现在MSE控制台的**MSE治理中心** \> **应用列表**中，包含应用实例，且有数据上报，则说明接入成功。


## 后续步骤

完成上述步骤后，您就为部署在开源K8s环境中的应用开启了MSE微服务治理。登录[MSE治理中心控制台](https://mse.console.aliyun.com/#/msc/home)，即可使用MSE微服务治理对您的Spring Cloud和Dubbo应用进行服务治理，详情请参见[使用指引](/cn.zh-CN/.md)。

## 卸载mse-pilot

当您不再需要需要治理开源K8s环境中的应用及服务时，可以卸载mse-pilot。

1.  执行以下命令卸载mse-pilot。

    ```
    helm del --purge mse-pilot
    ```

2.  重启您的应用Pod。


