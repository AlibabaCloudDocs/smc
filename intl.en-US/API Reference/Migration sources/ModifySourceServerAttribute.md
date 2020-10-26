# ModifySourceServerAttribute

Modifies the name and description of a migration source.

## Description

This operation can be called regardless of the status of the migration source.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=ModifySourceServerAttribute&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifySourceServerAttribute|The operation that you want to perform. Set this parameter to ModifySourceServerAttribute. |
|SourceId|String|Yes|s-bp17m1vi6x20c6g6\*\*\*\*|The ID of a source server. |
|Name|String|No|testSourceServerName|The name of the migration source. The name must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscore \(\_\), and hyphens \(-\). The name must start with a letter and cannot start with http:// or https://.

 Default value: null. |
|Description|String|No|This is a source server.|The description of the migration source. The parameter value must meet the following requirements:

 -   It can be up to 256 characters in length.
-   It cannot start with http:// or https://.
-   If this parameter is not specified, it is an empty string by default.

 Default value: null. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. |

## Examples

Sample requests

```
http(s)://smc.aliyuncs.com/? Action=ModifySourceServerAttribute
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
|400|SourceServerName.Duplicate|The specified source server name already exists. Please modify the source server name.|The error message returned because the specified migration source name already exists. Modify the migration source name.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the error persists, submit a ticket.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/smc).

