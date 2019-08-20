# DescribeReplicationJobs {#doc_api_smc_DescribeReplicationJobs .reference}

You can call this operation to query detailed information for one or more migration tasks.

## Description {#description .section}

You can specify multiple request parameters to be queried. Specified parameters have logical AND relations. Only specified parameters will be included in the filtering conditions.

## Debugging {#apiExplorer .section}

Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/#product=smc&api=DescribeReplicationJobs) to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|No|DescribeReplicationJobs| The operation that you want to perform. Set this parameter to DescribeReplicationJobs.

 |
|BusinessStatus|String|No|Preparing| The business status of the migration task to be queried. Valid values:

 -   Preparing
-   Syncing
-   Processing
-   Cleaning

 |
|JobId.N|RepeatList|No|j-xxxxxxxxxxxxxxx| The ID of migration task N. Valid values of N: 1 to 50.

 |
|Name|String|No|MyMigrationTask| The name of the migration task.

 |
|PageNumber|Integer|No|1| The number of the page to return. Pages start from page 1.

 Default value: 1

 |
|PageSize|Integer|No|10| The number of entries to return on each page. Valid values: 1 to 50

 Default value: 10

 |
|RegionId|String|No|cn-hangzhou| The ID of the Alibaba Cloud region to which the source server is to be migrated.

 If you want to migrate the source server to Shanghai, set the RegionId parameter to `cn-shanghai`. You can call the [DescribeRegions](~~25609~~) operation to query the latest regions of Alibaba Cloud.

 |
|SourceId.N|RepeatList|No|s-xxxxxxxxxxxxxxx| The ID of migration source N. Valid values of N: 1 to 50.

 |
|Status|String|No|Ready| The main status of the migration task. Valid values:

 -   Ready
-   Running
-   Stopped
-   InError
-   Finished
-   Expired
-   Deleting

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|PageNumber|Integer|1| The returned page number of the migration task list.

 |
|PageSize|Integer|10| The number of entries returned on each page.

 |
|ReplicationJobs| | | A collection of migration tasks.

 |
|└BusinessStatus|String|Preparing| The business status of the migration task.

 |
|└CreationTime|String|2014-07-24T13:00:52Z| The time when the migration task was created.

 |
|└DataDisks| | | The array of data disks for the target Alibaba Cloud ECS instance.

 |
|└Index|Integer|1| The serial number of a data disk.

 |
|└Size|Integer|40| The size of a data disk. Unit: GiB.

 |
|└Description|String|This is my migration task.| The description of the migration task.

 |
|└EndTime|String|2019-06-04T16:00:52Z| The time when the migration task was completed.

 |
|└ErrorCode|String|InternalError| The error code of the migration task.

 |
|└ImageId|String|xxxxxxxxxxxxxxxx| The ID of the target image delivered by the migration task.

 |
|└ImageName|String|MyAliCloudImage| The name of the target image delivered by the migration task.

 |
|└InstanceId|String|i-xxxxxxxxxxxx| The ID of the target instance.

 |
|└JobId|String|j-xxxxxxxxxxxx| The ID of the migration task.

 |
|└Name|String|MyMigrationTask| The name of the migration task.

 |
|└NetMode|Integer|0| The network type used for migration.

 |
|└Progress|Float|55.45| The overall progress of the migration task.

 |
|└RegionId|String|cn-hangzhou| The ID of the Alibaba Cloud region to which the source server is to be migrated.

 |
|└ReplicationParameters|String|BandWidthLimit:0| The replication driver parameters.

 |
|└ScheduledStartTime|String|2019-06-04T 13:35:00Z| The time when the migration task was executed.

 |
|└SourceId|String|s-xxxxxxxxxxx| The ID of the migration source.

 |
|└StartTime|String|2019-06-04T14:40:52Z| The start time of the migration task.

 |
|└Status|String|Running| The main status of the migration task.

 |
|└StatusInfo|String|statusinfo| The migration status information.

 |
|└SystemDiskSize|Integer|40| The system disk size of the target Alibaba Cloud ECS instance.

 |
|└TargetType|String|image| The type of migration destination delivered by the migration task.

 |
|└TransitionInstanceId|String|instanceid2| The ID of the intermediate instance.

 |
|└VSwitchId|String|xxxxxxxxxxxxxxx| The ID of the VSwitch connected to the specified VPC.

 |
|└ValidTime|String|2019-06-08T14:40:52Z| The time when the migration task is set to expire.

 |
|└VpcId|String|xxxxxxxxxxxxxxx| The ID of the VPC. The specified VPC must have Express Connect or VPN Gateway configured.

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |
|TotalCount|Integer|5| The total number of migration tasks.

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}

http(s)://smc.aliyuncs.com/?Action=DescribeReplicationJobs
&<Common request parameters>

```

Sample success response

`XML` format

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
      <Description>This is my migration task. </Description>
      <EndTime>2019-06-04T16:00:52Z</EndTime>
      <ErrorCode>InternalError</ErrorCode>
      <ImageId>xxxxxxxxxxxxxxx</ImageId>
      <ImageName>MyAilCloudImage</ImageName>
      <InstanceId>i-xxxxxxxxxxxxxxx</InstanceId>
      <JobId>j-xxxxxxxxxxxxxxx</JobId>
      <Name> MyMiagrationTask </Name>
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

`JSON` format

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

## Error codes {#section_8on_1qq_bcu .section}

[View error codes](https://error-center.aliyun.com/status/product/smc)

