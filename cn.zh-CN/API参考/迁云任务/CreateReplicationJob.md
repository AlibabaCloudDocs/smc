# CreateReplicationJob {#doc_api_smc_CreateReplicationJob .reference}

为迁移源创建一个迁移任务。

## 接口说明 {#description .section}

-   您只能为在线（Available）状态的迁移源创建迁移任务。
-   每个迁移源仅能关联一个未完成状态的迁移任务。未完成状态包括Ready（未开始）、Running（运行中）、Stopped（已暂停）、InError（出错）和Expired（已过期）。
-   每个阿里云账号可创建100个迁移任务。
-   迁移目标类型为镜像时，需指定Imagename、SystemDiskSize、DataDisk参数。
-   使用VPC内网迁移时，VSwitchId参数为必填，VpcId参数为可选。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=smc&api=CreateReplicationJob)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RegionId|String|是|cn-hangzhou|迁移源要迁入的目标阿里云地域ID。

 例如，您需要迁移源服务器至上海，则相应的阿里云地域ID为`cn-shanghai`。您可以调用[DescribeRegions](25609)查看最新的阿里云地域列表。

 |
|SourceId|String|是|s-xxxxxxxxxxxxxxx|迁移源ID。

 |
|SystemDiskSize|Integer|是|80|目标阿里云服务器ECS的系统盘大小。单位为GiB。取值范围：20~500

 **说明：** 该参数取值需要大于迁移源系统盘实际占用大小，例如，源系统盘大小为500 GiB，实际占用100 GiB，则该参数取值需大于100 GiB。

 |
|Action|String|否|CreateReplicationJob|系统规定参数。取值：CreateReplicationJob

 |
|ClientToken|String|否|xxxxxxxxxx|幂等token，防止重复创建。

 |
|DataDisk.N.Index|Integer|否|1|目标阿里云服务器ECS的数据盘顺序。取值范围：1~16。初始值为1。

 **说明：** 您只能为迁移源中存在的数据盘创建目标数据盘。

 |
|DataDisk.N.Size|Integer|否|100|目标阿里云服务器ECS的数据盘大小。单位为GiB。取值范围：20~32768

 **说明：** 该参数取值需要大于迁移源数据盘实际占用大小。例如，源数据盘大小为500 GiB，实际占用100 GiB，则该参数取值需大于100 GiB。

 |
|Description|String|否|This\_is\_a\_migration\_task|迁移任务描述。迁移任务描述的长度应为 2~128 个英文或中文字符，必须以大小字母或中文开头，不能以 http:// 和 https:// 开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 |
|ImageName|String|否|MyAliCloudImage|迁移任务交付的目标阿里云镜像名称。目标镜像的名称需满足以下要求：

 -   同一阿里云地域下，镜像名称必须唯一。
-   长度为 2~128 个英文或中文字符，必须以大小字母或中文开头，不能以 http:// 和 https:// 开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 **说明：** 迁移任务运行过程中，若当前地域已经存在相同名称的镜像，则默认在镜像名称中添加迁移任务ID（JobId）作为后缀，如：ImageName-JobId。

 |
|InstanceId|String|否|i-xxxxxxxxxxxxx|目标实例ID。

 |
|Name|String|否|MigrationTask|迁移任务名。迁移任务的名称需满足以下要求：

 -   任务名称必须唯一。
-   长度为 2~128 个英文或中文字符，必须以大小字母或中文开头，不能以 http:// 和 https:// 开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 |
|NetMode|Integer|否|0|数据传输网络模式，取值范围：

 -   0 表示公网传输模式。此时要求您的源服务器能够访问公网，迁云数据从公网传输。
-   2 表示内网传输模式，选用此模式必须设置VSwitchId参数（VpcId参数可以不设置，服务内部可以通过接口反查出来）。

 默认值：0。

 |
