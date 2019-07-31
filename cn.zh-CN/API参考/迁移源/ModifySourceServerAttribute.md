# ModifySourceServerAttribute {#doc_api_smc_ModifySourceServerAttribute .reference}

修改一个迁移源的名称和描述。

## 接口说明 {#description .section}

使用该API修改迁移源的名称和描述时，对迁移源的状态没有要求。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=smc&api=ModifySourceServerAttribute&type=RPC&version=2019-06-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|SourceId|String|是|s-xxxxxxxxxxx|迁移源ID。

 |
|Action|String|否|ModifySourceServerAttribute|系统规定参数。取值：ModifySourceServerAttribute

 |
|Description|String|否|This is a source server.|迁移源描述。取值需满足以下要求：

 -   能包含 0~256 个字符。
-   不能以 http:// 和 https:// 开头。
-   不填则为空。

 默认值：空。

 |
|Name|String|否|MySourceServer|迁移源名称。长度为2~128个英文或中文字符。必须以大小字母或中文开头，不能以 http:// 和 https:// 开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 默认值：空。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
http(s)://smc.aliyuncs.com/?Action=ModifySourceServerAttribute
&SourceId=s-xxxxxxxxxxx
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteReplicationJobResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DeleteReplicationJobResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|SourceServerState.Invalid|The specified source server status is invalid.|无效的迁移源状态|
|400|SourceServerName.Duplicate|The specified source server name already exists. Please modify the source server name.|迁移源名称已存在，请修改迁移源名称|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|内部错误，请重试。如果多次尝试失败，请提交工单|

访问[错误中心](https://error-center.aliyun.com/status/product/smc)查看更多错误码。

