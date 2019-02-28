## SAMBA 服务

> [samba配置参考链接](https://www.cnblogs.com/lxyqwer/p/7271369.html)

### 安装

    yum -y install samba
    
    yum -y install samba-client 

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



    （以下内容均来自网络学习）
    root用户执行
    1、使用yum -y install samba samba-client samba-common安装Samba
     　　rpm -qi samba可以查看samba版本信息
    [root@MiWiFi-R1CM-srv samba]# rpm -qi samba
    Name        : samba
    Epoch       : 0
    Version     : 4.2.10
    Release     : 6.2.el7_2
    Architecture: x86_64
    Install Date: Tue 19 Jul 2016 03:26:55 AM CST
    Group       : System Environment/Daemons
    Size        : 1895784
    License     : GPLv3+ and LGPLv3+
    Signature   : RSA/SHA256, Fri 24 Jun 2016 04:12:11 AM CST, Key ID 24c6a8a7f4a80eb5
    Source RPM  : samba-4.2.10-6.2.el7_2.src.rpm
    Build Date  : Fri 24 Jun 2016 02:38:45 AM CST
    Build Host  : worker1.bsys.centos.org
    Relocations : (not relocatable)
    Packager    : CentOS BuildSystem <http://bugs.centos.org>
    Vendor      : CentOS
    URL         : http://www.samba.org/
    Summary     : Server and Client software to interoperate with Windows machines
    Description :
    Samba is the standard Windows interoperability suite of programs for Linux and Unix.
    [root@MiWiFi-R1CM-srv samba]#

    2、设置开机启动：
    # systemctl enable smb.service

    3、查看是否设置成功
    # systemctl status smb.service

    4、启动samba服务
    # systemctl start smb.service

    5、再次查看启动状态
    # systemctl status smb.service

    [root@MiWiFi-R1CM-srv samba]# systemctl status smb.service
    ● smb.service - Samba SMB Daemon
       Loaded: loaded (/usr/lib/systemd/system/smb.service; enabled; vendor preset: disabled)
       Active: active (running) since Tue 2016-07-19 03:32:36 CST; 12min ago
     Main PID: 27455 (smbd)
       Status: "smbd: ready to serve connections..."
       CGroup: /system.slice/smb.service
               ├─27455 /usr/sbin/smbd
               ├─27460 /usr/sbin/smbd
               └─27601 /usr/sbin/smbd

    Jul 19 03:32:36 MiWiFi-R1CM-srv systemd[1]: Starting Samba SMB Daemon...
    Jul 19 03:32:36 MiWiFi-R1CM-srv systemd[1]: smb.service: Supervising process 27455 which is not our child. We'll most likely not n... exits.
    Jul 19 03:32:36 MiWiFi-R1CM-srv systemd[1]: Started Samba SMB Daemon.
    Jul 19 03:32:36 MiWiFi-R1CM-srv smbd[27455]: [2016/07/19 03:32:36.184968,  0] ../lib/util/become_daemon.c:124(daemon_ready)
    Jul 19 03:32:36 MiWiFi-R1CM-srv smbd[27455]:   STATUS=daemon 'smbd' finished starting up and ready to serve connections
    Hint: Some lines were ellipsized, use -l to show in full.
    [root@MiWiFi-R1CM-srv samba]#

    6、配置配置文件
    进入目录：
    # cd /etc/samba

    备份：
    # cp smb.conf smb.conf.backup

    修改smb.conf文件，找到“[homes]”，修改以下设置：

    [global]
        log file = /var/log/samba/log.%m
        load printers = yes
        cups options = raw
        server string = Samba Server Version %v
        writeable = yes
        force directory mode = 777
        force create mode = 777
        workgroup = MYGROUP
        security = user
        create mode = 777
        passdb backend = tdbsam
        max log size = 50

    新版的samba放在smb.conf最后是无效的

    7、添加用户
    # smbpasswd -a username

    如果出现bash: smbpasswd: command not found，就是没有安装samba-client了
    附： smbpasswd命令的常用方法
    smbpasswd -a 增加用户（要增加的用户必须以是系统用户）
    smbpasswd -d 冻结用户，就是这个用户不能在登录了
    smbpasswd -e 恢复用户，解冻用户，让冻结的用户可以在使用
    smbpasswd -n 把用户的密码设置成空.要在global中写入 null passwords -true
    smbpasswd -x 删除用户

    8、selinux设置
    # getsebool -a | grep samba
    # setsebool -P samba_enable_home_dirs on

    9、防火墙，使用新的防火墙firewall添加就可以，比iptables更方便
    # firewall-cmd --list-services

    # firewall-cmd --permanent --add-service=samba

    # firewall-cmd --reload

    # firewall-cmd --list-services

    由于redhat7开始，iptables被firewalld代替了，所以使用firewalld的方法
    关于firewalld的说明，可以看fedora官网介绍
    https://fedoraproject.org/wiki/FirewallD/zh-cn

    10、重启samba服务

    # systemctl restart smb.service
