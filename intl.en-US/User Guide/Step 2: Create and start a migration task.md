# Step 2: Create and start a migration task

After you import the information of a migration source, Server Migration Center \(SMC\) automatically generates a record of the migration source. You must create and start a migration task for the migration source in the SMC console. This topic describes how to create and start a migration task.

-   The information of a migration source is imported. For more information, see [Step 1: Import the information of a migration source](/intl.en-US/User Guide/Step 1: Import the information of a migration source.md).
-   The migration source is in the Active state. If the migration source is not in the Active state, you cannot create a migration task for the migration source. For more information about how to restore a migration source to the Active state, see the "What can I do if I cannot create a migration task because a migration source is not in the Active state?" section of the [SMC FAQ](/intl.en-US/FAQ/SMC FAQ.mdsection_weo_he3_b2a).

-   SMC can obtain the partitioning scheme of a source disk used by the migration source and generate the same partitioning scheme for the destination disk. This also improves the data transmission rate during migration.
-   You can use the migration template provided by SMC to create multiple migration tasks at a time. For more information, see [Import multiple migration tasks by using an Excel template](/intl.en-US/Best Practices/Import multiple migration tasks by using an Excel template.md).

1.  Log on to the [SMC console](https://smc.console.aliyun.com/).

2.  Create a migration task.

    1.  In the left-side navigation pane, click **Migration Sources**.

    2.  Find the migration source that you want to migrate.

        You can obtain the ID of the target migration source from the SMC client, as shown in the following figure. Then, you can use the ID to find the target migration source in the SMC console. For more information, see the "How do I find a migration source in the SMC console?" section of the [SMC FAQ](/intl.en-US/FAQ/SMC FAQ.mdsection_7hf_tn4_x5i).

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
            |**VPC**|SMC migrates data to the intermediate instance through a VPC. If you select VPC, you must specify a VPC and a VSwitch and make sure that the migration source can connect to the VPC. **Note:** If your server in the on-premises data center, virtual machine, or cloud host can connect to a VPC, we recommend that you select this mode to migrate data. Compared with data migration over the Internet, VPC-based data migration is more efficient and stable. You can use VPN Gateway, Express Connect, and Smart Access Gateway to connect a migration source to a VPC. For more information, see [Connect an on-premises data center to a VPC network](/intl.en-US/VPC network connections/Connect an on-premises data center to a VPC network.md). |

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

3.  Start the migration task.

    **Note:** If you set the Method to Run parameter to **Run Now**, skip this step. If you set the Method to Run parameter to **Create Only** or **Run Later**, you can perform the following steps to start the migration task:

    1.  In the left-side navigation pane, click **Migration Tasks**.

    2.  Find the target migration task and click **Start** in the Actions column.

        -   To start multiple migration tasks at a time, select the target tasks and click **Start/Retry** in the lower part of the Migration Tasks page. The status of the selected tasks must be **Ready**, **Stopped**, or **Error**.
        -   To suspend a migration task in the **Syncing** state, click **Pause** in the **Actions** column.

-   On the Migration Tasks page, wait until the migration task is complete. If the task enters the **Completed** state, the migration is successful.
    -   If you set Target Image Type to ECS Image, you can perform the following steps to create an ECS instance by using an image:
        1.  Verify the migration result. This feature verifies whether the image generated by the migration task can create and start instances. This verification is based on the Operation Orchestration Service \(OOS\) template named ACS-SMC-CreateAndVerifyInstance provided by Alibaba Cloud.
            1.  Click **Verify Migration Result** in the Actions column.
            2.  In the dialog box that appears, read the verification process, and click **Verify Now**.

                You can also click **Custom Verification Script** to set the parameters.

            3.  View the verification result in the **Last Migration Result** column.
                -   **Successful**: indicates that the migration is successful. You can click **View Output Parameter** to check the details.
                -   **Failed**: indicates that the migration failed. You can click **View Cause** to view the cause of failure and troubleshoot errors.
                -   You can also click the ![...](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9714973061/p169257.png) icon in the Actions column, and then click **Check Verification History in the OOS Console** to view the template history.
        2.  Click **Create Instance** in the Actions column.

            ![list](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6994588951/p129881.png)

        3.  Set the parameters to create the destination instance. For more information, see [Create an ECS instance by using a custom image](/intl.en-US/Instance/Create an instance/Create an ECS instance by using a custom image.md).
        4.  Connect to the destination instance and check its system. For more information, see the "[How do I check my system after I migrate a Windows server?](/intl.en-US/FAQ/SMC FAQ.md)" or "[How do I check my system after I migrate a Linux server?](/intl.en-US/FAQ/SMC FAQ.mdsection_8nx_71l_ksv)" section of the SMC FAQ.
    -   If you set Target Image Type to ECS Instance, you can click **View Target Instance** in the Actions column to go to the Target Instance page.
    -   If you set Target Image Type to Container Image, you can use a container image to deploy applications.**** For more information, see [Migrate source servers to Container Registry](/intl.en-US/Best Practices/Migrate source servers to Container Registry.mdsection_840_v5e_lea).

        ![smc docker](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6180963061/p134837.png)

-   If the migration task enters the **Error** state, the migration failed. You must perform the following steps:
    1.  Click **View Logs** in the **Actions** column. For information about common errors and solutions, see [SMC FAQ](/intl.en-US/FAQ/SMC FAQ.md).
    2.  On the Migration Tasks page, restart the migration task. The migration task resumes from the point where it was suspended.

        **Note:** If the intermediate instance is released, you must create another migration task. For more information, see the "What can I do if I have released an intermediate instance by mistake?" section of the [SMC FAQ](/intl.en-US/FAQ/SMC FAQ.mdsection_1nu_xd1_bip).


