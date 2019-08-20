# DescribeSourceServers {#doc_api_smc_DescribeSourceServers .reference}

You can call this operation to query one or more migration sources.

## Description {#description .section}

You can specify multiple request parameters to be queried. Specified parameters have logical AND relations. Only the parameters that are specified are included in the filtering conditions.

## Debugging {#apiExplorer .section}

Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/#product=smc&api=DescribeSourceServers) to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|No|DescribeSourceServers| The operation that you want to perform. Set this parameter to DescribeSourceServers.

 |
|JobId|String|No|j-xxxxxxxxxxxxxxx| The ID of the migration task for the migration source to query.

 |
|Name|String|No|MySourceServer| The name of the migration source to query. The name must be 2 to 128 characters in length and can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.

 Default value: null

 |
|PageNumber|Integer|No|1| The number of the page to return. Pages start from page 1.

 Default value: 1

 |
|PageSize|Integer|No|10| The number of entries to return on each page. Valid values: 1 to 50

 Default value: 10

 |
|SourceId.N|RepeatList|No|s-xxxxxxxxxxxxxxx| The list of migration source IDs.

 |
|State|String|No|Available| The status of the migration source. Valid values:

 -   Unavailable
-   Available
-   InUse
-   Deleting

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|PageNumber|Integer|1| The returned page number of the migration source list.

 |
|PageSize|Integer|10| The number of entries returned on each page.

 |
|RequestId|String|766A24CA-AA5D-436E-A525-3B870482195C| The ID of the request.

 |
|SourceServers| | | The array of migration sources.

 |
|└AgentVersion|String|1.5.2.3| The version number of the SMC client.

 |
|└Architecture|String|x86\_64| The system architecture of the migration source.

 |
|└CreationTime|String|2019-06-27T02:58:09Z| The creation time of the migration source.

 |
|└DataDisks|Array| | The array of data disks for the migration source.

 |
|└Index|Integer|1| The serial number of data disk N.

 |
|└Path|String|/home/data| The path of data disk N.

 |
|└Size|Integer|20| The size of data disk N. Unit: GiB.

 |
|└Description|String|Server Source Imported By GotoAliyun.| The description of the migration source.

 |
|└ErrorCode|String|SourceServer.Offline| The status error code of the migration source.

 |
|└HeartbeatRate|Integer|30| The period of time for the SMC heartbeat. Unit: seconds.

 |
|└JobId|String|j-xxxxxxxxxxxxxxx| The ID of the most recent migration task.

 |
|└KernelLevel|Integer|1| The kernel level of the migration source.

 |
|└Name|String|SourceServerName| The name of the migration source.

 |
|└Platform|String|OpenSUSE| The system platform of the migration source.

 |
|└ReplicationDriver|String|SMT| The replication driver used for migration. Default value: SMT.

 |
|└SourceId|String|s-xxxxxxxxxxx| The ID of the migration source.

 |
|└State|String|InUse| The status of the migration source.

 |
|└StatusInfo|String|\{"error\_code": "S1", "error\_msg": "Rsync not found. Please install rsync."\}| The status information of the migration source. This parameter is only returned when the migration source status is abnormal. This information is returned as a pair of JSON key-value pairs. The keys are as follows:

 ``` {#codeblock_1n6_0oi_pe9}

error_code
error_msg

```

 |
|└SystemDiskSize|Integer|40| The system disk size of the migration source. Unit: GiB.

 |
|└SystemInfo|String|\{\\"agent\_mode\\":\\"daemon\\",\\"agent\_type\\":\\"aliyun\\",\\"client\_type\\":\\"\\",\\"cores\\":\\"2\\",\\"cpu\_usage\\":\\"0.00\\",\\"hostname\\":\\"ixxxxxxxxxx\\",\\"ipv4\\":\\"10.0.0.1\\",\\"memory\\":\\"8.00\\",\\"memory\_usage\\":\\"3.61\\"\}| The system information of the migration source. The information is returned as multiple JSON key-value pairs. The maximum size of this returned value is 1 KB. Key-value pairs are extensible and have known fixed keys. Examples of keys are as follows:

 ``` {#codeblock_jix_499_6va}

AGENT_MODE
HOSTNAME
IPV4
IPV6
CORES
CPU_USAGE
MEMORY
MEMORY_USAGE

```

 |