|ReplicationParameters|String|否|BandWidthLimit:0|复制驱动器参数信息。最大长度为2048个字符。

 键值对Json格式可扩展，固定键值。不同驱动器（参见SourceServer.ReplicationDriver）支持参数可能不一致，如SMT支持参数：

 -   BandwidthLimit 传输速度带宽限制
-   CompressLevel 传输压缩率
-   Checksum 是否开启checksum校验
-   UseSSHTunnel 是否开启SSH加密通道EfficiencyLevel 高效传输等级

 |
|ScheduledStartTime|String|否|2019-06-04T13:35:00Z|迁移任务的执行时间。该参数值的设置需满足以下要求：

 -   遵循ISO8601标准，并需要使用UTC时间，格式为YYYY-MM-DDThh:mm:ssZ。示例：2018-01-01T12:00:00Z表示北京时间2018年01月01日20点00分00秒。
-   该参数值必须晚于当前时间，并且需要设置在30天以内。

 **说明：** 如果该参数值为空，则SMC不会启动迁移任务，需要您调用[StartReplicationJob](~~121823~~)启动任务。

 |
|TargetType|String|否|image|迁移任务交付的目标类型。取值范围：镜像。表示迁移成功后，SMC为您的迁移源生成阿里云镜像。您可使用该镜像创建ECS实例达到迁移至阿里云的目的。

 |
|VSwitchId|String|否|xxxxxxxxxxxxxx|指定VPC下的虚拟交换机ID。

 |
|ValidTime|String|否|2019-06-04T13:35:00Z|迁移任务的过期时间。取值范围：迁移任务创建时间+7天~迁移任务创建时间+90天

 -   过期时间须遵循ISO8601标准，并需要使用UTC时间，格式为YYYY-MM-DDThh:mm:ssZ。示例：2018-01-01T12:00:00Z，表示北京时间2018年01月01日20点00分00秒。
-   过期时间设置为空，表示任务无限期有效。
-   任务到期后会被标记为过期状态，保存7天，7天后系统会自动清理。

 默认值：迁移任务创建时间+30天。表示迁移任务的默认有效期为创建后30天。

 |
|VpcId|String|否|xxxxxxxxxxxxxx|已配置高速通道服务或者VPN网关的VPC ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|JobId|String|j-xxxxxxxxxxxxxxx|迁移任务ID。

 |
|RequestId|String|C8B26B44-0189-443E-9816-D951F59623A9|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://smc.aliyuncs.com/?Action=CreateReplicationJob
&RegionId=cn-hangzhou
&SourceId=s-xxxxxxxxxxxxxxx
&SystemDiskSize=80
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateReplicationJobResponse>
  <JobId>j-2xxxxxxxxxxxq</JobId>
  <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
</CreateReplicationJobResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"C8B26B44-0189-443E-9816-D951F59623A9",
	"JobId":"j-2xxxxxxxxxxq"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|SourceServerState.Invalid|The specified source server status is invalid.|无效的迁移源状态|
|400|ReplicationJobDataDiskIndex.Invalid|The specified replication job contains data disk index not found in source server.|迁移任务包含的数据盘索引在迁移源中不存在|
|400|VSwitchIdVpcId.Mismatch|The specified VSwitchId and VpcId does not match.|指定的VSwitchId和VpcId不匹配|
|400|InvalidSecurityGroupId.IncorrectNetworkType|The network type of the specified security group does not support this action.|安全组网络类型不支持该操作，请检查安全组网络类型|
|400|InvalidSecurityGroupId.VPCMismatch|The specified security group and the specified virtual switch are not in the same VPC.|指定的安全组和交换机不在一个专有网络|
|400|QuotaExceeded.ReplicationJob|The maximum number of replication jobs is exceeded. Please submit a ticket to raise the quota.|迁移任务的数量已超过最大允许值，请提交工单|
|400|ReplicationJobName.Duplicate|The specified replication job name already exists.|迁移任务名称已存在，请修改迁移任务名称|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|内部错误，请重试。如果多次尝试失败，请提交工单|

[查看本产品错误码](https://error-center.aliyun.com/status/product/smc)

