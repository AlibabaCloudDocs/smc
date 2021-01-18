# CutOverReplicationJob

调用CutOverReplicationJob将指定的自动增量迁移任务停止周期执行，并完成迁移任务。

## 接口说明

-   自动增量迁移任务的状态必须处于等待中（Waiting）。
-   调用该接口后，自动增量迁移任务将不再周期执行，而是根据`SyncData`参数取值进行判断。当`SyncData=false`时，不再进行数据迁移，直接自动清理中转资源后，完成迁移任务；当`SyncData=true`时，将进行最后一次全量数据迁移，然后自动清理中转资源，完成迁移任务。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=smc&api=CutOverReplicationJob&type=RPC&version=2019-06-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CutOverReplicationJob|系统规定参数。取值：CutOverReplicationJob |
|JobId|String|是|j-bp1fnx5y3djc4cop\*\*\*\*|自动增量迁移任务ID。 |
|SyncData|Boolean|否|false|是否需要进行最后一次全量数据迁移。

 默认值：false |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。 |

## 示例

请求示例

```
https://smc.aliyuncs.com/?Action=CutOverReplicationJob
&JobId=j-bp1fnx5y3djc4cop****
&SyncData=false
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CutOverReplicationJobResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</CutOverReplicationJobResponse>
```

`JSON` 格式

```
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"	
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ReplicationJob.InvalidStatus|The specified replication job status is invalid.|无效的迁移任务状态。|
|400|SourceServerState.Invalid|The specified source server status is invalid.|无效的迁移源状态。|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|内部错误，请重试。如果多次尝试失败，请提交工单。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/smc)查看更多错误码。

