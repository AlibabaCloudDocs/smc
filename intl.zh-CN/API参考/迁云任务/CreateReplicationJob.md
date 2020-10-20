# CreateReplicationJob

调用CreateReplicationJob为迁移源创建一个迁移任务。

## 接口说明

-   您只能为在线（Available）状态的迁移源创建迁移任务。
-   每个迁移源仅能关联一个未完成状态的迁移任务。未完成状态包括Ready（未开始）、Running（运行中）、Stopped（已暂停）、Waiting（等待中）、InError（出错）和Expired（已过期）。
-   每个阿里云账号可创建100个迁移任务。
-   迁移目标类型为镜像时，需指定ImageName、SystemDiskSize、DataDisk参数。
-   使用VPC内网迁移时，VSwitchId参数为必填，VpcId参数为可选。
-   支持迁移源的迁移目标为Docker容器镜像，实现低成本容器化应用迁移。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=smc&api=CreateReplicationJob&type=RPC&version=2019-06-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateReplicationJob|系统规定参数。取值：CreateReplicationJob |
|RegionId|String|是|cn-hangzhou|迁移源要迁入的目标阿里云地域ID。

 例如，您需要迁移源服务器至上海，则相应的阿里云地域ID为`cn-shanghai`。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|SourceId|String|是|s-bp1e2fsl57knvuug\*\*\*\*|迁移源ID。 |
|SystemDiskSize|Integer|是|80|目标阿里云服务器ECS的系统盘大小，单位为GiB。取值范围：20~500

 **说明：** 该参数取值需要大于迁移源系统盘实际占用大小，例如，源系统盘大小为500 GiB，实际占用100 GiB，则该参数取值需大于100 GiB。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。您可以从客户端生成一个不超过64个ASCII字符的参数值，并将值赋予ClientToken，保证重试请求的幂等性。更多详情，请参见[如何保证幂等性](~~25693~~)。 |
|Name|String|否|testMigrationTaskName|迁移任务名。迁移任务的名称需满足以下要求：

 -   任务名称必须唯一。
-   长度为2~128个英文或中文字符，必须以大小字母或中文开头，不能以`http://`和`https://`开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。 |
|Description|String|否|This\_is\_a\_migration\_task|迁移任务描述。

 长度应为2~128个英文或中文字符，必须以大小字母或中文开头，不能以`http://`和`https://`开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。 |
|TargetType|String|否|Image|迁移任务交付的目标类型。取值范围：

 -   Image：迁移成功后，SMC为您的迁移源生成阿里云镜像。
-   ContainerImage：迁移成功后，SMC为您的迁移源生成Docker容器镜像。 |
|ScheduledStartTime|String|否|2019-06-04T13:35:00Z|迁移任务的执行时间。该参数值的设置需满足以下要求：

 -   遵循ISO8601标准，并需要使用UTC+0时间，格式为YYYY-MM-DDThh:mm:ssZ。例如，2018-01-01T12:00:00Z，表示北京时间2018年01月01日20点00分00秒。
-   该参数值必须晚于当前时间，并且需要设置在30天以内。

 **说明：** 如果该参数值为空，则SMC不会启动迁移任务，需要您调用[StartReplicationJob](~~121823~~)启动任务。 |
|ValidTime|String|否|2019-06-04T13:35:00Z|迁移任务的过期时间。取值范围：迁移任务创建时间+7天~迁移任务创建时间+90天

 -   过期时间须遵循ISO8601标准，并需要使用UTC+0时间，格式为YYYY-MM-DDThh:mm:ssZ。例如，2018-01-01T12:00:00Z，表示北京时间2018年01月01日20点00分00秒。
-   过期时间设置为空，表示任务无限期有效。
-   任务到期后会被标记为过期状态，保存7天，7天后系统会自动清理。

 默认值：迁移任务创建时间+30天（表示迁移任务的默认有效期为创建后30天）。 |
|ImageName|String|否|testAliCloudImageName|迁移任务交付的目标阿里云镜像名称。目标镜像的名称需满足以下要求：

 -   同一阿里云地域下，镜像名称必须唯一。
