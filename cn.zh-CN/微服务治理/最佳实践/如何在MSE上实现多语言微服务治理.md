# 如何在MSE上实现多语言微服务治理

本文介绍通过MSE实现对容器服务Kubernetes版中多语言应用的服务管理。

-   [创建Kubernetes托管版集群](/cn.zh-CN/Kubernetes集群用户指南/集群管理/创建集群/创建Kubernetes托管版集群.md)
-   [创建服务网格]()

为部署在容器服务Kubernetes版中的应用安装MSE微服务治理组件，您无需修改任何代码，就能借助MSE对应用进行微服务治理。MSE微服务治理的详细信息请参见[MSE微服务治理入门概述]()。

## 在容器服务Kubernetes版中安装MSE微服务治理组件

在ACK中为目标集群安装MSE应用监控组件**ack-mse-rule-controller**，在该集群部署的应用即可接入MSE治理中心。

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏选择**市场** \> **应用目录**。

3.  在**应用目录**页面右上角的搜索框中输入mse，选择**ack-mse-rule-controller**组件。

4.  在**应用目录 - ack-mse-rule-controller**页面选择**参数**页签，修改serviceMesh\_id，关于serviceMesh\_id的获取请参见[网格管理](https://servicemesh.console.aliyun.com/#/instances)。

    关于MSE微服务治理组件参数配置说明如下。

    |参数|描述|默认值|
    |--|--|---|
    |controller.region\_id|容器服务集群所在的区域，如cn-beijing，cn-hangzhou，cn-shenzhen等，目前MSE已经开通北京、深圳、杭州、上海、青岛五个区域。|自动注入您集群所在的区域。|
    |controller.cluster\_id|容器服务集群ID|自动注入您的容器服务集群ID。|
    |controller.uid|阿里云的用户ID|自动注入您的阿里云账户ID。|
    |controller.accessKey|阿里云账号AccessKey|容器服务通过RAM work role方式授权。|
    |controller.accessKeySecret|阿里云账号SecretKey|容器服务通过RAM work role方式授权。|
    |controller.image|mse pilot镜像的下载地址|默认从您集群所在的Region下载镜像。|
    |controller.serviceMesh\_id|容器服务集群的服务网格ID|开启服务网格后的服务网格ID。|
    |controller.accessSource|接入的K8s集群的类型|容器服务K8s集群对应的类型为ACSK8s。|

5.  在**应用目录 - ack-mse-rule-controller**页面中的右侧**创建**面板中选中目标**集群**，并单击**创建**。

    ![创建ack-mse-rule-controller](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6878560061/p167801.png)


## 在容器服务Kubernetes版中发布应用

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在控制台左侧导航栏中，单击**集群**。

3.  在**集群列表**页面中，单击目目标集群右侧**操作**列下的**应用管理**。

4.  在**工作负载**页面左上角选择**命名空间**，然后选择**无状态**页签，单击**使用模板创建**。

5.  在**使用模板创建**页面选择**示例模板**，并在**模板**区域编辑创建应用的YAML文件。

    部署应用的YAML模板如下：

    ```
    apiVersion: v1
    kind: Service
    metadata:
      name: ratings
      labels:
        app: ratings
        service: ratings
    spec:
      ports:
      - port: 9080
        name: http
      selector:
        app: ratings
    ---
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: ratings-v1
      labels:
        app: ratings
        version: v1
    spec:
      replicas: 1
      selector:
        matchLabels:
          app: ratings
          version: v1
      template:
        metadata:
          labels:
            app: ratings
            version: v1
          annotations:
            mseServiceMeshOn: "on"
        spec:
          serviceAccountName: bookinfo-ratings
          containers:
          - name: ratings
            image: docker.io/istio/examples-bookinfo-ratings-v1:1.15.0
            imagePullPolicy: IfNotPresent
            ports:
            - containerPort: 9080
    ```

    **说明：** 您需要在应用中的labels里面写入对应的应用名，以及版本号。

    您可在**无状态**页签下查看所创建的应用。


## 为应用开启MSE微服务治理

1.  登录[服务网格控制台](https://servicemesh.console.aliyun.com/)。

2.  在左侧导航栏选择**服务网格** \> **网格管理**。

3.  单击目标网格名称，若没有服务网格，可先创建新网格，详情请参见[创建ASM实例]()。

4.  在**控制平面**区域选择**Namespace**页签，

5.  在目标命名空间**自动注入**列单击**启动Sidecar自动注入**。


完成上述步骤后，您就为部署在容器服务Kubernetes版中的应用开启了MSE多语言微服务治理。MSE目前支持服务网格的服务查询和标签路由功能。登录[MSE治理中心控制台](http://edasmsc.console.aliyun.com)，即可使用MSE对您的Istio服务进行服务治理，详情请参见[查询服务](/cn.zh-CN/微服务治理/Istio服务治理/查询服务.md)和[配置标签路由](/cn.zh-CN/微服务治理/Istio服务治理/配置标签路由.md)。

