# DeleteReplicationJob {#doc_api_smc_DeleteReplicationJob .reference}

You can call this operation to delete a migration task.

## Description {#description .section}

-   Deleted migration tasks cannot be restored.
-   After a migration task is deleted, associated resources such as intermediate instances are automatically released.

## Debugging {#apiExplorer .section}

Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/#product=smc&api=DeleteReplicationJob) to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|JobId|String|Yes|j-xxxxxxxxxx| The ID of the migration task to be deleted.

 |
|Action|String|No|DeleteReplicationJob| The operation that you want to perform. Set this parameter to DeleteReplicationJob.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}
http(s)://smc.aliyuncs.com/?Action=DeleteReplicationJob
&JobId=j-xxxxxxxxxx
&<Common request parameters>
```

Sample success response

`XML` format

``` {#xml_return_success_demo}
<DeleteReplicationJobResponse>
  <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DeleteReplicationJobResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#section_5zj_1up_cfi .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|ReplicationJob.InvalidStatus|The specified replication job status is invalid.|The error message returned because the operation is not supported while the migration task is in the current state.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

[View error codes](https://error-center.aliyun.com/status/product/smc)

