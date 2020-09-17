# API概览

本文列举了微服务引擎MSE支持的API接口。

## 实例相关API

实例相关的API如下。

|API|描述|
|---|--|
|[CreateZnode](/cn.zh-CN/API参考/实例相关接口/CreateZnode.md)|调用CreateZnode接口创建Zookeeper数据节点。|
|[CreateEngineNamespace](/cn.zh-CN/API参考/实例相关接口/CreateEngineNamespace.md)|调用CreateEngineNamespace接口，创建引擎命名空间。|
|[DeleteZnode](/cn.zh-CN/API参考/实例相关接口/DeleteZnode.md)|调用DeleteZnode接口释放Zookeeper数据节点。|
|[ListZnodeChildren](/cn.zh-CN/API参考/实例相关接口/ListZnodeChildren.md)|调用ListZnodeChildren接口查看ZooKeeper集群列表详情。|
|[ListAnsInstances](/cn.zh-CN/API参考/实例相关接口/ListAnsInstances.md)|调用ListAnsInstances接口查看实例详情。|
|[ListAnsServices](/cn.zh-CN/API参考/实例相关接口/ListAnsServices.md)|调用ListAnsServices接口查看服务详情。|
|[ListEngineNamespaces](/cn.zh-CN/API参考/实例相关接口/ListEngineNamespaces.md)|调用ListEngineNamespaces接口获取引擎命名空间列表信息。|
|[ListEurekaInstances](/cn.zh-CN/API参考/实例相关接口/ListEurekaInstances.md)|调用ListEurekaInstances接口查看Eureka实例详情。|
|[ListEurekaServices](/cn.zh-CN/API参考/实例相关接口/ListEurekaServices.md)|调用ListEurekaServices接口查看Eureka服务详情。|
|[QueryConfig](/cn.zh-CN/API参考/实例相关接口/QueryConfig.md)|调用QueryConfig接口查询接口配置。|
|[QueryZnodeDetail](/cn.zh-CN/API参考/实例相关接口/QueryZnodeDetail.md)|调用QueryZnodeDetail接口查询ZooKeeper数据节点详细。|
|[UpdateAcl](/cn.zh-CN/API参考/实例相关接口/UpdateAcl.md)|调用UpdateAcl接口修改白名单。|
|[UpdateConfig](/cn.zh-CN/API参考/实例相关接口/UpdateConfig.md)|调用UpdateConfig接口更新配置。|
|[UpdateEngineNamespace](/cn.zh-CN/API参考/实例相关接口/UpdateEngineNamespace.md)|调用UpdateEngineNamespace接口，更新引擎命名空间。|
|[UpdateZnode](/cn.zh-CN/API参考/实例相关接口/UpdateZnode.md)|调用UpdateZnode接口更新Zookeeper数据节点。|

## 集群相关API

集群相关的API如下。

|API|描述|
|---|--|
|[CreateCluster](/cn.zh-CN/API参考/集群相关接口/CreateCluster.md)|调用CreateCluster接口创建一个集群。|
|[DeleteCluster](/cn.zh-CN/API参考/集群相关接口/DeleteCluster.md)|调用DeleteCluster接口释放集群。|
|[QueryClusterDetail](/cn.zh-CN/API参考/集群相关接口/QueryClusterDetail.md)|调用QueryClusterDetail接口查询集群详情。|
|[ListCluster](/cn.zh-CN/API参考/集群相关接口/ListCluster.md)|调用ListClusters接口查询集群列表。|
|[ListAnsServiceClusters](/cn.zh-CN/API参考/集群相关接口/ListAnsServiceClusters.md)|调用ListAnsServiceClusters接口查看集群服务详情。|
|[QueryClusterSpecification](/cn.zh-CN/API参考/集群相关接口/QueryClusterSpecification.md)|调用QueryClusterSpecification接口查询集群规格。|
|[UpdateCluster](/cn.zh-CN/API参考/集群相关接口/UpdateCluster.md)|调用UpdateCluster接口修改集群信息。|
|[RestartCluster](/cn.zh-CN/API参考/集群相关接口/RestartCluster.md)|调用RestartCluster接口重启集群。|
|[ScalingCluster](/cn.zh-CN/API参考/集群相关接口/ScalingCluster.md)|调用ScalingCluster接口伸缩集群。|

## 报警相关API

报警相关的API如下。

|API|描述|
|---|--|
|[CreateAlarmRule](/cn.zh-CN/API参考/报警相关接口/CreateAlarmRule.md)|调用CreateAlarmRule接口创建报警规则。|
|[DeleteAlarmRule](/cn.zh-CN/API参考/报警相关接口/DeleteAlarmRule.md)|调用DeleteAlarmRule接口删除报警规则。|
|[ListAlarmContactGroups](/cn.zh-CN/API参考/报警相关接口/ListAlarmContactGroups.md)|调用ListAlarmContactGroups接口，获取报警联系人分组列表。|
|[ListAlarmItems](/cn.zh-CN/API参考/报警相关接口/ListAlarmItems.md)|调用ListAlarmItems接口获取报警列表。|
|[ListAlarmRules](/cn.zh-CN/API参考/报警相关接口/ListAlarmRules.md)|调用ListAlarmRules接口获取告警规则清单。|

## 监控相关API

监控相关的API如下。

|API|描述|
|---|--|
|[QueryMonitor](/cn.zh-CN/API参考/监控相关接口/QueryMonitor.md)|调用QueryMonitor接口查询监控信息。|

