# Estimate the time required for migration and test the data transfer speed

A migration period is divided into three phases: pre-migration, migration, and post-migration. A migration period is proportional to the number of servers to be migrated and the actual data volume. We recommend that you perform tests in advance to estimate the migration time. This topic describes how to estimate the time required for migration and how to test the data transfer speed.

If you need to migrate a server, Server Migration Center \(SMC\) first creates an intermediate instance for your account. Then, the system transfers data from the source server to the intermediate instance and creates an Elastic Compute Service \(ECS\) image for the intermediate instance. Therefore, the migration time is the sum of the data transfer time and the time to create an image. For more information, see [Estimate the time required for migration](#section_la1_hkl_a7b).

During a migration process, the speed of data transfer from the source server to the intermediate instance is the primary factor that determines the migration time. For more information, see [Test the data transfer speed](#section_9lq_702_evs).

In some cases, errors may occur.

-   The following table lists the possible causes and solutions if the data transfer speed is lower than the measured speed.

    |Possible cause|Solution|
    |--------------|--------|
    |The source server and the intermediate instance are in different regions or countries. Data transfer across regions and countries is sometimes slower than that in the same region.|Check whether the network for the source server is the same as that for the intermediate instance in the destination Alibaba Cloud region. If the problem is caused by cross-region transfer, you can perform the following steps:

    -   Migrate the source server to Alibaba Cloud by generating an image in the same region, and then copy the image to the destination region. For more information, see [Copy custom images](/intl.en-US/Images/Custom image/Copy custom images.md).
    -   Check whether the problem stems from the network service provider. |
    |The outbound bandwidth of the source server and the inbound bandwidth of the intermediate instance are used for migration. The bandwidth of the intermediate instance is limited. By default, the maximum inbound public bandwidth is 100 Mbit/s. Therefore, the maximum transmission speed over the Internet is 100 Mbit/s by default.|To resolve this error, you can use one of the following methods:    -   Method 1: Find the intermediate instance or destination instance in the ECS console. Convert the public IP address of the instance to a pay-as-you-go elastic IP address \(EIP\). Increase the peak bandwidth of the pay-as-you-go EIP to 200 Mbit/s. You are charged for upgrading the peak bandwidth of a pay-as-you-go EIP. For more information, see [Convert the public IP address of a VPC-type instance to an Elastic IP address](/intl.en-US/Network/Change IPv4 addresses/Convert the public IP address of a VPC-type instance to an Elastic IP address.md) and [Modify the bandwidth of an EIP](/intl.en-US/Instance/Change configurations/Modify bandwidth configurations/Modify the bandwidth of an EIP.md).

**Note:** If the public IP address of an instance is converted to a pay-as-you-go EIP, the IP address cannot be restored to its initial state. Therefore, you must manually release the pay-as-you-go EIP after the migration to avoid additional charges. For more information, see [Release an EIP](/intl.en-US/User Guide/Manage Pay-As-You-Go-billed EIPs/Release an EIP.md).

    -   Method 2: If the source server can access a virtual private cloud \(VPC\) network in an Alibaba Cloud region, we recommend that you perform migration over the **VPC network**. Compared with data migration over the Internet, VPC-based data migration is more efficient and stable. You can use VPN Gateway, Express Connect, and Smart Access Gateway to connect a migration source to a VPC. For more information, see [Connect an on-premises data center to a VPC network](/intl.en-US/Network connection/VPC network connections/Connect an on-premises data center to a VPC network.md). |
    |The source server has performance bottlenecks. For example, limited CPU, memory, and disk performance result in poor SMC transfer efficiency.|Improve the performance of the source server. For example, you can improve the CPU, memory, and disk performance.|
    |By default, the SMC client uses a single-threaded data transfer model, which may have bottlenecks in some network environments.|Enable multi-threaded transfer acceleration to maximize bandwidth utilization. For more information, see [Enable multi-threaded transfer acceleration](/intl.en-US/Best Practices/Enable multi-threaded transfer acceleration.md).|

-   This section describes the solutions to low outbound bandwidth.

    If the outbound bandwidth of the source server is low, for example, lower than 10 Mbit/s, you can modify the **Compression Level** parameter in the **Advanced Settings \(Optional\)** section. A high compression ratio improves transfer efficiency.


**Note:** The examples in this topic are for reference only.

## Estimate the time required for migration

The following figure shows how to estimate the time required for migration. In the preceding rules:

-   A snapshot is created at a speed of about 30 MB/s.
-   For more information about how to test the network speed, see [Test the data transfer speed](#section_9lq_702_evs).

![evaluate_migration_time](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6229177951/p67548.png)

If a server has an actual disk usage of 10 GB and an outbound bandwidth of 10 Mbit/s, you can use the following method to estimate the migration time:

1.  Convert units.

    -   Actual data volume: 10 GB = 10 × 1024 = 10240 MB
    -   Actual network speed: 10 Mbit/s = 10/8 = 1.25 MB/s
2.  Calculate the data transfer time.

    Data transfer time: 10240/1.25 = 8192 seconds = 2.27 hours

3.  Calculate the time required to create the image.

    Image creation time: 10240/30 = 341 seconds = 0.09 hours

4.  Calculate the time required for migration.

    Migration time: 2.27 + 0.09 = 2.36 hours


## Test the data transfer speed

The speed of data transfer from the source server to the intermediate instance is determined by the outbound bandwidth of the source server and the inbound bandwidth of the intermediate instance. By default, the inbound bandwidth of the intermediate instance is 200 Mbit/s. You can submit a ticket to increase the bandwidth.

For example:

-   Assume that the outbound bandwidth of the source server is 100 Mbit/s and the inbound bandwidth of the intermediate instance is 200 Mbit/s. The actual transmission speed is limited by the source server and does not exceed 100 Mbit/s.
-   Assume that the outbound bandwidth of the source server is 300 Mbit/s and the inbound bandwidth of the intermediate instance is 200 Mbit/s. The actual transmission speed is limited by the source server and does not exceed 200 Mbit/s.

**Note:** The instance bandwidth of 1 Mbit/s displayed in the ECS console is the outbound bandwidth of the intermediate instance. The 1 Mbit/s bandwidth does not affect the actual migration speed because the inbound bandwidth of the intermediate instance is used during migration.

To test the transfer speed by using iPerf, perform the following steps:

1.  Create a pay-as-you-go ECS instance in the destination Alibaba Cloud region.

2.  In the ECS instance, perform the following steps:

    1.  Install iPerf.

    2.  Start iPerf as a server.

    3.  Add a rule to the security group of the instance to allow traffic on the ports required by iPerf.

3.  On the source server, perform the following steps:

    1.  Install iPerf.

    2.  Start iPerf as a client. Set the IP address of the destination server to the public IP address of the pay-as-you-go instance created in [Step 1](#step_nyw_91l_z4c).


## Example of performing a transfer speed test on a Linux instance

A CentOS 7 instance is used in the following example. The operations may vary with the version of your operating system.

1.  Create a pay-as-you-go CentOS 7 instance in the destination Alibaba Cloud region.

2.  Add an inbound rule to the security group of the ECS instance to allow traffic on the ports required by iPerf.

    The default port for iPerf, TCP 5001, is used in this example.

3.  Connect to the CentOS 7 instance.

4.  In the CentOS 7 instance, perform the following steps:

    1.  Run the following command to install iPerf:

        ```
        yum -y install iperf3
        ```

    2.  Run the following command to start iPerf as a server:

        ```
        iperf3 -s
        ```

5.  On the source server, perform the following steps:

    1.  Download and install iPerf.

    2.  Run the following command to start iPerf as a client:

        Replace `<Instance IP address>` in the command with the public IP address of the created instance.

        ```
        iperf3 -c <Instance IP address> -i 1 -d  
        ```

6.  Wait until the iPerf test is complete, and then record the test results.


## Example of performing a transfer speed test on a Windows instance

A Windows Server 2008 instance is used in the following example. The operations may vary with the version of your operating system.

1.  Create a pay-as-you-go Windows Server 2008 instance in the destination Alibaba Cloud region.

2.  Add an inbound rule to the security group of the ECS instance to allow traffic on the ports required by iPerf.

    The default port for iPerf, TCP 5001, is used in this example.

3.  Connect to the instance.

4.  In the Windows Server 2008 instance, perform the following steps:

    1.  Download and install iPerf.

    2.  Open Command Prompt.

    3.  Run the `cd <directory where iPerf is located>` command to go to the tool directory.

    4.  Run the `iperf3.exe -s` command to start iPerf as a server.

5.  On the source server, perform the following steps:

    1.  Download and install iPerf.

    2.  Run the following command to start iPerf as a client:

        Replace `<Instance IP address>` in the command with the public IP address of the created instance.

        ```
        iperf3.exe -c <Instance IP address> -i 1 -d
        ```

6.  Wait until the iPerf test is complete, and then record the test results.


**Related topics**  


[Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md)

[Add security group rules](/intl.en-US/Security/Security groups/Add security group rules.md)

[OverviewGuidelines on instance connection](/intl.en-US/Instance/Connect to instances/Overview.md)

