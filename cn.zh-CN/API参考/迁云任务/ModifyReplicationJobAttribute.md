# ModifyReplicationJobAttribute

调用ModifyReplicationJobAttribute修改迁移任务信息。

## 接口说明

修改迁移任务之前，请阅读以下注意事项：

-   参数`Name`和`Description`在迁移任务的整个生命周期内均可以修改。
-   参数`Frequency`和`MaxNumberOfImageToKeep`只能在迁移任务执行前或任务状态为`等待中`时修改。
-   其他参数只能在迁移任务执行前修改。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=smc&api=ModifyReplicationJobAttribute&type=RPC&version=2019-06-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyReplicationJobAttribute|系统规定参数。取值：ModifyReplicationJobAttribute |
|JobId|String|是|j-bp19vlwm0tyigbmj\*\*\*\*|迁移任务ID。 |
|Name|String|否|testMigrationTaskName|迁移任务名称。迁移任务的名称需满足以下要求：

 -   任务名称必须唯一。
-   长度为2~128个英文或中文字符，必须以大小字母或中文开头，不能以`http://`和`https://`开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。 |
|Description|String|否|This\_is\_my\_migration\_task|迁移任务描述。

 长度应为2~128个英文或中文字符，必须以大小字母或中文开头，不能以`http://`和`https://`开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。 |
|TargetType|String|否|Image|迁移交付的目标类型。仅支持在迁移任务启动前修改。取值范围：

 -   Image：迁云成功后，SMC为您的源服务器生成阿里云镜像，您可使用该镜像创建ECS实例达到迁移至阿里云的目的。
-   ContainerImage：迁云成功后，SMC为您的源服务器生成容器镜像，您可以在容器镜像服务中使用该镜像。

 **说明：**

-   该参数的取值不区分大小写。
-   仅支持修改Linux系统迁移源的迁移交付目标类型。Windows操作系统暂不支持迁移至容器镜像，因此当迁移源为Windows操作系统时，该参数的取值只能为`Image`。 |
|ScheduledStartTime|String|否|2019-06-04T13:35:00Z|设置迁移任务的执行时间。SMC在指定时间自动为您启动迁移任务。

 执行时间遵循ISO8601标准，并需要使用UTC时间，格式为YYYY-MM-DDThh:mm:ssZ。例如，2018-01-01T12:00:00Z，表示北京时间2018年01月01日20点00分00秒。

 **说明：** 当执行时间为空时，SMC不自动启动迁移任务，您需要调用[StartReplicationJob](~~121823~~)启动。 |
|ImageName|String|否|testAliCloudImageName|迁移任务交付的目标镜像名称。目标镜像的名称需满足以下要求：

 -   同一阿里云地域下，镜像名称必须唯一。
-   长度为2~128个英文或中文字符，必须以大小字母或中文开头，不能以`http://`和`https://`开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 **说明：** 如果迁移任务运行过程中，当前地域已经存在相同名称的镜像，则系统默认在镜像名称后面添加迁移任务ID（JobId）作为后缀，如：ImageName-JobId。 |
|InstanceId|String|否|i-bp1f1dvfto1sigz5\*\*\*\*|目标实例ID。 |
|SystemDiskSize|Integer|否|50|目标阿里云服务器ECS的系统盘大小，单位：GiB。取值范围：20~500

 **说明：** 参数取值需要大于源服务器系统盘实际占用大小，例如，源系统盘大小为500 GiB，实际占用100 GiB，则该参数取值需大于100 GiB。 |
|SystemDiskPart.N.Device|String|否|0\_1|目标系统盘分区N设备标识。

 **说明：** N的实际取值请参考迁移源的分区设备标识。 |
|SystemDiskPart.N.SizeBytes|Long|否|254803968|目标系统盘分区N大小。单位：Byte。默认为源系统盘分区大小。

 **说明：** 分区空间大小不能超过系统盘空间大小，并且在系统盘下所有分区空间大小之和不能超过系统盘空间大小。 |
|SystemDiskPart.N.Block|Boolean|否|true|目标系统盘分区N是否开启块复制。取值范围：

 -   true
-   false |
|DataDisk.N.Size|Integer|否|100|目标阿里云服务器ECS的数据盘大小，单位：GiB。取值范围：20~32768

 **说明：** 参数取值需要大于源服务器数据盘实际占用大小。例如，源数据盘大小为500 GiB，实际占用100 GiB，则该参数取值需大于100 GiB。 |
