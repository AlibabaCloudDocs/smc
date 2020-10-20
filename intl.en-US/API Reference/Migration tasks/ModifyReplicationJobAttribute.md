# ModifyReplicationJobAttribute

Modifies the parameters of a migration task.

## Description

Before you modify the parameters of a migration task, note the following information:

-   The `Name` and `Description` parameters can be modified during the lifecycle of the migration task.
-   The `Frequency` and `MaxNumberOfImageToKeep` parameters can be modified only before the migration task is performed or when the migration task is in the `Waiting` state.
-   Other parameters can be modified only before the migration task is performed.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=ModifyReplicationJobAttribute&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyReplicationJobAttribute|The operation that you want to perform. Set the value to ModifyReplicationJobAttribute. |
|JobId|String|Yes|j-bp19vlwm0tyigbmj\*\*\*\*|The ID of the migration task. |
|Name|String|No|testMigrationTaskName|The name of the migration task. The name must meet the following requirements:

 -   It must be unique.
-   It must be 2 to 128 characters in length and can contain digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with `http://` or `https://`. |
|Description|String|No|This\_is\_my\_migration\_task|The description of the migration task.

 The description must be 2 to 128 characters in length and can contain digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with `http://` or `https://`. |
|TargetType|String|No|Image|The type of the destination image. You can modify the value only before the migration task starts. Valid values:

 -   Image: After the migration task is completed, Server Migration Center \(SMC\) generates a destination Elastic Compute Service \(ECS\) image for the source server. You can use the image to create an ECS instance.
-   ContainerImage: After the migration task is completed, SMC generates a container image for the source server. You can use the container image in Container Registry.

 **Note:**

-   The value of this parameter is case-insensitive.
-   You can modify only the type of the destination image that is created for a Linux server. Windows servers cannot be migrated to Container Registry. Therefore, when the migration source is a Windows server, this parameter can only be set to `Image`. |
|ScheduledStartTime|String|No|2019-06-04T13:35:00Z|The time when the migration task is performed. SMC starts the migration task at the specified time.

 Specify the time in the ISO 8601 standard in the YYYY-MM-DDThh:mm:ssZ format. The time must be in UTC. For example, 2018-01-01T12:00:00Z indicates 20:00:00 on January 1, 2018 \(UTC+8\).

 **Note:** If the parameter is not specified, SMC cannot start the migration task. You must call the [StartReplicationJob](~~121823~~) operation to start the task. |
|ImageName|String|No|testAliCloudImageName|The name of the destination image. The name must meet the following requirements:

 -   It must be unique in an Alibaba Cloud region.
-   It must be 2 to 128 characters in length and can contain digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with `http://` or `https://`.

 **Note:** If the specified image name already exists in the region where the migration task is running, the migration task ID is added to the image name as a suffix. Example: ImageName-JobId. |
|InstanceId|String|No|i-bp1f1dvfto1sigz5\*\*\*\*|The ID of the destination ECS instance. |
|SystemDiskSize|Integer|No|50|The system disk size of the destination ECS instance. Unit: GiB. Valid values: 20 to 500.

 **Note:** The value must be greater than the used space of the system disk on the source server. For example, if the total size of the source disk is 500 GiB and the used space is 100 GiB, the value of this parameter must be greater than 100 GiB. |
|SystemDiskPart.N.Device|String|No|0\_1|The ID of partition N in the destination system disk.

 **Note:** Each destination system disk corresponds to a source system disk. The partitions in a destination system disk are arranged in the same sequential order as those in the corresponding source system disk. |
|SystemDiskPart.N.SizeBytes|Long|No|254803968|The size of partition N in the destination system disk. Unit: bytes. The default value is equal to the partition size of the source system disk.

 **Note:** The total size of the partitions in the destination system disk cannot exceed the size of the destination system disk. |
|SystemDiskPart.N.Block|Boolean|No|true|Specifies whether to enable block replication for partition N in the destination system disk. Valid values:

 -   true
-   false |
|DataDisk.N.Size|Integer|No|100|The data disk size of the destination ECS instance. Unit: GiB. Valid values: 20 to 32768.

 **Note:** The size of a destination data disk must be greater than the size of data in the source data disk. For example, if a source data disk has 500 GiB of storage space and 100 GiB of data, you must set this parameter to a value greater than 100 GiB. |
