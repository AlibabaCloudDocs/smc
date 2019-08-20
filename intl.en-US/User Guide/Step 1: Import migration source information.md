# Step 1: Import migration source information {#task_778498 .task}

Migration sources refer to IDC servers, virtual machines, cloud hosts on other platforms, or other types of servers that you want to migrate. When using SMC for a migration, you must first run the SMC client on the migration source to connect the migration source to your Alibaba Cloud account. This topic describes the operations and steps you need to complete on a migration source.

You must complete preparations before performing operations on migration sources. For more information, see [Preparations \(before you start\)](reseller.en-US/User Guide/Preparations (before you start).md#).

1.  Download and decompress the SMC client package. 
    1.  On the migration source, download the [SMC client](https://p2v-tools.oss-cn-hangzhou.aliyuncs.com/smc/Alibaba_Cloud_Migration_Tool.zip).
    2.  Decompress the SMC client package. The SMC client is available for Windows and Linux in both the 32-bit version \(i386\) and the 64-bit version \(x86\_64\). Select the version compatible with the migration source. The following figure shows the decompressed client folder.

        ![smc_client_1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630372/156629991450475_en-US.png)

    3.  Decompress the selected client version. The following figure shows the files and directories stored in the decompressed folder.

        ![smc-client-2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630335/156629991449979_en-US.png)

        |File or folder|Description|
        |:-------------|:----------|
        |go2aliyun\_client.exe|The Windows CLI executable file.|
        |go2aliyun\_gui.exe|The Windows GUI executable file. For more information about the GUI version, see [Use the Windows GUI version of the SMC client](../../../../reseller.en-US/Best Practices/Use the Windows GUI version of the SMC client.md#).|
        |go2aliyun\_client|The Linux CLI executable file.|
        |user\_config.json|The configuration file of the migration source and destination.|
        |Excludes|The folder in which to add directories to exclude from migration.|
        |client\_data|The migration data file, which includes the intermediate instance information and migration progress.|

2.  \(Optional\) Exclude files or directories from migration. Exclude files or directories that do not need to be migrated. For more information, see [Exclude files or directories from migration](../../../../reseller.en-US/Best Practices/Use the SMC client in one-time job mode.md#step_oa6_e16_n99).
3.  Run the SMC client to import migration source information. 

    1.  Run the SMC client. 
        -   For Windows servers, use one of the following methods to run the SMC client:

            -   To run the Windows GUI version, double-click the go2aliyun\_gui.exe program.
            -   To run the Windows CLI version, double-click the go2aliyun\_client.exe program.
            **Note:** When you run the program, you must confirm your administrator privileges by clicking **OK**.

        -   For Linux servers, select how to run the SMC client based on whether you have root or sudo permissions on the migration source system.

            -   In the directory where go2aliyun\_client is located, run the following commands as the root user:

                ``` {#codeblock_1o2_t9i_5md}
                chmod +x go2aliyun_client
                ```

                ``` {#codeblock_of8_0ul_zhq}
                ./go2aliyun_client
                ```

            -   In the directory where go2aliyun\_client is located, run the following commands with sudo permissions:

                ``` {#codeblock_08k_g2u_ahg}
                sudo chmod +x ./go2aliyun_client
                ```

                ``` {#codeblock_7cs_7wl_a8e}
                sudo ./go2aliyun_client
                ```

            **Note:** Based on your permissions on the migration source system, run the following commands to import the migration source information without entering the AccessKey pair.

            -   Run the following command as a root user:

                ``` {#codeblock_axy_o17_422}
                ./go2aliyun_client --accessid=<Your AccessKeyID> --secretkey=<Your AccessKeySecret>
                ```

            -   Run the following command with sudo permissions:

                ``` {#codeblock_wf4_7xs_4ud}
                sudo ./go2aliyun_client --accessid=<Your AccessKeyID> --secretkey=<Your AccessKeySecret>
                ```

    2.  Enter the AccessKey pair of your account. 

        **Note:** If the AccessKey pair you entered is incorrect, open the user\_config.json file, delete the `access_id` and `secret_key` values, and re-run the client.

        -   For Windows servers
            -   If you use the Windows GUI version, set **Access Id** and **Secret Key** on the GUI, and then click **Run**. For more information, see [Use the Windows GUI version of the SMC client in Daemon mode](../../../../reseller.en-US/Best Practices/Use the Windows GUI version of the SMC client.md#section_cno_ye6_d7w).
            -   If you use the Windows CLI version, set `AccessKeyId` and `AccessKeySecret` and press `Enter`.
        -   For Linux servers

            Set `AccessKeyId` and `AccessKeySecret` and press `Enter`.

            ![smc-client-3](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630335/156629991549934_en-US.png)

            **Note:** 

            -   Rsync is installed in most mainstream migration source systems. If Rsync is not installed on the migration source system, the SMC client will give a prompt. Enter `yes` to install Rsync, as shown in the following figure.

                ![smc-client-4](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630372/156629991550398_en-US.png)

            -   If SELinux is enabled on the migration source system, the SMC client will prompt you to disable SELinux. Enter `yes` to disable SELinux, as shown in the following figure.

                ![smc-client-5](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630372/156629991550473_en-US.png)

    **Note:** Do not close the client until the migration is complete. Otherwise, the migration source will be disconnected from the SMC console and the migration cannot be completed.


-   If `Import Source Server [s-bxxxxxxxxxxxx] Successfully!` is displayed, the migration source information has been imported to the SMC console, as shown in the following figure. Keep the client program up and running and log on to the SMC console to complete the migration. For more information, see [Step 2: Create and start a migration task](reseller.en-US/User Guide/Step 2: Create and start a migration task.md#).

    ![smc-client-6](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630372/156629991550399_en-US.png)

-   If `Error` or `Goto Aliyun Not Finished!` is displayed, the migration source information has failed to be imported, as shown in the following figure. We recommend that you check the cause, fix the problem, and then re-run the client. For more information about FAQ, see [SMC FAQ](../../../../reseller.en-US/FAQ/SMC FAQ.md#).

    ![smc-client-7](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/630372/156629991550400_en-US.png)


