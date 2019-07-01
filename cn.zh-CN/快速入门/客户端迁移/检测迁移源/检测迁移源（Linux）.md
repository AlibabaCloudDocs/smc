# 检测迁移源（Linux） {#task_593176 .task}

迁移之前，您需要完成迁移前各项检查工作，并使用客户端的client\_check脚本检测迁移源是否满足迁移条件。

1.  确保迁移源的系统时间与其所在地域的标准时间一致。
2.  确保迁移源能访问下列网址及端口。 
    -   VPC：https://vpc.aliyuncs.com:443。
    -   STS：https://sts.aliyuncs.com:443。
    -   SMC：https://smc.aliyuncs.com:443。
    -   ECS：https://ecs.aliyuncs.com:443。

        **说明：** 更多地域的ECS API接入地址，请参见[接入地址](../../../../cn.zh-CN/API参考/快速入门/请求结构.md#section_mtp_xvb_wdb)。

    -   中转实例：端口8080和8703。

        **说明：** 中转实例是SMC自动创建的临时实例。迁云过程中出现网络连接问题时，您需要运行以下命令确认迁移源可以访问中转实例的8080和8703端口。

        ``` {#d7e56}
        telnet xxx.xx.xxx.xx 8080  #xxx.xx.xxx.xx为中转实例公网IP地址。当使用VPC内网迁移时，xxx.xx.xxx.xx为中转实例私网IP地址。
        telnet xxx.xx.xxx.xx 8703  #xxx.xx.xxx.xx为中转实例公网IP地址。当使用VPC内网迁移时，xxx.xx.xxx.xx为中转实例私网IP地址。
        ```

3.  检查授权应用。迁移到阿里云后，系统底层硬件设备会发生变化，可能会导致一些跟硬件绑定的应用许可证（license）失效，您需要做好检查。
4.  运行SMC客户端client\_check脚本，检测迁移源是否满足迁云条件。 检测项结果说明如下：

    -   检测项结果为`FAILED`，表示该检测项不符合迁移条件。

        您需要根据提示信息，修复问题后，再重新运行检测工具，直至所有检测项的结果均为`OK`。常见问题的修复方案如下：

        -   GRUB版本过低，需升级至1.99版本以上（部分Amazon Linux需升级至2.02版本以上）。具体步骤请参见[如何为Linux服务器安装GRUB](../../../../cn.zh-CN/镜像/常见问题/如何为Linux服务器安装GRUB.md#)。
        -   virtio驱动未安装，请参见[安装virtio驱动](../../../../cn.zh-CN/镜像/自定义镜像/导入镜像/安装virtio驱动.md#)。
        -   SELinux未关闭，请参见[如何关闭SELinux？](../../../../cn.zh-CN/.md#section_t4z_f8i_hkt)。
        -   Rsync未安装，请参见[如何安装Rsync？](../../../../cn.zh-CN/.md#section_6ai_ig1_k06)。
        -   cloud-init版本与阿里云不兼容。请卸载迁移源中的cloud-init，或安装阿里云cloud-init（具体步骤请参见[安装cloud-init](../../../../cn.zh-CN/镜像/自定义镜像/导入镜像/安装cloud-init.md#)）。
    -   检测项结果为`OK`，表示该检测项符合迁移条件。
    当所有检测项结果均为`OK`时，您可以进入下一步。