-   长度为2~128个英文或中文字符，必须以大小字母或中文开头，不能以`http://`和`https://`开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 **说明：** 迁移任务运行过程中，若当前地域已经存在相同名称的镜像，则系统默认给镜像名称添加迁移任务ID（JobId）作为后缀，如：ImageName\_j-2zexxxxxxxxxxxxx。 |
|InstanceId|String|否|i-bp1f1dvfto1sigz5\*\*\*\*|目标实例ID。 |
|DataDisk.N.Size|Integer|否|100|目标阿里云服务器ECS的数据盘大小，单位为GiB。取值范围：20~32768

 **说明：** 该参数取值需要大于迁移源数据盘实际占用大小。例如，源数据盘大小为500 GiB，实际占用100 GiB，则该参数取值需大于100 GiB。 |
|DataDisk.N.Index|Integer|否|1|目标阿里云服务器ECS的数据盘顺序。初始值为1。取值范围：1~16

 **说明：** 您只能为迁移源中存在的数据盘创建目标数据盘。 |
|DataDisk.N.Part.N.Device|String|否|0\_1|目标数据盘N分区N对应的分区设备标识。N的实际取值请参考迁移源的分区设备标识。

 **说明：** 当`DataDisk.N.Part.N.SizeBytes`不为空时，该参数也不能为空。 |
|DataDisk.N.Part.N.SizeBytes|Long|否|254803968|目标数据盘N分区N的大小。单位：Byte。默认为源数据盘分区大小。

 **说明：**

-   分区空间大小不能超过数据盘空间大小，并且在同一数据盘下所有分区空间大小之和不能超过数据盘空间大小。
-   当`DataDisk.N.Part.N.Device`不为空时，该参数也不能为空。 |
|DataDisk.N.Part.N.Block|Boolean|否|true|数据盘N分区N是否开启块复制。取值范围：

 -   true
-   false

 默认值：true |
|Tag.N.Key|String|否|TestKey|迁移任务的标签键。N的取值范围：1~20

 一旦传入该值，则不允许为空字符串。最多支持128个字符，不能以`aliyun`、`acs:`、`http://`或者`https://`开头。 |
|Tag.N.Value|String|否|TestValue|迁移任务的标签值。N的取值范围：1~20

 一旦传入该值，可以为空字符串。最多支持128个字符，不能以`aliyun`、`acs:`、`http://`或者`https://`开头。 |
|VpcId|String|否|vpc-bp1vwnn14rqpyiczj\*\*\*\*|已配置高速通道服务或者VPN网关的VPC ID。 |
|VSwitchId|String|否|vsw-bp1ddbrxdlrcbim46\*\*\*\*|指定VPC下的虚拟交换机ID。

 使用VPC内网迁移时，该参数为必填参数。 |
|ReplicationParameters|String|否|\{"bandwidth\_limit":0,"compress\_level":1,"checksum":true\}|复制驱动器的参数信息。参数信息为JSON格式键值对，键值固定。最大长度：2048个字符

 复制驱动器是指，复制源服务器数据到中转实例时所使用的工具。不同复制驱动器支持参数可能不同。复制驱动器SMT目前支持以下参数：

 -   bandwidth\_limit：传输速度带宽限制
-   compress\_level：传输压缩率
-   checksum：是否开启checksum校验

 复制驱动器的取值，请参见[DescribeSourceServers](~~121818~~)的返回参数`SourceServers.ReplicationDriver`。 |
|NetMode|Integer|否|0|数据传输网络模式。取值范围：

 -   0：表示公网传输模式。此时要求您的源服务器能够访问公网，迁云数据从公网传输。
-   2：表示内网传输模式，选用此模式必须设置VSwitchId参数（VpcId参数可以不设置，服务内部可以通过接口反查出来）。

 默认值：0 |
|RunOnce|Boolean|否|true|创建一次性迁移任务还是增量迁移任务。取值范围：

 -   true（默认值）：一次性迁移任务。任务创建后，仅执行一次。
-   false：增量迁移任务。任务创建后，按照您设置的`Frequency`参数值周期性自动执行。使用增量迁移任务，可在业务不暂停的情况下，同步源服务器的增量数据至阿里云，并为源服务器生成任务运行时刻的全量数据镜像。

 **说明：** 该参数值只能在创建迁移任务时指定。参数值一经指定，则无法更改。 |
