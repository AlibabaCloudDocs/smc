# Overview

This topic describes the best practices for using Server Migration Center \(SMC\) in different scenarios.

## Background information

SMC is a migration platform developed by Alibaba Cloud. You can use SMC to migrate data from your servers to Alibaba Cloud. SMC provides multiple features and benefits to simplify data migration. For more information, see [What is SMC?](/intl.en-US/Product Introduction/What is SMC?.md).

## Scenarios

You can use SMC to migrate data in the following scenarios:

-   If you migrate data from a server to Alibaba Cloud for the first time, we recommend that you perform a full migration. For more information, see [Migration process](/intl.en-US/User Guide/Migration process.md).
-   If you need to synchronize data changes from a server to Alibaba Cloud, we recommend that you perform an incremental migration. For more information, see [Migrate incremental data from a source server](/intl.en-US/Best Practices/Migrate incremental data from a source server.md).
-   If your server in the data center, virtual machine, or cloud host can connect to a VPC, we recommend that you migrate data over a VPC. Compared with migration over the Internet, migration over a VPC is more efficient and stable. For more information, see [t2038252.md\#]().
-   If you need to migrate data from multiple servers, you can import the information of the servers to SMC, and then import migration tasks in batches. For more information, see [Import multiple migration tasks by using an Excel template](/intl.en-US/Best Practices/Import multiple migration tasks by using an Excel template.md).
-   You can estimate the migration duration and the data transfer rate. For more information, see [Estimate the time required for migration and test the data transfer speed](/intl.en-US/Best Practices/Estimate the time required for migration and test the data transfer speed.md).
-   You can enable multithreading data transfer to utilize the maximum bandwidth. This allows you to improve transfer efficiency in high-bandwidth scenarios. For more information, see [Enable multi-threaded transfer acceleration](/intl.en-US/Best Practices/Enable multi-threaded transfer acceleration.md).
-   If your server can access a VPC in the destination region of data migration, we recommend that you migrate the server over the VPC. When you create a migration task, select VPC as the network type. For more information, see [Step 2: Create and start a migration task](/intl.en-US/User Guide/Step 2: Create and start a migration task.md). For more information about how to connect the server to a VPC, see [Connect an on-premises data center to a VPC network](/intl.en-US/Network connection/VPC network connections/Connect an on-premises data center to a VPC network.md).
-   If you need to migrate data from a server that runs an outdated operating system, you must first upgrade GRand Unified Bootloader \(GRUB\) to version 1.99 or later. Outdated operating systems include CentOS 5, RHEL 5, and Debian 7. If the operating system of the server is Amazon Linux, you must upgrade GRUB to version 2.02 or later. For more information about how to install GRUB, see [Install GRUB in a Linux server](/intl.en-US/Images/FAQ/Install GRUB on a Linux server.md).

