# DescribeSourceServers

Queries migration sources.

## Description

The AND operator is used to define the relationship between multiple request parameters. If a parameter is not specified, it will not be included in the filtering conditions.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=smc&api=DescribeSourceServers&type=RPC&version=2019-06-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeSourceServers|The operation that you want to perform. Set the value to DescribeSourceServers. |
|SourceId.N|RepeatList|No|s-bp1e2fsl57knvuug\*\*\*\*|The list of migration source IDs. |
|JobId|String|No|j-bp19vlwm0tyigbmj\*\*\*\*|The ID of the migration task. |
|State|String|No|Available|The status of the migration source. Valid values:

 -   Unavailable, including Inactive and InError
-   Available
-   InUse
-   Deleting |
|Name|String|No|testSourceServerName|The name of the migration source. The name must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. The name can contain digits, colons \(:\), underscores \(\_\), and hyphens \(-\).

 Default value: null. |
|PageNumber|Integer|No|1|The number of the page to return. Initial value: 1.

 Default value: 1. |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 50.

 Default value: 10. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RequestId|String|410E6073-66D0-45D3-AB3E-4DC3F5E42CAA|The ID of the request. |
|SourceServers|Array| |The array of migration sources. |
|SourceServer| | | |
|AgentVersion|String|1.5.2.3|The version number of the SMC client. |
|Architecture|String|x86\_64|The system architecture of the migration source. |
|CreationTime|String|2019-06-27T02:58:09Z|The time when the migration source was created. |
|DataDisks|Array| |The array of data disks on the migration source. |
|DataDisk| | | |
|Index|Integer|1|The index number of the data disk. |
|Parts|Array| |The information of data disk partitions. |
|Part| | | |
|CanBlock|Boolean|false|Indicates whether to enable block replication for data disk partitions. |
|Device|String|1\_0|The device ID of the data disk partition. |
|Need|Boolean|false|Indicates whether the data disk partition must be selected. |
|Path|String|/home/data|The path of the data disk partition. |
|SizeBytes|Long|21474836480|The size of the data disk partition. Unit: bytes. |
|Path|String|/home/data|The path of data disk N. |
|Size|Integer|20|The size of data disk N. Unit: GiB. |
|Description|String|Server Source Imported By GotoAliyun.|The description of the migration source. |
|ErrorCode|String|SourceServer.Offline|The status error code of the migration source. |
|HeartbeatRate|Integer|30|The interval at which heartbeats are sent from the SMC client. Unit: seconds. |
|JobId|String|j-bp19vlwm0tyigbmj\*\*\*\*|The ID of the last migration task. |
|KernelLevel|Integer|1|The kernel level of the migration source. |
|Name|String|SourceServerName|The name of the migration source. |
|Platform|String|OpenSUSE|The platform of the migration source. |
|ReplicationDriver|String|SMT|The replication driver used for migration. Default value: SMT. |
|SourceId|String|s-bp1e2fsl57knvuug\*\*\*\*|The ID of the migration source. |
|State|String|InUse|The status of the migration source. |
|StatusInfo|String|\{"error\_code": "S1", "error\_msg": "Rsync not found. Please install rsync."\}|The status information of the migration source. This parameter is returned if the migration source is in the InError state. The parameter must be specified as key-value pairs in JSON format. Example:

 ```

error_code
error_msg

``` |
|SystemDiskParts|Array| |The information of system disk partitions. |
|SystemDiskPart| | | |
|CanBlock|Boolean|true|Indicates whether to enable block replication for partitions on the system disk. |
|Device|String|0\_0|The device ID of the system disk partition. |
|Need|Boolean|true|Indicates whether to select a partition on the system disk. |
|Path|String|/boot|The path of the system disk partition. |
|SizeBytes|Long|254803968|The size of the system disk partition. Unit: bytes. |
|SystemDiskSize|Integer|40|The system disk size of the migration source. Unit: GiB. |
|SystemInfo|String|\{\\"agent\_mode\\":\\"daemon\\",\\"agent\_type\\":\\"aliyun\\",\\"client\_type\\":\\"\\",\\"cores\\":\\"2\\",\\"cpu\_usage\\":\\"0.00\\",\\"hostname\\":\\"ixxxxxxxxxx\\",\\"ipv4\\":\\"10.0.0.1\\",\\"memory\\":\\"8.00\\",\\"memory\_usage\\":\\"3.61\\"\}|The system information of the migration source. The parameter must be specified as key-value pairs in the JSON format. The key-value pairs are extensible and have fixed keys. The maximum value is 1 KB. Example:

 ```

AGENT_MODE
HOSTNAME
IPV4
IPV6
CORES
CPU_USAGE
MEMORY
MEMORY_USAGE

``` |
|TotalCount|Integer|1|The sum of migration sources. |

