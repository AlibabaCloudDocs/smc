# Migrate servers to ECS instances

Server Migration Center \(SMC\) allows you to migrate servers to Elastic Compute Service \(ECS\) instances. After you purchase an ECS instance, you can migrate your source server to an ECS instance. This topic describes how to migrate a server to an ECS instance.

-   The migration preparations are complete. For more information, see [Before you begin](/intl.en-US/User Guide/Before you begin.md).
-   An ECS instance is created. Make sure that the instance has no data or the data of the instance has been backed up by using images, snapshots, or other resources.

    **Warning:**

    -   After a migration task is created, all original data on the destination ECS instance is deleted. If the ECS instance contains important data, we recommend that you select ECS Image as the destination image type, and then create an ECS instance by using a custom image.
    -   If you migrate data from an ECS instance, you must make sure that the source ECS instance and the destination ECS instance are different. Otherwise, the migration may fail and data in the cloud disk of the source instance may be lost.
-   The information of the server is imported to the SMC console. For more information, see [Step 1: Import the information of a migration source](/intl.en-US/User Guide/Step 1: Import the information of a migration source.md).

    **Note:** Make sure that the SMC client is running during migration. If data transfer is interrupted, you can restart the client and the migration task to resume the migration.

-   The operating system of the ECS instance is the same as that of the server.
-   The number of data disks attached to the ECS instance is greater than or equal to that of the data disks attached to the server. Otherwise, you must attach more data disks to the ECS instance. For more information, see [Attach a data disk](/intl.en-US/Block Storage/Cloud disks/Attach a data disk.md).
-   The size of the system disks and data disks attached to the ECS instance is greater than or equal to that of the system disks and data disks attached to the server. Otherwise, you must scale up the data disks and system disks. For more information, see [Overview](/intl.en-US/Block Storage/Resize cloud disks/Overview.md).

## Procedure

1.  Log on to the [SMC console](https://smc.console.aliyun.com/).

2.  In the left-side navigation pane, click **Migration Sources**.

3.  Find the source server from which you want to migrate data. Click **Create Migration Task** in the **Actions** column.

4.  On the **Create Migration Task** page, set the required parameters.

    Set the following parameters to configure the ECS instance. For information about other parameters, see [Step 2: Create and start a migration task](/intl.en-US/User Guide/Step 2: Create and start a migration task.md).

    ![smc](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4214065061/p176825.png)

    -   **Target Image Type**: Select **ECS Instance**.
    -   **Target Instance**: Select an ECS instance based on your needs. After you select an ECS instance, the disk information of the instance is displayed.
    -   **Tag and Network \(Optional\)**: By default, the value of the **Network Type** parameter is the VPC that the ECS instance resides.
    The migration task immediately starts after it is created. Then, the migration task enters the Finished or InError state.

    -   If the migration task enters the **Finished** state, the task is completed and you can view the ECS instance.
    -   If the migration task enters the **InError** state, the task failed. You must check logs to troubleshoot the failure and restart the migration task. For information about common errors and solutions, see [SMC FAQ](/intl.en-US/FAQ/SMC FAQ.md).

**Related topics**  


[CreateReplicationJob](/intl.en-US/API Reference/Migration tasks/CreateReplicationJob.md)

