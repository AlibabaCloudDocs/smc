# SMC FAQ

本文介绍服务器迁移中心SMC相关的常见问题及解决方案。

-   一般性FAQ
    -   [我在什么场景下使用服务器迁移中心SMC？](#section_lqm_mcj_ht2)
    -   [服务器迁移中心SMC支持哪些迁移方式？](#section_ry6_ron_ify)
    -   [在一台物理主机数据库服务器上有单实例Oracle数据库，在向阿里云做迁移时，应该选择整台服务器（包含操作系统、数据库）迁移，还是选择数据库迁移（仅迁移数据库）？两种方式都有哪些利弊？](#section_7wr_yaq_j99)
    -   [SMC的迁移过程是什么？](#section_h30_ti7_cno)
    -   [SMC迁移所需时间如何评估？如何测试传输速度？](#section_mx1_h0s_1fv)
    -   [SMC是否支持断点续传？](#section_jas_0vg_mmr)
    -   [SMC是否支持增量迁移数据？](#section_qnr_e43_55i)
    -   [迁移中断或提示失败时，如何处理？](#section_aao_rej_1jy)
    -   [中转实例的规格有哪些？](#section_lii_mn5_7ki)
    -   [关于中转实例，我需要注意什么？](#section_vqn_j3d_190)
    -   [我的待迁移服务器需要在出方向访问哪些公网地址和端口？](#section_ora_z1t_efs)
    -   [阿里云支持激活哪些Windows Server？](#section_447_0cw_ulc)
    -   [如何安装Rsync？](#section_6ai_ig1_k06)
    -   [如何关闭SELinux？](#section_8za_stx_q0e)
-   迁移源FAQ
    -   [如何过滤、排除不需要迁移的文件或目录？](#section_9xm_osd_b9i)
-   SMC控制台FAQ
    -   [误释放了中转实例怎么办？](#section_1nu_xd1_bip)
    -   [我想要重新导入迁移源，怎么办？](#section_uez_q5r_a20)
    -   [迁移源为非在线状态时，无法创建迁移任务怎么办？](#section_weo_he3_b2a)
    -   [为什么无法删除迁移源？](#section_nu9_xbl_bad)
    -   [为什么新建迁移任务页面没有出现数据盘配置项？怎么办？](#section_nt4_qfc_tev)
    -   [迁移进行中或迁移报错时，是否可以为迁移源新建迁移任务？](#section_25p_nj0_7r5)
    -   [迁移任务多久过期？过期后会怎样？](#section_oe7_6bl_vu6)
    -   [迁移任务状态有哪些？分别表示什么？](#section_228_crt_kbx)
    -   [如何查找迁移源？](#section_7hf_tn4_x5i)
-   故障排查FAQ
    -   [日志提示子账号权限不足Forbidden.SubUser，怎么办？](#section_tqr_azb_drh)
    -   [日志提示Forbidden.Unauthorized错误，怎么办？](#section_xl0_pjl_069)
    -   [日志提示Your Account Haven't Completed Real-name Authentication错误，怎么办？](#section_7vo_kuy_s0k)
    -   [日志提示Your Account Haven't Authorized For SMC RAM Role错误，怎么办？](#section_0b6_33l_aa2)
    -   [日志提示IllegalTimestamp错误，怎么办？](#section_kg8_hvy_brj)
    -   [日志提示InvalidAccountStatus.NotEnoughBalance错误，怎么办？](#section_pxf_i43_kcs)
    -   [日志提示Forbidden.RAM错误，怎么办？](#section_5qw_dzv_7z7)
    -   [日志提示InvalidImageName.Duplicated错误，怎么办？](#section_f09_jaz_05u)
    -   [日志提示InvalidAccountStatus.SnapshotServiceUnavailable错误，怎么办？](#section_gph_ns2_acq)
    -   [日志提示Create transition vpc failed. \(QuotaExceeded.Vpc: VPC quota exceeded.\)错误，怎么办？](#section_qur_9g3_nka)
    -   [日志提示InvalidAccessKeyId.NotFound错误，怎么办？](#section_rfn_fot_g83)
    -   [日志提示Connect to Server Failed错误，怎么办？](#section_7ad_mse_m2s)
    -   [日志提示Do Rsync Disk x Failed错误，怎么办？](#section_gh1_ywk_103)
    -   [Linux服务器日志错误提示check rsync failed或者rsync not found，怎么办？](#section_i9v_jy5_513)
    -   [Linux服务器日志提示check virtio failed错误，怎么办？](#section_eji_23f_0ry)
    -   [Linux服务器日志错误提示check selinux failed，怎么办？](#section_wdz_y67_4sv)
    -   [Linux服务器日志错误提示Do Grub Failed，怎么办？](#section_284_a0c_8dl)
    -   [Windows服务器卡在Prepare For Rsync Disk 0阶段，怎么办？](#section_22e_ozc_d0w)
-   迁移后FAQ
    -   [迁移Windows服务器后，启动实例被提示需要激活Windows，怎么办？](#section_kxd_mod_x2b)
    -   [迁移Windows服务器后，启动实例发现数据盘缺失或者盘符错乱，怎么办？](#section_kxs_fqi_hz3)
    -   [迁移Windows服务器后，启动实例发现文件权限异常或部分系统菜单目录显示语言不统一，怎么办？](#section_6l1_guc_ms9)
    -   [迁移Windows服务器后怎么检查系统？](#section_c5i_33t_xn7)
    -   [迁移Linux服务器后怎么检查系统？](#section_8nx_71l_ksv)
    -   [迁移Linux服务器后，启动实例发现原数据盘目录下没有数据，怎么办？](#section_rak_i9w_gky)
    -   [迁移Linux服务器后，根据该自定义镜像创建的实例为何不能启动？](#section_4wq_e1j_can)
    -   [启动Others Linux实例后，网络服务不正常？](#section_d07_qlt_y6e)
    -   [迁移完成后，再次迁移该如何操作呢？](#section_sz6_lrl_8aa)
    -   [迁移完成得到自定义镜像后该如何操作？](#section_pd1_rka_nhr)
    -   [迁移完成后的结果是什么？](#section_203_izc_s31)
    -   [迁移后创建的ECS实例hostname依旧保留了其他云平台的名称，如何解决？](#section_6py_r5e_qgz)

## 我在什么场景下使用服务器迁移中心SMC？

SMC可将待迁移物理服务器、虚拟机以及其他云平台云主机一站式地迁移到阿里云ECS，支持迁移主流Windows和Linux操作系统。详情请参见[什么是服务器迁移中心](/cn.zh-CN/产品简介/什么是服务器迁移中心.md)。

## 服务器迁移中心SMC支持哪些迁移方式？

SMC支持控制台迁移模式。通过SMC客户端导入迁移源信息后，登录SMC控制台为迁移源创建并完成迁移任务。具体步骤，请参见[迁移流程概述](/cn.zh-CN/用户指南/迁移流程概述.md)。

## 在一台物理主机数据库服务器上有单实例Oracle数据库，在向阿里云做迁移时，应该选择整台服务器（包含操作系统、数据库）迁移，还是选择数据库迁移（仅迁移数据库）？两种方式都有哪些利弊？

请根据您的实际需要，选择迁移方式。 两种迁移方式的利弊如下：

-   如果您只需要Oracle数据库应用，则仅迁移Oracle应用更为轻量合适。缺点是您需要重新考虑Oracle应用的部署接入方式。
-   如果您既需要Oracle应用，又依赖整体操作系统的应用环境，则整体迁移服务器至阿里云更为方便。缺点是如果服务器整体量大，则迁移周期较长。

## SMC的迁移过程是什么？

SMC的迁移过程如下：

1.  将迁移源信息导入SMC控制台。
2.  SMC后台服务准备中转实例。
3.  SMC客户端传输迁移源数据至中转实例。
4.  SMC后台服务为迁移源生成目标阿里云镜像。

## SMC迁移所需时间如何评估？如何测试传输速度？

迁移周期主要分为迁移前、迁移过程中、迁移后三部分。迁移周期时长与待迁移服务器的数量和实际数据量成正比，建议您根据实际迁移测试演练进行评估。

迁移过程中所需时间的评估方法以及传输速度的测试方法，请参见[评估迁移时间与测试传输速度](/cn.zh-CN/最佳实践/评估迁移时间与测试传输速度.md)。

## SMC是否支持断点续传？

支持。数据传输中断后，重新运行客户端并重新启动迁移任务即可继续迁移。

## SMC是否支持增量迁移数据？

支持。具体操作，请参见[增量迁移源服务器](/cn.zh-CN/最佳实践/增量迁移源服务器.md)。

## 迁移中断或提示失败时，如何处理？

迁移任务中断或失败时，处理方式如下：

-   当SMC客户端程序异常退出或者迁移进度卡顿时，可以尝试重新运行SMC客户端并重启迁移任务以恢复迁移。
-   如果迁移任务状态为出错，您可以在SMC控制台查看迁移任务的日志文件，定位错误原因。

    如果问题仍未解决，建议您添加[支持钉钉群](https://wx.dingtalk.com/invite-page/weixin.html?bizSource=____source____&corpId=dingc9d6f7ff346016e135c2f4657eb6378f&inviterUid=F2460A59D575A69799372A3FA1525DE6&encodeDeptId=B924094833B5108D03A6AD1004DA0487)。更多联系方式，请参见[联系我们](/cn.zh-CN/常见问题/联系我们.md)。


## 中转实例的规格有哪些？

SMC会按下列顺序，根据库存情况，依次选择符合条件的实例规格来创建中转实例。

-   1 vCPU 2 GiB
-   1 vCPU 4 GiB
-   2 vCPU 2 GiB
-   2 vCPU 4 GiB
-   突发性能实例t6
-   突发性能实例t5
-   2 vCPU 8 GiB

如果以上实例规格均库存不足时，系统会选择其他性能和价格兼顾的实例规格。

## 关于中转实例，我需要注意什么？

有关中转实例的注意事项如下：

-   SMC自动创建、启动、停止和释放中转实例`No_Delete_SMC_Transition_Instance`。为保证顺利完成迁移任务，请勿干预中转实例的运行状态。
-   中转实例的默认安全组在入方向开放了8080和8703端口，这是中转实例的迁移服务端口，请勿修改或删除该安全组配置。
-   迁移任务完成后，中转实例会被自动释放，如果迁移失败，需要手动释放实例。释放步骤，请参见[释放实例](/cn.zh-CN/实例/管理实例/释放实例.md)。

## 我的待迁移服务器需要在出方向访问哪些公网地址和端口？

确认源服务器能访问以下服务地址和端口。

-   服务器迁移中心SMC：`https://smc.aliyuncs.com`443端口。
-   中转实例：公网IP地址8080和8703端口。当您使用**内网传输**的**网络模式**时，需访问私有IP地址。

**说明：** 源服务器不需要开放任何入方向的端口，但是需要在出方向访问上述公网地址和端口。

## 阿里云支持激活哪些Windows Server？

支持自动激活Windows Server 2003、2008、2012和2016。其他版本的Windows如果迁移至ECS，需要申请许可移动性证，详情请参见[申请许可移动性证](https://help.aliyun.com/document_detail/84749.html)。

## 如何安装Rsync？

请您根据源服务器的操作系统选择相应的命令安装Rsync。

-   CentOS：运行yum -y install rsync。
-   Ubuntu：运行apt-get -y install rsync。
-   Debian：运行apt-get -y install rsync。
-   SUSE：运行zypper install rsync。
-   其他发行平台系统：参见发行版官网的安装文档。

## 如何关闭SELinux？

建议您运行setenforce 0临时关闭SELinux，或编辑/etc/selinux/config文件设置`SELINUX=disabled`。

## 如何过滤、排除不需要迁移的文件或目录？

排除不需要迁移的文件或目录，需在运行SMC客户端之前配置。配置文件位于客户端Excludes目录下，包括以下文件。

-   系统盘配置文件：rsync\_excludes\_win.txt（Windows系统）或rsync\_excludes\_linux.txt（Linux系统）

-   数据盘配置文件：在系统盘的基础上以disk\[磁盘索引编号\]后缀命名，如rsync\_excludes\_win\_disk1.txt（Windows系统）或rsync\_excludes\_linux\_disk1.txt（Linux系统）


**说明：** 若配置文件缺失或被误删，您可自行创建相应文件。

-   配置示例一：为Windows服务器排除不迁移的文件或目录
    -   系统盘：
        -   待排除的文件或目录：

            ```
            C:\MyDirs\Docs\Words
            C:\MyDirs\Docs\Excels\Report1.txt
            ```

        -   在rsync\_excludes\_win.txt中添加内容：

            ```
            /MyDirs/Docs/Words/
            /MyDirs/Docs/Excels/Report1.txt
            ```

    -   数据盘：

        -   待排除的文件或目录：

            ```
            D:\MyDirs2\Docs2\Words2
            D:\MyDirs2\Docs2\Excels\Report2.txt
            ```

        -   在rsync\_excludes\_win\_disk1.txt中添加内容：

            ```
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

    ```
    /var/mydirs/docs/words
    /var/mydirs/docs/excels/report1.txt
    ```

-   在rsync\_excludes\_linux.txt中添加内容：

    ```
    /var/mydirs/docs/words/
    /var/mydirs/docs/excels/report1.txt
    ```

    -   数据盘：

-   待排除的文件或目录为：

    ```
    /mnt/disk1/mydirs2/docs2/words2
    /mnt/disk1/mydirs2/docs2/excels2/report2.txt
    ```

-   在rsync\_excludes\_linux\_disk1.txt中添加内容：

    ```
    /mydirs2/docs2/words2/
    /mydirs2/docs2/excels2/report2.txt
    ```

        **说明：** 排除Linux路径时需要去掉路径前缀（scr\_path），例如去掉上述示例中的/mnt/disk1。


## 我想要重新导入迁移源，怎么办？

您需要先删除迁移源后，再重新运行客户端导入迁移源。若迁移源已和迁移任务关联，请先删除与之关联的迁移任务，再删除迁移源。

## 误释放了中转实例怎么办？

如果误清理了中转资源，您可以删除当前的迁移任务，重新为迁移源新建并启动迁移任务。如果问题依然未解决，您可以[提交工单](https://workorder.console.aliyun.com/#/ticket/list/)联系客服处理该问题。

## 迁移源为非在线状态时，无法创建迁移任务怎么办？

先修复迁移源状态为在线后，再新建迁移任务。修复方法如下：

-   迁移源状态为离线：

    该状态表明迁移源已和SMC控制台失去联系。您需要重新运行SMC客户端，并且不能关闭客户端直至迁移完成。具体步骤，请参见[步骤一：导入迁移源](/cn.zh-CN/用户指南/步骤一：导入迁移源.md)。

-   迁移源状态为异常：您需要检查控制台日志、客户端日志（Logs目录下）和客户端界面显示的错误信息，根据提示处理。您也可以参考本文中的错误码及处理方法。若仍无法修复问题，请[联系我们](/cn.zh-CN/常见问题/联系我们.md)。

## 为什么无法删除迁移源？

因为迁移源关联了尚未完成的迁移任务。您需要先暂停并删除迁移任务后，再删除迁移源。

## 为什么新建迁移任务页面没有出现数据盘配置项？怎么办？

SMC客户端导入迁移源时，只会检测已挂载的磁盘分区。若您的迁移源没有数据盘，或数据盘未挂载，新建迁移任务页面便不会出现数据盘配置项。若您需要迁移未挂载的数据盘，需完成以下操作：

1.  挂载数据盘。
2.  重新运行SMC客户端。
3.  刷新SMC控制台迁移源页面后，重新打开新建迁移任务页面。

## 迁移进行中或迁移报错时，是否可以为迁移源新建迁移任务？

不可以。处理方式如下：

-   迁移源关联的迁移任务正在运行中时，先暂停并删除迁移任务后，再为迁移源新建迁移任务。
-   迁移源关联的迁移任务出错时，先删除迁移任务后，再为迁移源新建迁移任务。

## 迁移任务多久过期？过期后会怎样？

通过SMC控制台创建迁移任务时，由于控制台不提供过期时间的设置方式，因此任务的默认有效期为30天。通过CreateReplicationJob创建迁移任务时，您可根据实际需要设置任务的有效期（有效期范围为7天~90天）。API详情，请参见[CreateReplicationJob](/cn.zh-CN/API参考/迁云任务/CreateReplicationJob.md)。

迁移任务创建后，开始计算有效期。任务过期后的处理方式如下：

-   迁移任务状态为Running（运行中）时，不做处理。
-   迁移任务状态为Ready（未开始）、Stopped（已暂停）和 InError（出错）时，标记为过期状态。过期7天后，SMC自动清理迁移任务。

## 迁移任务状态有哪些？分别表示什么？

迁移任务的状态分为以下两种：

-   迁移任务主状态：迁移任务整个生命周期的状态。详情请参见[迁移任务主状态说明表](#table_njm_7xg_xep)。
-   迁移任务业务状态：迁移任务运行中（Running）的阶段状态。详情请参见[迁移任务业务状态说明表](#table_6p3_f67_5zr)。

迁移任务主状态和业务状态的关系如下图所示。

![job_status](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6949816951/p51026.png)

|迁移任务主状态|状态说明|该状态下您可以进行的操作|
|:------|:---|:-----------|
|未开始（Ready）|迁移任务已创建，未启动。|启动迁移任务。|
|运行中（Running）|迁移任务正在运行中。运行中（Running）状态不会直接显示在SMC控制台，而是以[业务状态](#table_6p3_f67_5zr)的形式展示在迁移任务的**状态**列。|等待迁移任务运行结束，或在迁移任务状态为**同步中（Syncing）**时暂停迁移任务。 **说明：** 您无法删除正在运行中的迁移任务。 |
|已暂停（Stopped）|迁移任务已暂停。|重启或删除迁移任务。|
|出错（InError）|迁移任务已失败。|查看客户端或控制台的提示信息或迁移日志，了解失败原因，修复问题。如果失败由客户端引起（如迁移源状态为离线、异常等），您需要先重启客户端，再重启迁移任务。|
|已完成（Finished）|迁移任务成功结束。|前往ECS控制台镜像列表的自定义镜像页面，查看SMC为您生成的镜像。|
|等待中（Waiting）|仅适用于增量迁移任务，表示任务在等待下一次周期性自动执行。增量迁移详情，请参见[增量迁移源服务器](/cn.zh-CN/最佳实践/增量迁移源服务器.md)。|此状态下，您可以： -   使用迁移任务已生成的镜像，创建ECS实例。
-   暂停迁移任务。
-   删除迁移任务。
-   手动增量迁移源服务器。
-   修改自动增量迁移的设置，包括迁移任务自动运行的时间间隔和任务可以保留的最大镜像数。 |
|已过期（Expired）|迁移任务已过期。|删除迁移任务。 **说明：** 迁移任务的默认有效期为30天。任务到期后，会被标记为过期状态并保存7天，7天后SMC自动清理该任务。详情请参见[迁移任务多久过期？过期后会怎样？](#section_oe7_6bl_vu6) |
|删除中（Deleting）|迁移任务删除中。|等待迁移任务删除完成，或为迁移源新建迁移任务。 **说明：** 删除迁移任务时，SMC会自动释放迁移过程中已创建的相关资源，如中转实例等。需要的时间较长，请您耐心等待。 |

|迁移任务业务状态|状态说明|该状态下您可以进行的操作|
|:-------|:---|:-----------|
|准备中（Preparing）|您启动迁移任务后，迁移任务状态即更新为准备中。|无。|
|同步中（Syncing）|迁移任务开始上传迁移源数据。|您可以暂停迁移任务。|
|处理中（Processing）|迁移任务正在制作目标镜像中。|无。|
|清除中（Cleaning）|清理中转环境，迁移任务即将完成。|无。|

## 如何查找迁移源？

查找迁移源的步骤如下：

1.  登录[SMC控制台](https://smc.console.aliyun.com/overview)。
2.  在左侧导航栏，单击**迁移源**。
3.  在迁移源页面，单击搜索框，并选择搜索项。

    搜索项包括**迁移源名称**、**迁移源ID**、**状态**和**最近一次迁移任务ID**。所有搜索项只支持精确查询。

4.  输入搜索项对应的查询值后，单击`Enter`键。

## 日志提示子账号权限不足Forbidden.SubUser，怎么办？

SMC需要使用账号访问密钥AccessKeyID和AccesKeySecret调用ECS API创建中转实例和云盘等资源，该操作属于下单操作。某些服务商账号可能不具备该权限，如果有迁移需求，可以[联系我们](/cn.zh-CN/常见问题/联系我们.md)。

## 日志提示Forbidden.Unauthorized错误，怎么办？

该错误表示您需要为当前RAM用户授予AliyunSMCFullAccess权限。授权方法，请参见[准备阿里云目标账号](/cn.zh-CN/用户指南/准备工作（迁移前必读）.md)。

## 日志提示Your Account Haven't Completed Real-name Authentication错误，怎么办？

该错误表示您的账号需要进行实名认证。实名认证的方法，请参见[准备阿里云目标账号](/cn.zh-CN/用户指南/准备工作（迁移前必读）.md)。

## 日志提示Your Account Haven't Authorized For SMC RAM Role错误，怎么办？

您需要为您的账号授予SMC Role相关权限。授权方法请参见[准备阿里云目标账号](/cn.zh-CN/用户指南/准备工作（迁移前必读）.md)。

## 日志提示IllegalTimestamp错误，怎么办？

迁移源的系统时间须和迁移源所在地域的标准时间一致。请检查迁移源的系统时间是否为正确时间。

## 日志提示InvalidAccountStatus.NotEnoughBalance错误，怎么办？

中转实例的默认计费方式为按量付费，您的支付方式余额不足时，无法顺利迁移。您需要更新账户状态后重试。按量付费详情，请参见[按量付费](/cn.zh-CN/产品定价/计费方式/按量付费.md)。

## 日志提示Forbidden.RAM错误，怎么办？

您使用的RAM账号权限不足，无法使用相关API。

您需要为RAM账号授予ECS和VPC访问权限`AliyunECSFullAccess`和`AliyunVPCFullAccess`，详情请参见[账号访问控制](/cn.zh-CN/安全/账号访问控制.md)。

## 日志提示InvalidImageName.Duplicated错误，怎么办？

您指定的参数image\_name不能与您已有的镜像名称重复。

## 日志提示InvalidAccountStatus.SnapshotServiceUnavailable错误，怎么办？

该错误表示您的账号可能未开通快照服务。开通快照服务的步骤，请参见[开通快照](/cn.zh-CN/快照/使用快照/开通快照.md)。

## 日志提示Connect to Server Failed错误，怎么办？

该错误表示无法连接中转实例。您可以按以下步骤检查：

1.  查看日志文件详细信息。
2.  依次检查：
    -   中转实例状态是否正常。
    -   本地网络服务是否正常。SMC客户端需要访问80、443、8703和8080通信端口，请确保您的服务器已经放行这些端口。
3.  问题解决后，再次运行主程序重试。

## 日志提示Create transition vpc failed. \(QuotaExceeded.Vpc: VPC quota exceeded.\)错误，怎么办？

该错误表示您的专有网络VPC超出限额。如果您没有为迁移任务设置专有网络VPC和虚拟交换机VSwitch参数，迁移任务运行过程中会自动创建中转VPC和VSwitch，迁移任务运行结束清理中转VPC和VSwitch。

每个阿里云账号在一个地域的VPC限额为10。如果您有批量迁移任务需要同时进行或目标地域的VPC数量已达到限额时，建议您在新建迁移任务时，指定VPC和VSwitch参数，以提高VPC的复用率。配置详情，请参见[迁移任务配置项说明表](/cn.zh-CN/用户指南/步骤二：创建并启动迁移任务.md) 。

VPC超出限额后，您可以通过下列一种方式处理。

-   删除现有VPC。具体步骤，请参见[删除专有网络](/cn.zh-CN/专有网络和交换机/管理专有网络/删除专有网络.md)。
-   调整VPC限额。请您[提交工单](https://workorder.console.aliyun.com/)。

## 日志提示InvalidAccessKeyId.NotFound错误，怎么办？

该错误表示您输入的访问密钥（AccessKey）不正确。您需要通过以下操作修复该错误。

1.  打开user\_config.json文件。
2.  删除访问密钥`AccessKeyId`和`AccessKeySecret`的值。
3.  保存并关闭文件。
4.  运行SMC客户端重新输入AccessKey。

## 日志提示Do Rsync Disk x Failed错误，怎么办？

该错误表示文件传输中断。您可以按以下步骤检查。

1.  查看错误日志文件详细信息。如果错误日志文件中多次出现`return: 3072`或`return: 7680`信息提示，请确认源服务器数据库服务或者容器服务是否未开启状态，例如，Oracle、MySQL、MS SQL Server、MongoDB和Docker等服务。您需要先暂停服务或者排除相关数据文件目录后再迁云。
2.  依次检查：
    -   中转实例状态是否正常。
    -   本地网络服务是否正常。SMC需要访问80、443、8703和8080通信端口，请确保您的服务器已经放行这些端口。
3.  问题解决后，再次运行主程序重试。

## Linux服务器日志错误提示check rsync failed或者rsync not found，怎么办？

请检查迁移源系统是否已安装rsync组件。安装rsync的步骤，请参见[如何安装Rsync？](#section_6ai_ig1_k06)

## Linux服务器日志提示check virtio failed错误，怎么办？

请检查迁移源系统是否已安装virtio驱动。安装virtio驱动的步骤，请参见[virtio驱动](/cn.zh-CN/镜像/自定义镜像/导入镜像/安装virtio驱动.md)。

## Linux服务器日志错误提示check selinux failed，怎么办？

请检查迁移源系统是否已禁用SElinux。禁用SELInux的操作步骤，请参见[如何关闭SELinux？](#section_8za_stx_q0e)

## Linux服务器日志错误提示Do Grub Failed，怎么办？

请确保源服务器已经安装了系统引导程序GRUB（GRand Unified Bootloader），并在安装GRUB之后重启SMC客户端和迁移任务。安装GRUB的步骤，请参见[如何为Linux服务器安装GRUB？](/cn.zh-CN/镜像/常见问题/如何为Linux服务器安装GRUB？.md)。

## Windows服务器卡在Prepare For Rsync Disk 0阶段，怎么办？

Windows 服务器迁云停在Prepare For Rsync Disk 0阶段，查看日志文件后发现显示`VssSnapshotul::VssSnapshotul GetSnapshotul Failed: 0x80042308`。此时您可以：

1.  开启Volume Shadow Copy服务。
    1.  在服务器中单击**开始**，在搜索框中输入**服务**，回车确认。
    2.  找到Volume Shadow Copy服务，单击**启动此服务**。
2.  卸载QEMU Guest Agent软件。
    1.  在服务器中单击**开始**，在搜索框中输入**服务**，回车确认。
    2.  查看是否有QEMU Guest Agent VSS Provider服务，若无该项服务，您可以直接重新运行SMC客户端。
    3.  找到卸载脚本，大概位置位于C:\\Program Files \(x86\)\\virtio\\monitor\\uninstall.bat目录，执行脚本卸载QEMU Guest Agent软件。
3.  重新运行SMC客户端。

## 迁移Windows服务器后，启动实例被提示需要激活Windows，怎么办？

您可以重装Windows KMS Client Key后通过KMS激活Windows服务。

1.  远程登录Windows实例。
2.  在[微软KMS Client Keys页面](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj612867(v%3dws.11))查询到Windows服务器对应的KMS Client Key，此处假设为xxxx-xxxx-xxxx-xxxx-xxxx。
3.  使用管理员权限打开命令行工具，依次运行以下命令：

    ```
    slmgr /upk
    ```

    ```
    slmgr /ipk xxxx-xxxx-xxxx-xxxx-xxxx
    ```

4.  使用KMS激活Windows。更多详情，请参见[VPC环境下ECS Windows系统激活方法](https://help.aliyun.com/document_detail/41056.html)。

## 迁移Windows服务器后，启动实例发现数据盘缺失或者盘符错乱，怎么办？

-   如果数据盘盘符缺失，您可以打开磁盘管理器，重新添加即可。
    1.  打开**控制面板** \> **系统与安全** \> **管理工具** \> **计算机管理**。

        ![盘符缺失1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3429816951/p13371.png)

    2.  找到并右击盘符缺失的数据盘，单击**更改驱动器和路径**。

        ![盘符缺失2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3429816951/p13372.png)

    3.  单击**添加**并添加数据盘盘符。

        ![盘符缺失3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3429816951/p13373.png)

-   如果数据盘盘符错乱，您可以打开磁盘管理器，重新更改即可。
    1.  打开**控制面板** \> **系统与安全** \> **管理工具** \> **计算机管理**。
    2.  找到并右击盘符缺失的数据盘，单击**更改驱动器和路径**。
    3.  单击**更改**并更改数据盘盘符。

        ![盘符缺失4](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4429816951/p13374.png)


## 迁移Windows服务器后，启动实例发现文件权限异常或部分系统菜单目录显示语言不统一，怎么办？

您需要等待文件系统权限修复操作成功完成。更多详情，请参见[迁移Windows服务器后怎么检查系统？](#section_c5i_33t_xn7)

## 迁移Windows服务器后怎么检查系统？

迁移Windows系统后初次启动实例时，您需要进行下列检查。

1.  检查系统盘数据是否完整。
2.  如果有数据盘缺失，进入磁盘管理检查盘符是否丢失。
3.  等待文件系统权限修复过程完成后，选择是否重启实例。

    ![windows系统检查](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6949816951/p13956.png)

    **说明：** 初次启动ECS实例后，如果文件系统权限修复程序未自启动，您可以运行C:\\go2aliyun\_prepare\\go2aliyun\_restore.exe手动修复。执行前要确保实例上的磁盘数量和盘符路径跟源系统保持一致。

4.  检查网络服务是否正常。
5.  检查其他系统应用服务是否正常。

## 迁移Linux服务器后怎么检查系统？

迁移Linux系统后初次启动实例时，您需要进行以下检查。

1.  检查系统盘数据是否完整。
2.  如果有数据盘，您需要自行挂载数据盘。详情请参见[挂载数据盘](/cn.zh-CN/块存储/云盘基础操作/挂载数据盘.md)。
3.  检查网络服务是否正常。
4.  然后检查其他系统服务是否正常。

## 迁移Linux服务器后，启动实例发现原数据盘目录下没有数据，怎么办？

迁移带有数据盘的Linux服务器后，启动实例时默认不挂载数据盘。您可以在启动ECS实例后运行ls /dev/vd\*命令查看数据盘设备，根据实际需要手动挂载，并编辑/etc/fstab配置开机自动挂载。

## 迁移Linux服务器后，根据该自定义镜像创建的实例为何不能启动？

您需要进行下列检查。

-   检查驱动。创建I/O优化的实例时，请确保源服务器已经安装[virtio驱动](/cn.zh-CN/镜像/自定义镜像/导入镜像/安装virtio驱动.md)。
-   检查源系统引导配置是否正确。
-   如果您的源服务器系统是内核版本较低的CentOS 5或者Debian 7，而且自带的GRUB程序版本低于1.9，同时在ECS控制台[远程连接](/cn.zh-CN/实例/连接实例/连接Linux实例/通过VNC远程连接登录Linux实例.md)登录实例发现开机界面如下图所示。

    ![Linux服务器启动检查](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6949816951/p50179.png)

    您需要升级GRUB系统引导程序至1.9版本以上后，重新迁移。升级GRUB的步骤，请参见[如何为Linux服务器安装GRUB？](/cn.zh-CN/镜像/常见问题/如何为Linux服务器安装GRUB？.md)。


## 启动Others Linux实例后，网络服务不正常？

导入Others Linux类型镜像时，阿里云不会对该自定义镜像所创建的实例做任何配置工作，包括相关网络配置和SSH配置等。此时，您需要自行修改系统相关网络配置。

自2018年03月31号开始，SMC客户端生成的镜像网络配置有变化，默认以DHCP（Dynamic Host Configuration Protocol）的方式获取IP地址。

## 迁移完成后，再次迁移该如何操作呢？

重新为迁移源新建并启动迁移任务。

## 迁移完成得到自定义镜像后该如何操作？

建议先使用该镜像创建一台按量付费的实例，检查系统是否正常。确认镜像可用后，选择合适您业务的实例规格，并创建一台或多台ECS实例。详情请参见[实例规格族](/cn.zh-CN/实例/实例规格族.md)和[使用向导创建实例](/cn.zh-CN/实例/创建实例/使用向导创建实例.md)。

## 迁移完成后的结果是什么？

SMC为您的迁移源生成一份自定义镜像。您可以在迁移任务页面，找到您的迁移任务，在**迁移结果**栏单击红框中的链接，可查看该自定义镜像。

![迁移结果](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6949816951/p50103.png)

## 迁移后创建的ECS实例hostname依旧保留了其他云平台的名称，如何解决？

该错误是由于ECS实例未安装、未启动cloud\_init，或cloud-init版本与阿里云平台不兼容。安装cloud-init后重启实例，hostname即可更新。具体步骤，请参见[安装cloud-init](/cn.zh-CN/镜像/自定义镜像/导入镜像/安装cloud-init.md)。

