# API 概览

本文介绍服务器迁移中心SMC提供的相关API接口。

更多API资源，请参见[OpenAPI开发者门户](https://next.api.aliyun.com/api/smc/2019-06-01)。

## 迁移源相关API

|API|描述|
|:--|:-|
|[DescribeSourceServers](/cn.zh-CN/API参考/迁移源/DescribeSourceServers.md)|查询一个或多个迁移源信息。|
|[DeleteSourceServer](/cn.zh-CN/API参考/迁移源/DeleteSourceServer.md)|删除一个迁移源。|
|[ModifySourceServerAttribute](/cn.zh-CN/API参考/迁移源/ModifySourceServerAttribute.md)|修改迁移源名称、描述。|

## 迁移任务相关API

|API|描述|
|:--|:-|
|[CreateReplicationJob](/cn.zh-CN/API参考/迁云任务/CreateReplicationJob.md)|创建一个迁移任务。|
|[DescribeReplicationJobs](/cn.zh-CN/API参考/迁云任务/DescribeReplicationJobs.md)|查询一个或多个迁移任务信息。|
|[DeleteReplicationJob](/cn.zh-CN/API参考/迁云任务/DeleteReplicationJob.md)|删除一个迁移任务。|
|[ModifyReplicationJobAttribute](/cn.zh-CN/API参考/迁云任务/ModifyReplicationJobAttribute.md)|修改一个迁移任务的属性信息。|
|[StartReplicationJob](/cn.zh-CN/API参考/迁云任务/StartReplicationJob.md)|启动一个迁移任务。|
|[StopReplicationJob](/cn.zh-CN/API参考/迁云任务/StopReplicationJob.md)|暂停一个迁移任务。|

## 标签相关API

|API|描述|
|:--|:-|
|[TagResources](/cn.zh-CN/API参考/标签/TagResources.md)|为指定的SMC资源（迁移源和迁移任务）创建并绑定标签。|
|[ListTagResources](/cn.zh-CN/API参考/标签/ListTagResources.md)|查询一个或多个SMC资源（迁移源和迁移任务）已经绑定的标签。|
|[UntagResources](/cn.zh-CN/API参考/标签/UntagResources.md)|为指定的SMC资源（迁移源和迁移任务）解绑并删除标签。|

