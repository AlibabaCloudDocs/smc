# DescribeSourceServers {#doc_api_smc_DescribeSourceServers .reference}

查询一个或多个迁移源。

## 接口说明 {#description .section}

请求参数的作用类似于一个过滤器，过滤器为逻辑与（AND）关系。如果某一参数为空，则过滤器不起作用。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=smc&api=DescribeSourceServers)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|否|DescribeSourceServers|系统规定参数。取值：DescribeSourceServers

 |
|JobId|String|否|j-xxxxxxxxxxxxxxx.1|迁移任务ID。

 |
|Name|String|否|MySourceServer|迁移源名称。长度为2~128个英文或中文字符。必须以大小字母或中文开头，不能以 http:// 和 https:// 开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 默认值：空。

 |
|PageNumber|Integer|否|1|返回的迁移源列表的页码。起始值：1。

 默认值：1。

 |
|PageSize|Integer|否|10|分页查询时设置的每页行数。最大值：50。

 默认值：10。

 |
|SourceId.N|RepeatList|否|s-xxxxxxxxxxxxxxx.1|迁移源ID，可以输入多个。

 |
|State|String|否|Available|迁移源状态。取值范围：

 -   Unavailable（不可用）
-   Available（可用）
-   InUse（使用中）
-   Deleting（删除中）

 迁移源状态详情，请参见[迁移状态](~~121594~~)。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|迁移源列表的页码。

 |
|PageSize|Integer|10|每页行数。

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。

 |
|SourceServers| | |迁移源数组

 |
|└AgentVersion|String|1.0|SMC客户端版本号。

 |
|└Architecture|String|x86\_64|迁移源的系统架构。

 |
|└CreationTime|String|2014-07-15T13:00:52Z|迁移源创建时间。

 |
|└DataDisks| | |迁移源的数据盘数组。

 |
|└Index|Integer|1|数据盘顺序。

 |
|└Path|String|PATH|数据盘N路径。

 |
|└Size|Integer|40|数据盘N大小。单位为GiB。

 |
|└Description|String|This is a source server.|迁移源描述。

 |
|└ErrorCode|String|403|错误码。

 |
|└HeartbeatRate|Integer|60|Agent心跳频率。单位：秒。

 |
|└JobId|String|j-xxxxxxxxxxxxxxx|最近一次的迁移任务ID。

 |
|└JobName|String|MyMigrationTask|最近一次迁移任务名称。

 |
|└KernelLevel|Integer|1|内核版本级别。

 |
|└Name|String|SourceServerName|迁移源名称。

 |
|└Platform|String|Windows Server 2008|迁移源的系统平台。

 |
|└ReplicationDriver|String|SMT|复制驱动器。默认值：SMT（迁云工具）。

 |
|└SourceId|String|s-xxxxxxxxxxx|迁移源ID。

 |
|└State|String|Available|迁移源状态。

 |
|└StatusInfo|String|Available|迁移源状态详细信息。

 |
|└SystemDiskSize|Integer|40|目标云服务器的系统盘大小。单位为GiB。

 |
|└SystemInfo|String|HOTENAME hostname|迁移源系统信息。Json格式键值对，可扩展，键值固定。大小不超过1KB。如：

 ```

HOSTNAME 主机名
IPV4 IPv4地址
IPV6 IPv6地址
MAC 网卡mac地址
KERNEL 内核版本
VENDER 制造商
CORES cpu核数
MEMORY 内存

```

 |
|TotalCount|Integer|5|迁移源总数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
http(s)://smc.aliyuncs.com/?Action=DescribeSourceServers
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeSourceServersReponse>
  <PageNumber>1</PageNumber>
  <PageSize>10</PageSize>
  <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
  <TotalCount>5</TotalCount>
  <SourceServers>
    <SourceServer>
      <AgentVesion>1.0</AgentVesion>
      <Architecture>x86_64</Architecture>
      <CreationTime>2014-07-15T13:00:52Z</CreationTime>
      <DataDisks>
        <DataDisk>
          <Index>1</Index>
          <Path>PATH</Path>
          <Size>40</Size>
        </DataDisk>
      </DataDisks>
      <Description>This is a source server.</Description>
      <ErrorCode>InternalError</ErrorCode>
      <HeartbeatRate>60</HeartbeatRate>
      <JobId>j-xxxxxxxxxxxxxxx</JobId>
      <JobName>MyMiagration Task</JobName>
      <KernelLevel>1</KernelLevel>
      <Name>SourceServerName</Name>
      <Platform>Windows Server 2008</Platform>
      <ReplicationDriver>SMT</ReplicationDriver>
      <SourceId>s-sourceid1</SourceId>
      <State>Available</State>
      <StatusInfo>statusinfo1</StatusInfo>
      <SystemDiskSize>40</SystemDiskSize>
      <SystemInfo>HOSTNAME hostname</SystemInfo>
    </SourceServer>
  </SourceServers>
</DescribeSourceServersReponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":"5",
	"PageSize":10,
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E",
	"SourceServers":{
		"SourceServer":[
			{
				"ReplicationDriver":"SMT",
				"Description":"This is a source server.",
				"SystemDiskSize":"40",
				"HeartbeatRate":"60",
				"JobName":"MyMiagration Task",
				"Architecture":"x86_64",
				"DataDisks":{
					"DataDisk":[
						{
							"Index":"1",
							"Size":"40",
							"Path":"PATH"
						}
					]
				},
				"SourceId":"s-sourceid1",
				"SystemInfo":"HOSTNAME hostname",
				"CreationTime":"2014-07-15T13:00:52Z",
				"Name":"SourceServerName",
				"StatusInfo":"statusinfo1",
				"State":"Available",
				"JobId":"j-xxxxxxxxxxxxxxx",
				"KernelLevel":"1",
				"AgentVesion":"1.0",
				"ErrorCode":"InternalError",
				"Platform":"Windows Server 2008"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/smc)

