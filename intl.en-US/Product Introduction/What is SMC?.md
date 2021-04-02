# What is SMC?

Server Migration Center \(SMC\) is a server migration platform developed by Alibaba Cloud. SMC allows you to migrate one or more source servers to Alibaba Cloud. Source servers can be servers in data centers, virtual machines, servers on other cloud platforms, and servers of other types.

## Features

SMC supports automatic data migration from one or more source servers to Alibaba Cloud. SMC provides the following features:

-   Incremental migration

    You can synchronize incremental data of a source server to Alibaba Cloud without interrupting your services. For more information, see [Migrate incremental data from a source server](/intl.en-US/Best Practices/Migrate incremental data from a source server.md).

-   Migrate multiple servers at a time
    -   You can start multiple migration tasks at a time in the SMC console.
    -   You can call the API operations of SMC to create and start migration tasks, query migration progress, and manage multiple migration tasks at a time. For more information, see [API operations](/intl.en-US/API Reference/API operations.md).
-   Block replication

    SMC can obtain the partitioning scheme of a source disk and replicate the partitioning scheme for the destination disk. You can specify the size of each partition of a destination disk. For more information, see [Migration task parameters](/intl.en-US/User Guide/Step 2: Create and start a migration task.md).

-   Data migration to Container Registry

    SMC allows you to migrate servers to Container Registry. You can use SMC to migrate containerized applications to Container Registry at low costs. Containerized applications are distributed applications that are managed in an automatic manner and deployed with high agility and low security risks. Application containerization improves resource usage and reduces computing costs. For more information, see [Migrate source servers to Container Registry](/intl.en-US/Best Practices/Migrate source servers to Container Registry.md).

-   Multi-threading data transmission

    The SMC client supports multi-threading data transmission. This feature improves the bandwidth usage and transmission efficiency if a high bandwidth is available. For more information, see [Enable multi-threaded transfer acceleration](/intl.en-US/Best Practices/Enable multi-threaded transfer acceleration.md).

-   Centralized monitoring of task processes
    -   When you migrate multiple source servers to Alibaba Cloud at a time, SMC allows you to monitor the migration status of each source server.
    -   You can view the status of each source server and migration task on the Overview page of the SMC console. This allows you to identify and troubleshoot issues that may occur during migration.

## Benefits

-   Migration from diverse platforms and environments
    -   SMC allows you to migrate source servers that run various versions of Windows and Linux operating systems. For more information, see [Limits](/intl.en-US/Product Introduction/Limits.md).
    -   SMC allows you to migrate data from servers in data centers, local virtual machines \(VMs\), and third-party cloud platforms to Alibaba Cloud. Supported VMs include VMware, VirtualBox, Xen, KVM, and Hyper-V. Third-party cloud platforms can be Amazon Web Services \(AWS\), Microsoft Azure, Google Cloud Platform \(GCP\), HUAWEI CLOUD, Tencent Cloud, UCloud, China Telecom e-Cloud, and QingCloud.

        ![Support for migration from diverse platforms](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8422834951/p71294.png)

-   Independence from the underlying environments of source servers
    -   SMC supports the following types of migration: physical-to-cloud \(P2C\), virtual-to-cloud \(V2C\), and cloud-to-cloud \(C2C\).
    -   SMC supports multiple types of file systems and disks.
-   Migration without service interruption

    During migration, you do not need to stop services that run on the source servers.

-   Simple, lightweight, and flexible configuration
    -   SMC provides a lightweight client that does not require installation.
    -   SMC provides multiple migration methods. You can select a method based on your needs.
    -   After you start a migration task, SMC manages the entire migration progress.
-   Secure data transmission
    -   By default, SMS uses 2048-bit RSA keys to encrypt data during data transmission.
    -   SMS allows you to migrate servers over the private network such as VPN gateway and physical connections provided by Alibaba Cloud Express Connect.

## Migration procedure

SMC consists of the SMC client and the SMC console. The following figure shows how to use SMC for migration. For more information, see [Migration process](/intl.en-US/User Guide/Migration process.md).

![smc2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8422834951/p92698.png)

## Pricing

When you use SMC, you are charged only for Alibaba Cloud Elastic Compute Service \(ECS\) resources that you use during migration. For more information, see [Pricing](/intl.en-US/Pricing/Pricing.md).

## Technical support

For information about how to obtain technical support, see [Contact us](/intl.en-US/FAQ/Contact us.md).

