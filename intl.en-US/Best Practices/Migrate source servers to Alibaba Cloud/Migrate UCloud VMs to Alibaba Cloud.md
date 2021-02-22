# Migrate UCloud VMs to Alibaba Cloud

This topic describes how to migrate UCloud virtual machines \(VMs\) to Alibaba Cloud.

Before the migration, complete the preparations based on the operating system of the VM. For more information, see the following topics:

-   [Prepare for the migration of a Windows-based UCloud VM to Alibaba Cloud](#section_tw7_piv_82n)
-   [Prepare for the migration of a Linux-based UCloud VM to Alibaba Cloud](#section_4jv_ynd_fqm)

After the preparations are complete, you can start the migration. For more information, see [Migrate UCloud VMs to Alibaba Cloud](#section_z1r_s12_f2i). If you migrate a VM for the first time, we recommend that you perform a test migration.

## Prepare for the migration of a Windows-based UCloud VM to Alibaba Cloud

Before the migration, perform the following operations:

-   Create snapshots to back up data.
-   Make sure that the system time of the VMWare VM is the same as the standard time of the region where the VMWare VM resides.
-   Make sure that the VMWare VM has access to the following URLs and ports:
    -   The endpoint `https://smc.aliyuncs.com:443` that is used to access SMC.
    -   Ports 8080 and 8703 that are required to connect to the intermediate instance during the migration process.

        **Note:** During the migration, SMC creates, starts, stops, and releases the intermediate instance No\_Delete\_SMC\_Transition\_Instance. The default security group of the intermediate instance allows access to ports 8080 and 8703. Both ports are the migration service ports of the intermediate instance.

-   Make sure that the Volume Shadow Copy Service \(VSS\) is enabled.
-   Check whether the QEMU Guest Agent is installed. If the QEMU Guest Agent is installed, you must uninstall it. For information about how to uninstall the QEMU Guest Agent, see [SMC FAQ](/intl.en-US/FAQ/SMC FAQ.md).
-   Check the validity of your application licenses. After you migrate the VMWare VM to Alibaba Cloud, the application licenses that are associated with the underlying hardware may become invalid.

## Prepare for the migration of a Linux-based UCloud VM to Alibaba Cloud

Before the migration, perform the following operations:

-   Create snapshots to back up data.
-   Make sure that the system time of the VMWare VM is the same as the standard time of the region where the VMWare VM resides.
-   Make sure that the VMWare VM has access to the following URLs and ports:
    -   The endpoint `https://smc.aliyuncs.com:443` that is used to access SMC.
    -   Ports 8080 and 8703 that are required to connect to the intermediate instance during the migration process.

        **Note:** During the migration, SMC creates, starts, stops, and releases the intermediate instance No\_Delete\_SMC\_Transition\_Instance. The default security group of the intermediate instance allows access to ports 8080 and 8703. Both ports are the migration service ports of the intermediate instance.

-   Check the validity of your application licenses. After you migrate the VMWare VM to Alibaba Cloud, the application licenses that are associated with the underlying hardware may become invalid.

## Migrate UCloud VMs to Alibaba Cloud

Create an Alibaba Cloud account. For more information, see [Before you begin](/intl.en-US/User Guide/Before you begin.md).

1.  Download and decompress the SMC client package.

    1.  Download the [SMC client package](https://p2v-tools.oss-cn-hangzhou.aliyuncs.com/smc/Alibaba_Cloud_Migration_Tool.zip?spm=5176.13581910.904.4.19a66145HXSeu9&file=Alibaba_Cloud_Migration_Tool.zip).

        If the migration source has access to the Internet, you can also download the SMC client package to the migration source.

        **Note:** You can log on to the [SMC console](https://smc.console.aliyun.com/). In the upper-right corner of the page, click **Download Latest SMC Client** to download the latest version of the SMC client.

    2.  Upload the SMC client package to the migration source.

        -   You can build an FTP site to upload files. For more information, see [Manually build an FTP site on a Windows instance](/intl.en-US/Tutorials/Build an application/Build an FTP site on an ECS instance/Manually build an FTP site on a Windows instance.md) or [Manually build an FTP site on a CentOS 7 instance](/intl.en-US/Tutorials/Build an application/Build an FTP site on an ECS instance/Manually build an FTP site on a CentOS 7 instance.md).
        -   You can also use a remote connection tool that supports file transfer. This allows you to upload the SMC client package to the migration source.
    3.  Decompress the SMC client package.

        The SMC client is available for Windows and Linux of the 32-bit version \(i386\) and the 64-bit version \(x86\_64\). Select the version that is compatible with the migration source. The following figure shows the decompressed client folders for Windows.

        **Note:** Linux systems run the unzip <name of the SMC client package\> command. This allows you to decompress the SMC client package. Make sure that the unzip utility is installed on the source server. For example, the installation command for CentOS 7 is yum -y install unzip.

        ![Client version](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4994588951/p50475.png)

    4.  Decompress the client package that is compatible with the operating system of your source server.

        The following figure shows the directories and files in the decompressed folder.

        ![Home directory of the client](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4994588951/p49979.png)

        |Folder or file|Description|
        |:-------------|:----------|
        |go2aliyun\_client.exe|The executable file of the command-line interface \(CLI\) program for Windows.|
        |go2aliyun\_gui.exe|The executable file of the graphical user interface \(GUI\) program for Windows. For more information, see [Use the Windows GUI version of an SMC client](/intl.en-US/Best Practices/Use the Windows GUI version of an SMC client.md).|
        |go2aliyun\_client|The executable file of the CLI program for Linux.|
        |user\_config.json|The configuration file of the migration source and destination.|
        |Excludes|The folder of the files and directories that are excluded from migration.|
        |client\_data|The migration data file. This includes the intermediate instance information and migration progress.|

2.  Optional. Exclude files or directories from migration.

    **Note:** If the source server supports block replication, you cannot exclude files or directories from migration.

    The configuration files are located in the Excludes directory of the SMC client. If a configuration file is lost or deleted by accident, you can create another one.

    -   System disk configuration file: rsync\_excludes\_win.txt \(for Windows servers\) or rsync\_excludes\_linux.txt \(for Linux servers\)

    -   Data disk configuration file: named by adding a suffix disk \[disk index number\] to the system disk, for example, rsync\_excludes\_win\_disk1.txt \(for Windows servers\) or rsync\_excludes\_linux\_disk1.txt \(for Linux servers\)

    -   Example 1: Exclude files or directories from migration of a Windows server
        -   System disk
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

        -   Data disk

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

            To exclude a Windows directory, perform the following operations:

            -   Remove the prefix of the directory \(scr\_path\). In the preceding example, you must remove `D:`.
            -   Replace `\` with `/`.
    -   Example 2: Exclude files or directories from migration of a Linux server
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

        -   Data disk

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

3.  Run the SMC client to import the migration source information.

    1.  Enter the SMC client folder and run the SMC client.

        -   For Windows servers, use one of the following methods to run the SMC client:

            -   To run the Windows GUI version, double-click the go2aliyun\_gui.exe file.
            -   To run the Windows CLI version, double-click the go2aliyun\_client.exe file.
            **Note:** When you run the program, you must click **OK** to confirm that you have the administrator privilege.

        -   For Linux servers, run the SMC client as a root or sudo user.

            -   In the directory of the go2aliyun\_client file, run the following commands as a root user:

                ```
                chmod +x go2aliyun_client
                ```

                ```
                ./go2aliyun_client
                ```

            -   In the directory of the go2aliyun\_client file, run the following commands as a sudo user:

                ```
                sudo chmod +x ./go2aliyun_client
                ```

                ```
                sudo ./go2aliyun_client
                ```

            If you have required permissions on the migration source system, you can also run the following commands to import the migration source information. In this case, you do not need to enter your AccessKey pair.

            -   Run the following command as a root user:

                ```
                ./go2aliyun_client --accessid=<Your AccessKeyID> --secretkey=<Your AccessKeySecret>
                ```

            -   Run the following command as a sudo user:

                ```
                sudo ./go2aliyun_client --accessid=<Your AccessKeyID> --secretkey=<Your AccessKeySecret>
                ```

    2.  Enter the AccessKey pair of your Alibaba Cloud account.

        **Note:** If the AccessKey pair you entered is invalid, open the user\_config.json file, delete the access\_id and secret\_key values, and then run the client again.

        -   For Windows servers
            -   If you use the Windows GUI version, enter the **AccessKey ID** in the **Access Id** field, enter the AccessKey secret in the Secret Key field, and then click **Start**. For more information, see [Use the Windows GUI version of the SMC client](/intl.en-US/Best Practices/Use the Windows GUI version of an SMC client.md).
            -   If you use the Windows CLI version, enter the AccessKey ID and AccessKey secret, and then press `Enter`.
        -   For Linux servers

            Enter the AccessKey ID and AccessKey secret, and then press `Enter`.

            ![Enter the AccessKey pair](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4994588951/p49934.png)

            The following prompts may appear:

            -   The rsync tool is installed in most mainstream migration sources. If rsync is not installed on the migration source, the SMC client displays a prompt. Enter yes to install rsync, as shown in the following figure.

                ![Install rsync](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4994588951/p50398.png)

            -   If SELinux is enabled on the migration source, you are prompted to disable SELinux. Enter yes to disable SELinux, as shown in the following figure.

                ![Disable SELinux](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4994588951/p50473.png)

    **Note:** Do not close the client until the migration is complete. Otherwise, the migration source will be disconnected from the SMC console and the migration fails.

4.  Log on to the [SMC console](https://smc.console.aliyun.com/).

5.  Create a migration task.

    1.  In the left-side navigation pane, click **Migration Sources**.

    2.  Find the migration source that you want to migrate.

        You can obtain the ID of the target migration source from the SMC client, as shown in the following figure. Then, you can use the ID to find the target migration source in the SMC console. For more information, see the "How do I find a migration source in the SMC console?" section of the [SMC FAQ](/intl.en-US/FAQ/SMC FAQ.md).

        ![Obtain the ID of the target migration source](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6994588951/p50022.png)

    3.  Click **Create Migration Task** in the Actions column.

    4.  In the **Create Migration Task** pane, read migration instructions and set the migration task parameters.

        The **Basic configuration** section includes the following parameters:

        -   **Target Region**: required. The ID of the destination region. For more information, see [Regions and zones]().
        -   **Task name**: the name of the migration task.

            **Note:** The task name must be unique in the destination region.

        -   **Description**: the description of the migration task.
        -   **Target Disk Size \(GiB\)**: the disk configuration of the destination server.

            ![Configure destination disks](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6994588951/p112652.png)

            The following table describes the parameters.

            |Parameter|Required|Description|
            |---------|--------|-----------|
            |**Enable Block Replication**|No|            -   Selected: Block replication ensures a stable data transmission rate during migration. This also ensures that the source and destination disks use the same partitioning scheme. You cannot modify the size of each partition in the destination disk. When you enable block replication, the **Whether to enable block replication** switch appears next to **Partition <N\>**.
            -   Cleared: SMC uses the default method to migrate the migration source. You can modify the size of each partition in the destination disk. |
            |**System Disk**|Yes|            -   **System Disk**: the system disk size of the destination ECS instance. Unit: GiB. Valid values: 20 to 500. The size of the destination system disk must be greater than the amount of data in the source system disk. For example, if the total size of the source system disk is 500 GiB but the size of data stored in this disk is only 100 GiB, you must set this parameter to a value greater than 100 GiB.

**Note:** The default value of this parameter is the size of the source system disk. We recommend that you retain the default value or specify a greater value.

            -   **Partition <N\>**: SMC generates a partitioning scheme for the destination system disk based on that of the source system disk. Unit: GiB. Valid values: 0 to 98. `N` indicates the serial number of the partition. For example, if the system disk of the migration source has only one partition, **Partition 0** is generated.
            -   **Whether to enable block replication**: This switch is available only when you select **Enable Block Replication**. If you want to turn on the switch, SMC allows or disallows you based on whether the migration source supports block replication.
                -   If the migration source does not support block replication for partitions, you are disallowed to turn on this switch.
                -   If the migration source supports block replication for partitions, you are allowed to turn on this switch to migrate disk data at the partition level. |
            |**Data Disk <N\>**|No|            -   **Data Disk <N\>**: the data disk size of the destination ECS instance. Unit: GiB. Valid values: 20 to 32768.
                -   If you select the **Data Disk <N\>** check box, a destination data disk is generated.
                -   `N` indicates the serial number of the data disk.
                -   The size of the destination data disk must be greater than that of the existing data in the source data disk. For example, if the total size of the source data disk is 500 GiB but the size of data stored in the disk is only 100 GiB, you must set this parameter to a value greater than 100 GiB.
            -   **Partition <N\>**: SMC generates a partitioning scheme for the destination data disk based on that of the source data disk. Unit: GiB. Valid values: 0 to 141. `N` indicates the serial number of the partition. For example, if a data disk of the migration source has only one partition, **Partition 0** is generated.
            -   **Whether to enable block replication**: This switch is available only when you select **Enable Block Replication**. If you want to turn on the switch, SMC allows or disallows you based on whether the migration source supports block replication.
                -   If the migration source does not support block replication for partitions, you are disallowed to turn on this switch.
                -   If the migration source supports block replication for partitions, you are allowed to turn on this switch to migrate disk data at the partition level.
**Note:** **Data Disk <N\>** is available only if the migration source has a data disk. For more information, see [Why are the data disk parameters of a migration source not displayed in the Create Migration Task pane? How can I resolve this issue?](/intl.en-US/FAQ/SMC FAQ.md) |

        -   **Target Image Type**: the type of the destination image. Valid values:
            -   **ECS Image**. The following table describes the parameters.

                |Parameter|Required|Description|
                |---------|--------|-----------|
                |**Image Name**|No|Specifies the name of the destination ECS image generated by SMC for the migration source. **Note:** The image name must be unique in the destination region. |
                |**Automatic incremental synchronization**|No|Specifies whether SMC automatically synchronizes incremental data of the migration source to Alibaba Cloud.                 -   To enable this feature, you must set the following parameters:

                    -   **Synchronization Interval**: the interval at which SMC automatically synchronizes incremental data to Alibaba Cloud.
                    -   **Maximum mirror retention**: the maximum number of images that can be retained during incremental migration.
SMC automatically synchronizes incremental data to Alibaba Cloud at the specified interval. For more information about best practices for incremental migration, see [Migrate incremental data from a source server](/intl.en-US/Best Practices/Migrate incremental data from a source server.md).

                -   If you disable this feature, incremental data is not synchronized. |

            -   **ECS Instance**. The following table describes the parameters.

                **Note:** The storage and operating systems of the source server and destination instance must be compatible. For more information, see [Migrate servers to ECS instances](/intl.en-US/Best Practices/Migrate servers to ECS instances.md).

                ![smc-instance](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6904865061/p176925.png)

                **Target Instance**: Select an ECS instance as the destination instance.

            -   **Container Image**. The following table describes the parameters.

                **Note:** SMC does not allow you to migrate Windows servers to Container Registry. For more information, see [Migrate source servers to Container Registry](/intl.en-US/Best Practices/Migrate source servers to Container Registry.md).

                |Parameter|Required|Description|
                |---------|--------|-----------|
                |**Namespace**|Yes|The namespace of the destination container image.|
                |**Repository Name**|Yes|The name of the repository that stores the destination container image.|
                |**Version**|No|The version of the destination container image.|
                |**RAM Role**|Yes|The instance RAM role that is attached to the intermediate instance.|

        -   **Method to Run**: specifies whether to run a task immediately after it is created and whether to automatically run the task.

            -   **Run Now**: The migration task runs immediately after it is created.
            -   **Run Later**: The migration task automatically runs at the specified time after it is created.

                **Note:** The earliest time that you can specify to run a migration task is 10 minutes after its creation.

            -   **Create Only**: After the task is created, you must manually start the task.
            Default value: **Run Now**.

        **Tag and Network \(Optional\)**:

        -   **Migration Task Tag**: the tags that you specify for the migration task. Each tag contains a key and a value. You can use tags to query and manage migration tasks.

            **Note:** You can specify a maximum of 20 tags for a migration task.

        -   **Network Type**: the type of the network that is used to migrate data to an intermediate instance. During migration, SMC creates an intermediate instance that connects to a VSwitch in a virtual private cloud \(VPC\). When you select Public Network, a public IP address is assigned to the intermediate instance.

            ![Network Type](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6994588951/p112663.png)

            The following table describes the parameters.

            |Parameter|Description|
            |---------|-----------|
            |**Public Network**|SMC migrates data to the intermediate instance over the Internet. If you select Public Network, make sure that the migration source can access the Internet. You can choose whether to specify a VPC and a VSwitch based on your requirements.             -   If you specify a VPC and a VSwitch, SMC creates an intermediate instance that connects to the specified VPC and VSwitch.

When you migrate multiple migration sources at a time, you can specify the same VPC and VSwitch for migration tasks. This improves the usage of VPC resources. You can migrate a maximum of 100 migration sources at a time.

            -   If you do not specify a VPC or a VSwitch, SMC automatically creates a VPC and a VSwitch and creates an intermediate instance that connects to the VPC and the VSwitch.

If you do not specify a VPC or a VSwitch before you migrate multiple migration sources at a time, SMC creates a VPC for each intermediate instance.

**Note:** Each Alibaba Cloud account can have a maximum of 10 VPCs in a region, including the VPCs that you create and the VPCs that are automatically created by SMC. Therefore, you can migrate a maximum of 10 migration sources at a time. To increase the VPC quota, [submit a ticket](https://workorder.console.aliyun.com/#/ticket/list/). |
            |**VPC**|SMC migrates data to the intermediate instance through a VPC. If you select VPC, you must specify a VPC and a VSwitch and make sure that the migration source can connect to the VPC. **Note:** If your server in the on-premises data center, virtual machine, or cloud host can connect to a VPC, we recommend that you select this mode to migrate data. Compared with data migration over the Internet, VPC-based data migration is more efficient and stable. You can use VPN Gateway, Express Connect, and Smart Access Gateway to connect a migration source to a VPC. For more information, see [Connect an on-premises data center to a VPC network](/intl.en-US/Network connection/VPC network connections/Connect an on-premises data center to a VPC network.md). |

        **Advanced Settings \(Optional\)**:

        -   **Transmission speed limit \(KB/S\)**: the maximum bandwidth for data transmission during migration. Unit: Kbit/s.

            The default value is 0, which indicates that the bandwidth is not limited.

        -   **Compression Level**: the compression ratio of data to be migrated. Set the compression ratio based on your requirements.

            -   If the bandwidth is limited, a high compression ratio improves the transmission efficiency.
            -   If a high bandwidth is available, we recommend that you do not compress data. Data compression consumes CPU resources of the migration source.
            The default value is 0, which indicates that data to be migrated is not compressed.

        -   **Checksum**: This feature enhances the verification of data consistency between the migration source and the destination server. However, this may slow the rate of data transmission.

            By default, this feature is disabled.

    5.  After the configuration is complete, click **OK**.

6.  Start the migration task.

    **Note:** If you set the Method to Run parameter to **Run Now**, skip this step. If you set the Method to Run parameter to **Create Only** or **Run Later**, you can perform the following steps to start the migration task:

    1.  In the left-side navigation pane, click **Migration Tasks**.

    2.  Find the target migration task and click **Start** in the Actions column.

        -   To start multiple migration tasks at a time, select the target tasks and click **Start/Retry** in the lower part of the Migration Tasks page. The status of the selected tasks must be **Ready**, **Stopped**, or **Error**.
        -   To suspend a migration task in the **Syncing** state, click **Pause** in the **Actions** column.

After the migration is complete, perform the following operations based on the destination image type:

-   ECS image: Create Elastic Compute Service \(ECS\) instances by using the custom image. For more information, see [Create an ECS instance by using a custom image](/intl.en-US/Instance/Create an instance/Create an ECS instance by using a custom image.md).
-   Container image: Deploy applications by using the container image. For more information, see [Migrate source servers to Container Registry](/intl.en-US/Best Practices/Migrate source servers to Container Registry.mdsection_840_v5e_lea).

## FAQ

Why am I unable to start or stop Linux instances in the Elastic Compute Service console?

You may be unable to start or stop Linux instances in the ECS console because some Linux kernels are customized by UCloud and may be incompatible with Alibaba Cloud. If your server runs the CentOS operating system, you can change the Linux kernels. For more information, visit [Active Versions of CentOS Linux](http://vault.centos.org/). For technical support, see [Contact us](/intl.en-US/FAQ/Contact us.md).

