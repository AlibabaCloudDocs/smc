# 启动迁移（Linux） {#task_593194 .task}

迁移源符合迁移条件后，您需要配置阿里云账号的访问密钥和迁移信息，并执行一键迁移命令。本文介绍如何使用Linux版本客户端配置迁移信息并迁移上云。

您已创建并获取子账号的访问密钥（AccessKey）。详情请参见[创建AccessKey](../../../../cn.zh-CN/通用参考/创建AccessKey.md#)。

**说明：** AccessKey是您访问阿里云API资源的重要凭证，请妥善保管。为防止AccessKey泄漏或被滥用，建议您使用子账号创建临时的AccessKey，在迁移完成之后再禁用该AccessKey。

Linux版本SMC客户端的详细介绍，请参见[Linux版本](../../../../cn.zh-CN/.md#section_uor_69k_kd8)。

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
        |platform|String|否|迁移源的操作系统。取值范围：CentOS | Ubuntu | SUSE | OpenSUSE | Debian | RedHat | Others Linux **说明：** 参数`platform`的取值需要与以上列表保持一致，必须区分大小写，并保持空格一致。

 |

    4.  配置迁移目标信息。 迁移目标信息的配置参数和详细描述，请参见下表。您可以参考参数表下方的配置示例。

        |参数名|类型|是否必填|描述|
        |:--|:-|:---|:-|
        |region\_id|String|是|迁移源预计迁入的阿里云地域ID。例如，您需要将服务器迁入杭州，则region\_id为cn-hangzhou。更多地域ID请参见[地域与可用区](../../../../cn.zh-CN/通用参考/地域和可用区.md#)。|
        |image\_name|String|是|目标阿里云ECS镜像的名称。 **说明：** 

        -   该名称不能与同一地域下现有镜像名重复。
        -   长度为 \[2, 128\] 个英文或中文字符。必须以大小字母或中文开头，不能以 http:// 和 https:// 开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。
 |
        |system\_disk\_size|Integer|是|目标阿里云服务器ECS系统盘的大小，单位为GiB。取值范围：\[20, 500\] **说明：** 该参数取值需要大于迁移源系统盘实际占用大小，例如，迁移源系统盘大小为500 GiB，实际占用100 GiB，那该参数取值只要大于100 GiB即可。

 |
        |data\_disks|Array|否|目标阿里云服务器ECS包含的数据盘列表，最多支持16块数据盘。具体参数参见[表 4](#table_65g_pka_u0u)。|
        |bandwidth\_limit|Integer|否|迁移过程中数据传输的带宽上限限制，单位为 KB/s。 默认值：0，表示不限制带宽速度。

 |

        |参数名|类型|是否必填|描述|
        |:--|:-|:---|:-|
        |data\_disk\_index|Integer|是|数据盘序号。取值范围：\[1, 16\] 初始值：1

 |
        |data\_disk\_size|Integer|是|数据盘大小。单位为GiB。取值范围：\[20, 32768\] **说明：** 该参数取值需大于迁移源数据盘实际占用大小。例如，迁移源数据盘大小为500 GiB，实际占用100 GiB，那该参数取值需要大于100 GiB。

 |
        |src\_path|String|是|数据盘源目录。取值举例： 例如，/mnt/disk1、/mnt/disk2或者/mnt/disk3。

**说明：** 不能配置为根目录或者系统目录，例如，/bin、/boot、/dev、/etc、/lib、/lib64、/sbin、/usr和/var。

 |

        -   **配置示例1：迁移一台无数据盘的Linux服务器到北京** 

            -   假设迁移源配置信息为：
                -   发行版本：CentOS 7.2
                -   系统架构：64位
                -   系统盘：30 GiB
            -   迁移目标为：
                -   目标地域：阿里云华北2（北京）地域（`cn-beijing`）
                -   镜像名称：CLIENT\_IMAGE\_CENTOS72\_01
                -   系统盘设置：50 GiB
            ``` {#codeblock_nno_vg3_f4m}
            {
                "access_id": "YourAccessKeyID",
                "secret_key": "YourAccessKeySecret",
                "region_id": "cn-beijing",
                "image_name": "CLIENT_IMAGE_CENTOS72_01",
                "system_disk_size": 50,
                "platform": "CentOS",
                "architecture": "x86_64",
                "data_disks": [],
                "bandwidth_limit": 0
            }
            ```

        -   **配置示例2：迁移一台有数据盘的Linux服务器到北京** 

            在示例3的基础上加入了2块数据盘，数据盘目录和大小分别为：

            -   待迁移数据盘分区信息：
                -   /mnt/disk1：50 GiB
                -   /mnt/disk2：100 GiB
            -   目标数据盘分区信息：
                -   /mnt/disk1：100 GiB
                -   /mnt/disk2：150 GiB
            ``` {#codeblock_2r1_1qx_u7g}
            {
                "access_id": "YourAccessKeyID",
                "secret_key": "YourAccessKeySecret",
                "region_id": "cn-beijing",
                "image_name": "CLIENT_IMAGE_CENTOS72_01",
                "system_disk_size": 50,
                "platform": "CentOS",
                "architecture": "x86_64",
                "data_disks":  [ {
                        "data_disk_index": 1,
                        "data_disk_size": 100,
                        "src_path": "/mnt/disk1"
                    }, {
                        "data_disk_index": 2,
                        "data_disk_size": 150,
                        "src_path": "/mnt/disk2"
                    }
                ],
                "bandwidth_limit": 0
            }
            ```

2.  （可选）排除不迁移的文件或目录。 配置文件在Excludes目录下，包括以下文件：

    -   系统盘配置文件：rsync\_excludes\_linux.txt
    -   数据盘配置文件：在系统盘的基础上以disk\[磁盘索引编号\]后缀命名，如rsync\_excludes\_linux\_disk1.txt
    **说明：** 若配置文件缺失或被误删，您可自行创建相应文件。

     **配置示例： 分别为系统盘和数据盘排除文件或目录** 

    -   系统盘（根目录 /）：
        -   待排除的文件或目录为：

            ``` {#codeblock_ok2_6d8_kau}
            /var/mydirs/docs/words
            /var/mydirs/docs/excels/report1.sh
            ```

        -   rsync\_excludes\_linux.txt需配置如下：

            ``` {#codeblock_0s3_6en_fbp}
            /var/mydirs/docs/words/
            /var/mydirs/docs/excels/report1.sh
            ```

    -   数据盘：

        -   待排除的文件或目录为：

            ``` {#codeblock_tuh_396_rpi}
            /mnt/disk1/mydirs2/docs2/words2
            /mnt/disk1/mydirs2/docs2/excels2/report2.sh
            ```

        -   rsync\_excludes\_linux\_disk1.txt需配置如下：

            ``` {#codeblock_63u_e65_uhx}
            /mydirs2/docs2/words2/
            /mydirs2/docs2/excels2/report2.sh
            ```

        **说明：** 排除Linux路径时需要去掉路径前缀（scr\_path），例如去掉上述示例中的/mnt/disk1。

3.  运行以下命令为主程序增加可执行权限。 

    ``` {#codeblock_hnx_0o7_uxr}
    # sudo chmod +x ./go2aliyun_client  
    ```

4.  运行以下命令迁移。 

    ``` {#codeblock_vrx_97j_9ra}
    # sudo ./go2aliyun_client
    ```


-   启动迁移后，客户端界面会显示迁移任务进度。
    -   当界面提示`Goto Aliyun Finished!`时，表明迁云成功。
    -   若迁移任务失败，您需要查看日志（<客户端主目录\>/Logs），定位失败原因，修复问题后，重新执行第4步。
-   启动迁移后，您也可以前往SMC控制台，查看该迁云任务的进度，或总览您账号下所有迁移任务的整体进度。
    -   若迁移任务页面显示迁移任务状态为**已完成**，表明迁云成功。
    -   若迁移任务失败，您需要定位失败原因，修复问题并重启任务，详情请参见[查看迁移进度](cn.zh-CN/快速入门/客户端迁移/查看迁移进度.md#)。

迁云成功后，您可以前往ECS控制台镜像列表的自定义镜像页面，查看SMC为您生成的阿里云镜像，并使用该镜像创建ECS实例。详情请参见[使用自定义镜像创建实例](../../../../cn.zh-CN/实例/创建实例/使用自定义镜像创建实例.md#)。

