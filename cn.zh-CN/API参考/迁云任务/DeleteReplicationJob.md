# DeleteReplicationJob {#doc_api_smc_DeleteReplicationJob .reference}

删除一个迁移任务。

## 接口说明 {#description .section}

-   迁移任务删除后不可恢复。
-   迁移任务删除后自动释放已创建的相关资源，如中转实例等。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=smc&api=DeleteReplicationJob)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|JobId|String|是|j-xxxxxxxxxx|迁移任务Id。

 |
|Action|String|否|DeleteReplicationJob|系统规定参数。取值：DeleteReplicationJob。

 |

## 返回参数 {#resultMapping .section}

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

[查看本产品错误码](https://error-center.aliyun.com/status/product/smc)

