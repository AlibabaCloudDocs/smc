# Call the SMC API

The Server Migration Center \(SMC\) API is an RPC-based API and can be called by using the GET and POST methods. This topic describes how to call the SMC API. Each SMC API request must be signed and authenticated.

## Tools

You can use developer tools such as OpenAPI Explorer, Alibaba Cloud CLI, Cloud Shell, and SDKs to debug and call Alibaba Cloud APIs.

-   OpenAPI Explorer

    [OpenAPI Explorer](https://api.aliyun.com/) is a visual web API calling tool. You can call Alibaba Cloud APIs to send requests and view response parameters in OpenAPI Explorer. For more information, see [Alibaba Cloud OpenAPI Explorer User Guide](/intl.en-US/Product Overview/What is OpenAPI Explorer?.md).

-   Alibaba Cloud CLI

    Alibaba Cloud CLI is an open source tool that is built on Alibaba Cloud SDK for Go. You can use Alibaba Cloud CLI to manage your Alibaba Cloud resources. For more information, see [Alibaba Cloud CLI User Guide]().

-   Cloud Shell

    Cloud Shell is a web-based command line tool. You can use Cloud Shell from any browser to run cloud commands and manage Alibaba Cloud resources. For more information, see [Cloud Shell User Guide](https://www.alibabacloud.com/help/zh/doc-detail/90256.htm).

-   SMC SDK

    You can obtain SMC SDKs from [SDK](https://next.api.aliyun.com/api-tools/sdk/smc?version=2019-06-01).


## Request syntax

This section describes the structure of an HTTP or HTTPS API request. Use the following URL format for a GET request:

```
http(s)://Endpoint/? Action=xx&Parameters
```

-   Endpoint: the endpoint of the cloud service. Example: `smc.aliyuncs.com`.
-   Action: the operation that you want to perform in the current request. For example, you can create a migration task by setting this value to CreateReplicationJob.
-   Parameters: the request parameters, which consist of both common and API-specific request parameters. Separate the request parameters with ampersands \(`&`\).

The following example shows how to call the CreateReplicationJob operation:

```
https://smc.aliyuncs.com/?Action=CreateReplicationJob
&SystemDiskSize=125
& Common request parameters
```

## Endpoints

The endpoint of the SMC API is smc.aliyuncs.com.

## Common parameters

The following table describes the common request parameters that you can specify when you send GET requests to call the SMC API.

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateReplicationJob|The operation that you want to perform. For more information, see [API operations](/intl.en-US/API Reference/API operations.md).|
|AccessKeyId|String|Yes|LTAIp4\*\*\*\*\*\*\*\*fjx|The AccessKey ID. For more information, see [Create an AccessKey pair]().|
|Signature|String|Yes|OLeaidS1JvxuMvnyHOwuJ%2BuX5qY%3D|The signature string of the current request. For more information, see [Request signatures](/intl.en-US/API Reference/Getting started/Request signatures.md).|
|SignatureMethod|String|Yes|HMAC-SHA1|The encryption method of the signature string. Set the value to HMAC-SHA1.|
|SignatureVersion|String|Yes|1.0|The version of the signature algorithm. Set the value to 1.0.|
|SignatureNonce|String|Yes|3ee8c1b8-\*\*\*\*-44af-\*\*\*\*-4e0ad82fd6cf|A unique, random number used to prevent network replay attacks. You must use different numbers for different requests.|
|Timestamp|String|Yes|2018-01-01T12:00:00Z|The timestamp of the request. Specify the time in the [ISO 8601](/intl.en-US/API Reference/Appendix/ISO 8601 Time Format.md) standard in the `yyyy-MM-ddTHH:mm:ssZ` format. The time must be in UTC.|
|Version|String|Yes|2014-08-28|The version number of the API. The value must be in the `YYYY-MM-DD` format. Set the value to 2019-06-01.|
|Format|String|No|json|The format in which to return the response. Valid values: JSON and XML. Default value: JSON. |

## RAM authorization

The following table describes the authentication rules for some SMC API operations. For information about the Alibaba Cloud Resource Name \(ARN\) formats of SMC API resources, see [RAM terms](/intl.en-US/Product Introduction/Terms.md).

|Action|ARN value|
|:-----|:--------|
|DeleteSourceServer|acs:smc:$regionid:$accountid:sourceServer/$sourceId|
|DescribeSourceServers|acs:smc:$regionid:$accountid:sourceServer/\*|
|ModifySourceServerAttribute|acs:smc:$regionid:$accountid:sourceServer/$sourceId|
|CreateReplicationJob|-   acs:smc:$regionid:$accountid:sourceServer/$sourceId
-   acs:smc:$regionid:$accountid:replicationJob/\* |
|DeleteReplicationJob|acs:smc:$regionid:$accountid:replicationJob/$jobId|
|DescribeReplicationJobs|acs:smc:$regionid:$accountid:replicationJob/\*|
|ModifyReplicationJobAttribute|acs:smc:$regionid:$accountid:replicationJob/$jobId|
|StartReplicationJob|acs:smc:$regionid:$accountid:replicationJob/$jobId|
|StopReplicationJob|acs:smc:$regionid:$accountid:replicationJob/$jobId|

