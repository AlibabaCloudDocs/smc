# Use the Windows GUI version of an SMC client

Alibaba Cloud provides a Windows graphical user interface \(GUI\) version for a Server Migration Center \(SMC\) client. This allows you to migrate Windows servers to Alibaba Cloud. The settings for the SMC client on the GUI are the same as that on the command-line interface \(CLI\). The Windows GUI version is compatible with the CLI version.

## Daemon mode

In the daemon mode, you can import the migration source information by using the SMC client. Then, you can log on to the SMC console to complete the migration. You only need to configure **Access Id** and **Secret Key**. For more information, see [Migration process](/intl.en-US/User Guide/Migration process.md).

The following figure shows the Windows GUI in the daemon mode.

![Aliyun GUI](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1229177951/p139138.png)

## Menu items on the GUI

The following figure shows the menu items of the Windows GUI client.

![Windows GUI](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1229177951/p139783.png)

The following table describes the menu items.

|No.|Section|Description|
|:--|:------|:----------|
|①|Top navigation bar|Consists of the **Config**, **Logs**, **View**, **Help**, and **Language** menus. -   **Config**:
    -   Click **Rsync** to set the bandwidth limit for data transmission. Unit: KB/s.
    -   Click **Save User Config** to save the current settings for batch operations.
    -   Click **Clear Client Data** to initialize the client configuration file.
-   **Logs**:
    -   Click **Open Log File** to open the migration log file.
    -   Click **Open Logs Dir** to find the path of the migration log file.
-   **View**: Select **Hide Progress Log** to hide the **Progress Logs** column.
-   **Help**: Obtain online documentation or the version information of the SMC client.
-   **Language**: Select the display language of the GUI. |
|②|Custom configuration section|Allows you to configure **Access Id** and **Secret Key**.The settings you configure are written to the user\_config.json file of the SMC client. |
|③|Task progress and log section|Allows you to view the task progress or troubleshoot issues as prompted after you run the SMC client.|

