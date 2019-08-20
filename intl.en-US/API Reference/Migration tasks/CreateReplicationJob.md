# CreateReplicationJob {#doc_api_smc_CreateReplicationJob .reference}

You can call this operation to create a migration task for a migration source.

## Description {#description .section}

-   Migration tasks can only be created for migration sources that are in the Available state.
-   Each migration source can only be associated with a single unfinished migration task. Unfinished states include Ready, Running, Stopped, InError, and Expired.
-   Each Alibaba Cloud account can have up to 100 migration tasks.
-   When the type of migration destination is image, you must specify the ImageName, SystemDiskSize, and DataDisk parameters.
-   When you perform a VPC-based migration, the VSwitchId parameter is required and the VpcId parameter is optional.

## Debugging {#apiExplorer .section}

Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/#product=smc&api=CreateReplicationJob) to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou| The ID of the Alibaba Cloud region to which the source server is to be migrated.

 If you want to migrate the source server to Shanghai, the corresponding Alibaba Cloud region ID is `cn-shanghai`. You can call the [DescribeRegions](~~25609~~) operation to view the latest regions of Alibaba Cloud.

 |
|SourceId|String|Yes|s-xxxxxxxxxxxxxxx| The ID of the migration source.

 |
|SystemDiskSize|Integer|Yes|80| The system disk size of the target Alibaba Cloud ECS instance. Unit: GiB. Valid values: 20 to 500.

 **Note:** The parameter value must be greater than the actual used space of the system disk on the source server. For example, if the size of the source disk was 500 GiB but the actual used space was only 100 GiB, you would only need to set this parameter to a value greater than 100 GiB.

 |
|Action|String|No|CreateReplicationJob| The operation that you want to perform. Set this parameter to CreateReplicationJob.

 |
|ClientToken|String|No|xxxxxxxxxx| A client token that is used to ensure the idempotence of the request.

 |
|DataDisk.N.Index|Integer|No|1| The serial number of data disk N for the target Alibaba Cloud ECS instance. Valid values: 1 to 16. The parameter value starts from 1.

 **Note:** This operation can only create target data disks for data disks that exist on the migration source.

 |
|DataDisk.N.Size|Integer|No|100| The size of data disk N for the target Alibaba Cloud ECS instance. Unit: GiB. Valid values: 20 to 32768.

 **Note:** The parameter value must be greater than the actual used space of the data disk on the source server. For example, if the size of the source disk was 500 GiB but the actual used space was only 100 GiB, you would only need to set this parameter to a value greater than 100 GiB.

 |
|Description|String|No|This\_is\_a\_migration\_task| The description of the migration task to be created. The description must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.

 |
|ImageName|String|No|MyAliCloudImage| The name of the target Alibaba Cloud image to be delivered by the migration task. The target image name must meet the following requirements:

 -   The image name must be unique in an Alibaba Cloud region.
-   The name must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.

 **Note:** If the specified image name already exists in the region where the migration task is running, the migration task ID is added to the image name as a suffix. Example: ImageName-JobId.

 |
|InstanceId|String|No|i-xxxxxxxxxxxxx| The ID of the target instance.

 |
|Name|String|No|MigrationTask| The name of the migration task. The migration task name must meet the following requirements:

 -   The task name must be unique.
-   The name must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.

 |
|NetMode|Integer|No|0| The network mode in which data is transmitted.

 -   A value of 0 indicates that data is transmitted through the public network. In this case, your source server is required to be able to access the public network, and cloud migration data is transmitted through the public network.
-   A value of 2 indicates that data is transmitted through the internal network. In this case, the VSwitchId parameter must be specified. The VpcId parameter can be left unspecified, and its value can be retrieved through the SMC API.

 Default value: 0

 |
|ReplicationParameters|String|No|BandWidthLimit:0| The replication driver parameters. The parameter information can be up to 2,048 characters in length.

 The parameters must be specified as key-value pairs in JSON format. The key-value pairs are extensible and have known fixed keys. Different drivers support different parameters. For more information, see SourceServer.ReplicationDriver. For example, the SMT driver supports the following parameters:

 -   BandwidthLimit: specifies the bandwidth limit for data transmission.
