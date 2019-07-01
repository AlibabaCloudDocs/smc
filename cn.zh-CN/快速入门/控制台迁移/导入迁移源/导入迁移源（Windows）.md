# 导入迁移源（Windows） {#task_593133 .task}

迁移源符合迁移条件后，您需要配置阿里云账号的访问密钥并运行客户端主程序，将迁移源信息导入SMC控制台。

您已创建并获取子账号的访问密钥（AccessKey）。详情请参见[创建AccessKey](../../../../cn.zh-CN/通用参考/创建AccessKey.md#)。

**说明：** AccessKey是您访问阿里云API资源的重要凭证，请妥善保管。为防止AccessKey泄漏或被滥用，建议您使用子账号创建临时的AccessKey，在迁移完成之后再禁用该AccessKey。

SMC客户端支持Windows GUI版本和Windows命令行版本。其中Windows GUI版本仅支持客户端迁云，因此您需要使用Windows命令行版本导入Windows系统迁移源。Windows命令行版本客户端详情，请参见[Windows命令行版本客户端](../../../../cn.zh-CN/.md#section_t4z_3c5_8ug)。

1.  打开客户端主目录下的user\_config.json文件。 
2.  配置子账号的访问密钥（AccessKey）。 
    -   access\_id：访问密钥的AccessKeyId。
    -   secret\_key：访问密钥AccessKeySecret。
3.  保存并关闭文件。
4.  运行客户端主程序go2aliyun\_client.exe将迁移源信息导入SMC控制台。 
    1.  打开cmd窗口。
    2.  进入SMC客户端所在目录。
    3.  运行`go2aliyun_client.exe --daemon`命令。

客户端会将您的迁移源导入SMC控制台，迁移源状态为在线。

登录SMC控制台，前往迁移源页面查看您的迁移源并新建迁移任务。

