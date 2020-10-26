# TagResources

Creates and attaches tags to a list of Server Migration Center \(SMC\) resources. The SMC resources include migration sources and tasks.

## Description

A maximum of 20 tags can be attached to each SMC resource.

Before you attach tags to an SMC resource, Alibaba Cloud checks the number of existing tags of the resource. If the maximum number is reached, an error message is returned.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=TagResources&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|TagResources|The operation that you want to perform. Set the value to TagResources. |
|ResourceId.N|RepeatList|Yes|s-bw526m1vi6x20c6g\*\*\*\*|The ID of the Nth SMC resource. SMC resources include migration sources and tasks. Valid values of N: 1 to 50. |
|ResourceType|String|Yes|sourceserver|The type of the SMC resource. Valid values:

 -   sourceserver: migration source
-   replicationjob: migration task |
|Tag.N.Key|String|No|TestKey|The key of tag N that is attached to the SMC resource. Valid values of N: 1 to 20.

 This parameter cannot be an empty string. It can be up to 128 characters in length and cannot start with acs: or aliyun. It cannot contain http:// or https://. |
|Tag.N.Value|String|No|TestValue|The value of tag N that is attached to the SMC resource. Valid values of N: 1 to 20.

 This parameter cannot be an empty string. The tag value can be up to 128 characters in length and cannot contain http:// or https://. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|3E8B9ABB-289A-44E6-942D-8AA9E4937208|The ID of the request. |

## Examples

Sample requests

```
https://smc.aliyuncs.com/?Action=TagResoruces
&RegionId=cn-hangzhou
&ResourceId.1=s-bw526m1vi6x20c6g****
&ResourceType=sourceserver
&Tag.1.Key=TestKey
&<Common request parameters>
```

Sample success responses

`XML` format

```
<TagResourcesResponse>
      <RequestId>3E8B9ABB-289A-44E6-942D-8AA9E4937208</RequestId>
</TagResourcesResponse>
```

`JSON` format

```
{
	"RequestId": "3E8B9ABB-289A-44E6-942D-8AA9E4937208"
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