-   CompressLevel: specifies the transmission compression rate.
-   Checksum: specifies whether to enable the checksum verification.
-   UseSSHTunnel: specifies whether to enable the SSH encrypted tunnel. EfficiencyLevel: specifies the efficiency level of data transmission.

 |
|ScheduledStartTime|String|No|2019-06-04T13:35:00Z| The time when the migration task will be executed. The parameter value must meet the following requirements:

 -   You must specify the time in the ISO 8601 standard in the YYYY-MM-DDThh:mm:ssZ format. The time must be in UTC. Example: 2018-01-01T12:00:00Z.
-   The value must be within 30 days after the current time.

 **Note:** If this parameter is not specified, the migration task will not be started automatically. You must call the [StartReplicationJob](~~121823~~) operation to start the task.

 |
|TargetType|String|No|image| The type of migration destination to be delivered by the migration task. Set the value to image. After successful migration, SMC will generate an Alibaba Cloud image for the migration source. You can use this image to create an ECS instance and complete the migration to Alibaba Cloud.

 |
|VSwitchId|String|No|xxxxxxxxxxxxxx| The ID of the VSwitch to connect to the specified VPC.

 |
|ValidTime|String|No|2019-06-04T13:35:00Z| The time when the migration task is set to expire. You can schedule the migration task to expire on a date within 7 to 90 days of creation.

 -   Specify the time in the ISO 8601 standard in the YYYY-MM-DDThh:mm:ssZ format. The time must be in UTC. Example: 2018-01-01T12:00:00Z.
-   If this parameter is not specified, the migration task will be permanently valid.
-   After the task expires, it is marked as expired and retained for seven days. After the seven days have passed, the system will clear the task.

 The default validity period for a migration task is 30 days after creation.

 |
|VpcId|String|No|xxxxxxxxxxxxxx| The ID of the VPC. The specified VPC must have Express Connect or VPN Gateway configured.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|JobId|String|j-xxxxxxxxxxxxxxx| The ID of the migration task.

 |
|RequestId|String|C8B26B44-0189-443E-9816-D951F59623A9| The ID of the request.

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}

http(s)://smc.aliyuncs.com/? Action=CreateReplicationJob
&RegionId=cn-hangzhou
&SourceId=s-xxxxxxxxxxxxxxx
&SystemDiskSize=80
&<Common request parameters>

```

Sample success response

`XML` format

``` {#xml_return_success_demo}
<CreateReplicationJobResponse>
  <JobId>j-2xxxxxxxxxxxq</JobId>
  <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
</CreateReplicationJobResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"C8B26B44-0189-443E-9816-D951F59623A9",
	"JobId":"j-2xxxxxxxxxxq"
}
```

## Error codes {#section_q1l_tfz_xgj .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|SourceServerState.Invalid|The specified source server status is invalid.|The error message returned because the operation is not supported while the migration source is in the current state.|
|400|ReplicationJobDataDiskIndex.Invalid|The specified replication job contains data disk index not found in source server.|The error message returned because the specified migration task contains data disk indexes not found in the migration source.|
|400|VSwitchIdVpcId.Mismatch|The specified VSwitchId and VpcId does not match.|The error message returned because the specified VSwitchId and VpcId do not correspond to each other.|
|400|InvalidSecurityGroupId.IncorrectNetworkType|The network type of the specified security group does not support this action.|The error message returned because the operation is not supported by security groups of the current network type. Check the network type of the security group.|
|400|InvalidSecurityGroupId.VPCMismatch|The specified security group and the specified virtual switch are not in the same VPC.|The error message returned because the specified security group and VSwitch do not belong to the same VPC.|
|400|QuotaExceeded.ReplicationJob|The maximum number of replication jobs is exceeded. Please submit a ticket to raise the quota.|The error message returned because the maximum number of migration tasks has been reached. Submit a ticket to raise the quota.|
|400|ReplicationJobName.Duplicate|The specified replication job name already exists.|The error message returned because the specified migration task name already exists. Modify the migration task name.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

