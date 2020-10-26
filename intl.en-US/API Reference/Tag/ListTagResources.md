# ListTagResources

Queries the tags that are attached to one or more Server Migration Center \(SMC\) resources. SMC resources include migration sources and tasks.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=ListTagResources&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListTagResources|The operation that you want to perform. Set the value to ListTagResources. |
|ResourceType|String|Yes|sourceserver|The type of the SMC resource. Valid values:

 -   sourceserver: migration source
-   replicationjob: migration task |
|ResourceId.N|RepeatList|No|s-bp1e2fsl57knvuug\*\*\*\*|The ID of SMC resource N. SMC resources include migration sources and tasks. Valid values of N: 1 to 50. |
|Tag.N.Key|String|No|TestKey|The key of tag N that is attached to the SMC resource. A tag key must be 1 to 128 characters in length. Valid values of N: 1 to 20.

 Tag.N is used for exact match of SMC resources to which tags are attached. Tag N consists of one key-value pair.

 -   Tag keys and values are case-sensitive.
-   If you specify only Tag.N.Key, all resources that are attached to this tag key are returned.
-   If you specify only Tag.N.Value, the error message InvalidParameter.TagValue is returned.
-   If you specify multiple tag key-value pairs at the same time, only SMC resources that match all tag key-value pairs are returned. |
|Tag.N.Value|String|No|TestValue|The value of the tag N of the resource. This value can be 1 to 128 characters in length. Valid values of N: 1 to 20. |
|NextToken|String|No|caeba0bbb2be03f84eb48b699f0a4883|The token for the next query. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|NextToken|String|caeba0bbb2be03f84eb48b699f0a4883|The token for the next query.

 The value of the NextToken parameter is null. All information is displayed on the page. |
|RequestId|String|17743161-66F3-4E7F-B8AE-845FB28B928F|The ID of the request. |
|TagResources|Array| |A collection of SMC resources and tags. The collection includes the resource IDs, types, tag keys, and tag values. |
|TagResource| | | |
|ResourceId|String|s-bp1e2fsl57knvuug\*\*\*\*|The ID of the resource. |
|ResourceType|String|ALIYUN::SMC::SOURCESERVER|The type of the resource. |
|TagKey|String|TestKey|The tag key of the resource. |
|TagValue|String|TestValue|The tag value of the resource. |

## Examples

Sample requests

```
http(s)://smc.aliyuncs.com/? Action=ListTagResources
&ResourceType=sourceserver
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListTagResourcesResponse>
      <TagResources>
            <TagResource>
                  <ResourceType>ALIYUN::SMC::SOURCESERVER</ResourceType>
                  <TagValue>TestValue</TagValue>
                  <ResourceId>s-bp1e2fsl57knvuug****</ResourceId>
                  <TagKey>TestKey</TagKey>
            </TagResource>
            <TagResource>
                  <ResourceType>ALIYUN::SMC::SOURCESERVER</ResourceType>
                  <TagValue>TestValue</TagValue>
                  <ResourceId>s-bp133rsym9xiek5k****</ResourceId>
                  <TagKey>TestKey</TagKey>
            </TagResource>
      </TagResources>
      <NextToken></NextToken>
      <RequestId>17743161-66F3-4E7F-B8AE-845FB28B928F</RequestId>
</ListTagResourcesResponse>
```

`JSON` format

```
{
	"TagResources": {
		"TagResource": [
			{
				"ResourceType": "ALIYUN::SMC::SOURCESERVER",
				"TagValue": "TestValue",
				"ResourceId": "s-bp1e2fsl57knvuug****",
				"TagKey": "TestKey"
			},
			{
				"ResourceType": "ALIYUN::SMC::SOURCESERVER",
				"TagValue": "TestValue",
				"ResourceId": "s-bp133rsym9xiek5k****",
				"TagKey": "TestKey"
			}
		]
	},
	"NextToken": "",
	"RequestId": "17743161-66F3-4E7F-B8AE-845FB28B928F"
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

