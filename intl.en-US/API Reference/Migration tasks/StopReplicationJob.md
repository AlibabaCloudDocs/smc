# StopReplicationJob

Starts a migration task.

## Description

This operation can be used to stop only migration tasks that are in the Running and Syncing states.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=StopReplicationJob&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|StopReplicationJob|The operation that you want to perform. Set this parameter to StopReplicationJob. |
|JobId|String|Yes|j-bw526m1vi6x21qh\*\*\*\*|The ID of the migration task. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
http(s)://smc.aliyuncs.com/? Action=StopReplicationJob
&JobId=j-bw526m1vi6x21qh****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<StopReplicationJobResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</StopReplicationJobResponse>
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
|400|ReplicationJob.InvalidStatus|The specified replication job status is invalid.|The error message returned because the operation is not supported while the migration task is in the current status.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the error persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/smc).

