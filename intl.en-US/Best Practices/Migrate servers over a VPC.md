# Migrate servers over a VPC

If your server can connect to a virtual private cloud \(VPC\) from your data center, virtual machine, or cloud host, we recommend that you migrate data over a VPC. Compared with migration over the Internet, migration over a VPC is more efficient and stable.

-   A server is connected to a VPC by using VPN Gateway, Express Connect, or Smart Access Gateway \(SAG\). For more information, see [Connect an on-premises data center to a VPC network](/intl.en-US/Network connection/VPC network connections/Connect an on-premises data center to a VPC network.md).
-   Ports 8703 and 8080 are configured on the firewall of your server. This ensures that data can be transferred between the server and the intermediate instance.

The following table lists the scenarios where you can migrate servers over a VPC. The table also provides the solutions for these scenarios.

|Scenario|Solution|
|--------|--------|
|Your server cannot access the Internet.|Connect the server to a VPC by using VPN Gateway, Express Connect, or SAG, configure a proxy server, and then use the proxy server to access SMC.|
|Your server can access the Internet and you can migrate the server to SMC over the Internet. However, you want to increase the data transfer rate.|Connect the server to a VPC by using VPN Gateway, Express Connect, or SAG. Then, specify VPC as the network type when you create a migration task. Compared with migration over the Internet, migration over a VPC is more efficient.|

## Migration process

Migration process:

1.  Download the [SMC client](https://p2v-tools.oss-cn-hangzhou.aliyuncs.com/smc/Alibaba_Cloud_Migration_Tool.zip?file=Alibaba_Cloud_Migration_Tool.zip) package and install the SMC client on the source server.
2.  Run the SMC client on the source server and use the proxy server to import the information of the source server to the SMC console. For more information about proxy servers, see[Forward proxies](#section_fef_t9b_m2l).
3.  Create a migration task, specify VPC as the network type, and then start the task.
4.  SMC creates resources based on the migration task configurations and migrates data from the source server to Alibaba Cloud over a VPC.
5.  During the migration, the proxy server replaces the source server. Then, the proxy server receives instructions from the SMC console. For example, if an error occurs during the migration task, SMC stops the migration and sends an error log to the SMC client.

Perform the following steps during the migration:

1.  Create a proxy server in the VPC used to access the source server.

    **Note:** If your source server can access the Internet, skip this step.

    You can deploy a proxy server on the cloud by using the image of a forward proxy provided by Alibaba Cloud. After the proxy server is deployed, you must ensure that it is connected to the source server and can access the SMC console \(`smc.aliyuncs.com`\). For information about how to join the technical support group on DingTalk and deploy the proxy server based on an image, see [Contact us](/intl.en-US/FAQ/Contact us.md).

2.  Download and install an SMC client on the source server, and import the information of the source server to the SMC console.

    For more information, see[Step 1: Import the information of a migration source](/intl.en-US/User Guide/Step 1: Import the information of a migration source.md). Before you import the information of the source server, take note of the following information:

    -   If you do not need a proxy server, you can directly import the information of the source server.
    -   If you need a proxy server, you must configure the proxy server information in the configuration file of your SMC client. Then, you can run the client to import the information of the source server. In the following example, Linux is used to show the procedure of configuring the proxy server:
        1.  In the `go2aliyun_client` directory, run the following command to open `client_data`:

            ```
            vim client_data
            ```

        2.  Find the parameters of `proxy`, as shown in the following figure.

            ![proxy](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2434854161/p232563.png)

        3.  Set the `ip_port` to the IP address and port number of the proxy server.

            Example:

            ```
            "proxy": {
                "ip_port": "172.31. **.**:8080",
                "user_pwd": ""
            }
            ```

            After the configuration is complete, press the Esc key, enter `:wq`, and then press the Enter key to save and exit the configuration file.

3.  In the SMC console, import and run the migration task.

    For more information, see [Step 2: Create and start a migration task](/intl.en-US/User Guide/Step 2: Create and start a migration task.md). When you create a migration task, you must set **Network Type** to **VPC**, and specify a VPC and vSwitch. Make sure that the VPC can be connected to the source server.

    ![Network type](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2434854161/p232570.png)


## Forward proxies

If your source server cannot be accessed over the Internet, you must migrate the server over a private network. Make sure that the source server meets the following conditions:

-   The server is connected to a VPC by using VPN Gateway, Express Connect, or Smart Access Gateway \(SAG\).
-   A proxy server is configured for the source server and the information of the source server is imported to the SMC console.

This section describes forward proxies.

A forward proxy is a proxy server that is located between a client and a server. If the client cannot access the server over the Internet, a proxy server can be configured to communicate with the client and then send requests to the server. After the server receives the requests, it sends responses to the proxy server. Then, the proxy server sends the responses to the client.

A forward proxy has the following benefits:

-   Allows clients to access data resources on the Internet.
-   Caches Internet data that clients frequently access. When such data is accessed for the second time, it can be directly retrieved from the cache. This increases the resource access efficiency for the clients.
-   Grants access permissions to clients and ensures data security on client computers.
-   Hides client information and stores access logs when clients access Internet resources.

**Related topics**  


[What is SMC?](/intl.en-US/Product Introduction/What is SMC?.md)

[SMC FAQ](/intl.en-US/FAQ/SMC FAQ.md)