## Examples

Sample requests

```
http(s)://smc.aliyuncs.com/? Action=DescribeSourceServers
&SourceId.1=s-bp1e2fsl57knvuug****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeSourceServersReponse>
      <SourceServers>
            <SourceServer>
                  <Description>Server Source Imported By GotoAliyun. Hostname: ubuntu14 IP Address: 192.168. **. **</Description>
                  <SystemInfo>{"agent_mode":"daemon","agent_type":"aliyun","client_type":"","cores":"1","cpu_info":"","cpu_usage":"0.00","hostname":"ubuntu14","ipv4":"192.168. **.**","memory":"1.00","memory_usage":"0.73"}</SystemInfo>
                  <Platform>Ubuntu</Platform>
                  <Architecture>x86_64</Architecture>
                  <AgentVersion>2.2.0</AgentVersion>
                  <SystemDiskSize>9</SystemDiskSize>
                  <SourceId>s-bp1e2fsl57knvuug****</SourceId>
                  <SystemDiskParts>
                        <SystemDiskPart>
                              <Path>/boot</Path>
                              <Device>0_0</Device>
                              <CanBlock>true</CanBlock>
                              <SizeBytes>254803968</SizeBytes>
                        </SystemDiskPart>
                        <SystemDiskPart>
                              <Path>/</Path>
                              <Device>0_1</Device>
                              <CanBlock>true</CanBlock>
                              <SizeBytes>9403629568</SizeBytes>
                        </SystemDiskPart>
                  </SystemDiskParts>
                  <Name>testSourceServerName</Name>
                  <KernelLevel>1</KernelLevel>
                  <ReplicationDriver>SMT</ReplicationDriver>
                  <State>Unavailable</State>
                  <CreationTime>2020-04-26T12:49:10Z</CreationTime>
                  <HeartbeatRate>30</HeartbeatRate>
                  <ErrorCode>SourceServer.Offline</ErrorCode>
                  <JobId>j-bp19vlwm0tyigbmj****</JobId>
            </SourceServer>
      </SourceServers>
      <TotalCount>1</TotalCount>
      <RequestId>410E6073-66D0-45D3-AB3E-4DC3F5E42CAA</RequestId>
      <PageSize>10</PageSize>
      <PageNumber>1</PageNumber>
</DescribeSourceServersReponse>
```

`JSON` format

```
{
  "SourceServers": {
    "SourceServer": [
      {
        "Description": "Server Source Imported By GotoAliyun. Hostname: ubuntu14 IP Address: 192.168. **. **",
        "SystemInfo": "{\"agent_mode\":\"daemon\",\"agent_type\":\"aliyun\",\"client_type\":\"\",\"cores\":\"1\",\"cpu_info\":\"\",\"cpu_usage\":\"0.00\",\"hostname\":\"ubuntu14\",\"ipv4\":\"192.168. **.**\",\"memory\":\"1.00\",\"memory_usage\":\"0.73\"}",
        "Platform": "Ubuntu",
        "Architecture": "x86_64",
        "AgentVersion": "2.2.0",
        "SystemDiskSize": 9,
        "SourceId": "s-bp1e2fsl57knvuug****",
        "SystemDiskParts": {
          "SystemDiskPart": [
            {
              "Path": "/boot",
              "Device": "0_0",
              "CanBlock": true,
              "SizeBytes": 254803968
            },
            {
              "Path": "/",
              "Device": "0_1",
              "CanBlock": true,
              "SizeBytes": 9403629568
            }
          ]
        },
        "Name": "testSourceServerName",
        "KernelLevel": 1,
        "ReplicationDriver": "SMT",
        "State": "Unavailable",
        "CreationTime": "2020-04-26T12:49:10Z",
        "HeartbeatRate": 30,
        "ErrorCode": "SourceServer.Offline",
        "JobId": "j-bp19vlwm0tyigbmj****"
      }
    ]
  },
  "TotalCount": 1,
  "RequestId": "410E6073-66D0-45D3-AB3E-4DC3F5E42CAA",
  "PageSize": 10,
  "PageNumber": 1
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/smc).

