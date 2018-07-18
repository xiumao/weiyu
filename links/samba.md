## SAMBA 服务

> [samba配置参考链接](https://www.cnblogs.com/lxyqwer/p/7271369.html)

### 安装

    yum -y install samba

    systemctl restart smb

    useradd root  

    pdbedit -a root  

### 配置

vim /etc/samba/smb.conf

    [global]

          workgroup = MYGROUP

    [wwwroot]
           path = /
           public = yes
           browseable = yes
           writable = yes
           write list = root
           valid users = root

### 测试

    [root@myhost2 ~]# smbclient  -U user //192.168.4.7/tools（共享名）
    Enter user's password:                 //输入samba用户user的密码
    Domain=[SAMBA] OS=[Windows 6.1] Server=[Samba 4.2.3]
    smb: \> ls
    .                                   D        0  Fri Jul 28 22:02:25 2017
    ..                                 DR        0  Fri Jul 28 21:32:58 2017
                                D        0  Fri Jul 28 22:02:25 2017

### 帮助

    1、客户端登录samba时出现以下提示：
    session setup failed: NT_STATUS_LOGON_FAILURE
    该错误提示表示用户有误，可能是用户不存在，也可能是密码错误，或者只是在samba用户和系统用户及密码出现错误，总之就是用户和密码的问题。
    tree connect failed: NT_STATUS_BAD_NETWORK_NAME
    该错误表示坏的网络名，表示共享目录不存在，或共享目录权限问题
    可用setfacl -m给用户加权限
    Connection to 192.168.4.7 failed (Error NT_STATUS_HOST_UNREACHABLE)
    2、客户端连接到samba共享目录时出现以下提示：
    smb: \> ls
    NT_STATUS_ACCESS_DENIED listing \*
    文件权限不足，或者存在selinux限制
    调整文件的权限，并打开selinux开关
    3、执行setsebool -P 操作启用SElinux开关参数时失败，提示：Killed
    内存不足，而且交换空间也不足
    添加交换分区（1GB）在重试
