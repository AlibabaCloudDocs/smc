# DescribeReplicationJobs {#doc_api_smc_DescribeReplicationJobs .reference}

查询一个或多个迁移任务的详细信息。

## 接口说明 {#description .section}

请求参数的作用类似于一个过滤器，过滤器为逻辑与（AND）关系。如果某一参数为空，则过滤器不起作用。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=smc&api=DescribeReplicationJobs)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|否|DescribeReplicationJobs|系统规定参数。取值：DescribeReplicationJobs

 |
|BusinessStatus|String|否|Preparing|迁移任务的业务状态，取值范围：

 -   Preparing（准备中）
-   Syncing（同步中）
-   Processing（处理中）
-   Cleaning（清除中）

 |
|JobId.N|RepeatList|否|j-xxxxxxxxxxxxxxx|迁移任务ID列表。N的最大值：50。

 |
|Name|String|否|MyMigrationTask|迁移任务的名称。

 |
|PageNumber|Integer|否|1|返回结果中，迁移任务列表的页码。起始值：1。

 默认值：1。

 |
|PageSize|Integer|否|10|分页查询时设置的每页行数。最大值：50。

 默认值：10。

 |
|RegionId|String|否|cn-hangzhou|迁移源需迁入的目标阿里云地域ID。

 例如，您需要迁移源服务器至上海，则RegionId为`cn-shanghai`。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|SourceId.N|RepeatList|否|s-xxxxxxxxxxxxxxx|迁移源ID列表。N的最大值：50。

 |
|Status|String|否|Ready|迁移任务的主状态。取值范围：

 -   Ready（未开始）
-   Running（运行中）
-   Stopped（已暂停）
-   InError（出错）
-   Finished（已完成）
-   Expired（已过期）
-   Deleting（删除中）

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|迁移任务列表的页码。

 |
|PageSize|Integer|10|每页行数。

 |
|ReplicationJobs| | |迁移任务详情集合。

 |
|└BusinessStatus|String|Preparing|迁移任务的业务状态。

 |
|└CreationTime|String|2014-07-24T13:00:52Z|迁移任务的创建时间。

 |
|└DataDisks| | |目标阿里云服务器ECS的数据盘。

 |
|└Index|Integer|1|数据盘顺序。

 |
|└Size|Integer|40|数据盘大小，单位为GiB。

 |
|└Description|String|This is my migration task.|迁移任务的描述。

 |
|└EndTime|String|2019-06-04T16:00:52Z|迁移任务的完成时间。

 |
|└ErrorCode|String|InternalError|迁移任务的错误码。

 |
|└ImageId|String|xxxxxxxxxxxxxxxx|迁移任务交付的目标镜像ID。

 |
|└ImageName|String|MyAliCloudImage|迁移任务交付的目标镜像名称。

 |
|└InstanceId|String|i-xxxxxxxxxxxx|目标实例ID。

 |
|└JobId|String|j-xxxxxxxxxxxx|迁移任务ID。

 |
|└Name|String|MyMigrationTask|迁移任务名称。

 |
|└NetMode|Integer|0|迁移时使用的网络类型。

 |
|└Progress|Float|55.45|迁移任务总进度。

 |
|└RegionId|String|cn-hangzhou|迁移源需迁入的目标阿里云地域ID。

 |
|└ReplicationParameters|String|BandWidthLimit:0|复制驱动器参数信息。

 |
|└ScheduledStartTime|String|2019-06-04T 13:35:00Z|迁移任务的执行时间。

 |
|└SourceId|String|s-xxxxxxxxxxx|迁移源ID。

 |
|└StartTime|String|2019-06-04T14:40:52Z|迁移任务的开始时间。

 |
|└Status|String|Running|迁移任务的主状态。

 |
|└StatusInfo|String|statusinfo|迁移状态的详细信息。

 |
|└SystemDiskSize|Integer|40|目标阿里云服务器ECS的系统盘大小。

 |
|└TargetType|String|image|迁移交付的目标类型。

 |
|└TransitionInstanceId|String|instanceid2|迁移中转实例ID。

 |
