# Limits {#concept_593068 .concept}

SMC has the following limits.

-   The following table lists the limits for the number of migration sources and tasks.

    |Item|Limit|Exception application \(increase limit\)|
    |----|-----|----------------------------------------|
    |Number of registrable migration sources|100|Submit a ticket|
    |Number of migration tasks that can be created|100|Submit a ticket|
    |Number of migration tasks that can be executed concurrently|20|Submit a ticket|

-   Each migration source can only be associated with a single unfinished migration task. Unfinished states include Ready, Running, Stopped, InError, and Expired.
-   Each intermediate instance creates a VPC. Each Alibaba Cloud account can have a maximum of 10 VPCs in a region, including your own VPCs and the VPCs created by intermediate instances. To raise the VPC quota, submit a ticket.
-   You must use Grand Unified Bootloader \(GRUB\) V1.99 or later for migration sources running the Linux operating system. For more information about how to install GRUB, see [Install GRUB v1.99 in a Linux server](../../../../reseller.en-US/Images/FAQ/Install GRUB v1.99 in a Linux server.md#).

    **Note:** 

    -   You must use GRUB V1.99 or later for earlier versions of operating systems such as CentOS 5, Red Hat 5, and Debian 7.
    -   You must use GRUB V2.02 or later for some operating systems such as Amazon Linux.
-   The SMC client applies to the following operating systems.

    |Windows|Linux|
    |:------|:----|
    |     -   Windows Server 2003
    -   Windows Server 2008
    -   Windows Server 2012
    -   Windows Server 2016
 |     -   Amazon Linux 2014 and later
    -   CentOS 5/6/7
    -   Debian 7/8/9
    -   Gentoo 13.0
    -   OpenSUSE 13.1
    -   Oracle Linux 5/6/7
    -   Red Hat 5/6/7
    -   SUSE 11.4/12.1/12.2
    -   Ubuntu 10/12/14/16/17
 |


