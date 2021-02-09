# CutOverReplicationJob

Stops and completes an incremental migration task that is periodically performed.

## Description

-   The incremental migration task must be in the Waiting state.
-   If you call this operation, the incremental migration task is no longer periodically performed. Instead, Server Migration Center \(SMC\) determines whether to implement the incremental migration task based on the value of the `SyncData` parameter. If the SyncData parameter is set to `false`, SMC releases intermediate resources and completes the migration task without migrating data. If the SyncData parameter is set to `true`, SMC migrates all data, releases intermediate resources, and completes the migration task.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=CutOverReplicationJob&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CutOverReplicationJob|The operation that you want to perform. Set the value to CutOverReplicationJob. |
|JobId|String|Yes|j-bp1fnx5y3djc4cop\*\*\*\*|The ID of the incremental migration task. |
|SyncData|Boolean|No|false|Specifies whether to migrate all data for the last time.

 Default value: false. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
https://smc.aliyuncs.com/?Action=CutOverReplicationJob
&JobId=j-bp1fnx5y3djc4cop****
&SyncData=false
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CutOverReplicationJobResponse>
      <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</CutOverReplicationJobResponse>
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
|400|ReplicationJob.InvalidStatus|The specified replication job status is invalid.|The error message returned because the operation is not supported when the migration task is in the current state.|
|400|SourceServerState.Invalid|The specified source server status is invalid.|The error message returned because the operation is not supported when the source server is in the current state.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/smc).