|└VSwitchId|String|xxxxxxxxxxxxxxx|指定VPC下的虚拟交换机ID。

 |
|└ValidTime|String|2019-06-08T14:40:52Z|迁移任务的过期时间。

 |
|└VpcId|String|xxxxxxxxxxxxxxx|已配置高速通道服务或者VPN网关的VPC ID。

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。

 |
|TotalCount|Integer|5|迁移任务总个数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://smc.aliyuncs.com/?Action=DescribeReplicationJobs
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeReplicationJobsResponse>
  <PageNumber>1</PageNumber>
  <PageSize>10</PageSize>
  <ReplicationJobs>
    <ReplicationJob>
      <BusinessStatus>Preparing</BusinessStatus>
      <CreationTime>2014-07-24T13:00:52Z</CreationTime>
      <DataDisks>
        <DataDisk>
          <Index>1</Index>
          <Size>40</Size>
        </DataDisk>
      </DataDisks>
      <Description>This is my migration task.</Description>
      <EndTime>2019-06-04T16:00:52Z</EndTime>
      <ErrorCode>InternalError</ErrorCode>
      <ImageId>xxxxxxxxxxxxxxx</ImageId>
      <ImageName>MyAilCloudImage</ImageName>
      <InstanceId>i-xxxxxxxxxxxxxxx</InstanceId>
      <JobId>j-xxxxxxxxxxxxxxx</JobId>
      <Name>MyMiagrationTask</Name>
      <NetMode>0</NetMode>
      <Progress>55.45</Progress>
      <RegionId>cn-hangzhou</RegionId>
      <ReplicationParameters>BandWidthLimit:0</ReplicationParameters>
      <ScheduledStartTime>2019-06-04T13:35:00Z</ScheduledStartTime>
      <SourceId>s-xxxxxxxxxxxxxxx</SourceId>
      <StartTime>2019-06-04T14:40:52Z</StartTime>
      <Status>Running</Status>
      <StatusInfo>statusinfo</StatusInfo>
      <SystemDiskSize>40</SystemDiskSize>
      <TargetType>image</TargetType>
      <TransitionInstanceId>instanceid2</TransitionInstanceId>
      <VSwitchId>xxxxxxxxxxxxxxx</VSwitchId>
      <VaildTime>30</VaildTime>
      <Vpcld>xxxxxxxxxxxxxxx</Vpcld>
    </ReplicationJob>
  </ReplicationJobs>
  <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
  <TotalCount>5</TotalCount>
</DescribeReplicationJobsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":"5",
	"PageSize":10,
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E",
	"ReplicationJobs":{
		"ReplicationJob":[
			{
				"Vpcld":"xxxxxxxxxxxxxxx",
				"ImageId":"xxxxxxxxxxxxxxx",
				"InstanceId":"i-xxxxxxxxxxxxxxx",
				"VSwitchId":"xxxxxxxxxxxxxxx",
				"StatusInfo":"statusinfo",
				"ImageName":"MyAilCloudImage",
				"ScheduledStartTime":"2019-06-04T13:35:00Z",
				"BusinessStatus":"Preparing",
				"JobId":"j-xxxxxxxxxxxxxxx",
				"StartTime":"2019-06-04T14:40:52Z",
				"Description":"This is my migration task.",
				"SystemDiskSize":"40",
				"TargetType":"image",
				"VaildTime":"30",
				"DataDisks":{
					"DataDisk":[
						{
							"Index":"1",
							"Size":"40"
						}
					]
				},
				"ReplicationParameters":"BandWidthLimit:0",
				"NetMode":"0",
				"SourceId":"s-xxxxxxxxxxxxxxx",
				"Progress":"55.45",
				"Name":"MyMiagrationTask",
				"CreationTime":"2014-07-24T13:00:52Z",
				"Status":"Running",
				"RegionId":"cn-hangzhou",
				"TransitionInstanceId":"instanceid2",
				"EndTime":"2019-06-04T16:00:52Z",
				"ErrorCode":"InternalError"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/smc)

