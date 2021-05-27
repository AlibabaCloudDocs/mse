# 快速体验Ingress网关

您可以为微服务创建一个Ingress网关，通过从MSE Nacos添加服务或者从容器服务ACK关联服务，然后在网关中为服务创建路由策略，以便该服务通过网关对外提供服务。本文帮助您快速体验Ingress网关。

## 体验流程

微服务如果部署到容器服务ACK或注册到MSE Nacos注册中心，微服务网关可直接从ACK关联服务，也可以从MSE Nacos添加服务。

![Ingress网关体验流程](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9616802261/p278075.png)

1.  [新建Ingress网关](/cn.zh-CN/Ingress网关/网关管理/新建Ingress网关.md)

    根据已有微服务环境，创建微服务网关。

2.  [新建服务来源](/cn.zh-CN/Ingress网关/服务来源管理/新建服务来源.md)

    在微服务网关中添加服务来源，包括容器服务ACK和MSE Nacos。

3.  [添加服务](/cn.zh-CN/Ingress网关/服务管理/添加服务.md)

    微服务网关能够根据容器服务ACK或MSE Nacos来源获取服务的命名空间，将已有的服务添加到微服务网关，作为备选服务。

4.  [新建路由配置](/cn.zh-CN/Ingress网关/路由配置管理/新建路由配置.md)

    为该服务添加路由策略并发布。