|DataDisk.N.Index|Integer|No|1|The index of data disk N on the destination ECS instance. Valid values: 1 to 16.

 The data disks on a destination ECS instance are arranged in a sequential order that starts from 1.

 **Note:** To create a destination data disk for a source server, make sure that this source server has data disks. |
|DataDisk.N.Part.N.Device|String|No|0\_1|The ID of partition N in the destination data disk.

 **Note:** Each destination data disk corresponds to a source data disk. The partitions in a destination data disk are arranged in the same sequential order as those in the corresponding source data disk. |
|DataDisk.N.Part.N.SizeBytes|Long|No|254803968|The size of partition N in the destination data disk. Unit: bytes. The default value is equal to the partition size of the source data disk.

 **Note:** The total size of the partitions in the destination data disk cannot exceed the size of the destination data disk. |
|DataDisk.N.Part.N.Block|Boolean|No|true|Specifies whether to enable block replication for partition N in the destination data disk. Valid values:

 -   true
-   false |
|Frequency|Integer|No|10|The interval at which an incremental migration task runs. Unit: hours. Valid values: 1 to 168.

 `This parameter is required if you set`RunOnce to false. |
|MaxNumberOfImageToKeep|Integer|No|5|The maximum number of images that are retained for an incremental migration task. Valid values: 1 to 10.

 `This parameter is required if you set`RunOnce to false. |
|InstanceType|String|No|ecs.c5.large|The type of the intermediate instance.

 You can call the [DescribeInstanceTypes](~~25620~~) operation to query the instance types that are provided by ECS.

 -   If you specify this parameter, SMC creates an intermediate instance of the specified type. If the specified instance type is unavailable, you cannot create the migration task.
-   If you do not specify this parameter, SMC selects an available instance type in a specific order to create an intermediate instance. For more information about available intermediate instance types, see [SMC FAQ](~~121707~~). |
|InstanceRamRole|String|No|SMCAdmin|The RAM role that is attached to an intermediate instance. |
|ContainerNamespace|String|No|testNamespace|The namespace of the destination Docker container image. For more information about Docker container images, see [Container Registry](~~60744~~). |
|ContainerRepository|String|No|testRepository|The repository that stores the destination Docker container image. For more information about Docker container images, see [Container Registry](~~60744~~). |
|ContainerTag|String|No|CentOS:v1|The tag of the destination Docker container image. For more information about Docker container images, see [Container Registry](~~60744~~). |
|ValidTime|String|No|2019-06-04T13:35:00Z|The time when the migration task expires. You can schedule the migration task to expire 7 to 90 days after the task is created.

 -   This parameter can be modified only when the migration task is in the Ready, Running, Stopped, InError, or Waiting state.
-   Specify the time in the ISO 8601 standard in the `YYYY-MM-DDThh:mm:ssZ` format. The time must be in UTC. For example, 2018-01-01T12:00:00Z indicates 20:00:00 on January 1, 2018 \(UTC+8\).
-   If this parameter is not specified, the migration task does not expire.
-   When a migration task expires, the task enters the Expired state. SMC retains the migration task for seven days after the task expires. After the retention period, SMC deletes the migration task.

 By default, a migration task is valid within 30 days after it is created. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|1C488B66-B819-4D14-8711-C4EAAA13AC01|The ID of the request. |

## Examples

Sample requests

```
http(s)://smc.aliyuncs.com/? Action=ModifyReplicationJobAttribute
&JobId=j-bp19vlwm0tyigbmj****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteReplicationJobResponse>
    <RequestId>1C488B66-B819-4D14-8711-C4EAAA13AC01</RequestId>
</DeleteReplicationJobResponse>
```

`JSON` format

```
{
	"RequestId":"1C488B66-B819-4D14-8711-C4EAAA13AC01"	
}
```

## Error code

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|DataDisk.DuplicateIndex|The source server data disk cannot contain the same index.|The error message returned because the data disks of the migration source have duplicate indexes.|
|400|ReplicationJob.InvalidStatus|The specified replication job status is invalid.|The error message returned because the operation is not supported while the migration task is in the current status.|
|400|ReplicationJobDataDiskIndex.Invalid|The specified replication job contains data disk index not found in source server.|The error message returned because the specified migration task contains data disk indexes that are not found in the source server.|
|400|ReplicationJobName.Duplicate|The specified replication job name already exists.|The error message returned because the specified migration task name already exists. Modify the migration task name.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the error persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/smc).

