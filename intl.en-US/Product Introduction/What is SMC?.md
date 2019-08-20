# What is SMC? {#concept_592998 .concept}

Server Migration Center \(SMC\) is a migration platform developed by Alibaba Cloud. SMC allows you to migrate one or more migration sources to Alibaba Cloud. Migration sources refer to IDC servers, virtual machines, cloud hosts on other platforms, or other types of servers that you want to migrate.

## Benefits {#section_zh5_u7v_u8q .section}

-   An underlying environment independent of migration sources

    SMC supports physical-to-cloud \(P2C\), virtual-to-cloud \(V2C\), and cloud-to-cloud \(C2C\) migrations for a variety of file systems and disk types.

-   Automatic collection of migration source information

    You do not need to manually configure system settings for migration sources. After running the relevant commands, the SMC client automatically collects the migration source information and imports it to the SMC console to prepare for subsequent migration operations.

-   Ease of use

    The SMC console allows you to easily configure migration tasks and migrate data to the cloud.

-   Support for batch migration

    You can select multiple migration tasks in the SMC console and perform a batch migration.

-   Central tracking of migration progress

    When migrating source servers to Alibaba Cloud in batches, you must track the migration status of each source server. The SMC console overview page displays the status of all your migration sources and tasks. It shows the overall migration progress and allows you to identify and troubleshoot problems that occur during migration.


## Migration process {#section_th2_8wh_pd3 .section}

SMC consists of a client and a console. The following figure shows the migration process of SMC. For more information, see [Migration process](../../../../reseller.en-US/User Guide/Migration process.md#).

![migrationFlow](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/475582/156629948550105_en-US.png)

