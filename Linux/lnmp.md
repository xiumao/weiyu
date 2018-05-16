# lnmp-install

## PHP

    1.命令 wget http://hk1.php.net/get/php-5.4.45.tar.gz/from/this/mirror

    2.命令 tar -zxvf mirror

    3.命令 cd php-5.4.45

    4.命令 ./configure --prefix=/usr/local/php5.4 --enable-fpm

    5.命令 make

    6.命令 sudo make install

<!--more-->   

## 命令

    启动PHP-FPM
    sudo /usr/local/php/sbin/php-fpm

    查找进程任务
    ps -aux |grep php-fpm

    杀死进程
    kill -int(quit) 进程ID

## 资源

> [VirtualBox下载](https://www.virtualbox.org/wiki/Downloads)

> [CentOs下载](https://www.centos.org/download/)    

> [PHP下载](http://php.net/releases/)

> [Mysql下载](https://dev.mysql.com/downloads/mysql/)

> [apache下载](http://httpd.apache.org/)

> [archive-apache下载](http://archive.apache.org/dist/)

> [pcre下载](https://ftp.pcre.org/pub/pcre/)

> [nginx下载](http://nginx.org/)
