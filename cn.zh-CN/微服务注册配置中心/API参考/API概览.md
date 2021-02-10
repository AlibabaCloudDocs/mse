# API概览

本文列举了微服务引擎MSE支持的API接口。

## 实例管理API

实例管理相关的API如下。

|API|描述|
|---|--|
|[CreateZnode](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/CreateZnode.md)|调用CreateZnode接口创建Zookeeper数据节点。|
|[CreateEngineNamespace](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/CreateEngineNamespace.md)|调用CreateEngineNamespace接口，创建引擎命名空间。|
|[DeleteZnode](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/DeleteZnode.md)|调用DeleteZnode接口释放Zookeeper数据节点。|
|[ListZnodeChildren](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/ListZnodeChildren.md)|调用ListZnodeChildren接口查看ZooKeeper集群列表详情。|
|[ListAnsInstances](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/ListAnsInstances.md)|调用ListAnsInstances接口查看实例详情。|
|[ListAnsServices](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/ListAnsServices.md)|调用ListAnsServices接口查看服务详情。|
|[ListEngineNamespaces](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/ListEngineNamespaces.md)|调用ListEngineNamespaces接口获取引擎命名空间列表信息。|
|[ListEurekaInstances](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/ListEurekaInstances.md)|调用ListEurekaInstances接口查看Eureka实例详情。|
|[ListEurekaServices](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/ListEurekaServices.md)|调用ListEurekaServices接口查看Eureka服务详情。|
|[QueryConfig](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/QueryConfig.md)|调用QueryConfig接口查询接口配置。|
|[QueryZnodeDetail](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/QueryZnodeDetail.md)|调用QueryZnodeDetail接口查询ZooKeeper数据节点详细。|
|[UpdateAcl](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/UpdateAcl.md)|调用UpdateAcl接口修改白名单。|
|[UpdateConfig](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/UpdateConfig.md)|调用UpdateConfig接口更新配置。|
|[UpdateEngineNamespace](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/UpdateEngineNamespace.md)|调用UpdateEngineNamespace接口，更新引擎命名空间。|
|[UpdateZnode](/cn.zh-CN/微服务注册配置中心/API参考/实例管理/UpdateZnode.md)|调用UpdateZnode接口更新Zookeeper数据节点。|

## 集群管理API

集群管理相关的API如下。

|API|描述|
|---|--|
|[CreateCluster](/cn.zh-CN/微服务注册配置中心/API参考/集群管理/CreateCluster.md)|调用CreateCluster接口创建一个集群。|
|[DeleteCluster](/cn.zh-CN/微服务注册配置中心/API参考/集群管理/DeleteCluster.md)|调用DeleteCluster接口释放集群。|
|[QueryClusterDetail](/cn.zh-CN/微服务注册配置中心/API参考/集群管理/QueryClusterDetail.md)|调用QueryClusterDetail接口查询集群详情。|
|[ListClusters](/cn.zh-CN/微服务注册配置中心/API参考/集群管理/ListClusters.md)|调用ListClusters接口查询集群列表。|
|[ListAnsServiceClusters](/cn.zh-CN/微服务注册配置中心/API参考/集群管理/ListAnsServiceClusters.md)|调用ListAnsServiceClusters接口查看集群服务详情。|
|[QueryClusterSpecification](/cn.zh-CN/微服务注册配置中心/API参考/集群管理/QueryClusterSpecification.md)|调用QueryClusterSpecification接口查询集群规格。|
|[UpdateCluster](/cn.zh-CN/微服务注册配置中心/API参考/集群管理/UpdateCluster.md)|调用UpdateCluster接口修改集群信息。|
|[RestartCluster](/cn.zh-CN/微服务注册配置中心/API参考/集群管理/RestartCluster.md)|调用RestartCluster接口重启集群。|
|[ScalingCluster](/cn.zh-CN/微服务注册配置中心/API参考/集群管理/ScalingCluster.md)|调用ScalingCluster接口伸缩集群。|

## 报警管理API

报警管理相关的API如下。

|API|描述|
|---|--|
|[CreateAlarmRule](/cn.zh-CN/微服务注册配置中心/API参考/报警管理/CreateAlarmRule.md)|调用CreateAlarmRule接口创建报警规则。|
|[DeleteAlarmRule](/cn.zh-CN/微服务注册配置中心/API参考/报警管理/DeleteAlarmRule.md)|调用DeleteAlarmRule接口删除报警规则。|
|[ListAlarmContactGroups](/cn.zh-CN/微服务注册配置中心/API参考/报警管理/ListAlarmContactGroups.md)|调用ListAlarmContactGroups接口，获取报警联系人分组列表。|
|[ListAlarmItems](/cn.zh-CN/微服务注册配置中心/API参考/报警管理/ListAlarmItems.md)|调用ListAlarmItems接口获取报警列表。|
|[ListAlarmRules](/cn.zh-CN/微服务注册配置中心/API参考/报警管理/ListAlarmRules.md)|调用ListAlarmRules接口获取告警规则清单。|

## 监控管理API

监控管理相关的API如下。

|API|描述|
|---|--|
|[QueryMonitor](/cn.zh-CN/微服务注册配置中心/API参考/监控管理/QueryMonitor.md)|调用QueryMonitor接口查询监控信息。|

