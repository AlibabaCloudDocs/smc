# 使用SMC客户端一次性迁移模式 {#task_827230 .task}

除使用控制台迁移外，您还可以使用SMC客户端独立完成迁移，所有操作均在迁移源上完成。本文介绍如何使用客户端一次性迁移源服务器，而无需控制台操作。迁移源（或源服务器）概指您的待迁移IDC服务器、虚拟机、其他云平台的云主机或其他类型的服务器。

已完成准备工作。详情请参见[准备工作（迁移前必读）](../cn.zh-CN/用户指南/准备工作（迁移前必读）.md#)。

一次性迁移模式的基本流程如下：

1.  [下载和解压SMC客户端](#step_n8y_y2p_4li)
2.  [配置迁移源和迁移目标信息](#step_8sr_1nx_vy9)
3.  [（可选）排除不迁移的目录和文件](#step_oa6_e16_n99)
4.  [运行SMC客户端的一次性迁移模式](#step_as4_pin_hb6)

1.  下载并解压SMC客户端。 
    1.  在迁移源上，下载[SMC客户端](https://p2v-tools.oss-cn-hangzhou.aliyuncs.com/smc/Alibaba_Cloud_Migration_Tool.zip)。
    2.  解压缩SMC客户端。 SMC客户端为Windows和Linux系统均提供32位和64位版本（i386表示32位，x86\_64表示64位）。请根据迁移源的平台类型，选择相应的客户端版本。解压后的客户端文件夹，如下图所示。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630372/156196662850475_zh-CN.png)

    3.  解压缩您选择的客户端版本。 解压后文件夹中包含的目录和文件，如下图所示。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630335/156196662949979_zh-CN.png)

        |文件（夹）名|描述|
        |:-----|:-|
        |go2aliyun\_client.exe|（Windows版本）命令行主程序。|
        |go2aliyun\_gui.exe|（Windows版本） GUI主程序。GUI版本详情，请参见[使用SMC客户端Windows GUI版本](../cn.zh-CN/最佳实践/使用SMC客户端Windows GUI版本.md#)。|
        |go2aliyun\_client|（Linux版本）命令行主程序。|
        |user\_config.json|迁移源和迁移目标的配置文件。|
        |Excludes|排除不迁移文件目录的配置文件夹。|
        |client\_data|迁移数据文件，包含ECS中转实例信息和迁移进度等。|

2.  配置迁移源和迁移目标信息。 
    1.  打开user\_config.json文件。 以下为user\_config.json文件的初始状态。

        ``` {#codeblock_klu_ukb_nby}
        {
            "access_id": "",
            "secret_key": "",
            "region_id": "",
            "image_name": "",
            "system_disk_size": -1,
            "platform": "",
            "data_disks": [],
            "bandwidth_limit": 0
        }
        ```

    2.  根据[迁移参数配置说明表](#table_wej_b1q_027)和[数据盘参数配置说明表](#table_b52_fiy_2vv)，配置迁移源和迁移目标信息。 

        |参数名|类型|是否必填|描述|
        |:--|:-|:---|:-|
        |access\_id|String|是|您阿里云账号或子账号的访问密钥AccessKeyId。更多详情，请参见[创建AccessKey](../../../../../cn.zh-CN/通用参考/创建AccessKey.md#)。|
        |secret\_key|String|是|您阿里云账号或子账号的访问密钥AccessKeySecret。更多详情，请参见[创建AccessKey](../../../../../cn.zh-CN/通用参考/创建AccessKey.md#)。|
        |region\_id|String|是|您的迁移源需要迁入的阿里云地域ID。更多地域ID取值，请参见[地域与可用区](../../../../../cn.zh-CN/通用参考/地域和可用区.md#)。|
        |image\_name|String|是|SMC为您的迁移源生成的目标阿里云镜像名称。取值要求：         -   不能与同一地域下现有镜像名重复。
        -   长度为 2~128 个英文或中文字符，必须以大小字母或中文开头，不能以 http:// 和 https:// 开头，可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。
 |
        |system\_disk\_size|Integer|是|目标阿里云服务器ECS的系统盘大小，单位为GiB。取值范围：\[20, 500\] **说明：** 该参数取值需要大于迁移源系统盘实际占用大小，例如，迁移源的系统盘大小为500 GiB，实际占用100 GiB，则该参数取值大于100 GiB即可。

 |
        |platform|String|否|迁移源的操作系统。取值范围：Windows Server 2003 | Windows Server 2008 | Windows Server 2012 | Windows Server 2016 | CentOS | Ubuntu | SUSE | OpenSUSE | Debian | RedHat | Others Linux **说明：** 参数 `platform` 的取值需要与以上列表保持一致，必须区分大小写，并保持空格一致。

 |
        |bandwidth\_limit|Integer|否|迁移过程中，数据传输的带宽上限限制，单位为KB/s。 默认值：0，表示不限制带宽速度。

 |
        |data\_disks|Array|否|目标阿里云服务器ECS的数据盘列表，最多支持16块数据盘。数据盘的具体参数，请参见[数据盘配置参数说明](#table_b52_fiy_2vv)。|

        |参数名|类型|是否必填|描述|
        |:--|:-|:---|:-|
        |data\_disk\_index|Integer|是|目标阿里云服务器ECS的数据盘序号。取值范围：\[1, 16\] 初始值：1

 |
        |data\_disk\_size|Integer|是|目标阿里云服务器ECS的数据盘大小。单位为GiB。取值范围：\[20, 32768\] **说明：** 该参数取值需要大于迁移源数据盘实际占用大小。例如，迁移源的数据盘大小为500 GiB，实际占用100 GiB，则该参数取值需大于100 GiB。

 |
        |src\_path|String|是|迁移源的数据盘目录。取值举例：         -   Windows指定盘符，例如，`D:`、`E:`或者`F:`。
        -   Linux指定目录，例如，/mnt/disk1、/mnt/disk2或者/mnt/disk3。

**说明：** 不能配置为根目录或者系统目录。例如，禁止配置为/bin、/boot、/dev、/etc、/lib、/lib64、/sbin、/usr和/var。

 |

        -   配置示例一：迁移一台无数据盘的Windows服务器到阿里云华东1（杭州）地域

            -   假设源服务器配置信息为：
                -   操作系统：Windows Server 2008
                -   系统盘：30 GiB
            -   迁移目标为：
                -   目标地域：阿里云华东1地域（`cn-hangzhou`）
                -   镜像名称：CLIENT\_IMAGE\_WIN08\_01
                -   系统盘设置：50 GiB
            ``` {#codeblock_l2p_mew_sve}
            {
                "access_id": "YourAccessKeyID",
                "secret_key": "YourAccessKeySecret",
                "region_id": "cn-hangzhou",
                "image_name": "CLIENT_IMAGE_WIN08_01",
                "system_disk_size": 50,
                "platform": "Windows Server 2008",
                "data_disks": [],
                "bandwidth_limit": 0
            }
            ```

        -   配置示例二：迁移一台带数据盘的Windows服务器到阿里云华东1（杭州）地域

            在配置示例一的基础上加入了2块数据盘，数据盘目录和大小分别为：

            -   源数据盘分区信息：
                -   D：50 GiB
                -   E：100 GiB
            -   目标数据盘分区信息：
                -   D：100 GiB
                -   E：150 GiB
            ``` {#codeblock_srh_1ou_ymx}
            {
                "access_id": "YourAccessKeyID",
                "secret_key": "YourAccessKeySecret",
                "region_id": "cn-hangzhou",
                "image_name": "CLIENT_IMAGE_WIN08_01",
                "system_disk_size": 50,
                "platform": "Windows Server 2008",
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

        -   配置示例三：迁移一台无数据盘的Linux服务器到阿里云华东1（杭州）地域

            -   假设源服务器配置信息为：
                -   发行版本：CentOS 7.2
                -   系统盘：30 GiB
            -   迁移目标为：
                -   目标地域：阿里云华东1地域（`cn-hangzhou`）
                -   镜像名称：CLIENT\_IMAGE\_CENTOS72\_01
                -   系统盘设置：50 GiB
            ``` {#codeblock_ha5_o4o_zub}
            {
                "access_id": "YourAccessKeyID",
                "secret_key": "YourAccessKeySecret",
                "region_id": "cn-hangzhou",
                "image_name": "CLIENT_IMAGE_CENTOS72_01",
                "system_disk_size": 50,
                "platform": "CentOS",
                "data_disks": [],
                "bandwidth_limit": 0
            }
            ```

        -   配置示例四：迁移一台有数据盘的Linux服务器到阿里云华东1（杭州）地域

            在配置示例三的基础上加入了2块数据盘，数据盘目录和大小分别为：

            -   源数据盘分区信息：
                -   /mnt/disk1：50 GiB
                -   /mnt/disk2：100 GiB
            -   目标数据盘分区信息：
                -   /mnt/disk1：100 GiB
                -   /mnt/disk2：150 GiB
            ``` {#codeblock_a55_jh4_i94}
            {
                "access_id": "YourAccessKeyID",
                "secret_key": "YourAccessKeySecret",
                "region_id": "cn-hangzhou",
                "image_name": "CLIENT_IMAGE_CENTOS72_01",
                "system_disk_size": 50,
                "platform": "CentOS",
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

3.  （可选）排除不迁移的文件或目录。 配置文件在SMC客户端的Excludes目录下，包括以下文件：

    -   系统盘配置文件：rsync\_excludes\_win.txt（Windows系统）或rsync\_excludes\_linux.txt（Linux系统）

    -   数据盘配置文件：在系统盘的基础上以disk\[磁盘索引编号\]后缀命名，如rsync\_excludes\_win\_disk1.txt（Windows系统）或rsync\_excludes\_linux\_disk1.txt（Linux系统）

    **说明：** 若配置文件缺失或被误删，您可自行创建相应文件。

    -   配置示例一：为Windows服务器排除不迁移的文件或目录
        -   系统盘：
            -   待排除的文件或目录：

                ``` {#codeblock_3t6_0ms_qg4}
                C:\MyDirs\Docs\Words
                C:\MyDirs\Docs\Excels\Report1.txt
                ```

            -   在rsync\_excludes\_win.txt中添加内容：

                ``` {#codeblock_okd_vsu_4tr}
                /MyDirs/Docs/Words/
                /MyDirs/Docs/Excels/Report1.txt
                ```

        -   数据盘：

            -   待排除的文件或目录：

                ``` {#codeblock_bob_ob5_vwj}
                D:\MyDirs2\Docs2\Words2
                D:\MyDirs2\Docs2\Excels\Report2.txt
                ```

            -   在rsync\_excludes\_win\_disk1.txt中添加内容：

                ``` {#codeblock_qe6_bot_smu}
                /MyDirs2/Docs2/Words2/
                /MyDirs2/Docs2/Excels2/Report2.txt
                ```

            **说明：** 

            排除Windows路径时，您需要：

            -   去掉路径前缀（scr\_path），例如去掉上述示例中的`D:`。
            -   将原路径中的`\`替换为`/`。
    -   配置示例二：为Linux服务器排除不迁移的文件或目录
        -   系统盘（根目录 /）：

-   待排除的文件或目录为：

    ``` {#codeblock_tb7_2z3_1nq}
    /var/mydirs/docs/words
    /var/mydirs/docs/excels/report1.txt
    ```

-   在rsync\_excludes\_linux.txt中添加内容：

    ``` {#codeblock_zce_114_yii}
    /var/mydirs/docs/words/
    /var/mydirs/docs/excels/report1.txt
    ```

        -   数据盘：

-   待排除的文件或目录为：

    ``` {#codeblock_utm_f1l_t3o}
    /mnt/disk1/mydirs2/docs2/words2
    /mnt/disk1/mydirs2/docs2/excels2/report2.txt
    ```

-   在rsync\_excludes\_linux\_disk1.txt中添加内容：

    ``` {#codeblock_8uy_yq7_dib}
    /mydirs2/docs2/words2/
    /mydirs2/docs2/excels2/report2.txt
    ```

            **说明：** 排除Linux路径时需要去掉路径前缀（scr\_path），例如去掉上述示例中的/mnt/disk1。

4.  运行SMC客户端的一次性迁移模式。 

    -   Windows系统 ：选择以下任一方式运行。
        -   GUI版本

            1.  双击运行主程序go2aliyun\_gui.exe。
            2.  单击**配置** \> **一次性迁移模式**。
            3.  单击**确定**。
            4.  单击**运行**。
            **说明：** 程序运行时会提示需要管理员权限，单击**确定**即可。

        -   命令行版本
            1.  打开cmd窗口。
            2.  进入go2aliyun\_client.exe所在目录。
            3.  运行`go2aliyun_client.exe --onetime`命令。
    -   Linux服务器：根据迁移源操作系统对root权限和sudo权限的支持情况，选择运行方式。
        -   在go2aliyun\_client所在目录下，使用root权限依次运行以下命令。

            ``` {#codeblock_ufy_4so_jpa}
            chmod +x ./go2aliyun_client --onetime
            ```

            ``` {#codeblock_38g_164_grm}
            ./go2aliyun_client --onetime
            ```

        -   在go2aliyun\_client所在目录下，使用sudo权限依次运行以下命令。

            ``` {#codeblock_zdg_8wd_rd8}
            sudo chmod +x ./go2aliyun_client --onetime
            ```

            ``` {#codeblock_617_zpk_432}
            sudo ./go2aliyun_client --onetime
            ```

    运行SMC客户端后，您无需其他操作，请耐心等待迁移完成。客户端会获取迁移源的CPU核数、内存大小以及各自的使用率信息并打印在客户端界面上。同时迁移状态会以流式日志的形式打印在客户端界面上。


-   当客户端界面提示`Goto Aliyun Finished!`时，表示迁移成功，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/668852/156196662950084_zh-CN.png)

    此时，您可以：

    1.  前往[ECS管理控制台镜像详情页](https://ecs.console.aliyun.com/#/image/region/cn-hangzhou/imageList)，选择您预设的目标阿里云地域，查看生成的自定义镜像。
    2.  [使用该自定义镜像创建按量付费ECS实例](../cn.zh-CN/实例/创建实例/使用自定义镜像创建实例.md#)或者[使用自定义镜像更换系统盘](../cn.zh-CN/块存储/云盘/更换系统盘/更换系统盘（非公共镜像）.md#)，测试自定义镜像能否正常运行。

        **说明：** 使用自定义镜像更换实例系统盘时，只支持不带数据盘的自定义镜像。

    3.  远程连接实例，检查迁移后的系统，详情请参见[迁移Windows服务器后怎么检查系统？](../cn.zh-CN/常见问题/SMC FAQ.md#section_c5i_33t_xn7)或[迁移Linux服务器后怎么检查系统？](../cn.zh-CN/常见问题/SMC FAQ.md#section_8nx_71l_ksv)。
-   当客户端界面提示`Goto Aliyun Not Finished!`时，表示迁移失败，如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/668852/156196662950085_zh-CN.png)

    此时，您需要：

    1.  检查客户端Logs目录下日志文件中的报错提示，修复问题。常见问题的修复方案，请参见[SMC FAQ](../cn.zh-CN/常见问题/SMC FAQ.md#)。
    2.  重新运行SMC客户端，客户端会从上一次结束的进度处继续迁移。

        **说明：** 如果中转实例已被释放，则需要重新迁移，请参见[释放了中转实例怎么办](../../../../../cn.zh-CN/迁移服务/P2V 迁云工具/迁云工具FAQ.md#Release)和[什么时候需要清理client\_data文件](../../../../../cn.zh-CN/迁移服务/P2V 迁云工具/迁云工具FAQ.md#ClearClient_data)。


