# Limits

This topic describes the limits that apply to Server Migration Center \(SMC\).

-   The following table lists the limits on the number of migration sources and tasks.

    |Item|Limit|Adjustable|
    |----|-----|----------|
    |Number of migration sources that can be registered|100|Submit a ticket.|
    |Number of migration tasks that can be created|100|Submit a ticket.|
    |Number of migration tasks that can be concurrently executed|20|Submit a ticket.|

-   You can create only one migration task for each source server. If the migration task of a source server is unfinished, you cannot create a new migration task for the source server. A migration task is regarded as unfinished if it is in the Ready, Running, Stopped, InError, or Expired state.
-   A virtual private cloud \(VPC\) is created for each intermediate instance. Each Alibaba Cloud account can have a maximum of 10 VPCs in a region, including your own VPCs and the VPCs created for the intermediate instances. To raise the VPC quota, [submit a ticket](https://workorder.console.aliyun.com/#/ticket/list/).
-   You must use Grand Unified Bootloader \(GRUB\) V1.99 or later for migration sources that run the Linux operating system. For more information, see [Install GRUB in a Linux server](/intl.en-US/Images/FAQ/Install GRUB in a Linux server.md).

    **Note:** You must use GRUB V2.02 or later for earlier versions of operating systems such as CentOS 5, Red Hat 5, Debian 7, Amazon Linux, and Oracle Linux.

-   The SMC client is supported by the following operating systems.

    |Windows|Linux|
    |:------|:----|
    |    -   Windows Server 2003
    -   Windows Server 2008
    -   Windows Server 2012
    -   Windows Server 2016
    -   Windows Server 2019
|    -   CentOS 5/6/7/8
    -   Red Hat 5/6/7/8
    -   Ubuntu 10/12/14/16/17/18/19/20
    -   Debian 7/8/9
    -   OpenSUSE 13/42/15
    -   SUSE 11/12/15
    -   Gentoo 13.0
    -   Alibaba Cloud Linux
    -   Oracle Linux 5/6/7/8
    -   Amazon Linux 2014 and later |


