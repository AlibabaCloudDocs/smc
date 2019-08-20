# ModifySourceServerAttribute {#doc_api_smc_ModifySourceServerAttribute .reference}

You can call this operation to modify the name and description of a migration source.

## Description {#description .section}

This operation can be called regardless of the status of the migration source.

## Debugging {#apiExplorer .section}

Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/#product=smc&api=ModifySourceServerAttribute) to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|SourceId|String|Yes|s-xxxxxxxxxxx| The ID of the migration source to modify.

 |
|Action|String|No|ModifySourceServerAttribute| The operation that you want to perform. Set this parameter to ModifySourceServerAttribute.

 |
|Description|String|No|This is a source server.| The description of the migration source. The parameter value must meet the following requirements:

 -   It can be up to 256 characters in length.
-   It cannot start with http:// or https://.
-   It can be an empty string.

 Default value: null

 |
|Name|String|No|MySourceServer| The name of the migration source. The name must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.

 Default value: null

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}
http(s)://smc.aliyuncs.com/? Action=ModifySourceServerAttribute
&SourceId=s-xxxxxxxxxxx
&<Common request parameters>
```

Sample success response

`XML` format

``` {#xml_return_success_demo}
<ModifySourceServerAttributeResponse>
  <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</ModifySourceServerAttributeResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#section_6ps_w7x_jno .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|SourceServerState.Invalid|The specified source server status is invalid.|The error message returned because the operation is not supported while the migration source is in the current state.|
|400|SourceServerName.Duplicate|The specified source server name already exists. Please modify the source server name.|The error message returned because the specified migration source name already exists. Modify the migration source name.|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|

[View error codes](https://error-center.aliyun.com/status/product/smc)

