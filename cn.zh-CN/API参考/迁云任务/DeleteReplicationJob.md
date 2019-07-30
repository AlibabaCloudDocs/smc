# DeleteReplicationJob {#doc_api_smc_DeleteReplicationJob .reference}

删除一个迁移任务。

## 接口说明 {#description .section}

-   迁移任务删除后不可恢复。
-   迁移任务删除后自动释放已创建的相关资源，如中转实例等。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=smc&api=DeleteReplicationJob&type=RPC&version=2019-06-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|JobId|String|是|j-xxxxxxxxxx|迁移任务Id。

 |
|Action|String|否|DeleteReplicationJob|系统规定参数。取值：DeleteReplicationJob

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求 ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
http(s)://smc.aliyuncs.com/?Action=DeleteReplicationJob
&JobId=j-xxxxxxxxxx
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteReplicationJobResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DeleteReplicationJobResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ReplicationJob.InvalidStatus|The specified replication job status is invalid.|无效的迁移任务状态|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|内部错误，请重试。如果多次尝试失败，请提交工单|

访问[错误中心](https://error-center.aliyun.com/status/product/smc)查看更多错误码。

