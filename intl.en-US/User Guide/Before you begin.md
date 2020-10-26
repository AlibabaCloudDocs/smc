# Before you begin

Before you use Server Migration Center \(SMC\) to perform migration, you must create an Alibaba Cloud account, add funds to the account, and complete the real-name verification.

## Procedure

Before you start a migration task, perform the following steps:

1.  On the [Alibaba Cloud official website](https://account.alibabacloud.com/register/intl_register.htm), create an Alibaba Cloud account.
2.  Associate a credit card or PayPal account with your Alibaba Cloud account.

    For more information, see [Add a payment method](https://www.alibabacloud.com/help/doc-detail/50517.htm).

3.  Before you migrate servers to mainland China, complete the real-name verification.

    Use one of the following verification methods:

    -   Method 1: Go to the [real-name verification](https://account-intl.console.aliyun.com/#/intlAuth) page.
    -   Method 2: Log on to the [SMC console](https://smc.console.aliyun.com). You are prompted to complete the real-name verification.
4.  Make sure that Resource Access Management \(RAM\) is activated and SMC is authorized to access your cloud resources.

    Use one of the following methods to authorize SMC:

    -   Method 1: Log on to the [RAM console](https://ram.console.aliyun.com/#/role/authorize?request=%7B%22Requests%22:%20%7B%22request1%22:%20%7B%22RoleName%22:%20%22AliyunSMCDefaultRole%22,%20%22TemplateId%22:%20%22DefaultRole%22%7D%7D,%20%22ReturnUrl%22:%20%22https:%2F%2Fsmc.console.aliyun.com%2F%22,%20%22Service%22:%20%22SMC%22%7D), and click **Confirm Authorization Policy** to complete authorization.
    -   Method 2: Log on to the [SMC console](https://smc.console.aliyun.com). You are prompted to authorize a RAM user.
    RAM user authorization: Use your Alibaba Cloud account to log on to the [RAM console](https://ram.console.aliyun.com/users), and grant the AliyunSMCFullAccess permission to the RAM user.

5.  Create the AccessKey pair for your Alibaba Cloud account or RAM user and obtain the AccessKey pair. For more information, see [Create an AccessKey]().

    **Note:** AccessKey pairs are credentials that you can use to access Alibaba Cloud API resources. Therefore, we recommend that you keep your AccessKey pair strictly confidential. We recommend that you use a RAM user to create a temporary AccessKey pair and then disable the AccessKey pair after the migration is complete. This prevents the AccessKey pair from being leaked or misused.

6.  Make sure that the snapshot service is activated. For more information, see [Activate ECS Snapshot](/intl.en-US/Snapshots/Use snapshots/Activate ECS Snapshot.md).

## Usage notes

Before you use SMC to perform migration, note the following information:

-   Do not perform operations on the intermediate instance.

    To run a migration task, SMC creates a temporary intermediate instance named `No_Delete_SMC_Transition_Instance` for your Alibaba Cloud account. For more information, see [What are the specifications available for intermediate instances?](/intl.en-US/FAQ/SMC FAQ.md) Do not stop, restart, or release the intermediate instance during a migration task. Otherwise, the migration task fails. After the migration is complete, the intermediate instance is released.

-   By default, the following data directories are migrated:
    -   For Windows servers: Only data on the C drive \(including shared directories that are attached to the C drive\) is migrated as a partition of the system disk. If you need to migrate the data from other partitions such as the D drive, you must select and configure the data disk when you create a migration task. For more information, see [Migration task parameters](/intl.en-US/User Guide/Step 2: Create and start a migration task.md).
    -   For Linux servers: Data in all subdirectories \(including shared subdirectories\) in the root directory is migrated as a partition of the system disk. If you need to migrate the data in other directories such as /disk1, you must select and configure the data disk when you create a migration task. For more information, see [Migration task parameters](/intl.en-US/User Guide/Step 2: Create and start a migration task.md). If you do not need to migrate the data of multiple directories, see [\(Optional\) Exclude files or directories from migration](/intl.en-US/User Guide/Step 1: Import the information of a migration source.md).

