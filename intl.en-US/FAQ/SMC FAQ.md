# SMC FAQ {#concept_610474 .concept}

This topic describes common problems in SMC and their solutions.

-   General FAQ
    -   [What scenarios can I use SMC for?](#section_lqm_mcj_ht2)
    -   [What migration methods are supported by SMC?](#section_ry6_ron_ify)
    -   [I have a single Oracle database instance on a physical database server. Should I migrate the entire server \(including the operating system and database\) or only the database to Alibaba Cloud? What are the advantages and disadvantages of the two methods?](#section_7wr_yaq_j99)
    -   [What is the migration process of SMC?](#section_h30_ti7_cno)
    -   [Does SMC support resumable data transfer?](#section_jas_0vg_mmr)
    -   [Does SMC support incremental migration of data?](#section_qnr_e43_55i)
    -   [What do I do if a migration is interrupted or fails?](#section_aao_rej_1jy)
    -   [What specifications are available for intermediate instances?](#section_lii_mn5_7ki)
    -   [What do I need to know about intermediate instances?](#section_vqn_j3d_190)
    -   [Which public IP addresses and ports does my source server need to access in the outbound direction?](#section_ora_z1t_efs)
    -   [Which Windows Server licenses does Alibaba Cloud support?](#section_447_0cw_ulc)
    -   [How do I install Rsync?](#section_6ai_ig1_k06)
    -   [How do I disable SELinux?](#section_8za_stx_q0e)
-   Migration source FAQ
    -   [How do I filter and exclude files or directories that do not need to be migrated?](#section_9xm_osd_b9i)
-   SMC console FAQ
    -   [What do I do if I released an intermediate instance by mistake?](#section_1nu_xd1_bip)
    -   [What do I do if I want to re-import a migration source?](#section_uez_q5r_a20)
    -   [What do I do if I cannot create a migration task for a migration source in an inactive state?](#section_weo_he3_b2a)
    -   [Why cannot I delete a migration source?](#section_nu9_xbl_bad)
    -   [Why no data disk parameters are displayed in the Create Migration Task right-side pane? How can this problem be solved?](#section_nt4_qfc_tev)
    -   [Can I create a new migration task for a migration source while the migration source is being migrated or if an error occurs during the migration?](#section_25p_nj0_7r5)
    -   [What is the validity period of a migration task? What will happen after the task expires?](#section_oe7_6bl_vu6)
    -   [What are the migration task states? What do they mean?](#section_228_crt_kbx)
    -   [How do I find a migration source?](#section_7hf_tn4_x5i)
-   Troubleshooting FAQ
    -   [Why have I received a "Forbidden.Subuser" error message?](#section_tqr_azb_drh)
    -   [Why have I received a "Forbidden.Unauthorized" error message?](#section_xl0_pjl_069)
    -   [Why have I received a "Your Account Hasn't Completed Real-name Authentication" error message?](#section_7vo_kuy_s0k)
    -   [Why have I received a "Your Account Doesn't Have Enough RAM Authority For SMC" error message?](#section_0b6_33l_aa2)
    -   [Why have I received an "IllegalTimestamp" error message?](#section_kg8_hvy_brj)
    -   [Why have I received an "InvalidAccountStatus.NotEnoughBalance" error message?](#section_pxf_i43_kcs)
    -   [Why have I received a "Forbidden.RAM" error message?](#section_5qw_dzv_7z7)
    -   [Why have I received an "InvalidImageName.Duplicated" error message?](#section_f09_jaz_05u)
    -   [Why have I received an "InvalidAccountStatus.SnapshotServiceUnavailable" error message?](#section_gph_ns2_acq)
    -   [Why have I received a "Create transition vpc failed \(QuotaExceeded.Vpc: VPC quota exceeded.\)" error message?](#section_qur_9g3_nka)
    -   [Why have I received an "InvalidAccessKeyId.NotFound" error message?](#section_rfn_fot_g83)
    -   [Why have I received a "Connect to Server Failed" error message?](#section_7ad_mse_m2s)
    -   [Why have I received a "Do Rsync Disk x Failed" error message?](#section_gh1_ywk_103)
    -   [Why have I received a "check rsync failed" or "rsync not found" error message on my Linux server?](#section_i9v_jy5_513)
    -   [Why have I received a "check virtio failed" error message on my Linux server?](#section_eji_23f_0ry)
    -   [Why have I received a "check selinux failed" error message on my Linux server?](#section_wdz_y67_4sv)
    -   [Why have I received a "Do Grub Failed" error message on my Linux server?](#section_284_a0c_8dl)
    -   [What do I do if Windows server migration stops at the "Prepare For Rsync Disk 0" stage?](#section_22e_ozc_d0w)
-   After-migration FAQ
    -   [What do I do if the system prompts me to activate Windows after a Windows server migration?](#section_kxd_mod_x2b)
    -   [What do I do if the drive letters of data disks are missing or incorrect after a Windows server migration?](#section_kxs_fqi_hz3)
    -   [After a Windows server is migrated, the file system access permission is found to be abnormal or some system menus are displayed in different languages at instance startup. What do I do?](#section_6l1_guc_ms9)
    -   [How can I check my system after migrating a Windows server?](#section_c5i_33t_xn7)
    -   [How can I check my system after migrating a Linux server?](#section_8nx_71l_ksv)
    -   [Why no data is found in the original data disk directory at instance startup after a Linux server migration?](#section_rak_i9w_gky)
    -   [Why cannot I start the ECS instance that is created based on the custom image generated after a Linux server migration?](#section_4wq_e1j_can)
    -   [What do I do if network service is abnormal when Others Linux instances are started?](#section_d07_qlt_y6e)
    -   [How do I perform another migration of the same migration source?](#section_sz6_lrl_8aa)
    -   [What do I do after a migration is complete and a custom image has been generated?](#section_pd1_rka_nhr)
    -   [What happens after a migration is complete?](#section_203_izc_s31)
    -   [The hostname of the ECS instance created after a migration still contains the name of another cloud platform. How can this problem be solved?](#section_6py_r5e_qgz)

## What scenarios can I use SMC for? {#section_lqm_mcj_ht2 .section}

SMC can migrate data from physical servers, virtual machines, and other cloud platform hosts to Alibaba Cloud ECS for most Windows and Linux operating systems. For more information, see [What is SMC?](../reseller.en-US/Product Introduction/What is SMC?.md#).

## What migration methods are supported by SMC? {#section_ry6_ron_ify .section}

SMC supports two migration modes: Daemon mode and one-time job mode.

-   Daemon mode: Import migration source information through the SMC client, and then log on to the SMC console to create and complete a migration task for the migration source. For detailed steps, see [Migration process](../reseller.en-US/User Guide/Migration process.md#).
-   One-time migration mode: Configure the migration parameters in the SMC client. You can then run the client to migrate the source server to Alibaba Cloud without performing further operations from the SMC console. For detailed steps, see [Use the SMC client in one-time job mode](../reseller.en-US/Best Practices/Use the SMC client in one-time job mode.md#).

## I have a single Oracle database instance on a physical database server. Should I migrate the entire server \(including the operating system and database\) or only the database to Alibaba Cloud? What are the advantages and disadvantages of the two methods? {#section_7wr_yaq_j99 .section}

Select a migration method based on your actual needs. The two migration methods have the following advantages and disadvantages:

-   If you only need a database application, it is better to only migrate the application. However, you may need to consider how to deploy the application in the new environment.
-   If you need both the application and its operating environment, it is better to migrate the entire server to Alibaba Cloud. However, this migration may take a long time to complete if the server has a large volume of resources.

## What is the migration process of SMC? {#section_h30_ti7_cno .section}

The migration process of SMC is as follows:

1.  You import migration source information to the SMC console.
2.  The SMC back-end service prepares the intermediate instance.
3.  The SMC client transfers the migration source information to the intermediate instance.
4.  The SMC back-end service generates a target Alibaba Cloud image for the migration source.

## Does SMC support resumable data transfer? {#section_jas_0vg_mmr .section}

Yes. SMC supports resumable data transfer. If data transfer is interrupted, you can resume the migration by re-running the client and restarting the migration task.

## Does SMC support incremental migration of data? {#section_qnr_e43_55i .section}

No. Incremental data migration is not allowed. We recommend that you stop applications such as databases and container services, or use the Excludes directory of the SMC client to configure related application directories to be excluded from migration. Synchronize any data related to those applications after the migration has been completed. For more information about how to exclude directories, see [How do I filter and exclude files or directories that do not need to be migrated?](#section_9xm_osd_b9i)

## What do I do if a migration is interrupted or fails? {#section_aao_rej_1jy .section}

-   When the SMC client program suddenly closes or becomes frozen, you can try to re-run the SMC client and restart the migration task to resume the migration.
-   If the migration is interrupted or fails, you can check the log file of the migration task in the SMC console to locate the cause of the error.

    If the problem persists, we recommend that you join the [SMC support group on DingTalk](https://h5.dingtalk.com/invite-page/index.html?spm=a2c4g.11186623.2.31.x8X0fd&code=ca190154ff). For more contact information, see [Contact us](reseller.en-US/FAQ/Contact us.md#).


## What specifications are available for intermediate instances? {#section_lii_mn5_7ki .section}

When creating an intermediate instance, SMC selects instance specifications that meet requirements from the following options. However, you cannot create a burstable performance instance \(t5\) as an intermediate instance.

-   1 vCPU 2 GiB
-   1 vCPU 4 GiB
-   2 vCPU 2 GiB
-   2 vCPU 4 GiB

## What do I need to know about intermediate instances? {#section_vqn_j3d_190 .section}

Take note of the following points for intermediate instances:

-   SMC automatically creates, starts, stops, and releases intermediate instance `No_Delete_SMC_Transition_Instance`. To ensure that the migration goes smoothly, do not perform operations on the intermediate instance.
-   The default security group of the intermediate instance allows inbound access to ports 8080 and 8703. Do not modify or delete these security group rules.
-   After the migration is complete, the intermediate instance is automatically released. If the migration fails, you have to manually release the instance. For more information about how to release an intermediate instance, see [Release an instance](../reseller.en-US/Instances/Manage instances/Release an instance.md#).

## Which public IP addresses and ports does my source server need to access in the outbound direction? {#section_ora_z1t_efs .section}

Check whether the source server can access the following service endpoints and ports:

-   SMC: `https://smc.aliyuncs.com`: 443.
-   Intermediate instance: ports 8080 and 8703 corresponding to public IP addresses. To perform a VPC-based migration, you must access the private IP address of the intermediate instance. For more information about VPC-based migration, see [Migrate to the cloud through Alibaba Cloud VPC](../../reseller.en-US/Migration Service/Cloud Migration tool for P2V and V2V/Migrate to the cloud through Alibaba Cloud VPC.md#).

**Note:** The source server does not need to open any inbound ports, but it must have outbound access to the public IP addresses and ports.

## Which Windows Server licenses does Alibaba Cloud support? {#section_447_0cw_ulc .section}

Alibaba Cloud supports licenses for Windows Server 2003, 2008, 2012, and 2016.

## How do I install Rsync? {#section_6ai_ig1_k06 .section}

Select the appropriate command to install Rsync based on the operating system of your source server.

-   CentOS: Run the yum -y install rsync command.
-   Ubuntu: Run the apt-get -y install rsync command.
-   Debian: Run the apt-get -y install rsync command.
-   SUSE: Run the zypper install rsync command.
-   Other system release versions: see the installation documentation on the official website.

## How do I disable SELinux? {#section_8za_stx_q0e .section}

We recommend that you run the setenforce 0 command to temporarily disable SELinux, or open the /etc/selinux/config file and set `SELINUX = disabled`.

## How do I filter and exclude files or directories that do not need to be migrated? {#section_9xm_osd_b9i .section}

You must configure files or directories to be excluded from migration before running the SMC client. The following configuration files are located in the Excludes directory of the client.

-   A system disk configuration file: rsync\_excludes\_win.txt \(for Windows servers\) or rsync\_excludes\_linux.txt \(for Linux servers\)

-   A data disk configuration file: named by adding a suffix disk \[disk index number\] to the system disk, such as rsync\_excludes\_win\_disk1.txt \(for Windows servers\) or rsync\_excludes\_linux\_disk1.txt \(for Linux servers\).


**Note:** If a configuration file is lost or deleted by accident, you can create another one.

-   Example 1: Exclude files or directories from migration of a Windows Server
    -   System disk:
        -   Specify the files or directories to be excluded:

            ``` {#d7e706}
            C:\MyDirs\Docs\Words
            C:\MyDirs\Docs\Excels\Report1.txt
            ```

        -   Add the following information to the rsync\_excludes\_win.txt file:

            ``` {#d7e715}
            /MyDirs/Docs/Words/
            /MyDirs/Docs/Excels/Report1.txt
            ```

    -   Data disk:

        -   Specify the files or directories to be excluded:

            ``` {#d7e727}
            D:\MyDirs2\Docs2\Words2
            D:\MyDirs2\Docs2\Excels\Report2.txt
            ```

        -   Add the following information to the rsync\_excludes\_win\_disk1.txt file:

            ``` {#d7e736}
            /MyDirs2/Docs2/Words2/
            /MyDirs2/Docs2/Excels2/Report2.txt
            ```

        **Note:** 

        To exclude a Windows directory, you must perform the following operations:

        -   Remove the prefix of the directory \(scr\_path\). In the preceding example, you must remove `D:`.
        -   Replace `\` with `/`.
-   Example 2: Exclude files or directories from migration of a Linux server
    -   System disk \(root directory/\):

-   Specify the files or directories to be excluded:

    ``` {#d7e783}
    /var/mydirs/docs/words
    /var/mydirs/docs/excels/report1.txt
    ```

-   Add the following information to the rsync\_excludes\_linux.txt file:

    ``` {#d7e792}
    /var/mydirs/docs/words/
    /var/mydirs/docs/excels/report1.txt
    ```

    -   Data disk:

-   Specify the files or directories to be excluded:

    ``` {#d7e807}
    /mnt/disk1/mydirs2/docs2/words2
    /mnt/disk1/mydirs2/docs2/excels2/report2.txt
    ```

-   Add the following information to the rsync\_excludes\_linux\_disk1.txt file:

    ``` {#d7e816}
    /mydirs2/docs2/words2/
    /mydirs2/docs2/excels2/report2.txt
    ```

        **Note:** To exclude a Linux directory, you must remove the prefix of the directory \(scr\_path\). In the preceding example, you must remove /mnt/disk1.


## What do I do if I want to re-import a migration source? {#section_uez_q5r_a20 .section}

You must delete the migration source and then re-run the client to import the migration source. If the migration source is associated with a migration task, you must delete the associated migration task before you can delete the migration source.

## What do I do if I released an intermediate instance by mistake? {#section_1nu_xd1_bip .section}

If you have released an intermediate instance by mistake, you can delete the current migration task, and then create and start a new migration task for the migration source. If the problem persists, you can [submit a ticket](https://workorder.console.aliyun.com/#/ticket/list/) or contact customer service to solve the problem.

## What do I do if I cannot create a migration task for a migration source in an inactive state? {#section_weo_he3_b2a .section}

Restore the migration source to the Active state, and then create a migration task. The restoration method is as follows:

-   When the migration source is in an inactive state:

    This status indicates that the migration source has been disconnected from the SMC console. You must re-run the SMC client and wait until the migration is complete before you can close the client. For detailed steps, see [Step 1: Import migration source information](../reseller.en-US/User Guide/Step 1: Import migration source information.md#).

-   When the migration source is in an abnormal state: You must check the console and client logs in the Logs directory and the error message displayed on the client interface, and fix the error as prompted. You can also refer to the error codes and troubleshooting methods in this topic. If the problem persists, [Contact us](reseller.en-US/FAQ/Contact us.md#).

## Why cannot I delete a migration source? {#section_nu9_xbl_bad .section}

The migration source is in use by an unfinished migration task. You must stop and delete the migration task before you can delete the migration source.

## Why no data disk parameters are displayed in the Create Migration Task right-side pane? How can this problem be solved? {#section_nt4_qfc_tev .section}

When you import a migration source, the SMC client only detects partitions of attached disks. If your migration source does not have a data disk or no data disk is attached, the data disk parameters will not be displayed in the Create Migration Task right-side pane. To migrate a data disk that is not attached to an instance, perform the following steps:

1.  Attach the data disk.
2.  Re-run the SMC client.
3.  Refresh the Migration Sources page in the SMC console, and bring up the Create Migration Task right-side pane again.

## Can I create a new migration task for a migration source while the migration source is being migrated or if an error occurs during the migration? {#section_25p_nj0_7r5 .section}

No. The steps you can take in the preceding two scenarios are as follows:

-   If the migration source is associated with a running migration task, stop and delete the migration task, and then create a new migration task for the migration source.
-   If the migration task associated with a migration source experiences an error, delete the migration task and then create a new migration task for the migration source.

## What is the validity period of a migration task? What will happen after the task expires? {#section_oe7_6bl_vu6 .section}

When you create a migration task in the SMC console, the default validity period of the task is 30 days. The expiration time cannot be set from the console. When calling the CreateReplicationJob operation to create a migration task, you can set the task validity period as needed. The validity period ranges from 7 to 90 days. For more information about the operation, see [CreateReplicationJob](../reseller.en-US/API Reference/Migration tasks/CreateReplicationJob.md#).

The validity period starts from when the migration task is created. The processing method after the task expires is as follows:

-   When the migration task is in the Running state, no further processing is required.
-   When the migration task is in the Ready, Stopped, or InError state, it is marked as expired. Seven days after expiration, SMC will clear the migration task.

## What are the migration task states? What do they mean? {#section_228_crt_kbx .section}

The status of a migration task is divided into the following two types:

-   Migration task status: the status of the migration task throughout its entire lifecycle. For more information, see [Migration task status](#table_njm_7xg_xep).
-   Migration task business status: the status of the migration task in the Running stage. For more information, see [Migration task business status](#table_6p3_f67_5zr).

The following figure shows the relationship between the migration task status and business status.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/490278/156630279851026_en-US.png)

|Migration task status|Description|Operation that can be performed in this state|
|:--------------------|:----------|:--------------------------------------------|
|Ready|The migration task has been created but has not been started.|Start the migration task.|
|Running|The migration task is running. Instead of being displayed in the SMC console, the running status is displayed in the **Status** column in the form of [business status](#table_6p3_f67_5zr).|Stop the migration task when it is complete or when its status is **Syncing**. **Note:** You cannot delete a running migration task.

 |
|Stopped|The migration task has been stopped.|Restart or delete the migration task.|
|InError|The migration task has failed.|View the error message or migration logs of the client or console to learn the cause of the failure and fix the problem. If the migration failed as a result of an inactive or abnormal migration source in the client, restart the client before restarting the migration task.|
|Finished|The migration task is finished.|Go to the Custom Images tab in the ECS console to view the image generated by SMC.|
|Expired|The migration task has expired.|Delete the migration task. **Note:** By default, the migration task is valid for 30 days. When the task expires, it is marked as expired and then retained for seven days. After seven days, SMC clears the task. For more information, see [What is the validity period of a migration task? What will happen after the task expires?](#section_oe7_6bl_vu6)

 |
|Deleting|The migration task is being deleted.|Wait until the migration task is deleted, or create a new migration task for the migration source. **Note:** After a migration task is deleted, SMC releases related resources that have been created during the migration process, such as the intermediate instance. This process may take a while to complete.

 |

|Migration task business status|Description|Operation that can be performed in this state|
|:-----------------------------|:----------|:--------------------------------------------|
|Preparing|When you start the migration task, the status of the migration task becomes Preparing.|None|
|Syncing|The migration task is uploading the migration source data.|You can stop the migration task.|
|Processing|The migration task is creating the target image.|None|
|Cleaning|The intermediate instance is being cleared, and the migration task is about to be completed.|None|

## How do I find a migration source? {#section_7hf_tn4_x5i .section}

To find the migration source, perform the following steps:

1.  Log on to the SMC console.
2.  In the left-side navigation pane, click **Migration Sources**.
3.  On the Migration Sources page that appears, click the search box and select a search item from the drop-down list.

    Search items include **Migration Source Name**, **Migration Source ID**, **Status**, and **Latest Migration Task ID**. All searches will return results that are an exact match to the input parameters.

4.  Enter a value for the selected search item, and press `Enter`.

## Why have I received a "Forbidden.Subuser" error message? {#section_tqr_azb_drh .section}

SMC must use the account AccessKey ID and AccesKey Secret to call the ECS API and create resources such as intermediate instances and cloud disks, which requires additional authorizations. Some service provider accounts may not have permission to create instances. If you need to migrate resources, you can [Contact us](reseller.en-US/FAQ/Contact us.md#).

## Why have I received a "Forbidden.Unauthorized" error message? {#section_xl0_pjl_069 .section}

This error indicates that you must grant full access permission on SMC to the current RAM user. For more information about the authorization method, see [Prepare an Alibaba Cloud account](../reseller.en-US/User Guide/Preparations (before you start).md#section_1yg_nf4_rco).

## Why have I received a "Your Account Hasn't Completed Real-name Authentication" error message? {#section_7vo_kuy_s0k .section}

This error indicates that your account requires real-name authentication. For more information about the real-name authentication method, see [Prepare an Alibaba Cloud account](../reseller.en-US/User Guide/Preparations (before you start).md#section_1yg_nf4_rco).

## Why have I received a "Your Account Doesn't Have Enough RAM Authority For SMC" error message? {#section_0b6_33l_aa2 .section}

Your account must be granted SMC role-related permissions. For more information about the authorization method, see [Prepare an Alibaba Cloud account](../reseller.en-US/User Guide/Preparations (before you start).md#section_1yg_nf4_rco).

## Why have I received an "IllegalTimestamp" error message? {#section_kg8_hvy_brj .section}

The system time of a migration source must be consistent with the standard time of the region where the migration source is located. Check whether the system time is configured correctly.

## Why have I received an "InvalidAccountStatus.NotEnoughBalance" error message? {#section_pxf_i43_kcs .section}

The default billing method of intermediate instances is pay-as-you-go. If your account balance is insufficient, the migration cannot be completed. You must recharge your account and try again. For more information about the pay-as-you-go billing method, see [Pay-as-you-go](../reseller.en-US/Pricing/Pay-As-You-Go.md#).

## Why have I received a "Forbidden.RAM" error message? {#section_5qw_dzv_7z7 .section}

The RAM user account does not have sufficient permissions to call the operation.

You must grant ECS and VPC access permissions `AliyunECSFullAccess` and `AliyunVPCFullAccess` to the RAM user account. For more information, see [Account access control](../reseller.en-US/Security/Implement access control by using RAM.md#).

## Why have I received an "InvalidImageName.Duplicated" error message? {#section_f09_jaz_05u .section}

The specified value of image\_name cannot be the same as that of an existing image.

## Why have I received an "InvalidAccountStatus.SnapshotServiceUnavailable" error message? {#section_gph_ns2_acq .section}

This error indicates that the snapshot service may not be activated in your account. For more information about how to activate the snapshot service, see [Activate ECS Snapshot](../../reseller.en-US/Snapshots/Use snapshots/Activate ECS Snapshot.md#).

## Why have I received a "Connect to Server Failed" error message? {#section_7ad_mse_m2s .section}

This error indicates that SMC is unable to connect to the intermediate instance. You can perform the following steps to troubleshoot the error:

1.  View the migration log for any migration exception.
2.  Before you proceed, perform the following checks:
    -   Check whether the status of the intermediate instance is normal.
    -   Check whether the network service of the on-premises server is normal. Check whether TCP ports 80, 443, 8703, and 8080 have been enabled on your server. SMC must have access permissions on these ports.
3.  After the error has been fixed, run the go2aliyun\_client again.

## Why have I received a "Create transition vpc failed \(QuotaExceeded.Vpc: VPC quota exceeded.\)" error message? {#section_qur_9g3_nka .section}

This error indicates that your VPC quota has been reached. If you have not set VPC and VSwitch parameters for your migration task, an intermediate VPC and VSwitch are automatically created during migration. After the migration task is complete, the intermediate VPC and VSwitch are cleared.

Each Alibaba Cloud account can have a maximum of 10 VPCs in a region. When the VPC quota has been reached, you can use any of the following methods:

-   Delete an existing VPC. For detailed steps, see [Create a VPC](../../reseller.en-US/VPCs and VSwitches/VPC and subnets/Create a VPC.md#section_j4l_1xw_rdb).
-   Adjust the VPC quota. [Submit a ticket](https://workorder.console.aliyun.com/).

## Why have I received an "InvalidAccessKeyId.NotFound" error message? {#section_rfn_fot_g83 .section}

This error indicates that the AccessKey pair you entered is incorrect. You must perform the following steps to fix the error:

1.  Open the user\_config.json file.
2.  Delete the values of `AccessKeyId` and `AccessKeySecret`.
3.  Save and close the file.
4.  Run the SMC client and enter a new AccessKey pair.

## Why have I received a "Do Rsync Disk x Failed" error message? {#section_gh1_ywk_103 .section}

This error indicates that the data transfer has been interrupted. You can perform the following steps to troubleshoot the error:

1.  View the migration log for any migration exception. If `return: 3072` or `return: 7680` is displayed in the log file, check whether the database or container service such as Oracle, MySQL, MS SQL Server, MongoDB, or Docker has been enabled on the source server. If the service is enabled, you can disable the service or exclude the related directory before you start the migration again.
2.  Before you proceed, perform the following checks:
    -   Check whether the status of the intermediate instance is normal.
    -   Check whether the network service of the on-premises server is normal. Check whether TCP ports 80, 443, 8703, and 8080 have been enabled on your server. SMC must have access permissions on these ports.
3.  After the error has been fixed, run the go2aliyun\_client again.

## Why have I received a "check rsync failed" or "rsync not found" error message on my Linux server? {#section_i9v_jy5_513 .section}

Check whether the Rsync component has been installed on the migration source system. For more information about how to install Rsync, see [How do I install Rsync?](#section_6ai_ig1_k06)

## Why have I received a "check virtio failed" error message on my Linux server? {#section_eji_23f_0ry .section}

Check whether the VirtIO driver has been installed on the migration source system. For more information about how to install the VirtIO driver, see [VirtIO driver](../reseller.en-US/Images/Custom image/Import images/Install virtio driver.md#).

## Why have I received a "check selinux failed" error message on my Linux server? {#section_wdz_y67_4sv .section}

Check whether SELinux has been disabled on the migration source system. For more information about how to disable SELInux, see [How do I disable SELinux?](#section_8za_stx_q0e)

## Why have I received a "Do Grub Failed" error message on my Linux server? {#section_284_a0c_8dl .section}

Check that GRand Unified Bootloader \(GRUB\) is installed on the source server. After GRUB is installed, restart the SMC client and migration task. For more information about how to install GRUB, see [Install GRUB v1.99 in a Linux server](../../reseller.en-US/Images/FAQ/Install GRUB v1.99 in a Linux server.md#).

## What do I do if Windows server migration stops at the "Prepare For Rsync Disk 0" stage? {#section_22e_ozc_d0w .section}

Windows server migration stops at the "Prepare For Rsync Disk 0" stage, and `VssSnapshotul::VssSnapshotul GetSnapshotul Failed: 0x80042308` is displayed in the log file. In this scenario, you can perform the following steps:

1.  Enable the Volume Shadow Copy service:
    1.  Log on to your on-premises server. Click **Start**, enter **services.msc** in the search box, and press Enter.
    2.  Find the Volume Shadow Copy service, and click **Start the service**.
2.  Uninstall the QEMU Guest Agent software:
    1.  Log on to your on-premises server. Click **Start**, enter **services.msc** in the search box, and press Enter.
    2.  Check whether the QEMU Guest Agent VSS Provider service is running. If this service is not available, you can re-run the SMC client.
    3.  Find the uninstall program, possibly in the C:\\Program Files \(x86\)\\virtio\\monitor\\uninstall.bat directory, and execute the program to uninstall the QEMU Guest Agent.
3.  Re-run the SMC client.

## What do I do if the system prompts me to activate Windows after a Windows server migration? {#section_kxd_mod_x2b .section}

You can use KMS to activate Windows after reinstalling Windows KMS Client Key.

1.  Remotely connect to the Windows ECS instance.
2.  On the Microsoft [Appendix A: KMS Client Setup Keys](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj612867(v%3dws.11)) page, find your relevant KMS client key. It is assumed to be xxxx-xxxx-xxxx-xxxx-xxxx here.
3.  Open the Command Prompt as an administrator, and run the following commands:

    ``` {#codeblock_6vr_a9x_yce}
    slmgr /upk
    ```

    ``` {#codeblock_hwz_m1o_mky}
    slmgr /ipk xxxx-xxxx-xxxx-xxxx-xxxx
    ```

4.  Use KMS to activate Windows.

## What do I do if the drive letters of data disks are missing or incorrect after a Windows server migration? {#section_kxs_fqi_hz3 .section}

-   If the drive letters are missing, you can manually add the drive letters in the Disk Management utility.
    1.  Choose **Control Panel** \> **System and Security** \> **Administrative Tools** \> **Computer Management**.
    2.  In the Disk Management utility, find and right-click a data disk that has a missing drive letter, and click **Change Drive Letters and Path...**.
    3.  Click **Add** and specify a drive letter.
-   If the drive letters are incorrect, you can change them in the Disk Management utility.
    1.  Choose **Control Panel** \> **System and Security** \> **Administrative Tools** \> **Computer Management**.
    2.  In the Disk Management utility, find and right-click a data disk whose drive letter is incorrect, and click **Change Drive Letters and Path...**.
    3.  Click **Change** and assign a drive letter.

## After a Windows server is migrated, the file system access permission is found to be abnormal or some system menus are displayed in different languages at instance startup. What do I do? {#section_6l1_guc_ms9 .section}

You must wait until the automatic recovery of the file system access permission is complete. For more information, see [How can I check my system after migrating a Windows server?](#section_c5i_33t_xn7)

## How can I check my system after migrating a Windows server? {#section_c5i_33t_xn7 .section}

When you start the created instance for the first time after a Windows server migration, you must perform the following checks:

1.  Check whether the system disk data is complete.
2.  If a data disk is missing, go to the Disk Management utility to check whether the drive letter is missing.
3.  After the automatic recovery of the file system access permission is complete, select whether to restart the instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/22635/156630279913956_en-US.png)

    **Note:** If the Goto Aliyun Restore Tool does not start during the first startup attempt, you can run the C:\\go2aliyun\_prepare\\go2aliyun\_restore.exe command to manually invoke the recovery process. Make sure that the number of disks and drive letter paths on the instance are consistent with those of the source system before running the command.

4.  Check whether the network service is normal.
5.  Check whether other system services are operating normally.

## How can I check my system after migrating a Linux server? {#section_8nx_71l_ksv .section}

When you start the created instance for the first time after a Linux server migration, you must perform the following checks:

1.  Check whether the system disk data is complete.
2.  If data disks exist, you must attach the data disks. For more information, see [Attach a data disk](../reseller.en-US/Block Storage/Block storage/Attach a cloud disk.md#).
3.  Check whether the network service is normal.
4.  Check whether other system services are operating normally.

## Why no data is found in the original data disk directory at instance startup after a Linux server migration? {#section_rak_i9w_gky .section}

When you migrate a Linux server with data disks, the data disks are not attached automatically upon instance startup. You can run the ls /dev/vd\* command to view the data disk devices. You can attach the data disks manually as needed, and edit the configuration file in the /etc/fstab directory to enable the data disks to be attached upon instance startup.

## Why cannot I start the ECS instance that is created based on the custom image generated after a Linux server migration? {#section_4wq_e1j_can .section}

You must perform the following checks:

-   Check the driver. Before creating an I/O optimized instance, make sure that the [VirtIO driver](../reseller.en-US/Images/Custom image/Import images/Install virtio driver.md#) has been installed on the source server.
-   Check whether the boot configurations of the source server system are correct.
-   If your source server system is CentOS 5 or Debian 7, the GRUB version is earlier than 1.9, and the following output appears when you connect to the ECS instance by using the [Management Terminal](../reseller.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to an instance by using the Management Terminal.md#) in the ECS console,

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/490278/156630279950179_en-US.png)

    you must upgrade GRUB to V1.9 or later, and then perform the migration again. For more information about how to upgrade GRUB, see [Install GRUB v1.99 in a Linux server](../../reseller.en-US/Images/FAQ/Install GRUB v1.99 in a Linux server.md#).


## What do I do if network service is abnormal when Others Linux instances are started? {#section_d07_qlt_y6e .section}

Alibaba Cloud does not perform any configurations such as network or SSH configurations on ECS instances that were created from imported images of the Others Linux type. You can manually modify the network service configurations.

As of March 31, 2018, the network configurations of images generated by the SMC client have changed. By default, IP addresses are allocated with the Dynamic Host Configuration Protocol \(DHCP\).

## How do I perform another migration of the same migration source? {#section_sz6_lrl_8aa .section}

Create and start a new migration task for the migration source.

## What do I do after a migration is complete and a custom image has been generated? {#section_pd1_rka_nhr .section}

We recommend that you use the image to create a pay-as-you-go instance, and then make sure that the system is operating normally. After confirming that the image functions normally, select instance types that meet your business requirements and create one or more ECS instances. For more information, see [Instance type families](../../reseller.en-US/Instances/Instance type families.md#) and [Create an instance by using the wizard](../../reseller.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).

## What happens after a migration is complete? {#section_203_izc_s31 .section}

SMC generates a custom image for your migration source. You can find your migration task on the Migration Tasks page, and click the image link in the **Migration Result** column to view the custom image.

## The hostname of the ECS instance created after a migration still contains the name of another cloud platform. How can this problem be solved? {#section_6py_r5e_qgz .section}

This error occurs because cloud\_init has not been installed or started on the ECS instance, or the version of cloud-init is not compatible with Alibaba Cloud. Install cloud-init and then restart the instance to update the hostname. For detailed steps, see [Install cloud-init for Linux images](../../reseller.en-US/Images/Custom image/Import images/Install cloud-init for Linux images.md#).

