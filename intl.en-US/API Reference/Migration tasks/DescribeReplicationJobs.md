# DescribeReplicationJobs

Queries the details of one or more migration tasks.

## Description

-   You can specify multiple request parameters. The parameters that you specify have logical AND relations. If you leave a parameter empty, this parameter is not included in the conditions to filter query results.
-   You can migrate source servers to Docker container images. SMC allows you to migrate containerized applications to Container Registry at low costs. For more information, see [Container Registry](~~60744~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=DescribeReplicationJobs&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeReplicationJobs|The operation that you want to perform. Set the value to DescribeReplicationJobs. |
|SourceId.N|RepeatList|No|s-bp1e2fsl57knvuug\*\*\*\*|The ID of a source server. Maximum value of N: 50. |
|JobId.N|RepeatList|No|j-bp19vlwm0tyigbmj\*\*\*\*|The ID of a migration task. Maximum value of N: 50. |
|Name|String|No|testMigrationTaskName|The name of a migration task. |
|RegionId|String|No|cn-hangzhou|The ID of the destination Alibaba Cloud region.

 For example, if you want to migrate the source server to Shanghai, set the value to `cn-shanghai`. You can call [DescribeRegions](~~25609~~) to query the latest list of Alibaba Cloud regions. |
|Status|String|No|Ready|The main status of the migration task. Valid values:

 -   Ready
-   Running
-   Stopped
-   InError
-   Finished
-   Waiting
-   Expired
-   Deleting |
|BusinessStatus|String|No|Preparing|The business status of the migration task. Valid values:

 -   Preparing
-   Syncing
-   Processing
-   Cleaning |
|PageNumber|Integer|No|1|The number of the page to return. Page numbers start from 1.

 Default value: 1. |
|PageSize|Integer|No|10|The number of entries returned on each page. Maximum value: 50.

 Default value: 10. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|PageNumber|Integer|1|The number of the page returned. |
|PageSize|Integer|10|The number of entries returned on each page. |
|ReplicationJobs|Array| |A list of migration tasks. |
|ReplicationJob| | | |
|BusinessStatus|String|Preparing|The business status of the migration task. |
|ContainerNamespace|String|testNamespace|The namespace of the Docker container image. |
|ContainerRepository|String|testRepository|The repository that stored a Docker container image. |
|ContainerTag|String|CentOS:v1|The tag of a Docker container image. |
|CreationTime|String|2014-07-24T13:00:52Z|The time when the migration task was created. |
|DataDisks|Array| |A list of data disks on the destination ECS instance. |
|DataDisk| | | |
|Index|Integer|1|The index number of the data disk. |
|Parts|Array| |A list of partitions in the data disk. |
|Part| | | |
|Block|Boolean|true|Indicates whether block replication was enabled for a partition in the destination data disk. |
|Device|String|0\_1|The device ID of the data disk partition. |
|SizeBytes|Long|21474836480|The size of a partition in the destination data disk. Unit: bytes. |
|Size|Integer|40|The size of the data disk. Unit: GiB. |
|Description|String|This is my migration task.|The description of the migration task. |
|EndTime|String|2019-06-04T16:00:52Z|The time when a migration task was completed. |
|ErrorCode|String|InternalError|The error code returned during a migration task. |
|Frequency|Integer|15|The interval at which the incremental migration task runs. Unit: hours. Valid values: 1 to 168. |
|ImageId|String|m-o6w3gy99qf89rkga\*\*\*\*|The ID of the destination image. |
|ImageName|String|testAliCloudImageName|The name of the destination image. |
|InstanceId|String|i-bp1ff25rzvnul6kr\*\*\*\*|The ID of the destination ECS instance. |
|InstanceRamRole|String|SMCAdmin|The RAM role that was attached to the intermediate instance. |
|InstanceType|String|ecs.sn1ne.large|The type of the intermediate instance. |
|JobId|String|j-bp19vlwm0tyigbmj\*\*\*\*|The ID of the migration task. |
|LaunchTemplateId|String|lt-launchtemplateid|The ID of the launch template. |
|LaunchTemplateVersion|String|1|One or more launch template versions. |
|MaxNumberOfImageToKeep|Integer|8|The maximum number of images retained for the incremental migration task. Valid values: 1 to 10. |
|Name|String|testMigrationTaskName|The name of the migration task. |
|NetMode|Integer|0|The network mode used for data transmission. |
|Progress|Float|55.45|The progress of the migration task. |
|RegionId|String|cn-hangzhou|The ID of the destination Alibaba Cloud region. |
|ReplicationJobRuns|Array| |A list of the logs of migration tasks. |
|ReplicationJobRun| | | |
|EndTime|String|2019-10-04T13:35:00Z|The time when a migration was complete. |
|ImageId|String|m-o6w3gy99qf89rkga\*\*\*\*|The ID of the destination image. |
|StartTime|String|2019-10-01T13:35:00Z|The time when a migration task was started. |
|Type|String|Schedule|The method used to run the migration task. Valid values:

 -   Manual: A migration task is manually started.
-   Schedule: A migration task is started at a scheduled time or at a specified interval. |
|ReplicationParameters|String|BandWidthLimit:0|A string of key-value pairs to configure a replication driver. |
|RunOnce|Boolean|true|Indicates whether incremental migration was disabled for a source server. Valid values:

 -   true: disables incremental migration. Incremental data of a source server is not synchronized.
-   false: enables incremental migration. SMC synchronizes incremental data to Alibaba Cloud at a specified `Frequency`. |
|ScheduledStartTime|String|2019-06-04T13:35:00Z|The time when the migration task was performed. |
|SourceId|String|s-bp1e2fsl57knvuug\*\*\*\*|The ID of the source server. |
|StartTime|String|2019-06-04T14:40:52Z|The time when the migration task was started. |
|Status|String|Running|The main status of the migration task. |
|StatusInfo|String|statusinfo|The migration status information. |
|SystemDiskParts|Array| |The information of system disk partitions. |
|SystemDiskPart| | | |
|Block|Boolean|true|Indicates whether block replication was enabled for a partition in the destination system disk. |
|Device|String|0\_1|The device ID of the system disk partition. |
|SizeBytes|Long|254803968|The size of a partition in the destination system disk. Unit: bytes. |
|SystemDiskSize|Integer|40|The system disk size of the destination ECS instance. |
|TargetType|String|image|The type of the destination image. |
|TransitionInstanceId|String|i-bp1ff25rzvnul6kr\*\*\*\*|The ID of the intermediate instance. |
|VSwitchId|String|vsw-bp1ddbrxdlrcbim46\*\*\*\*|The ID of the VSwitch in the specified VPC. |
|ValidTime|String|2019-06-08T14:40:52Z|The time when the migration task expired. |
|VpcId|String|vpc-bp1vwnn14rqpyiczj\*\*\*\*|The ID of a VPC for which you have configured Express Connect or VPN Gateway. |
|RequestId|String|6E1187E8-843A-4850-B97E-2F17F00D48F7|The ID of the request. |
|TotalCount|Integer|5|The total number of migration tasks. |

## Examples

Sample requests

```
http(s)://smc.aliyuncs.com/? Action=DescribeReplicationJobs
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeReplicationJobsResponse>
      <TotalCount>1</TotalCount>
      <ReplicationJobs>
            <ReplicationJob>
                  <Status>Running</Status>
                  <Progress>75</Progress>
                  <TransitionInstanceId>i-bp1ff25rzvnul6kr****</TransitionInstanceId>
                  <DataDisks>
                        <DataDisk>
                              <Parts>
                                    <Part>
                                          <Device>2_0</Device>
                                          <Block>true</Block>
                                          <SizeBytes>5334102016</SizeBytes>
                                    </Part>
                              </Parts>
                              <Size>20</Size>
                              <Index>2</Index>
                        </DataDisk>
                  </DataDisks>
                  <SystemDiskSize>20</SystemDiskSize>
                  <NetMode>0</NetMode>
                  <SourceId>s-bp1e2fsl57knvuug****</SourceId>
                  <SystemDiskParts>
                        <SystemDiskPart>
                              <Device>0_0</Device>
                              <Block>true</Block>
                              <SizeBytes>21466120192</SizeBytes>
                        </SystemDiskPart>
                  </SystemDiskParts>
                  <StartTime>2020-05-14T12:01:24Z</StartTime>
                  <BusinessStatus>Processing</BusinessStatus>
                  <Name>testMigrationTaskName</Name>
                  <ValidTime>2020-06-13T12:01:24Z</ValidTime>
                  <RunOnce>true</RunOnce>
                  <TargetType>Image</TargetType>
                  <CreationTime>2020-05-14T12:01:24Z</CreationTime>
                  <RegionId>cn-hangzhou</RegionId>
                  <ErrorCode></ErrorCode>
                  <JobId>j-bp19vlwm0tyigbmj****</JobId>
            </ReplicationJob>
      </ReplicationJobs>
      <RequestId>6E1187E8-843A-4850-B97E-2F17F00D48F7</RequestId>
      <PageSize>10</PageSize>
      <PageNumber>1</PageNumber>
</DescribeReplicationJobsResponse>
```

`JSON` format

```
{
  "TotalCount": 1,
  "ReplicationJobs": {
    "ReplicationJob": [
      {
        "Status": "Running",
        "Progress": 75.0,
        "TransitionInstanceId": "i-bp1ff25rzvnul6kr****",
        "DataDisks": {
          "DataDisk": [
            {
              "Parts": {
                "Part": [
                  {
                    "Device": "2_0",
                    "Block": true,
                    "SizeBytes": 5334102016
                  }
                ]
              },
              "Size": 20,
              "Index": 2
            }
          ]
        },
        "SystemDiskSize": 20,
        "NetMode": 0,
        "SourceId": "s-bp1e2fsl57knvuug****",
        "SystemDiskParts": {
          "SystemDiskPart": [
            {
              "Device": "0_0",
              "Block": true,
              "SizeBytes": 21466120192
            }
          ]
        },
        "StartTime": "2020-05-14T12:01:24Z",
        "BusinessStatus": "Processing",
        "Name": "testMigrationTaskName",
        "ValidTime": "2020-06-13T12:01:24Z",
        "RunOnce": true,
        "TargetType": "Image",
        "CreationTime": "2020-05-14T12:01:24Z",
        "RegionId": "cn-hangzhou",
        "ErrorCode": "",
        "JobId": "j-bp19vlwm0tyigbmj****"
      }
    ]
  },
  "RequestId": "6E1187E8-843A-4850-B97E-2F17F00D48F7",
  "PageSize": 10,
  "PageNumber": 1
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/smc).

