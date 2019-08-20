# Make API requests {#concept_dwx_cmf_ndb .concept}

The SMC API is an RPC-based API and can be called using the GET and POST methods. This topic describes how to call the SMC API. Every request made to the SMC API must be signed and authenticated.

## Request structure {#section_rn1_hmf_ndb .section}

This section describes the structure of an API request made over HTTP or HTTPS. The URL format of a GET request is as follows:

``` {#codeblock_4f2_ppk_qsz}
http(s)://Endpoint/? Action=xx&Parameters
```

-   Endpoint: the cloud service access point. Example: `smc.aliyuncs.com`.
-   Action: the operation to be performed for the current request. For example, you can create a migration task by specifying this value as CreateReplicationJob.
-   Parameters: the request parameters, consisting of both common and API-specific request parameters. Separate each parameter with an ampersand \(`&`\).

The following example shows how to call the CreateReplicationJob operation:

``` {#codeblock_j23_x97_sxz}
https://smc.aliyuncs.com/?Action=CreateReplicationJob
&SystemDiskSize=125
& Common request parameters
```

## Endpoints {#section_kb4_ojs_h91 .section}

The endpoint of the SMC API is smc.aliyuncs.com.

## Common parameters {#section_njt_q7b_2g7 .section}

The following table describes common request parameters used when you send GET requests through the URL to call the SMC API. For more information about common parameters, see [RPC APIs](../../../../reseller.en-US/Alibaba Cloud API/Common parameters/RPC APIs.md#).

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateReplicationJob|The operation that you want to perform. For more information about the parameter values, see [List of operations by function](reseller.en-US/API Reference/List of operations by function.md#).|
|AccessKeyId|String|Yes|LTAIp4\*\*\*\*\*\*\*\*fjx|The AccessKey ID. For more information, see [Create an AccessKey](../../../../reseller.en-US/General Reference/Create an AccessKey.md#).|
|Signature|String|Yes|OLeaidS1JvxuMvnyHOwuJ%2BuX5qY%3D|Your signature. For more information about RPC-based API signatures, see [Sign RPC APIs](../../../../reseller.en-US/Alibaba Cloud API/Signature/Sign RPC APIs.md#).|
|SignatureMethod|String|Yes|HMAC-SHA1|The signature method. Set the value to HMAC-SHA1.|
|SignatureVersion|String|Yes|1.0|The version of the signature algorithm. Set the value to 1.0.|
|SignatureNonce|String|Yes|3ee8c1b8-\*\*\*\*-44af-\*\*\*\*-4e0ad82fd6cf|A unique random number that is used to prevent network replay attacks. Different random numbers must be used for different requests.|
|Timestamp|String|Yes|2018-01-01T12:00:00Z|The timestamp of the request. Specify the time in the [ISO 8601](reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard in the `yyyy-MM-ddTHH:mm:ssZ` format. The time must be in UTC.|
|Version|String|Yes|2014-08-28|The API version to use. The value must be in the `YYYY-MM-DD` format. Set the value to 2019-06-01.|
|Format|String|No|json|The output format of the response. Valid values: json and xml. Default value: json

 |

## RAM authentication {#section_506_bgp_8nd .section}

The following table describes the authentication rules for some API operations. For more information about the Alibaba Cloud Resource Name \(ARN\) formats of SMC API resources, see [RAM terms](../../../../reseller.en-US/Product Introduction/Terms.md#).

|Action|ARN value|
|:-----|:--------|
|DeleteSourceServer|acs:smc:$regionid:$accountid:sourceServer/$sourceId|
|DescribeSourceServers|acs:smc:$regionid:$accountid:sourceServer/\*|
|ModifySourceServerAttribute|acs:smc:$regionid:$accountid:sourceServer/$sourceId|
|CreateReplicationJob| -   acs:smc:$regionid:$accountid:sourceServer/$sourceId
-   acs:smc:$regionid:$accountid:replicationJob/\*

 |
|DeleteReplicationJob|acs:smc:$regionid:$accountid:replicationJob/$jobId|
|DescribeReplicationJobs|acs:smc:$regionid:$accountid:replicationJob/\*|
|ModifyReplicationJobAttribute|acs:smc:$regionid:$accountid:replicationJob/$jobId|
|StartReplicationJob|acs:smc:$regionid:$accountid:replicationJob/$jobId|
|StopReplicationJob|acs:smc:$regionid:$accountid:replicationJob/$jobId|

