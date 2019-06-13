# 启动迁移（Windows命令行） {#task_593187 .task}

迁移源符合迁移条件后，您需要配置阿里云账号的访问密钥和迁移信息，之后运行客户端命令迁移上云。本文介绍如何使用Windows命令行版本客户端配置信息并迁移。

您已创建并获取子账号的访问密钥（AccessKey）。详情请参见[创建AccessKey](../../../../cn.zh-CN/通用参考/创建AccessKey.md#)。

**说明：** AccessKey是您访问阿里云API资源的重要凭证，请妥善保管。为防止AccessKey泄漏或被滥用，建议您使用子账号创建临时的AccessKey，在迁移完成之后再禁用该AccessKey。

SMC客户端包含Windows GUI版本、Windows命令行版本和Linux版本。Windows命令行版本客户端的详细介绍，请参见[Windows命令行版本](../../../../cn.zh-CN/.md#section_t4z_3c5_8ug)。

1.  配置迁移信息。 
    1.  打开user\_config.json文件。
    2.  配置阿里云子账号的访问密钥。 

        |参数名|类型|是否必填|描述|
        |:--|:-|:---|:-|
        |access\_id|String|是|阿里云子账号访问密钥的AccessKeyID。|
        |secret\_key|String|是|阿里云子账号访问密钥的AccessKeySecret。|

    3.  配置迁移源的操作系统类型。 

        |参数名|类型|是否必填|描述|
        |:--|:-|:---|:-|
        |platform|String|否|迁移源的操作系统。取值范围：Windows Server 2003 | Windows Server 2008 | Windows Server 2012 | Windows Server 2016 **说明：** 参数`platform`的取值需要与以上列表保持一致，必须区分大小写，并保持空格一致。

 |

    4.  配置迁移目标信息。 迁移目标信息的配置参数和详细描述，请参见下表。 配置示例请参见。

        |参数名|类型|是否必填|描述|
        |:--|:-|:---|:-|
        |region\_id|String|是|迁移源预计迁入的阿里云地域ID。例如，您需要将服务器迁入杭州，则region\_id为cn-hangzhou。更多地域ID请参见[地域与可用区](../../../../cn.zh-CN/通用参考/地域和可用区.md#)。|
        |image\_name|String|是|目标阿里云ECS镜像的名称。 **说明：** 

        -   该名称不能与同一地域下现有镜像名重复。
        -   长度为 \[2, 128\] 个英文或中文字符。必须以大小字母或中文开头，不能以 http:// 和 https:// 开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。
 |
        |system\_disk\_size|Integer|是|目标阿里云服务器ECS系统盘的大小，单位为GiB。取值范围：\[20, 500\] **说明：** 该参数取值需要大于迁移源系统盘实际占用大小，例如，迁移源系统盘大小为500 GiB，实际占用100 GiB，那该参数取值只要大于100 GiB即可。

 |
        |bandwidth\_limit|Integer|否|迁移过程中数据传输的带宽上限限制，单位为 KB/s。 默认值：0，表示不限制带宽速度。

 |
        |data\_disks|Array|否|目标阿里云服务器ECS包含的数据盘列表，最多支持16块数据盘。具体参数参见[表 4](#table_huo_2ez_2g1)。|

        |参数名|类型|是否必填|描述|
        |:--|:-|:---|:-|
        |data\_disk\_index|Integer|是|数据盘序号。取值范围：\[1, 16\] 初始值：1

 |
        |data\_disk\_size|Integer|是|数据盘大小。单位为GiB。取值范围：\[20, 32768\] **说明：** 该参数取值需大于迁移源数据盘实际占用大小。例如，迁移源数据盘大小为500 GiB，实际占用100 GiB，那该参数取值需要大于100 GiB。

 |
        |src\_path|String|是|数据盘源目录。取值举例： 例如，D、E 或者 F。|

        配置示例如下：

        -   **示例1：迁移一台无数据盘的Windows服务器到杭州** 

            -   假设迁移源配置信息为：
                -   操作系统：Windows Server 2008
                -   系统架构：64位
                -   系统盘：30 GiB
            -   迁移目标为：
                -   目标地域：阿里云华东1（杭州）地域（`cn-hangzhou`）
                -   镜像名称：CLIENT\_IMAGE\_WIN08\_01
                -   系统盘设置：50 GiB
            ``` {#codeblock_9b2_8b3_mbl}
            {
                "access_id": "YourAccessKeyID",
                "secret_key": "YourAccessKeySecret",
                "region_id": "cn-hangzhou",
                "image_name": "CLIENT_IMAGE_WIN08_01",
                "system_disk_size": 50,
                "platform": "Windows Server 2008",
                "architecture": "x86_64",
                "data_disks": [],
                "bandwidth_limit": 0
            }
            ```

        -   **示例2：迁移一台带数据盘的Windows服务器到杭州** 

            在示例1的基础上加入了2块数据盘，数据盘目录和大小分别为：

            -   迁移源数据盘分区信息：
                -   D：50 GiB
                -   E：100 GiB
            -   目标数据盘分区信息：
                -   D：100 GiB
                -   E：150 GiB
            ``` {#codeblock_qq9_5if_0yg}
            {
                "access_id": "YourAccessKeyID",
                "secret_key": "YourAccessKeySecret",
                "region_id": "cn-hangzhou",
                "image_name": "CLIENT_IMAGE_WIN08_01",
                "system_disk_size": 50,
                "platform": "Windows Server 2008",
                "architecture": "x86_64",
                "data_disks":  [ {
                        "data_disk_index": 1,
                        "data_disk_size": 100,
                        "src_path": "D:"
                    }, {
                        "data_disk_index": 2,
                        "data_disk_size": 150,
                        "src_path": "E:"
                    }
                ],
                "bandwidth_limit": 0
            }
            ```

2.  （可选）排除不迁移的文件或目录。 配置文件在Excludes目录下，包括以下文件：

    -   系统盘配置文件：rsync\_excludes\_win.txt
    -   数据盘配置文件：在系统盘的基础上以disk\[磁盘索引编号\]后缀命名，如rsync\_excludes\_win\_disk1.txt
    **说明：** 若配置文件缺失或被误删，您可自行创建相应文件。

    配置示例如下：

    -   系统盘

        待排除的文件或目录：

        ``` {#codeblock_unl_32a_q28}
        C:\MyDirs\Docs\Words
        C:\MyDirs\Docs\Excels\Report1.xlsx
        ```

        rsync\_excludes\_win.txt文件需配置如下：

        ``` {#codeblock_g7i_5yr_gvb}
        /MyDirs/Docs/Words/
        /MyDirs/Docs/Excels/Report1.xlsx
        ```

    -   数据盘

        待排除的文件或目录：

        ``` {#codeblock_hgr_6hf_d3r}
        D:\MyDirs2\Docs2\Words2
        D:\MyDirs2\Docs2\Excels\Report2.xlsxx
        ```

        rsync\_excludes\_win\_disk1.txt需配置如下：

        ``` {#codeblock_8z3_pw0_d7o}
        /MyDirs2/Docs2/Words2/
        /MyDirs2/Docs2/Excels2/Report2.xlsx
        ```

        **说明：** 排除Windows路径时需将`\`更换为`/`并去掉路径前缀（ scr\_path），例如去掉上述示例中的D:\\。

3.  使用管理员权限，双击运行应用程序go2aliyun\_client启动迁移。

-   启动迁移后，客户端界面会显示迁移任务进度。
    -   当界面提示`Goto Aliyun Finished!`时，表明迁云成功。
    -   若迁移任务失败，您需要查看日志（<客户端主目录\>\\Logs\\go2aliyun\_client\_<迁云日期\>），定位失败原因，修复问题后，重新执行第3步。
-   启动迁移后，您也可以前往SMC控制台，查看该迁云任务的进度，或总览您账号下所有迁移任务的整体进度。
    -   若迁移任务页面显示迁移任务状态为**已完成**，表明迁云成功。
    -   若迁移任务失败，您需要定位失败原因，修复问题并重启任务，详情请参见[查看迁移进度](cn.zh-CN/快速入门/客户端迁移/查看迁移进度.md#)。

迁云成功后，您可以前往ECS控制台镜像列表的自定义镜像页面，查看SMC为您生成的阿里云镜像，并使用该镜像创建ECS实例。详情请参见[使用自定义镜像创建实例](../../../../cn.zh-CN/实例/创建实例/使用自定义镜像创建实例.md#)。

