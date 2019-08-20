# StartReplicationJob {#doc_api_smc_StartReplicationJob .reference}

You can call this operation to start a migration task.

## Description {#description .section}

This operation can only be used to start migration tasks that are in the **Ready**, **Stopped**, or **InError** state.

## Debugging {#apiExplorer .section}

Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/#product=smc&api=StartReplicationJob) to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|JobId|String|Yes|j-xxxxxxxxxxxxxx| The ID of the migration task to be started.

 |
|Action|String|No|StartReplicationJob| The operation that you want to perform. Set this parameter to StartReplicationJob.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}
http(s)://smc.aliyuncs.com/?Action=StartReplicationJob
&JobId=j-xxxxxxxxxxxxxx
&<Common request parameters>
```

Sample success response

`XML` format

``` {#xml_return_success_demo}
<StartReplicationJobResponse>
  <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</StartReplicationJobResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#section_2i0_h8k_emy .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|ReplicationJob.InvalidStatus|The specified replication job status is invalid.|The error message returned because the operation is not supported while the migration task is in the current state.|
|400|SourceServerState.Invalid|The specified source server status is invalid.|The error message returned because the operation is not supported while the migration source is in the current state.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

[View error codes](https://error-center.aliyun.com/status/product/smc)

