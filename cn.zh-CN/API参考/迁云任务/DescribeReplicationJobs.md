# DescribeReplicationJobs

调用DescribeReplicationJobs查询一个或多个迁移任务的详细信息。

## 接口说明

-   请求参数的作用类似于一个过滤器，过滤器为逻辑与（AND）关系。如果某一参数为空，则过滤器不起作用。
-   支持迁移源的迁移目标为Docker容器镜像，实现低成本容器化应用迁移。关于Docker容器镜像详情请参见[容器镜像服务](~~60744~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=smc&api=DescribeReplicationJobs&type=RPC&version=2019-06-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeReplicationJobs|系统规定参数。取值：DescribeReplicationJobs |
|SourceId.N|RepeatList|否|s-bp1e2fsl57knvuug\*\*\*\*|迁移源ID列表。N的最大值：50 |
|JobId.N|RepeatList|否|j-bp19vlwm0tyigbmj\*\*\*\*|迁移任务ID列表。N的最大值：50 |
|Name|String|否|testMigrationTaskName|迁移任务的名称。 |
|RegionId|String|否|cn-hangzhou|迁移源需迁入的目标阿里云地域ID。

 例如，您需要迁移源服务器至上海，则RegionId为`cn-shanghai`。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。 |
|Status|String|否|Ready|迁移任务的主状态。取值：

 -   Ready（未开始）
-   Running（运行中）
-   Stopped（已暂停）
-   InError（出错）
-   Finished（已完成）
-   Waiting（等待中）
-   Expired（已过期）
-   Deleting（删除中） |
|BusinessStatus|String|否|Preparing|迁移任务的业务状态。取值：

 -   Preparing（准备中）
-   Syncing（同步中）
-   Processing（处理中）
-   Cleaning（清理中） |
|PageNumber|Integer|否|1|返回结果中，迁移任务列表的页码。起始值：1

 默认值：1 |
|PageSize|Integer|否|10|分页查询时设置的每页行数。最大值：50

 默认值：10 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|迁移任务列表的页码。 |
|PageSize|Integer|10|每页行数。 |
|ReplicationJobs|Array of ReplicationJob| |迁移任务详情的集合。 |
|ReplicationJob| | | |
|BusinessStatus|String|Preparing|迁移任务的业务状态。 |
|ContainerNamespace|String|testNamespace|Docker的命名空间。 |
|ContainerRepository|String|testRepository|Docker的镜像仓库。 |
|ContainerTag|String|CentOS:v1|Docker的镜像标签。 |
|CreationTime|String|2014-07-24T13:00:52Z|迁移任务的创建时间。 |
|DataDisks|Array of DataDisk| |目标阿里云服务器ECS的数据盘。 |
|DataDisk| | | |
|Index|Integer|1|数据盘顺序。 |
|Parts|Array of Part| |数据盘分区信息。 |
|Part| | | |
|Block|Boolean|true|分区是否开启块复制。 |
|Device|String|0\_1|数据盘分区设备标识。 |
|SizeBytes|Long|21474836480|数据盘分区大小。单位：Byte |
|Size|Integer|40|数据盘大小。单位：GiB |
|Description|String|This is my migration task.|迁移任务的描述。 |
|EndTime|String|2019-06-04T16:00:52Z|迁移任务的完成时间。 |
|ErrorCode|String|InternalError|迁移任务的错误码。 |
|Frequency|Integer|15|增量迁移任务自动执行的时间间隔，单位：小时。取值范围：1~168 |
|ImageId|String|m-o6w3gy99qf89rkga\*\*\*\*|迁移任务交付的目标镜像ID。 |
|ImageName|String|testAliCloudImageName|迁移任务交付的目标镜像名称。 |
|InstanceId|String|i-bp1ff25rzvnul6kr\*\*\*\*|目标实例ID。 |
|InstanceRamRole|String|SMCAdmin|实例RAM角色名称。 |
|InstanceType|String|ecs.sn1ne.large|中转实例的实例规格。 |
|JobId|String|j-bp19vlwm0tyigbmj\*\*\*\*|迁移任务ID。 |
|LaunchTemplateId|String|lt-launchtemplateid|实例启动模板ID。 |
|LaunchTemplateVersion|String|1|一个或多个实例启动模板版本。 |
|LicenseType|String|BYOL|迁移任务的许可证类型。可能值：

 -   空值：无许可证
-   BYOL：自带许可 |
|MaxNumberOfImageToKeep|Integer|8|增量迁移任务默认保留的最大镜像数。取值范围：1~10 |
|Name|String|testMigrationTaskName|迁移任务名称。 |
|NetMode|Integer|0|迁移时使用的网络类型。 |
|Progress|Float|55.45|迁移任务总进度。 |
|RegionId|String|cn-hangzhou|迁移源需迁入的目标阿里云地域ID。 |
|ReplicationJobRuns|Array of ReplicationJobRun| |迁移任务运行记录。 |
|ReplicationJobRun| | | |
|EndTime|String|2019-10-04T13:35:00Z|迁移任务运行的结束时间。 |
|ImageId|String|m-o6w3gy99qf89rkga\*\*\*\*|迁移任务生成的镜像ID。 |
|StartTime|String|2019-10-01T13:35:00Z|迁移任务运行的开始时间。 |
|Type|String|Schedule|迁移任务的执行方式。取值：

 -   Manual：手动执行。
-   Schedule：定时执行或周期执行。 |
|ReplicationParameters|String|BandWidthLimit:0|复制驱动器参数信息。 |
|RunOnce|Boolean|true|区分一次性迁移任务和增量迁移任务。取值：

 -   true：一次性迁移任务。任务创建后仅执行一次。
-   false：增量迁移任务。任务创建后，按照`Frequency`设置的时间间隔，周期性自动执行。 |
|ScheduledStartTime|String|2019-06-04T13:35:00Z|迁移任务的执行时间。 |
|SourceId|String|s-bp1e2fsl57knvuug\*\*\*\*|迁移源ID。 |
|StartTime|String|2019-06-04T14:40:52Z|迁移任务的开始时间。 |
|Status|String|Running|迁移任务的主状态。 |
|StatusInfo|String|statusinfo|迁移状态的详细信息。 |
|SystemDiskParts|Array of SystemDiskPart| |系统盘分区信息。 |
|SystemDiskPart| | | |
|Block|Boolean|true|系统盘分区是否开启块复制。 |
|Device|String|0\_1|系统盘分区设备标识符。 |
|SizeBytes|Long|254803968|系统盘分区大小。单位：Byte |
|SystemDiskSize|Integer|40|目标阿里云服务器ECS的系统盘大小。 |
|TargetType|String|image|迁移交付的目标类型。 |
|TransitionInstanceId|String|i-bp1ff25rzvnul6kr\*\*\*\*|迁移中转实例ID。 |
|VSwitchId|String|vsw-bp1ddbrxdlrcbim46\*\*\*\*|指定VPC下的虚拟交换机ID。 |
|ValidTime|String|2019-06-08T14:40:52Z|迁移任务的过期时间。 |
|VpcId|String|vpc-bp1vwnn14rqpyiczj\*\*\*\*|已配置高速通道服务或者VPN网关的VPC ID。 |
|RequestId|String|6E1187E8-843A-4850-B97E-2F17F00D48F7|请求ID。 |
|TotalCount|Integer|5|迁移任务总个数。 |

## 示例

请求示例

```
http(s)://smc.aliyuncs.com/?Action=DescribeReplicationJobs
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeReplicationJobsResponse>
      <TotalCount>1</TotalCount>
      <ReplicationJobs>
            <ReplicationJob>
                  <Status>Running</Status>
                  <Progress>75</Progress>
                  <TransitionInstanceId>i-bp1ff25rzvnul6kr****</TransitionInstanceId>
                  <DataDisks>
                        <DataDisk>
                              <Parts>
                                    <Part>
                                          <Device>2_0</Device>
                                          <Block>true</Block>
                                          <SizeBytes>5334102016</SizeBytes>
                                    </Part>
                              </Parts>
                              <Size>20</Size>
                              <Index>2</Index>
                        </DataDisk>
                  </DataDisks>
                  <SystemDiskSize>20</SystemDiskSize>
                  <NetMode>0</NetMode>
                  <SourceId>s-bp1e2fsl57knvuug****</SourceId>
                  <SystemDiskParts>
                        <SystemDiskPart>
                              <Device>0_0</Device>
                              <Block>true</Block>
                              <SizeBytes>21466120192</SizeBytes>
                        </SystemDiskPart>
                  </SystemDiskParts>
                  <StartTime>2020-05-14T12:01:24Z</StartTime>
                  <BusinessStatus>Processing</BusinessStatus>
                  <Name>testMigrationTaskName</Name>
                  <ValidTime>2020-06-13T12:01:24Z</ValidTime>
                  <RunOnce>true</RunOnce>
                  <TargetType>Image</TargetType>
                  <CreationTime>2020-05-14T12:01:24Z</CreationTime>
                  <RegionId>cn-hangzhou</RegionId>
                  <ErrorCode></ErrorCode>
                  <JobId>j-bp19vlwm0tyigbmj****</JobId>
            </ReplicationJob>
      </ReplicationJobs>
      <RequestId>6E1187E8-843A-4850-B97E-2F17F00D48F7</RequestId>
      <PageSize>10</PageSize>
      <PageNumber>1</PageNumber>
</DescribeReplicationJobsResponse>
```

`JSON` 格式

```
{
  "TotalCount": 1,
  "ReplicationJobs": {
    "ReplicationJob": [
      {
        "Status": "Running",
        "Progress": 75.0,
        "TransitionInstanceId": "i-bp1ff25rzvnul6kr****",
        "DataDisks": {
          "DataDisk": [
            {
              "Parts": {
                "Part": [
                  {
                    "Device": "2_0",
                    "Block": true,
                    "SizeBytes": 5334102016
                  }
                ]
              },
              "Size": 20,
              "Index": 2
            }
          ]
        },
        "SystemDiskSize": 20,
        "NetMode": 0,
        "SourceId": "s-bp1e2fsl57knvuug****",
        "SystemDiskParts": {
          "SystemDiskPart": [
            {
              "Device": "0_0",
              "Block": true,
              "SizeBytes": 21466120192
            }
          ]
        },
        "StartTime": "2020-05-14T12:01:24Z",
        "BusinessStatus": "Processing",
        "Name": "testMigrationTaskName",
        "ValidTime": "2020-06-13T12:01:24Z",
        "RunOnce": true,
        "TargetType": "Image",
        "CreationTime": "2020-05-14T12:01:24Z",
        "RegionId": "cn-hangzhou",
        "ErrorCode": "",
        "JobId": "j-bp19vlwm0tyigbmj****"
      }
    ]
  },
  "RequestId": "6E1187E8-843A-4850-B97E-2F17F00D48F7",
  "PageSize": 10,
  "PageNumber": 1
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|An error occurred while processing your request. Please try again. If the problem still exists, please submit a ticket.|内部错误，请重试。如果多次尝试失败，请提交工单。|
|403|Forbidden.Unauthorized|A required authorization for the specified action is not supplied.|用户未授权操作指定的资源。|

访问[错误中心](https://error-center.aliyun.com/status/product/smc)查看更多错误码。

