# 检测迁移源（Windows） {#task_593106 .task}

迁移之前，您需要完成各项检查工作，确保网络可以连通及迁移所需的配置正确，提升迁移上云的成功率。

1.  确保迁移源的系统时间与其所在地域的标准时间一致。
2.  确保迁移源能访问下列网址及端口。 
    -   VPC：https://vpc.aliyuncs.com:443。
    -   STS：https://sts.aliyuncs.com:443。
    -   SMC：https://smc.aliyuncs.com:443。
    -   ECS：https://ecs.aliyuncs.com:443。

        **说明：** 更多地域的ECS API接入地址，请参见[接入地址](../../../../cn.zh-CN/API参考/快速入门/请求结构.md#section_mtp_xvb_wdb)。

    -   中转实例：端口8080和8703。

        **说明：** 中转实例是SMC自动创建的临时实例。迁云过程中出现网络连接问题时，您需要运行以下命令确认迁移源可以访问中转实例的8080和8703端口。

        ``` {#codeblock_sg3_doi_any}
        telnet xxx.xx.xxx.xx 8080  #xxx.xx.xxx.xx为中转实例公网IP地址。当使用VPC内网迁移时，xxx.xx.xxx.xx为中转实例私网IP地址。
        telnet xxx.xx.xxx.xx 8703  #xxx.xx.xxx.xx为中转实例公网IP地址。当使用VPC内网迁移时，xxx.xx.xxx.xx为中转实例私网IP地址。
        ```

3.  检查授权应用。迁移到阿里云后，系统底层硬件设备会发生变化，可能会导致一些跟硬件绑定的应用许可证（license）失效，您需要做好检查。

