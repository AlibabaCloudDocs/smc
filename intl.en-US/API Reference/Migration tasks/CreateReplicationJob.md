# CreateReplicationJob

Creates a migration task for a source server.

## Description

-   You can create migration tasks only for source servers that are in the Active state.
-   Each source server can be associated with only one migration task that is in the Ready, Running, Stopped, Waiting, InError, or Expired state.
-   You can create a maximum of 100 migration tasks for each Alibaba Cloud account.
-   If you migrate a source server to a destination image, you must specify the ImageName, SystemDiskSize, and DataDisk parameters.
-   If you use a virtual private cloud \(VPC\) to migrate data, the VSwitchId parameter is required but the VpcId parameter is optional.
-   SMC allows you to migrate source servers to Docker container images. You can use SMC to migrate containerized applications to Container Registry at low costs.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=CreateReplicationJob&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateReplicationJob|The operation that you want to perform. Set the value to CreateReplicationJob. |
|RegionId|String|Yes|cn-hangzhou|The ID of the destination Alibaba Cloud region.

For example, if you want to migrate the source server to Shanghai, set the value to `cn-shanghai`. You can call the [DescribeRegions](~~25609~~) operation to query the latest list of Alibaba Cloud regions. |
|SourceId|String|Yes|s-bp1e2fsl57knvuug\*\*\*\*|The ID of the source server. |
|SystemDiskSize|Integer|Yes|80|The system disk size of the destination ECS instance. Unit: GiB. Valid values: 20 to 500.

**Note:** The value must be greater than the used space of the system disk on the source server. For example, if the total size of the source disk is 500 GiB and the used space is 100 GiB, the value of this parameter must be greater than 100 GiB. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to guarantee the idempotence of the request. You can use the client to generate the value. The token can contain only ASCII characters and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~). |
|Name|String|No|testMigrationTaskName|The name of the migration task. The name must meet the following requirements:

-   It must be unique.
-   It must be 2 to 128 characters in length and can contain digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with `http://` or `https://`. |
|Description|String|No|This\_is\_a\_migration\_task|The description of the migration task.

The description must be 2 to 128 characters in length and can contain digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with `http://` or `https://`. |
|TargetType|String|No|Image|The type of the destination image. Valid values:

-   Image: After the migration task is completed, SMC generates a destination ECS image for the source server.
-   ContainerImage: After the migration task is completed, SMC generates a destination Docker container image for the source server.
-   Instance: After the migration task is completed, SMC migrates the source server to the destination instance. If you set this parameter, the ``InstanceId parameter is required. |
|ScheduledStartTime|String|No|2019-06-04T13:35:00Z|The time when the migration task is performed. This parameter must meet the following requirements:

-   The time is specified in the ISO 8601 standard by using the YYYY-MM-DDThh:mm:ssZ format. For example, 2018-01-01T12:00:00Z indicates 20:00:00 on January 1, 2018 \(UTC+8\).
-   The value must be within 30 days after the current time.

**Note:** If you do not specify this parameter, you must manually start the migration task by calling the [StartReplicationJob](~~121823~~) operation. |
|ValidTime|String|No|2019-06-04T13:35:00Z|The time when the migration task expires. You can schedule the migration task to expire 7 to 90 days after the task is created.

-   The time is specified in the ISO 8601 standard by using the YYYY-MM-DDThh:mm:ssZ format. For example, 2018-01-01T12:00:00Z indicates 20:00:00 on January 1, 2018 \(UTC+8\).
-   If this parameter is not specified, the migration task does not expire.
-   When a migration task expires, the task enters the Expired state. SMC retains the migration task for seven days after the task expires. After the task is retained for seven days, SMC deletes the migration task.

By default, a migration task is valid for 30 days after it is created. |
|ImageName|String|No|testAliCloudImageName|The name of the destination image. The name must meet the following requirements:

-   It must be unique in the destination region.
-   It must be 2 to 128 characters in length and can contain digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with `http://` or `https://`.

**Note:** If you specify an image name that already exists in the destination region, the migration task ID is appended to the image name as a suffix. Example: ImageName\_j-2zexxxxxxxxxxxxx. |
|InstanceId|String|No|i-bp1f1dvfto1sigz5\*\*\*\*|The ID of the destination ECS instance. |
|DataDisk.N.Size|Integer|No|100|The size of a data disk on the destination ECS instance. Unit: GiB. Valid values: 20 to 32768.

