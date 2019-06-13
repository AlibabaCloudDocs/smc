# SMC FAQ {#concept_610474 .concept}

-   [如何安装Rsync？](#section_6ai_ig1_k06)
-   [如何关闭SELinux？](#section_t4z_f8i_hkt)

## 如何安装Rsync？ {#section_6ai_ig1_k06 .section}

请您根据源服务器的操作系统选择相应的命令安装。

-   CentOS：运行`yum -y install rsync`。
-   Ubuntu：运行`apt-get -y install rsync`。
-   Debian：运行`apt-get -y install rsync`。
-   SUSE：运行`zypper install rsync`。
-   其他发行平台系统：参见发行版官网的安装文档。

## 如何关闭SELinux？ {#section_t4z_f8i_hkt .section}

您可以采用下列方法关闭SELinux：

-   运行`setenforce 0`命令临时关闭SELinux。
-   修改/etc/selinux/config文件，配置`SELINUX=disabled`永久禁用SELinux。

