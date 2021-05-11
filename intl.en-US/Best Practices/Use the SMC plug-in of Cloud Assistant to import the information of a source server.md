# Use the SMC plug-in of Cloud Assistant to import the information of a source server

If you have installed a Cloud Assistant client on your source server, you can use the SMC plug-in to import the information of the source server in a convenient and efficient manner. This topic describes how to use the SMC plug-in to import the information of a source server in Linux and Windows.

-   The preparations for using SMC are completed. For more information, see [Before you begin](/intl.en-US/User Guide/Before you begin.md).
-   A Cloud Assistant client later than 2.2.1.107 is installed on the source server.
    -   If your source server is an ECS instance, a Cloud Assistant client is installed by default. You need to call the [DescribeCloudAssistantStatus](/intl.en-US/API Reference/Cloud assistant/DescribeCloudAssistantStatus.md) API operation to view the version of the Cloud Assistant client installed on the ECS instance. If you are using an early version of Cloud Assistant, you need to upgrade the client to a version later than 2.2.1.107. For more information, see [Update or disable updates for the Cloud Assistant client](/intl.en-US/Deployment & Maintenance/Cloud assistant/Configure the Cloud Assistant client/Update or disable updates for the Cloud Assistant client.md).
    -   If your source server is not an ECS instance, you must manually install a Cloud Assistant client later than 2.2.1.107. For more information, see [Install the Cloud Assistant client](/intl.en-US/Deployment & Maintenance/Cloud assistant/Configure the Cloud Assistant client/Install the Cloud Assistant client.md).

To ensure stable migration, we recommend that you exclude directories that store dynamic data, such as data directories of large databases. Then, you can stop the services that are running on the server and start the migration task. For information about how to exclude directories that store dynamic data without stopping services, see [Step 1: Import the information of a migration source](/intl.en-US/User Guide/Step 1: Import the information of a migration source.md).

**Note:** If the data stored on the source server is required after migration, you can save the data and upload it to the destination server.

## Import the information of the source server on a Linux server

1.  Run the following command to view the list of Cloud Assistant plug-ins and make sure that the plug-ins are available:

    ```
    acs-plugin-manager -l
    ```

    If the following information is displayed, the `smc-client-plugin` plug-in is available.

    ![smc-client-plugin-linux](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0990730261/p264940.png)

2.  Run the following command to import the information of the source server:

    ```
    acs-plugin-manager -e -P smc-client-plugin -p --accessid=<AccessKey ID\>,--secretkey=<AccessKey Secret\>,--nocheckversion
    ```

    <AccessKey ID\> and <AccessKey Secret\> indicates the AccessKey pair of your Alibaba Cloud account. Make sure that you have created an AccessKey pair. For more information, see [Create an AccessKey pair]().

    If the following information is displayed, the information of the source server is imported.

    ![smc-success-linux](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0990730261/p264964.png)

    After the information of the source server is imported, SMC automatically generates a record of the migration source. You must create and start a migration task for the migration source in the SMC console. For more information, see [Step 2: Create and start a migration task](/intl.en-US/User Guide/Step 2: Create and start a migration task.md).


## Import the information of the source server on a Windows server

1.  Go to the installation directory of the Cloud Assistant client.

    -   If your source server is an ECS instance, the default installation directory of the Cloud Assistant client is C:\\ProgramData\\aliyun\\assist\\<Cloud Assistant version number\>, for example, `C:\ProgramData\aliyun\assist\2.1.1.140`.

        **Note:** The `C:\ProgramData` folder is hidden. Therefore, you must show hidden folders in advance. You must also ensure the data security of this folder to prevent system exceptions caused by misoperations.

    -   If your source server is not an ECS instance, you must go to the installation directory of the Cloud Assistant client.
2.  In the installation directory of the Cloud Assistant client, press the Shift key and right-click the blank area at the same time. Then, click **Open command window here**.

3.  Run the following command to view the list of Cloud Assistant plug-ins and make sure that the plug-ins are available:

    ```
    acs-plugin-manager.exe -l
    ```

    If the following information is displayed, the `smc-client-plugin` plug-in is available.

    ![smc-client-plugin-win](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0990730261/p264981.png)

4.  Run the following command to import the information of the source server:

    ```
    acs-plugin-manager.exe -e -P smc-client-plugin-win -p --accessid=<AccessKey ID\>,--secretkey=<AccessKey Secret\>,--nocheckversion
    ```

    <AccessKey ID\> and <AccessKey Secret\> indicates the AccessKey pair of your Alibaba Cloud account. Make sure that you have created an AccessKey pair. For more information, see [Create an AccessKey pair]().

    Then, a command window appears. If the following information is displayed, the information of the source server is imported.

    ![smc-success-win](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0990730261/p264983.png)

    After the information of the source server is imported, SMC automatically generates a record of the migration source. You must create and start a migration task for the migration source in the SMC console. For more information, see [Step 2: Create and start a migration task](/intl.en-US/User Guide/Step 2: Create and start a migration task.md).