**Note:** The size of a destination data disk must be larger than the size of data in the source data disk. For example, if the size of the source disk is 500 GiB but the actual used space is only 100 GiB, you only need to set this parameter to a value greater than 100 GiB. |
|DataDisk.N.Index|Integer|No|1|The index of data disk N on the destination ECS instance. Data disks on a destination ECS instance are arranged in a sequential order that starts from 1. Valid values: 1 to 16.

**Note:** To create a destination data disk for a source server, make sure that the source server has data disks. |
|DataDisk.N.Part.N.Device|String|No|0\_1|The device ID of partition N on the destination data disk. The partitions in the destination data disk are arranged in the same sequential order as those in the corresponding source data disk.

**Note:** You must specify both the DataDisk.N.Part.N.Device and `DataDisk.N.Part.N.SizeBytes` parameters or leave both parameters empty. |
|DataDisk.N.Part.N.SizeBytes|Long|No|254803968|The size of partition N on the destination data disk. Unit: bytes. The default value is equal to the partition size of the source data disk.

**Note:**

-   The total size of all partitions in a destination data disk cannot exceed the size of the destination data disk.
-   You must specify both the `DataDisk.N.Part.N.Device` and DataDisk.N.Part.N.SizeBytes parameters or leave both parameters empty. |
|DataDisk.N.Part.N.Block|Boolean|No|true|Specifies whether to enable block replication for partition N in a destination data disk. Valid values:

-   true
-   false

Default value: true. |
|Tag.N.Key|String|No|TestKey|The key of a tag for the migration task. Valid values of N: 1 to 20.

This parameter cannot be an empty string. The key can be up to 128 characters in length, and cannot start with `aliyun`, `acs:`, `http://`, or `https://`. |
|Tag.N.Value|String|No|TestValue|The value of a tag for the migration task. Valid values of N: 1 to 20.

You can enter an empty string as the parameter value. The key can be up to 128 characters in length, and cannot start with `aliyun`, `acs:`, `http://`, or `https://`. |
|VpcId|String|No|vpc-bp1vwnn14rqpyiczj\*\*\*\*|The ID of the VPC for which you have configured Express Connect or VPN Gateway. |
|VSwitchId|String|No|vsw-bp1ddbrxdlrcbim46\*\*\*\*|The ID of the VSwitch in the specified VPC.

This parameter is required if you use a VPC to migrate data. |
|ReplicationParameters|String|No|\{"bandwidth\_limit":0,"compress\_level":1,"checksum":true\}|A string of key-value pairs that are used to configure the replication driver. The parameters must be specified as key-value pairs in the JSON format. The keys are fixed for each type of replication driver. The JSON string can be up to 2,048 characters in length.

A replication driver is a tool that is used to migrate a source server to an intermediate instance. The parameters vary based on the replication driver type. If you use an SMT driver, you can set the following parameters:

-   bandwidth\_limit: the maximum bandwidth for data transmission.
-   compress\_level: the compression ratio of data to be transmitted.
-   checksum: specifies whether to enable checksum verification.

For more information about replication drivers, see the response parameter [ReplicationDriver](~~121818~~) in the `DescribeSourceServers` operation. |
|NetMode|Integer|No|0|The network mode for data transmission. Valid values:

-   0: Data is transmitted over the Internet. Make sure that the source server can access the Internet.
-   2: Data is transmitted over a VPC. You must specify the VSwitchId parameter. You can call an API operation to query the value of the VpcId parameter based on the VSwitchId parameter. Therefore, you do not need to specify the VpcId parameter.

Default value: 0. |
|RunOnce|Boolean|No|true|Specifies whether to disable incremental migration for the source server. Default value: true. Valid values:

-   true: disables incremental migration. Incremental data of the source server is not synchronized.
-   false: enables incremental migration. You must specify the `Frequency` parameter. SMC synchronizes incremental data of the source server to Alibaba Cloud at the specified frequency. SMC can synchronize incremental data from the source server to Alibaba Cloud without interrupting your business. SMC generates a full data image for the source server when the migration task is running.

