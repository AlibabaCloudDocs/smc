# Preparations \(before you start\) {#concept_778499 .concept}

Before using SMC for a migration, you must prepare an Alibaba Cloud account and read the migration precautions.

## Prepare an Alibaba Cloud account {#section_1yg_nf4_rco .section}

1.  On the [Alibaba Cloud official website](https://account.aliyun.com/register/register.htm), create an account.
2.  Ensure that you have completed real-name authentication.

    The authentication methods are as follows:

    -   Method 1: Go to the [real-name authentication](https://account.console.aliyun.com/v2/#/authc/types) page to complete authentication.
    -   Method 2: Log on to the [SMC console](https://smc.console.aliyun.com). If you have not completed real-name authentication, the console will prompt you to do so.
3.  Ensure that you have activated the RAM service and authorized SMC to access your cloud resources.

    The authorization methods are as follows:

    -   Method 1: Log on to the [RAM console](https://ram.console.aliyun.com/#/role/authorize?request=%7B%22Requests%22:%20%7B%22request1%22:%20%7B%22RoleName%22:%20%22AliyunSMCDefaultRole%22,%20%22TemplateId%22:%20%22DefaultRole%22%7D%7D,%20%22ReturnUrl%22:%20%22https:%2F%2Fsmc.console.aliyun.com%2F%22,%20%22Service%22:%20%22SMC%22%7D), and click **Confirm Authorization Policy** to complete authorization.
    -   Method 2: Log on to the [SMC console](https://smc.console.aliyun.com). If you have not authorized a RAM role, the console will prompt you to do so.
4.  Ensure that you have created and obtained the AccessKey pair of your Alibaba Cloud account or RAM user account. For more information, see [Create an AccessKey](../../../../reseller.en-US/General Reference/Create an AccessKey.md#).

    **Note:** AccessKey pairs are important credentials to access Alibaba Cloud API resources, and must be kept strictly confidential. To prevent your AccessKey pair from being exposed or misused, we recommend that you use a RAM user account to create a temporary AccessKey pair, and then disable the AccessKey pair after migration.


## Precautions {#section_vee_kc6_gfl .section}

-   Do not perform operations on the intermediate instance.

    During a migration, SMC will create a temporary intermediate instance named `No_Delete_SMC_Transition_Instance` under your Alibaba Cloud account to assist in the migration. For more information about the intermediate instance types, see [What specifications are available for intermediate instances?](../../../../reseller.en-US/FAQ/SMC FAQ.md#section_lii_mn5_7ki). To avoid migration failures, do not stop, restart, or release the intermediate instance during the migration. After the migration is complete, the intermediate instance will be automatically released.

-   By default, the following data directories are migrated:

    -   For Windows servers: Only data on the C drive \(including shared directories attached to the C drive\) is migrated as a partition of the system disk. If you want to migrate data on other partitions such as the D drive, you must select and configure the data disk when creating a migration task. For more information, see [Data disk parameter settings](reseller.en-US/User Guide/Step 2: Create and start a migration task.md#table_pv7_ll3_9ko).
    -   For Linux servers: Data on all subdirectories \(including shared directories\) in the root directory \(/\) is migrated as a partition of the system disk. If you want to migrate data on other directories such as /disk1, you must select and configure the data disk when creating a migration task. For more information, see [Data disk parameter settings](reseller.en-US/User Guide/Step 2: Create and start a migration task.md#table_pv7_ll3_9ko). If you do not need to migrate data on some directories, see [\(Optional\) Exclude files or directories from migration](reseller.en-US/User Guide/Step 1: Import migration source information.md#step_4dv_fwg_doq).
-   Incremental data migration is not allowed.

    We recommend that you stop applications such as databases and containers, or [filter specified data directories](../../../../reseller.en-US/FAQ/SMC FAQ.md#section_9xm_osd_b9i) before a migration and then synchronize these data directories after the migration.


