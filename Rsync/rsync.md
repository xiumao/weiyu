## Rsync

### rsync安装

> yum install -y rsync //7.4系统默认已安装，不需要额外安装

### 命令

    netstat -a | grep rsync

    ps -aux | grep rsync

    rsync --daemon

    kill -9 pid

### 配置 B机器

> 文件 /etc/rsyncd.conf

    uid = www
    gid = www
    read only = no
    use chroot = yes
    max connections = 8   #最大连接数
    read only = no
    pid file = /var/run/rsyncd.pid
    lock file = /var/log/rsync.lock
    log file = /var/log/rsyncd.log
    address = 172.19.6.xxx //自己的地址
    hosts allow = 172.19.153.xxx #允许访问ip
    [yaf]//共享模块名称
    path = /home/wwwroot //源目录实际路径

    可选参数
    port 873 //默认端口
    comment = Document Root of www.aa.com //描述备注信息
    read only = yes //只读 no 可读可写则是yes
    dont compress = .gz .bz2 .tgz .zip .rar .z //排除的压缩类型
    auth users = backuper //授权登陆rsync的账户（不是系统用户）
    secrets file = /etc/rsyncd.secret //存放账户的文件


> 文件 /etc/rsyncd.secret

    backuper:123456

### A机器同步至B机器

> /usr/bin/rsync -avzP  /root/xx.md 172.19.6.102::yaf
