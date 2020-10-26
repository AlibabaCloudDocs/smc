# UntagResources

Removes tags from Server Migration Center \(SMC\) resources. The SMC resources include migration sources and tasks.

****

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=UntagResources&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UntagResources|The operation that you want to perform. Set the value to UntagResources. |
|ResourceId.N|RepeatList|Yes|s-bw526m1vi6x20c6g\*\*\*\*|The ID of the Nth SMC resource. SMC resources include migration sources and tasks. Valid values of N: 1 to 50. |
|ResourceType|String|Yes|sourceserver|The type of the SMC resource. Valid values:

 -   sourceserver: migration source
-   replicationjob: migration task |
|TagKey.N|RepeatList|No|TestKey|The key of tag N that is attached to the SMC resource. Tag keys are case-sensitive. Valid values of N: 1 to 20. |
|All|Boolean|No|false|Specifies whether to remove all tags from the SMC resource. This parameter is valid only when the `TagKey.N` parameter is not specified in the request. Valid values:

 -   true: All the tags that are attached to the specified SMC resource are removed. If no tags are attached to the specified SMC resource, no operation is performed.
-   false: No tags that are attached to the specified SMC resource are removed.

 Default value: false. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|2D69A58F-345C-4FDE-88E4-BF5189484043|The ID of the request. |

## Examples

Sample requests

```
http(s)://smc.aliyuncs.com/? Action=UntagResources
&ResourceId.1=s-bw526m1vi6x20c6g****
&ResourceType=sourceserver
&TagKey.1=TestKey
&<Common request parameters>
```

Sample success responses

`XML` format

```
<UntagResourcesResponse>
      <RequestId>2D69A58F-345C-4FDE-88E4-BF5189484043</RequestId>
</UntagResourcesResponse>
```

`JSON` format

```
{
    "RequestId": "2D69A58F-345C-4FDE-88E4-BF5189484043"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|NumberExceed.Tags|The maximum number of the Tag parameters cannot exceed 20.|The error message returned because the maximum number of tags has been reached. Maximum value: 20.|
|400|MissingParameter.ResourceType|You must specify ResourceType.|The error message returned because the ResourceType parameter is not specified.|
|400|InvalidResourceType.NotFound|The specified ResourceType does not exist.|The error message returned because the specified value of the ResourceType parameter does not exist.|
|400|NumberExceed.ResourceIds|The maximum number of ResourceId parameters cannot exceed 50.|The error message returned because the maximum number of resource IDs has been reached. Maximum value: 50.|
|400|Duplicate.ResourceId|The ResourceId contains duplicate values.|The error message returned because the specified value of the ResourceId parameter already exists.|
|400|InvalidResourceId.NotFound|The specified ResourceIds do not exist.|The error message returned because the specified value of the ResourceId parameter does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/smc).

