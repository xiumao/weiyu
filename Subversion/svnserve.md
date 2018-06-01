## svnserve 安装

> yum install subversion  

> svnserve --version

### 命令

    ps aux | grep svn

    kill -9 pid

### 修改默认数据目录

    vi /etc/sysconfig/svnserve

将这行代码

    OPTIONS="-r /var/svn";

修改为

    OPTIONS="-r /home/svnrepo";

然后创建仓库根目录

    mkdir /home/svnrepo   

创建版本库

    vnadmin create /home/svnrepo/test

创建完成后进到/home/svnrepo/test/conf目录下

修改 authz、passwd、svnserve.conf 这三个文件

vi authz 添加下面的代码

    [/]  
    admin = rw  

vi passwd 添加账号对应的密码

    admin = 123456  

vi svnserve.conf 把下面五行代码前的注释;打开，并修改为下面所示。

    anon-access = none # 未登录用户不给任何权限
    auth-access = write # 授权用户的权限
    authz-db = authz # 用户权限配置文件
    password-db = passwd # 用户密码配置文件
    realm = spring-hello-world # 版本库的认证域，在登录时提示的认证域名称

### 启动SVN服务

    sudo systemctl start svnserve.service  

### 设置成开机启动

    sudo systemctl enable svnserve.service  

到这应该就完成了，如果检出无相应，查看是不是防火墙没有开启3690端口
