# 如何在MSE上实现多语言微服务治理

本文介绍通过MSE实现对容器服务Kubernetes版中多语言应用的服务管理。

-   [创建Kubernetes托管版集群](/cn.zh-CN/Kubernetes集群用户指南/集群/创建集群/创建Kubernetes托管版集群.md)
-   [创建服务网格]()

为部署在容器服务Kubernetes版中的应用安装MSE微服务治理组件，您无需修改任何代码，就能借助MSE对应用进行微服务治理。MSE微服务治理的详细信息请参见[微服务治理中心入门概述]()。

## 在ASM安装MSE微服务治理组件

1.  登录[ASM控制台](https://servicemesh.console.aliyun.com)。

2.  在左侧导航栏选择**服务网格** \> **网格管理**

3.  在**网格管理**页面，找到待配置的实例，单击实例的名称或在**操作**列中单击**管理**。

4.  在网关管理详情页面右上方单击**功能设置**。

5.  在**功能设置更新**面板单击**展开高级选项**，选中**启用MSE微服务治理组件**，然后单击**确定**。


## 在容器服务Kubernetes版中发布应用

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在控制台左侧导航栏中，单击**集群**。

3.  在**集群列表**页面中，单击目目标集群右侧**操作**列下的**应用管理**。

4.  在集群管理页面左侧导航栏选择**工作负载** \> **无状态**，选择集群的**命名空间**，单击**使用YAML创建资源**。

5.  在**创建**页面选择**示例模板**，并在**模板**区域编辑创建应用的YAML文件。

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

    **说明：** 您可以自定义命名YAML模板中的示例值。

    -   name：表示应用的名称。
    -   labels：包含对应的应用名app，以及版本号version。
    您可在**无状态**页面下查看所创建的应用。


## 为应用开启MSE微服务治理

1.  登录[服务网格控制台](https://servicemesh.console.aliyun.com/)。

2.  在左侧导航栏选择**服务网格** \> **网格管理**。

3.  单击目标网格名称，若没有服务网格，可先创建新网格，详情请参见[创建ASM实例]()。

4.  在**控制平面**区域选择**Namespace**页签，

5.  在目标命名空间**自动注入**列单击**启动Sidecar自动注入**。


完成上述步骤后，您就为部署在容器服务Kubernetes版中的应用开启了MSE多语言微服务治理。MSE目前支持服务网格的服务查询和标签路由功能。登录[MSE治理中心控制台](http://edasmsc.console.aliyun.com)，即可使用MSE对您的Istio服务进行服务治理，详情请参见[查询服务](/cn.zh-CN/微服务治理/多语言服务治理/查询服务.md)和[配置标签路由](/cn.zh-CN/微服务治理/多语言服务治理/配置标签路由.md)。