|TotalCount|Integer|1| The total number of migration sources.

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}
http(s)://smc.aliyuncs.com/? Action=DescribeSourceServers
&<Common request parameters>
```

Sample success response

`XML` format

``` {#xml_return_success_demo}
<DescribeSourceServersReponse>
  <PageNumber>1</PageNumber>
  <PageSize>10</PageSize>
  <RequestId>766A24CA-AA5D-436E-A525-3B870482195C</RequestId>
  <TotalCount>1</TotalCount>
  <SourceServers>
    <SourceServer>
      <AgentVesion>1.5.2.3</AgentVesion>
      <ReplicationDriver>SMT</ReplicationDriver>
      <Description>Server Source Imported By GotoAliyun. </Description>
      <SystemDiskSize>40</SystemDiskSize>
      <HeartbeatRate>30</HeartbeatRate>
      <Architecture>x86_64</Architecture>
      <DataDisks>
        <DataDisk>
          <Index>1</Index>
          <Path>/home/data</Path>
          <Size>20</Size>
        </DataDisk>
      </DataDisks>
      <SourceId>s-xxxxxxxxxx</SourceId>
      <SystemInfo>{\"agent_mode\":\"daemon\",\"agent_type\":\"aliyun\",\"client_type\":\"\",\"cores\":\"2\",\"cpu_usage\":\"0.00\",\"hostname\":\"ixxxxxxxxxx\",\"ipv4\":\"10.0.0.1\",\"memory\":\"8.00\",\"memory_usage\":\"3.61\"}</SystemInfo>
      <Name>SourceServerName</Name>
      <CreationTime>2019-06-27T02:58:09Z</CreationTime>
      <State>InUse</State>
      <JobId>j-xxxxxxxxxxxxxxx</JobId>
      <KernelLevel>1</KernelLevel>
      <ErrorCode/>
      <Platform>OpenSUSE</Platform>
    </SourceServer>
  </SourceServers>
</DescribeSourceServersReponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"766A24CA-AA5D-436E-A525-3B870482195C",
	"SourceServers":{
		"SourceServer":[
			{
				"AgentVersion":"1.5.2.3",
				"ReplicationDriver":"SMT",
				"Description":"Server Source Imported By GotoAliyun.",
				"SystemDiskSize":40,
				"HeartbeatRate":30,
				"JobName":"MyMigrationTask",
				"Architecture":"x86_64",
				"DataDisks":{
					"DataDisk":[
						{
							"Index":1,
							"Path":"/home/data",
							"Size":20
						}
					]
				},
				"SourceId":"s-xxxxxxxxxxx",
				"SystemInfo":"{\"agent_mode\":\"daemon\",\"agent_type\":\"aliyun\",\"client_type\":\"\",\"cores\":\"2\",\"cpu_usage\":\"0.00\",\"hostname\":\"ixxxxxxxxxxx\",\"ipv4\":\"10.0.0.1\",\"memory\":\"8.00\",\"memory_usage\":\"3.61\"}",
				"Name":"sourceServerName",
				"CreationTime":"2019-06-27T02:58:09Z",
				"State":"InUse",
				"JobId":"j-xxxxxxxxxx",
				"KernelLevel":1,
				"ErrorCode":"",
				"Platform":"OpenSUSE"
			}
		]
	}
}
```

## Error codes {#section_0xz_8oc_zvq .section}

[View error codes](https://error-center.aliyun.com/status/product/smc)