**Note:** You can specify this parameter only when you create a migration task. The value cannot be modified after it is specified. |
|Frequency|Integer|No|12|The interval at which SMC synchronizes incremental data to Alibaba Cloud. Unit: hours. Valid values: 1 to 168.

This parameter is required if you set `RunOnce` to false.

By default, this parameter is unspecified. |
|MaxNumberOfImageToKeep|Integer|No|10|The maximum number of images that can be retained during incremental migration. Valid values: 1 to 10.

This parameter is required if you set `RunOnce` to false.

By default, this parameter is unspecified. |
|InstanceType|String|No|ecs.c6.large|The type of the intermediate instance.

You can call the [DescribeInstanceTypes](~~25620~~) operation to query ECS instance types.

-   If you specify this parameter, SMC creates an intermediate instance of the specified type. If the specified instance type is unavailable, you cannot create the migration task.
-   If you do not specify this parameter, SMC selects an available instance type in a specific order to create an intermediate instance. For more information, see [SMC FAQ](~~121707~~). |
|SystemDiskPart.N.Device|String|No|0\_1|The device ID of partition N on the destination system disk. The partitions in the destination system disk are arranged in the same sequential order as those in the corresponding source system disk.

**Note:** You must specify both the SystemDiskPart.N.Device and `SystemDiskPart.N.SizeBytes` parameters or leave both parameters empty. |
|SystemDiskPart.N.SizeBytes|Long|No|254803968|The size of partition N in the destination system disk. Unit: bytes. The default value is equal to the partition size of the source system disk.

**Note:**

-   The total size of all partitions in the destination system disk cannot exceed the size of the destination system disk.
-   You must specify both the `SystemDiskPart.N.Device` and SystemDiskPart.N.SizeBytes parameters or leave both parameters empty. |
|SystemDiskPart.N.Block|Boolean|No|true|Specifies whether to enable block replication for partition N in the destination system disk. Valid values:

-   true
-   false

Default value: true. |
|InstanceRamRole|String|No|SMCAdmin|The RAM role that is attached to the intermediate instance. |
|ContainerNamespace|String|No|testNamespace|The namespace of the destination Docker container image. For more information, see [Container Registry](~~60744~~). |
|ContainerRepository|String|No|testRepository|The repository that stores the destination Docker container image. For more information, see [Container Registry](~~60744~~). |
|ContainerTag|String|No|CentOS:v1|The tag of the destination Docker container image. For more information, see [Container Registry](~~60744~~). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|JobId|String|j-bp17bclvg344jlyt\*\*\*\*|The ID of the migration task. |
|RequestId|String|C8B26B44-0189-443E-9816-D951F59623A9|The ID of the request. |

## Examples

Sample requests

```
http(s)://smc.aliyuncs.com/? Action=CreateReplicationJob
&RegionId=cn-hangzhou
&SourceId=s-bp1e2fsl57knvuug****
&SystemDiskSize=80
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateReplicationJobResponse>
    <JobId>j-bp17bclvg344jlyt****</JobId>
    <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
</CreateReplicationJobResponse>
```

`JSON` format

```
{
    "JobId": "j-bp17bclvg344jlyt****",
    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|SourceServerState.Invalid|The specified source server status is invalid.|The error message returned because the operation is not supported while the source server is in the current status.|
|400|ReplicationJobDataDiskIndex.Invalid|The specified replication job contains data disk index not found in source server.|The error message returned because the specified migration task contains data disk indexes that are not found in the source server.|
|400|VSwitchIdVpcId.Mismatch|The specified VSwitchId and VpcId does not match.|The error message returned because the specified VSwitchId and VpcId do not match.|
|400|InvalidSecurityGroupId.IncorrectNetworkType|The network type of the specified security group does not support this action.|The error message returned because the operation is not supported by the network type of the security group.|
|400|InvalidSecurityGroupId.VPCMismatch|The specified security group and the specified virtual switch are not in the same VPC.|The error message returned because the specified security group and VSwitch are not connected to the same VPC.|
|400|QuotaExceeded.ReplicationJob|The maximum number of replication jobs is exceeded. Please submit a ticket to raise the quota.|The error message returned because the maximum number of migration tasks has been exceeded. Submit a ticket to raise the quota.|
|400|ReplicationJobName.Duplicate|The specified replication job name already exists.|The error message returned because the specified migration task name already exists. Modify the migration task name.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the error persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/smc).

