# DeleteSourceServer

Deletes a migration source.

## Description

-   If the migration source is being used by a running migration task, it cannot be deleted.
-   If the migration source is being used by a migration task that is not in the running state, you must set the `Force` parameter to true before you can delete the migration source.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=DeleteSourceServer&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteSourceServer|The operation that you want to perform. Set this parameter to DeleteSourceServer. |
|SourceId|String|Yes|s-bp17m1vi6x20c6g6\*\*\*\*|The ID of the migration source. |
|Force|Boolean|No|true|Specifies whether to forcibly delete the migration source.

 -   true: specifies to forcibly delete the migration source, the corresponding migration task, and the intermediate resources of the task.
-   false: specifies to not delete the migration source if it is being used by a migration task. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
http(s)://smc.aliyuncs.com/? Action=DeleteSourceServer
&SourceId=s-bp17m1vi6x20c6g6****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteReplicationJobResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DeleteReplicationJobResponse>
```

`JSON` format

```
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"	
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|SourceServerState.Invalid|The specified source server status is invalid.|The error message returned because the operation is not supported while the source server is in the current status.|
|400|SourceServer.WithRunningReplicationJob|The specified source server has related replication jobs that are running.|The error message returned because the migration source is being used by a running migration task.|
|400|ReplicationJob.Related|The specified source server has related replication jobs.|The error message returned because the migration source is being used by a migration task.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the error persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/smc).

