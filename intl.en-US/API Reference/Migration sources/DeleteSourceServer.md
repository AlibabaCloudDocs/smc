# DeleteSourceServer {#doc_api_smc_DeleteSourceServer .reference}

You can call this operation to delete a migration source.

## Description {#description .section}

-   If the migration source is in use by a running migration task, it cannot be deleted.
-   If the migration source is in use by a migration task that is not in the running state, you must set `Force=true` to delete the migration source.

## Debugging {#apiExplorer .section}

Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/#product=smc&api=DeleteSourceServer) to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|SourceId|String|Yes|s-xxxxxxxxxxxxxxx| The ID of the migration source to be deleted.

 |
|Action|String|No|DeleteSourceServer| The operation that you want to perform. Set this parameter to DeleteSourceServer.

 |
|Force|Boolean|No|true| Specifies whether to forcibly delete the migration source.

 -   true: specifies to forcibly delete the migration source, the corresponding migration task, and the intermediate resources of the task.
-   false: specifies to not delete the migration source if it is in use by a migration task.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}
http(s)://smc.aliyuncs.com/? Action=DeleteSourceServer
&SourceId=s-xxxxxxxxxxxxxxx
&<Common request parameters>
```

Sample success response

`XML` format

``` {#xml_return_success_demo}
<DeleteSourceServerResponse>
  <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DeleteSourceServerResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#section_k9y_xyt_45o .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|SourceServerState.Invalid|The specified source server status is invalid.|The error message returned because the operation is not supported while the migration source is in the current state.|
|400|SourceServer.WithRunningReplicationJob|The specified source server has related replication jobs that are running.|The error message returned because the migration source is in use by a running migration task.|
|400|ReplicationJob.Related|The specified source server has related replication jobs.|The error message returned because the migration source is in use by a migration task.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

[View error codes](https://error-center.aliyun.com/status/product/smc)

