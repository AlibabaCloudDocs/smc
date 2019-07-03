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
|JobId|String|否|j-xxxxxxxxxxxxxxx|迁移任务ID。

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
|SourceId.N|RepeatList|否|s-xxxxxxxxxxxxxxx|迁移源ID，可以输入多个。

 |
|State|String|否|Available|迁移源状态。取值范围：

 -   Unavailable（不可用，包括离线和出错）
-   Available（在线）
-   InUse（迁移中）
-   Deleting（删除中）

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|迁移源列表的页码。

 |
|PageSize|Integer|10|每页行数。

 |
|RequestId|String|766A24CA-AA5D-436E-A525-3B870482195C|请求ID。

 |
|SourceServers| | |迁移源数组

 |
|└AgentVersion|String|1.5.2.3|SMC客户端版本号。

 |
|└Architecture|String|x86\_64|迁移源的系统架构。

 |
|└CreationTime|String|2019-06-27T02:58:09Z|迁移源的注册时间。

 |
|└DataDisks| | |迁移源的数据盘数组。

 |
|└Index|Integer|1|数据盘顺序。

 |
|└Path|String|/home/data|数据盘N路径。

 |
|└Size|Integer|20|数据盘N大小。单位为GiB。

 |
|└Description|String|Server Source Imported By GotoAliyun.|迁移源描述。

 |
|└ErrorCode|String|SourceServer.Offline|迁移源状态错误码。

 |
|└HeartbeatRate|Integer|30|SMC客户端（SMC Agent）心跳频率。单位：秒。

 |
|└JobId|String|j-xxxxxxxxxxxxxxx|最近一次的迁移任务ID。

 |
|└KernelLevel|Integer|1|内核版本级别。

 |
|└Name|String|SourceServerName|迁移源的名称。

 |
|└Platform|String|OpenSUSE|迁移源的系统平台。

 |
|└ReplicationDriver|String|SMT|复制驱动器。默认值：SMT（迁云工具）。

 |
|└SourceId|String|s-xxxxxxxxxxx|迁移源ID。

 |
|└State|String|InUse|迁移源状态。

 |
|└StatusInfo|String|\{"error\_code": "S1", "error\_msg": "Rsync not found. Please install rsync."\}|迁移源状态详细信息。该参数在迁移源状态为异常时返回。JSON格式键值对，如：

 ```

error_code 错误码
error_msg 错误信息

```

 |
|└SystemDiskSize|Integer|40|迁移源的系统盘大小。单位为GiB。

 |
|└SystemInfo|String|\{\\"agent\_mode\\":\\"daemon\\",\\"agent\_type\\":\\"aliyun\\",\\"client\_type\\":\\"\\",\\"cores\\":\\"2\\",\\"cpu\_usage\\":\\"0.00\\",\\"hostname\\":\\"ixxxxxxxxxx\\",\\"ipv4\\":\\"10.0.0.1\\",\\"memory\\":\\"8.00\\",\\"memory\_usage\\":\\"3.61\\"\}|迁移源系统信息。JSON格式键值对，可扩展，键值固定。大小不超过1KB。如：

 ```

AGENT_MODE 迁移模式
HOSTNAME 主机名
IPV4 IPv4地址
IPV6 IPv6地址
CORES cpu核数
CPU_USAGE CPU使用率
MEMORY 内存
MEMORY_USAGE 内存使用率

```

 |
|TotalCount|Integer|1|迁移源总数。

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
  <RequestId>766A24CA-AA5D-436E-A525-3B870482195C</RequestId>
  <TotalCount>1</TotalCount>
  <SourceServers>
    <SourceServer>
      <AgentVesion>1.5.2.3</AgentVesion>
      <ReplicationDriver>SMT</ReplicationDriver>
      <Description>Server Source Imported By GotoAliyun.</Description>
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
      <Platform>OpenSUSE</Platform>
    </SourceServer>
  </SourceServers>
</DescribeSourceServersReponse>

```

`JSON` 格式

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

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/smc)