|DataDisk.N.Index|Integer|否|1|目标阿里云服务器ECS的数据盘顺序。取值范围：1~16

 初始值：1

 **说明：** 您只能为源服务器中存在的数据盘创建目标数据盘。 |
|DataDisk.N.Part.N.Device|String|否|0\_1|目标数据盘N分区N对应的分区设备标识。

 **说明：** N的实际取值请参考迁移源的分区设备标识。 |
|DataDisk.N.Part.N.SizeBytes|Long|否|254803968|目标数据盘N分区N的大小。单位：Byte。默认为源数据盘分区大小。

 **说明：** 分区空间大小不能超过数据盘空间大小，并且在同一数据盘下所有分区空间大小之和不能超过数据盘空间大小。 |
|DataDisk.N.Part.N.Block|Boolean|否|true|目标数据盘N分区N是否开启块复制。取值范围：

 -   true
-   false |
|Frequency|Integer|否|10|增量迁移任务运行的时间间隔，单位：小时。取值范围：1~168

 `RunOnce`参数值为false时，该参数为必填参数。 |
|MaxNumberOfImageToKeep|Integer|否|5|增量迁移任务默认保留的最大镜像数。取值范围：1~10

 `RunOnce`参数值为false时，该参数为必填参数。 |
|InstanceType|String|否|ecs.c5.large|中转实例的实例规格。

 调用[DescribeInstanceTypes](~~25620~~)可查询云服务器ECS提供的实例规格。

 -   指定该参数后，系统会选择该实例规格创建中转实例。若该实例规格库存不足，则迁移任务创建失败。
-   不指定该参数时，系统会默认按照一定顺序选择实例规格来创建中转实例，详情请参见[SMC FAQ 中转实例规格有哪些](~~121707~~)。 |
|InstanceRamRole|String|否|SMCAdmin|实例RAM角色名称。 |
|ContainerNamespace|String|否|testNamespace|Docker的命名空间。关于Docker容器镜像详情请参见[容器镜像服务](~~60744~~)。 |
|ContainerRepository|String|否|testRepository|Docker的镜像仓库。关于Docker容器镜像详情请参见[容器镜像服务](~~60744~~)。 |
|ContainerTag|String|否|CentOS:v1|Docker的镜像标签。关于Docker容器镜像详情请参见[容器镜像服务](~~60744~~)。 |
|ValidTime|String|否|2019-06-04T13:35:00Z|迁移任务的过期时间。取值范围：迁移任务创建时间+7天~迁移任务创建时间+90天

 -   过期时间只允许迁移任务在Ready（未开始）、Running（运行中）、Stopped（已暂停）、InError（出错）或Waiting（等待中）状态下修改。
-   过期时间须遵循ISO8601标准，并需要使用UTC+0时间，格式为`YYYY-MM-DDThh:mm:ssZ`。例如，2018-01-01T12:00:00Z，表示北京时间2018年01月01日20点00分00秒。
-   过期时间设置为空，表示任务无限期有效。
-   任务到期后会被标记为过期状态，保存7天，7天后系统会自动清理。

 默认值：迁移任务创建时间+30天（表示迁移任务的默认有效期为创建后30天）。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|1C488B66-B819-4D14-8711-C4EAAA13AC01|请求ID。 |

## 示例

请求示例

```
http(s)://smc.aliyuncs.com/?Action=ModifyReplicationJobAttribute
&JobId=j-bp19vlwm0tyigbmj****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteReplicationJobResponse>
    <RequestId>1C488B66-B819-4D14-8711-C4EAAA13AC01</RequestId>
</DeleteReplicationJobResponse>
```

`JSON` 格式

```
{
	"RequestId":"1C488B66-B819-4D14-8711-C4EAAA13AC01"	
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|DataDisk.DuplicateIndex|The source server data disk cannot contain the same index.|迁移源数据盘包含相同的索引，请检查磁盘索引是否重复。|
|400|ReplicationJob.InvalidStatus|The specified replication job status is invalid.|无效的迁移任务状态。|
|400|ReplicationJobDataDiskIndex.Invalid|The specified replication job contains data disk index not found in source server.|迁移任务包含的数据盘索引在迁移源中不存在。|
|400|ReplicationJobName.Duplicate|The specified replication job name already exists.|迁移任务名称已存在，请修改迁移任务名称。|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|内部错误，请重试。如果多次尝试失败，请提交工单。|

访问[错误中心](https://error-center.aliyun.com/status/product/smc)查看更多错误码。