|Frequency|Integer|否|12|增量迁移任务运行的时间间隔，单位：小时。取值范围：1~168

 `RunOnce`参数值为false时，该参数为必填参数。

 默认值：无 |
|MaxNumberOfImageToKeep|Integer|否|10|增量迁移任务默认保留的最大镜像数。取值范围：1~10

 `RunOnce`参数值为false时，该参数为必填参数。

 默认值：无 |
|InstanceType|String|否|ecs.c6.large|中转实例的实例规格。

 调用[DescribeInstanceTypes](~~25620~~)可查询云服务器ECS提供的实例规格。

 -   指定该参数后，系统会选择该实例规格创建中转实例。若该实例规格库存不足，则迁移任务创建失败。
-   不指定该参数时，系统默认会按照一定顺序选择实例规格来创建中转实例，详情请参见[SMC FAQ 中转实例规格有哪些](~~121707~~)。 |
|SystemDiskPart.N.Device|String|否|0\_1|目标系统盘分区N设备标识。N的实际取值请参考迁移源的分区设备标识。

 **说明：** 当`SystemDiskPart.N.SizeBytes`不为空时，该参数也不能为空。 |
|SystemDiskPart.N.SizeBytes|Long|否|254803968|系统盘分区N大小。单位：Byte。默认为源系统盘分区大小。

 **说明：**

-   分区空间大小不能超过系统盘空间大小，并且在系统盘下所有分区空间大小之和不能超过系统盘空间大小。
-   当`SystemDiskPart.N.Device`不为空时，该参数也不能为空。 |
|SystemDiskPart.N.Block|Boolean|否|true|系统盘分区N是否开启块复制。取值范围：

 -   true
-   false

 默认值：true |
|InstanceRamRole|String|否|SMCAdmin|实例RAM角色名称。 |
|ContainerNamespace|String|否|testNamespace|Docker的命名空间。关于Docker容器镜像详情请参见[容器镜像服务](~~60744~~)。 |
|ContainerRepository|String|否|testRepository|Docker的镜像仓库。关于Docker容器镜像详情请参见[容器镜像服务](~~60744~~)。 |
|ContainerTag|String|否|CentOS:v1|Docker的镜像标签。关于Docker容器镜像详情请参见[容器镜像服务](~~60744~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|JobId|String|j-bp17bclvg344jlyt\*\*\*\*|迁移任务ID。 |
|RequestId|String|C8B26B44-0189-443E-9816-D951F59623A9|请求ID。 |

## 示例

请求示例

```
http(s)://smc.aliyuncs.com/?Action=CreateReplicationJob
&RegionId=cn-hangzhou
&SourceId=s-bp1e2fsl57knvuug****
&SystemDiskSize=80
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateReplicationJobResponse>
    <JobId>j-bp17bclvg344jlyt****</JobId>
    <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
</CreateReplicationJobResponse>
```

`JSON` 格式

```
{
    "JobId": "j-bp17bclvg344jlyt****",
    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|SourceServerState.Invalid|The specified source server status is invalid.|无效的迁移源状态。|
|400|ReplicationJobDataDiskIndex.Invalid|The specified replication job contains data disk index not found in source server.|迁移任务包含的数据盘索引在迁移源中不存在。|
|400|VSwitchIdVpcId.Mismatch|The specified VSwitchId and VpcId does not match.|指定的VSwitchId和VpcId不匹配。|
|400|InvalidSecurityGroupId.IncorrectNetworkType|The network type of the specified security group does not support this action.|安全组网络类型不支持该操作，请检查安全组网络类型。|
|400|InvalidSecurityGroupId.VPCMismatch|The specified security group and the specified virtual switch are not in the same VPC.|指定的安全组和交换机不在一个专有网络。|
|400|QuotaExceeded.ReplicationJob|The maximum number of replication jobs is exceeded. Please submit a ticket to raise the quota.|迁移任务的数量已超过最大允许值，请提交工单。|
|400|ReplicationJobName.Duplicate|The specified replication job name already exists.|迁移任务名称已存在，请修改迁移任务名称。|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|内部错误，请重试。如果多次尝试失败，请提交工单。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/smc)查看更多错误码。

