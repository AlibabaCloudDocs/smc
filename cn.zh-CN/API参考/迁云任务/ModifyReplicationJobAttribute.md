# ModifyReplicationJobAttribute {#doc_api_smc_ModifyReplicationJobAttribute .reference}

修改迁移任务信息。

## 接口说明 {#description .section}

您只能在迁移任务启动前，修改该任务信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=smc&api=ModifyReplicationJobAttribute&type=RPC&version=2019-06-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|JobId|String|是|j-xxxxxxxxxxx|迁移任务ID。

 |
|Action|String|否|ModifyReplicationJobAttribute|系统规定参数。取值：ModifyReplicationJobAttribute

 |
|DataDisk.N.Index|Integer|否|1|目标阿里云服务器ECS的数据盘顺序。取值范围：1~16

 初始值：1

 **说明：** 您只能为源服务器中存在的数据盘创建目标数据盘。

 |
|DataDisk.N.Size|Integer|否|100|目标阿里云服务器ECS的数据盘大小。单位为GiB。取值范围：20~32768

 **说明：** 该参数取值需要大于您源服务器数据盘实际占用大小。例如，源数据盘大小为500 GiB，实际占用100 GiB，则该参数取值需大于100 GiB。

 |
|Description|String|否|This\_is\_my\_migration\_task|迁移任务描述。迁移任务描述的长度应为 2~128 个英文或中文字符，必须以大小字母或中文开头，不能以 http:// 和 https:// 开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 |
|ImageName|String|否|MyAliCloudImage|迁移任务交付的目标镜像名称。目标镜像的名称需满足以下要求：

 -   同一阿里云地域下，镜像名称必须唯一。
-   长度为 2~128 个英文或中文字符，必须以大小字母或中文开头，不能以 http:// 和 https:// 开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 **说明：** 如果迁移任务运行过程中，当前地域已经存在当前名称的镜像，镜像名称默认添加迁移任务ID（JobId）作为后缀，如：ImageName-JobId。

 |
|InstanceId|String|否|i-xxxxxxxxxxxx|目标实例ID。

 |
|Name|String|否|MyMigrationTask|迁移任务名称。迁移任务的名称需满足以下要求：

 -   任务名称必须唯一。
-   长度为 2~128 个英文或中文字符，必须以大小字母或中文开头，不能以 http:// 和 https:// 开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 |
|ScheduledStartTime|String|否|2019-06-04T13:35:00Z|设置迁移任务的执行时间。SMC在指定时间自动为您启动迁移任务。执行时间遵循ISO8601标准，并需要使用UTC时间，格式为 YYYY-MM-DDThh:mm:ssZ。示例：2018-01-01T12:00:00Z 表示北京时间2018年01月01日20点00分00秒。

 **说明：** 当执行时间为空时，SMC不自动启动迁移任务，您需要调用[StartReplicationJob](~~121823~~)启动。

 |
|SystemDiskSize|Integer|否|50|目标阿里云服务器ECS的系统盘大小。单位为GiB。取值范围：20~500

 **说明：** 该参数取值需要大于您源服务器系统盘实际占用大小，例如，源系统盘大小为500 GiB，实际占用100 GiB，则该参数取值需大于100 GiB。

 |
|TargetType|String|否|image|迁移交付的目标类型。取值范围：image。

 **说明：** 迁云成功后，SMC为您的源服务器生成阿里云镜像，您可使用该镜像创建ECS实例达到迁移至阿里云的目的。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|1C488B66-B819-4D14-8711-C4EAAA13AC01|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
http(s)://smc.aliyuncs.com/?Action=ModifyReplicationJobAttribute
&JobId=j-xxxxxxxxxxx
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteReplicationJobResponse>
    <RequestId>1C488B66-B819-4D14-8711-C4EAAA13AC01</RequestId>
</DeleteReplicationJobResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"1C488B66-B819-4D14-8711-C4EAAA13AC01"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/smc)查看更多错误码。

