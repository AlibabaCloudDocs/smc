# 导入迁移源（Linux） {#task_593142 .task}

迁移源符合迁移条件后，您需要配置阿里云账号的访问密钥并运行客户端主程序，将迁移源信息导入SMC控制台。

您已创建并获取子账号的访问密钥（AccessKey）。详情请参见[创建AccessKey](../../../../cn.zh-CN/通用参考/创建AccessKey.md#)。

**说明：** AccessKey是您访问阿里云API资源的重要凭证，请妥善保管。为防止AccessKey泄漏或被滥用，建议您使用子账号创建临时的AccessKey，在迁移完成之后再禁用该AccessKey。

1.  打开客户端主目录下的user\_config.json文件。 Linux版本客户端的介绍及文件说明，请参见[Linux版本客户端](../../../../cn.zh-CN/.md#section_uor_69k_kd8)。
2.  配置子账号的访问密钥（AccessKey）。 
    -   access\_id：访问密钥的AccessKeyId。
    -   secret\_key：访问密钥AccessKeySecret。
3.  保存后，关闭文件。
4.  运行以下命令，将迁移源信息导入SMC控制台。 

    ``` {#codeblock_hia_4ty_7sg}
    sudo chmod +x ./go2aliyun_client
    sudo ./go2aliyun_client --daemon
    ```


客户端会将您的迁移源导入SMC控制台，迁移源状态为在线。

登录SMC控制台，前往迁移源页面查看您的迁移源并新建迁移任务。

