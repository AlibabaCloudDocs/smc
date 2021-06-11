# SMC FAQ

This topic provides answers to some frequently asked questions \(FAQ\) about Server Migration Center \(SMC\).

-   General FAQ
    -   [What scenarios can I use SMC for?](#section_lqm_mcj_ht2)
    -   [What migration modes does SMC support?](#section_ry6_ron_ify)
    -   [I have a single Oracle database instance on a physical server. Do I need to migrate the entire server \(including the operating system and database\) or only the database to Alibaba Cloud? What are the advantages and disadvantages of the two methods?](#section_7wr_yaq_j99)
    -   [What migration process does SMC use?](#section_h30_ti7_cno)
    -   [How do I estimate the time required for a migration task? How do I test the data transfer rate?](#section_mx1_h0s_1fv)
    -   [Is bring your own license \(BYOL\) supported when I migrate servers by using SMC?](#section_v7z_kk9_haw)
    -   [Does SMC support resumable data transfer?](#section_jas_0vg_mmr)
    -   [Does SMC support incremental data migration?](#section_qnr_e43_55i)
    -   [What can I do if a migration task is interrupted or fails?](#section_aao_rej_1jy)
    -   [How does SMC create an intermediate instance?](#section_lii_mn5_7ki)
    -   [What do I need to know about intermediate instances?](#section_vqn_j3d_190)
    -   [What public endpoints and ports does my source server need to access?](#section_ora_z1t_efs)
    -   [What Windows Server licenses does Alibaba Cloud support?](#section_447_0cw_ulc)
    -   [How do I install Rsync?](#section_6ai_ig1_k06)
    -   [How do I disable SELinux?](#section_8za_stx_q0e)
-   Migration source FAQ
    -   [How do I exclude files or directories from a migration task?](#section_9xm_osd_b9i)
-   SMC console FAQ
    -   [What can I do if I release an intermediate instance by accident?](#section_1nu_xd1_bip)
    -   [What can I do if I want to reimport a migration source?](#section_uez_q5r_a20)
    -   [What can I do if I cannot create a migration task because a migration source is not in the Active state?](#section_weo_he3_b2a)
    -   [Why am I unable to delete a migration source?](#section_nu9_xbl_bad)
    -   [Why are the data disk parameters of a migration source not displayed in the Create Migration Task pane? How can I resolve this issue?](#section_nt4_qfc_tev)
    -   [Can I create a migration task for a migration source that has a running or failed migration task?](#section_25p_nj0_7r5)
    -   [What is the validity period of a migration task? What happens after a migration task expires?](#section_oe7_6bl_vu6)
    -   [What are the statuses of migration tasks? What do these statuses indicate?](#section_228_crt_kbx)
    -   [How do I find a migration source in the SMC console?](#section_7hf_tn4_x5i)
-   Troubleshooting FAQ
    -   [Why do I receive a "Forbidden.SubUser" error?](#section_tqr_azb_drh)
    -   [Why do I receive a "Forbidden.Unauthorized" error?](#section_xl0_pjl_069)
    -   [Why do I receive a "Your Account Haven't Completed Real-name Authentication" error?](#section_7vo_kuy_s0k)
    -   [Why do I receive a "Your Account Haven't Authorized For SMC RAM Role" error?](#section_0b6_33l_aa2)
    -   [Why do I receive an "IllegalTimestamp" error?](#section_kg8_hvy_brj)
    -   [Why do I receive an "InvalidAccountStatus.NotEnoughBalance" error?](#section_pxf_i43_kcs)
    -   [Why do I receive a "Forbidden.RAM" error?](#section_5qw_dzv_7z7)
    -   [Why do I receive an "InvalidImageName.Duplicated" error?](#section_f09_jaz_05u)
    -   [Why do I receive an "InvalidAccountStatus.SnapshotServiceUnavailable" error?](#section_gph_ns2_acq)
    -   [Why do I receive a "Create transition vpc failed" error message? \(QuotaExceeded.Vpc: VPC quota exceeded.\)error message?](#section_qur_9g3_nka)
    -   [Why do I receive an "InvalidAccessKeyId.NotFound" error?](#section_rfn_fot_g83)
    -   [Why do I receive a "Connect to Server Failed" error?](#section_7ad_mse_m2s)
    -   [Why do I receive a "Do Rsync Disk x Failed" error?](#section_gh1_ywk_103)
    -   [Why do I receive a "check rsync failed" or "rsync not found" error on my Linux server?](#section_i9v_jy5_513)
    -   [Why do I receive a "check virtio failed" error message on my Linux server?](#section_eji_23f_0ry)
    -   [Why do I receive a "check selinux failed" error message on my Linux server?](#section_wdz_y67_4sv)
    -   [Why do I receive a "Do Grub Failed" error on my Linux server?](#section_284_a0c_8dl)
    -   [What can I do if Windows server migration stops in the "Prepare For Rsync Disk 0" stage?](#section_22e_ozc_d0w)
-   Post-migration FAQ
    -   [What can I do if I am prompted to activate the Windows service after I migrate a Windows server?](#section_kxd_mod_x2b)
    -   [What can I do if the drive letters of data disks are missing or invalid after I migrate a Windows server?](#section_kxs_fqi_hz3)
    -   [What can I do if the file system access is inaccessible or system menus are displayed in different languages during instance startup after I migrate a Windows server?](#section_6l1_guc_ms9)
    -   [How do I check my system after I migrate a Windows server?](#section_c5i_33t_xn7)
    -   [How do I check my system after I migrate a Linux server?](#section_8nx_71l_ksv)
    -   [Why does no data exist in the original data disk directory during instance startup after I migrate a Linux server?](#section_rak_i9w_gky)
    -   [What can I do if I am unable to start the ECS instance created based on the custom image after a Linux server migration?](#section_4wq_e1j_can)
    -   [Why does the LVM partitions of my Linux server change to standard partitions?](#section_r6m_dya_fvv)
    -   [Why is the network service unavailable when an Others Linux instance is started?](#section_d07_qlt_y6e)
    -   [How do I migrate a server again?](#section_sz6_lrl_8aa)
    -   [What do I do after a migration task is completed and a custom image is generated?](#section_pd1_rka_nhr)
    -   [What happens after a migration task is completed?](#section_203_izc_s31)
    -   [Why does the hostname of the ECS instance created after a migration task contain the name of another cloud platform?](#section_6py_r5e_qgz)

## What scenarios can I use SMC for?

You can use SMC to migrate various types of servers to Elastic Compute Service \(ECS\), such as physical servers, virtual machines \(VMs\), and third-party cloud servers. These servers can run on Windows or Linux. For more information, see [What is SMC?](/intl.en-US/Product Introduction/What is SMC?.md)

## What migration modes does SMC support?

SMC supports the daemon mode. In this mode, you can import the information of the migration source by using an SMC client. Then, you can log on to the SMC console to create and complete a migration task. For more information, see [Migration process](/intl.en-US/User Guide/Migration process.md).

## I have a single Oracle database instance on a physical server. Do I need to migrate the entire server \(including the operating system and database\) or only the database to Alibaba Cloud? What are the advantages and disadvantages of the two methods?

You can migrate the entire server or only the database based on your business requirements. The two methods have the following advantages and disadvantages:

-   If you need only the Oracle database, we recommend that you migrate only the database. However, you may need to deploy the database in a new environment.
-   If you need both the database and its operating environment, we recommend that you migrate the entire server to Alibaba Cloud. However, if the server has a large volume of resources, the migration may require more time to complete.

## What migration process does SMC use?

SMC uses the following migration process:

1.  You import the information of the migration source to the SMC console.
2.  The SMC backend server prepares an intermediate instance.
3.  The SMC client transfers data from the migration source to the intermediate instance.
4.  SMC creates an image from the migration source and installs the image on Alibaba Cloud.

## How do I estimate the time required for a migration task? How do I test the data transfer rate?

You can estimate the time required for a migration task based on the migration period. The migration period is divided into three phases: pre-migration, migration, and post-migration. The migration period is proportional to the number of servers that you want to migrate and the volume of data. We recommend that you perform a test migration to estimate the time required for a migration task.

For more information, see [Estimate the time required for migration and test the data transfer speed](/intl.en-US/Best Practices/Estimate the time required for migration and test the data transfer speed.md).

## Is bring your own license \(BYOL\) supported when I migrate servers by using SMC?

Yes, SMC supports BYOL. BYOL licenses are used in the following scenarios:

-   Microsoft

    Microsoft BYOL licenses are used in the following scenarios:

    -   BYOL implemented by using Software Assurance \(SA\)

        BYOL can be implemented for software programs that support License Mobility when ECS instances are created, such as SQL Server and SharePoint.

    -   Windows operating systems

        Windows [client access licenses \(CALs\)](https://docs.microsoft.com/zh-cn/windows-server/remote/remote-desktop-services/rds-client-access-license) do not support License Mobility. Therefore, existing Windows licenses cannot be used in shared hardware environments. You must deploy Windows operating systems in a dedicated physical environment, which can be an Alibaba Cloud dedicated host or an ECS bare metal instance. For more information, see the [DDH documentation](/intl.en-US/Product Introduction/What is DDH?.md) and [ECS Bare Metal Instance documentation](/intl.en-US/Instance/Instance type families/ECS Bare Metal Instance types/Overview.md).

        Alibaba Cloud does not provide Key Management Service \(KMS\), Windows Server Update Services \(WSUS\), or software technical support for these kinds of ECS instances. You can contact Microsoft for software technical support.

    -   No SA is available or BYOLs implemented through SA are not supported

        This scenario is similar to the Windows operating system scenario. You can reuse software licenses that you have purchased and downloaded, and deploy software programs in a dedicated hardware environment.

-   Red Hat

    Red Hat provides the Cloud Access program. If you migrate Red Hat subscriptions to Alibaba Cloud by using the bring your own subscription \(BYOS\) method, you can register with Red Hat Cloud Access. For more information, see [Step 1: Sign up with Red Hat Cloud Access]().


## Does SMC support resumable data transfer?

Yes, SMC supports resumable data transfer. If data transfer is interrupted, you can restart the client and the migration task to resume migration.

## Does SMC support incremental data migration?

Yes, SMC supports incremental data migration. For more information, see [Migrate incremental data from a source server](/intl.en-US/Best Practices/Migrate incremental data from a source server.md).

## What can I do if a migration task is interrupted or fails?

If a migration task is interrupted or fails, use the following troubleshooting methods:

-   If the SMC client exits due to an exception or the migration process stalls, restart the client and the migration task to resume the migration.
-   If the migration task is in the InError state, check the log file of the migration task in the SMC console to locate the cause of error.

    If the problem persists, we recommend that you join the [SMC support group on DingTalk](https://wx.dingtalk.com/invite-page/weixin.html?bizSource=____source____&corpId=dingc9d6f7ff346016e135c2f4657eb6378f&inviterUid=F2460A59D575A69799372A3FA1525DE6&encodeDeptId=B924094833B5108D03A6AD1004DA0487). For more information, see [Contact us](/intl.en-US/FAQ/Contact us.md).


## How does SMC create an intermediate instance?

SMC attempts to create an intermediate instance based on the following specifications in sequence.

-   1 vCPU 2 GiB
-   1 vCPU 4 GiB
-   2 vCPU 2 GiB
-   2 vCPU 4 GiB
-   t6, burstable instance family
-   t5, burstable instance family
-   2 vCPU 8 GiB

If the preceding instance specifications are unavailable, SMC selects other cost-effective instance specifications.

## What do I need to know about intermediate instances?

You need to know the following information about intermediate instances:

-   SMC creates, starts, stops, and releases an intermediate instance named `No_Delete_SMC_Transition_Instance` during a migration process. To ensure a smooth migration, do not modify the status of the intermediate instance.
-   The default security group of the intermediate instance allows access to ports 8080 and 8703. These ports are the migration service ports of the intermediate instance. Do not modify or delete the security group.
-   After the migration is completed, the intermediate instance is automatically released. If the migration fails, you must manually release the instance. For more information, see [Release an instance](/intl.en-US/Instance/Manage instances/Release an instance.md).

## What public endpoints and ports does my source server need to access?

A source server must access the following endpoint and ports:

-   The SMC endpoint: `https://smc.aliyuncs.com:443`.
-   Ports 8080 and 8703 of the intermediate instance. If the migration is performed over a **virtual private cloud \(VPC\)**, the source server must also access the private IP address of the intermediate instance.****

**Note:** You do not need to enable inbound ports for the source server. However, you must make sure that the server can access the preceding endpoint and ports.

## What Windows Server licenses does Alibaba Cloud support?

Alibaba Cloud supports licenses for Windows Server 2003, 2008, 2012, and 2016. To migrate servers that run other versions of Windows operating systems to Alibaba Cloud, you must apply for license mobility. For more information, see [Apply for License Mobility through Software Assurance](https://www.alibabacloud.com/help/doc-detail/84749.html).

## How do I install Rsync?

To install Rsync, run one of the following commands based on the operating system of your source server:

-   CentOS: yum -y install rsync.
-   Ubuntu: apt-get -y install rsync.
-   Debian: apt-get -y install rsync.
-   SUSE: zypper install rsync.
-   Other operating systems: See the installation documentation on the official website.

## How do I disable SELinux?

To temporarily disable SELinux, run the setenforce 0 command. To permanently disable SELinux, open the configuration file in the /etc/selinux/config directory, and then set SELINUX to `disabled`.

## How do I exclude files or directories from a migration task?

To exclude files or directories from a migration task, add the corresponding file paths or directory paths to the following configuration files. The configuration files reside in the Excludes directory of the client.

-   A system disk configuration file: rsync\_excludes\_win.txt \(for Windows servers\) or rsync\_excludes\_linux.txt \(for Linux servers\)

-   A data disk configuration file: named by adding a suffix disk \[disk index number\] to the system disk, such as rsync\_excludes\_win\_disk1.txt \(for Windows servers\) or rsync\_excludes\_linux\_disk1.txt \(for Linux servers\).


**Note:** If a configuration file is lost or deleted by accident, you can create another one.

-   Example 1: Exclude files or directories from migration of a Windows Server
    -   System disk:
        -   Specify the files or directories to be excluded:

            ```
            C:\MyDirs\Docs\Words
            C:\MyDirs\Docs\Excels\Report1.txt
            ```

        -   Add the following information to the rsync\_excludes\_win.txt file:

            ```
            /MyDirs/Docs/Words/
            /MyDirs/Docs/Excels/Report1.txt
            ```

    -   Data disk:

        -   Specify the files or directories to be excluded:

            ```
            D:\MyDirs2\Docs2\Words2
            D:\MyDirs2\Docs2\Excels\Report2.txt
            ```

        -   Add the following information to the rsync\_excludes\_win\_disk1.txt file:

            ```
            /MyDirs2/Docs2/Words2/
            /MyDirs2/Docs2/Excels2/Report2.txt
            ```

        **Note:**

        To exclude a Windows directory, you must perform the following operations:

        -   Remove the prefix of the directory \(scr\_path\). In the preceding example, you must remove `D:`.
        -   Replace `\` with `/`.
-   Example 2: Exclude files or directories from the migration of a Linux server
    -   System disk \(root directory/\):

-   Specify the files or directories to be excluded:

    ```
    /var/mydirs/docs/words
    /var/mydirs/docs/excels/report1.txt
    ```

-   Add the following information to the rsync\_excludes\_linux.txt file:

    ```
    /var/mydirs/docs/words/
    /var/mydirs/docs/excels/report1.txt
    ```

    -   Data disk:

-   Specify the files or directories to be excluded:

    ```
    /mnt/disk1/mydirs2/docs2/words2
    /mnt/disk1/mydirs2/docs2/excels2/report2.txt
    ```

-   Add the following information to the rsync\_excludes\_linux\_disk1.txt file:

    ```
    /mydirs2/docs2/words2/
    /mydirs2/docs2/excels2/report2.txt
    ```

        **Note:** To exclude a Linux directory, you must remove the prefix of the directory \(scr\_path\). In the preceding example, you must remove /mnt/disk1.


## What can I do if I want to reimport a migration source?

You must delete the migration source, restart the client, and then reimport the migration source. If the migration source is associated with a migration task, you must delete the migration task before you delete the migration source.

## What can I do if I release an intermediate instance by accident?

If you release an intermediate instance by accident, delete the current migration task, create a migration task for the migration source, and then start the migration task. If the problem persists, you can [submit a ticket](https://workorder.console.aliyun.com/#/ticket/list/).

## What can I do if I cannot create a migration task because a migration source is not in the Active state?

Restore the migration source to the Active state, and then create a migration task. Perform the following steps to fix the issue:

-   If the migration source is in the Inactive state,

    the migration source is disconnected from the SMC console. You must restart the SMC client and wait until the migration is completed. For more information, see [Step 1: Import the information of a migration source](/intl.en-US/User Guide/Step 1: Import the information of a migration source.md).

-   If the migration source is in the InError state, you must check the console logs. You must also check the client logs in the Logs directory and the error messages on the client UI. Resolve the error based on the logs. You can also use the error codes and troubleshooting methods in this topic for reference. If the problem persists, contact Alibaba Cloud. For more information, see [Contact us](/intl.en-US/FAQ/Contact us.md).

## Why am I unable to delete a migration source?

You cannot delete a migration source if it is associated with an unfinished migration task. You must stop and delete the migration task before you can delete the migration source.

## Why are the data disk parameters of a migration source not displayed in the Create Migration Task pane? How can I resolve this issue?

This is because your migration source is not equipped with data disks or no data disk is attached to the migration source. If your migration source has no data disk or is not attached to a data disk, the data disk parameters are not displayed in the Create Migration Task pane. To resolve this problem, perform the following steps:

1.  Attach the data disk.
2.  Restart the SMC client.
3.  Refresh the Migration Sources page in the SMC console, and open the Create Migration Task pane again.

## Can I create a migration task for a migration source that has a running or failed migration task?

No, you cannot create a migration task for the migration source in this case. However, you can create a migration task after you perform the following steps:

-   If an existing migration task is in progress, stop and delete the migration task.
-   If an error occurs on an existing migration task, delete the migration task.

## What is the validity period of a migration task? What happens after a migration task expires?

A migration task expires 30 days after it is created in the SMC console. The expiration time cannot be changed in the console. If you call the [CreateReplicationJob](/intl.en-US/API Reference/Migration tasks/CreateReplicationJob.md) operation to create a migration task, you can set a value for the validity period based on your needs. The validity period ranges from 7 to 90 days.

The validity period starts from the time when the migration task is created. The following two methods are used to process an expired migration task:

-   If the migration task is in the Running state, no operations are performed.
-   If the migration task is in the Ready, Stopped, or InError state, it enters the Expired state. SMC deletes the migration task seven days after the task expires.

## What are the statuses of migration tasks? What do these statuses indicate?

The statuses of a migration task are divided into the following two types:

-   Status of a migration task: the status of the migration task throughout the entire lifecycle. For more information, see [Statuses of a migration task](#table_njm_7xg_xep).
-   Business status of a migration task: the status of a migration task in the Running state. For more information, see [Business statuses of a migration task](#table_6p3_f67_5zr).

The following figure shows the relationships between the statuses and business statuses of a migration task.

![job_status](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2159816951/p51026.png)

|Status|Description|Supported operation|
|:-----|:----------|:------------------|
|Ready|The migration task is created but is not started.|Start the migration task.|
|Running|The migration task is running. The business status rather than the running status is displayed in the **Status** column of the SMC console. For more information, see [Business statuses of a migration task](#table_6p3_f67_5zr).|Stop the migration task when it is completed or when it is in the **Syncing** state. **Note:** You cannot delete a migration task that is in the Running state. |
|Stopped|The migration task is stopped.|Restart or delete the migration task.|
|InError|The migration task fails.|Check the error message or migration logs in the client or console to identify the cause and fix the issue. If the migration source is in the Inactive or InError state, the failure is caused by the SMC client. You must restart the client before you restart the migration task.|
|Finished|The migration task is completed.|Go to the Custom Images tab in the Elastic Compute Service \(ECS\) console to view the image generated by SMC.|
|Waiting|The task is pending execution. Only incremental migration tasks can reach this status. For more information, see [Migrate incremental data from a source server](/intl.en-US/Best Practices/Migrate incremental data from a source server.md).|If the migration task is in the Waiting state, you can perform the following steps: -   Use the image generated by the migration task to create an ECS instance.
-   Stop the migration task.
-   Delete the migration task.
-   Perform incremental migration of source servers.
-   Modify the settings of automatic incremental migration. The settings include the interval at which the migration task runs and the maximum number of images that can be retained for the task. |
|Expired|The migration task has expired.|Delete the migration task. **Note:** Each migration task is valid for 30 days. When a migration task expires, the status of the task changes to Expired and the task is retained for seven days. SMC deletes the migration task seven days after the task expires. For more information, see [What is the validity period of a migration task? What happens after a migration task expires?](#section_oe7_6bl_vu6) |
|Deleting|The migration task is being deleted.|Wait until the migration task is deleted, or create another migration task for the migration source. **Note:** After a migration task is deleted, SMC releases the resources used during the migration process, such as the intermediate instance. This process may take a while to complete. |

|Business status|Description|Supported operation|
|:--------------|:----------|:------------------|
|Preparing|After you start a migration task, the status of the task changes to Preparing.|None|
|Syncing|The migration task is uploading data from the migration source.|Stop the migration task.|
|Processing|The migration task is creating an image of the migration source.|None|
|Cleaning|The intermediate instance is being released and the migration task is almost completed.|None|

## How do I find a migration source in the SMC console?

To find a migration source, perform the following steps:

1.  Log on to the [SMC console](https://smc.console.aliyun.com/overview).
2.  In the left-side navigation pane, click **Migration Sources**.
3.  On the Migration Sources page, click the search box and select a search item from the drop-down list.

    Search items include **Migration Source Name**, **Migration Source ID**, **Status**, and **Latest Migration Task ID**. All search queries return the results that exactly match the search items.

4.  Enter a value for the selected search item and press `Enter`.

## Why do I receive a "Forbidden.SubUser" error?

You receive the error because SMC requires a RAM user who has permissions to purchase instances. You must use the AccessKey pair of the account to call the ECS API and create resources such as intermediate instances and disks. Service provider accounts may not have the permissions to purchase instances. If you need to migrate resources, contact Alibaba Cloud. For more information, see [Contact us](/intl.en-US/FAQ/Contact us.md).

## Why do I receive a "Forbidden.Unauthorized" error?

You receive the error because you are using a RAM user who has no permissions to access SMC. For more information about the authorization methods, see [Procedure](/intl.en-US/User Guide/Before you begin.md).

## Why do I receive a "Your Account Haven't Completed Real-name Authentication" error?

You receive the error because your account has not passed real-name verification. For more information about how to complete real-name verification, see [Procedure](/intl.en-US/User Guide/Before you begin.md).

## Why do I receive a "Your Account Haven't Authorized For SMC RAM Role" error?

You receive the error because the required role is not created or assigned to SMC. For more information about the authorization methods, see [Procedure](/intl.en-US/User Guide/Before you begin.md).

## Why do I receive an "IllegalTimestamp" error?

You receive the error because the system time of a migration source is inconsistent with the standard time of the region where the migration source is located. Make sure that the system time is consistent with the standard time of that region.

## Why do I receive an "InvalidAccountStatus.NotEnoughBalance" error?

You receive the error because your account balance is insufficient. The default billing method of intermediate instances is pay-as-you-go. If your account balance is insufficient, migration cannot be completed. You must add sufficient funds to your account and try again. For more information, see [Pay-as-you-go](/intl.en-US/Pricing/Billing methods/Pay-as-you-go.md).

## Why do I receive a "Forbidden.RAM" error?

You receive the error because you are using a RAM user that has no permissions to call the operation.

You must grant full access permissions on ECS and VPC to the RAM user by attaching the `AliyunECSFullAccessECS` and `AliyunVPCFullAccess` policies to the RAM user. For more information, see [Account access control](/intl.en-US/Security/Implement access control by using RAM.md).

## Why do I receive an "InvalidImageName.Duplicated" error?

You receive the error because the specified image\_name already exists.

## Why do I receive an "InvalidAccountStatus.SnapshotServiceUnavailable" error?

You receive the error because the snapshot service has not been activated for your Alibaba Cloud account. For more information, see [Activate ECS Snapshot](/intl.en-US/Snapshots/Use snapshots/Activate ECS Snapshot.md).

## Why do I receive a "Connect to Server Failed" error?

You receive the error because SMC cannot connect to the intermediate instance. To resolve the error, perform the following steps:

1.  Check the detailed migration logs.
2.  Perform the following steps:
    -   Check whether the intermediate instance is running as expected.
    -   Check whether the network of the on-premises server is connected. Check whether TCP ports 80, 443, 8703, and 8080 are enabled on your server. SMC must have access to these ports.
3.  After you resolve the error, run the SMC client again.

## Why do I receive a "Create transition vpc failed" error message? \(QuotaExceeded.Vpc: VPC quota exceeded.\)error message?

You receive the error because your VPC quota is exceeded. If you do not specify a VPC and vSwitch for your migration task, SMC creates an intermediate VPC and vSwitch during the migration. After the migration task is completed, SMC deletes the intermediate VPC and vSwitch.

Each Alibaba Cloud account can have a maximum of 10 VPCs in a region. If you perform multiple migration tasks at a time or the number of VPCs in the destination region reaches the quota, we recommend that you increase the VPC reuse rate. To do so, you can specify the same VPC and vSwitch when you create migration tasks. For more information, see [Migration task parameters](/intl.en-US/User Guide/Step 2: Create and start a migration task.md).

If the VPC quota is reached, perform one of the following steps:

-   Delete an existing VPC. For more information, see [Delete a VPC](/intl.en-US/VPCs and vSwitchs/Work with VPCs.md).
-   Increase the VPC quota. [Submit a ticket](https://workorder.console.aliyun.com/).

## Why do I receive an "InvalidAccessKeyId.NotFound" error?

You receive the error because the AccessKey pair you specified is invalid. To resolve this error, perform the following steps:

1.  Open the user\_config.json file.
2.  Delete the values of `AccessKeyId` and `AccessKeySecret`.
3.  Save and close the file.
4.  Run the SMC client and enter a valid AccessKey pair.

## Why do I receive a "Do Rsync Disk x Failed" error?

You receive the error because the data transfer is interrupted. To resolve the error, perform the following steps:

1.  Check the migration logs for exceptions. If the log file contains `return:3072` or `return:7680`, check whether the database or container services such as Oracle, MySQL, Microsoft SQL Server, MongoDB, or Docker are enabled on the source server. If the services are enabled, disable these services or exclude the related directories before you migrate data.
2.  Perform the following steps:
    -   Check whether the intermediate instance is running as expected.
    -   Check whether the network of the on-premises server is connected. Check whether TCP ports 80, 443, 8703, and 8080 are enabled on your server. SMC must have access to these ports.
3.  After you resolve the error, run the SMC client again.

## Why do I receive a "check rsync failed" or "rsync not found" error on my Linux server?

You receive the error because you have not installed the Rsync component on the source server. For more information, see [How do I install Rsync?](#section_6ai_ig1_k06)

## Why do I receive a "check virtio failed" error message on my Linux server?

You receive the error because you have not installed the virtio driver on the source server. For more information, see [Install a virtio driver](/intl.en-US/Images/Custom image/Import images/Install a virtio driver.md).

## Why do I receive a "check selinux failed" error message on my Linux server?

You receive the error because you have enabled SELinux on the source server. For more information, see [How do I disable SELinux?](#section_8za_stx_q0e)

## Why do I receive a "Do Grub Failed" error on my Linux server?

You receive the error because you have not installed GRand Unified Bootloader \(GRUB\) on the source server. If GRUB is not installed, install GRUB and then restart the SMC client and the migration task. For more information, see [Install GRUB on a Linux server](/intl.en-US/Images/FAQ/Install GRUB on a Linux server.md).

## What can I do if Windows server migration stops in the "Prepare For Rsync Disk 0" stage?

If Windows server migration stops in the "Prepare For Rsync Disk 0" stage and `VssSnapshotul::VssSnapshotul GetSnapshotul Failed:0x80042308` is displayed in the log file, perform the following steps:

1.  Enable the Volume Shadow Copy service.
    1.  Log on to your on-premises server. Click **Start**, enter **services.msc** in the search box, and then press Enter.
    2.  Find the Volume Shadow Copy service and click **Start Service**.
2.  Uninstall the QEMU Guest Agent software.
    1.  Log on to your on-premises server. Click **Start**, enter **services.msc** in the search box, and then press Enter.
    2.  Check whether the QEMU Guest Agent VSS Provider service is running. If this service is unavailable, restart the SMC client.
    3.  Find the uninstall.bat file in the C:\\Program Files \(x86\)\\virtio\\monitor\\uninstall.bat directory, and execute the file to uninstall QEMU Guest Agent.
3.  Restart the SMC client.

## What can I do if I am prompted to activate the Windows service after I migrate a Windows server?

You can reinstall Key Management Service \(KMS\) to activate the Windows service.

1.  Connect to the Windows instance.
2.  On the Microsoft [KMS Client Setup Keys](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj612867(v%3dws.11)) page, find your KMS client key. For example, the key is xxxx-xxxx-xxxx-xxxx-xxxx.
3.  Open Command Prompt as an administrator, and run the following commands:

    ```
    slmgr /upk
    ```

    ```
    slmgr /ipk xxxx-xxxx-xxxx-xxxx-xxxx
    ```

4.  Use KMS to activate the Windows service.

## What can I do if the drive letters of data disks are missing or invalid after I migrate a Windows server?

-   If the drive letters are missing, add them in the Disk Management utility.
    1.  Choose **Control Panel** \> **System and Security** \> **Administrative Tools** \> **Computer Management**.
    2.  In the Disk Management utility, right-click the data disk whose drive letter is missing, and click **Change Drive Letters and Path**.
    3.  Click **Add** and specify a drive letter.
-   If the drive letters are invalid, you can change them in the Disk Management utility.
    1.  Choose **Control Panel** \> **System and Security** \> **Administrative Tools** \> **Computer Management**.
    2.  In the Disk Management utility, right-click the data disk whose drive letter is missing, and click **Change Drive Letters and Path**.
    3.  Click **Change** to change the drive letter.

## What can I do if the file system access is inaccessible or system menus are displayed in different languages during instance startup after I migrate a Windows server?

You must wait until the access permissions on the file system automatically recover. For more information, see [How do I check my system after I migrate a Windows server?](#section_c5i_33t_xn7)

## How do I check my system after I migrate a Windows server?

After you migrate your Windows server, you must perform the following steps when you start the created instance for the first time:

1.  Check whether the system disk data is complete.
2.  If a data disk is missing, go to the Disk Management utility to check whether the drive letter is missing.
3.  After the access permissions on the file system automatically recover, select whether to restart the instance.

    ![Windows system check](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2159816951/p13956.png)

    **Note:** If the Goto Aliyun Restore Tool does not start during the first startup, run the C:\\go2aliyun\_prepare\\go2aliyun\_restore.exe command to invoke the recovery process. Before you run the command, make sure that the number of disks on the instance is consistent with the number of disks on the source system. In addition, make sure that the driver letter paths on the instance are consistent with the driver letter paths on the source system.

4.  Check whether the network is connected.
5.  Check whether other system services are running as expected.

## How do I check my system after I migrate a Linux server?

After you migrate your Linux server, you must perform the following steps when you start the created instance for the first time:

1.  Check whether the system disk data is complete.
2.  If data disks exist, you must attach them to the instance. For more information, see [Attach a data disk](/intl.en-US/Block Storage/Cloud disks/Attach a data disk.md).
3.  Check whether the network is connected.
4.  Check whether other system services are running as expected.

## Why does no data exist in the original data disk directory during instance startup after I migrate a Linux server?

This is because the data disks are not attached during instance startup by default after you migrate a Linux server with data disks. To resolve this issue, run the ls /dev/vd\* command to view the data disks. Attach the data disks based on your needs. Edit the configuration file in the /etc/fstab directory to allow the data disks to be attached during instance startup.

## What can I do if I am unable to start the ECS instance created based on the custom image after a Linux server migration?

To resolve this issue, perform the following steps:

-   Check the driver. Before you create an I/O optimized instance, make sure that the virtio driver is installed on the source server. For more information, see [Install a virtio driver](/intl.en-US/Images/Custom image/Import images/Install a virtio driver.md).
-   Check whether the GRUB configurations of the source server are valid.
-   If the following conditions apply, you must upgrade GRUB to version 1.9 or later, and then perform the migration again: The operating system of your source server is CentOS 5 or Debian 7 and the GRUB version is earlier than 1.9. In addition, the following output appears when you connect to the ECS instance by using the Management Terminal in the ECS console. For information about how to connect to the ECS instance, see [Connect to a Linux instance by using password authentication](/intl.en-US/Instance/Connect to instances/Connect to an instance by using VNC/Connect to a Linux instance by using password authentication.md).

    ![Linux server check during startup](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2159816951/p50179.png)

    For information about how to upgrade GRUB to version 1.9 or later, see [Install GRUB on a Linux server](/intl.en-US/Images/FAQ/Install GRUB on a Linux server.md).


## Why does the LVM partitions of my Linux server change to standard partitions?

SMC does not allow you to replicate Logical Volume Manager \(LVM\) partitions. After a Linux server is migrated, the LVM partitions of the server is changed to standard partitions.

## Why is the network service unavailable when an Others Linux instance is started?

This is because Alibaba Cloud does not perform configurations such as network or Secure Shell \(SSH\) configurations on ECS instances created from imported images of the Others Linux type. To resolve this issue, you can change the network configurations.

The network configurations of the images generated by the SMC client were changed on March 31, 2018. By default, IP addresses are allocated based on the Dynamic Host Configuration Protocol \(DHCP\).

## How do I migrate a server again?

To migrate a migration source again, create a migration task for the migration source, and then start the task.

## What do I do after a migration task is completed and a custom image is generated?

We recommend that you use the image to create a pay-as-you-go instance, and then check whether the system is running as expected. Select instance types that meet your business requirements and create ECS instances. For more information, see [Instance families](/intl.en-US/Instance/Instance families.md) and [Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md).

## What happens after a migration task is completed?

After a migration task is completed, SMC generates a custom image for your migration source. You can find your migration task on the Migration Tasks page, and click the link in the **Migration Result** column to view the custom image.

![Migration result](../images/p50103.png)

## Why does the hostname of the ECS instance created after a migration task contain the name of another cloud platform?

This is because cloud\_init is not installed or started on the ECS instance, or the cloud-init versions of the source server and Alibaba Cloud are incompatible. To resolve this issue, you can install cloud-init and then restart the instance to update the hostname. For more information, see [Install cloud-init](/intl.en-US/Images/Custom image/Import images/Install cloud-init.md).

