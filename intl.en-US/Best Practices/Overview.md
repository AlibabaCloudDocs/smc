# Overview

This topic describes the best practices for using Server Migration Center \(SMC\) in different scenarios.

## Background information

SMC is a migration platform developed by Alibaba Cloud. You can use SMC to migrate data from your servers to Alibaba Cloud. SMC provides multiple features and benefits to simplify data migration. For more information, see [What is SMC?](/intl.en-US/Product Introduction/What is SMC?.md)

## Scenarios

You can use SMC to migrate data in the following scenarios.

|Scenario|Description|
|--------|-----------|
|[Use the SMC plug-in of Cloud Assistant to import the information of a source server](/intl.en-US/Best Practices/Use the SMC plug-in of Cloud Assistant to import the information of a source server.md)|If you have installed a Cloud Assistant client on your server, you can use the built-in SMC plug-in to import the server information in a convenient and efficient manner.|
|[Use the Windows GUI version of an SMC client](/intl.en-US/Best Practices/Use the Windows GUI version of an SMC client.md)|If your server uses Windows, you can use the Windows GUI version of an SMC client to import the server information.|
|[Migrate incremental data from a source server](/intl.en-US/Best Practices/Migrate incremental data from a source server.md)|If you need to synchronize data changes from your server to Alibaba Cloud, we recommend that you perform an incremental migration.|
|[Migrate source servers to Container Registry](/intl.en-US/Best Practices/Migrate source servers to Container Registry.md)|SMC allows you to migrate servers to Container Registry. You can use SMC to migrate containerized applications to Container Registry at low costs. Containerized applications are distributed applications that are managed in an automatic manner and deployed with high agility and low security risks. Application containerization improves resource usage and reduces computing costs.|
|[Migrate servers to ECS instances](/intl.en-US/Best Practices/Migrate servers to ECS instances.md)|SMC allows you to migrate servers to Elastic Compute Service \(ECS\) instances. After you purchase an ECS instance, you can migrate your server to the ECS instance.|
|[Estimate the time required for migration and test the data transfer speed](/intl.en-US/Best Practices/Estimate the time required for migration and test the data transfer speed.md)|You can estimate the migration duration and the data transfer rate.|
|[Migrate servers over a VPC](/intl.en-US/Best Practices/Migrate servers over a VPC.md)|If your server can connect to a virtual private cloud \(VPC\) from your data center, virtual machine, or cloud host, we recommend that you migrate data over a VPC. Compared with migration over the Internet, migration over a VPC is more efficient and stable.|
|[Enable multi-threaded transfer acceleration](/intl.en-US/Best Practices/Enable multi-threaded transfer acceleration.md)|You can enable multithreading data transfer to utilize the maximum bandwidth. This allows you to improve transfer efficiency in high-bandwidth scenarios.|
|[Install GRUB on a Linux server](/intl.en-US/Images/FAQ/Install GRUB on a Linux server.md)|SMC allows you to migrate a Linux server to Alibaba Cloud. However, for earlier operating systems, such as CentOS 5, Red Hat 5, and Debian 7, you must upgrade GRUB to version 1.99 or later. For Amazon Linux, you must upgrade GRUB to version 2.02 or later.|

