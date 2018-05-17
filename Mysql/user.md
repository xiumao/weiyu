# mysql


## mysql

    * 远程连接上Linux系统，确保Linux系统已经安装上了MySQL数据库。

        * 登陆数据库。mysql -uroot -p（密码）

    * 创建用户用来远程连接

        * GRANT ALL PRIVILEGES ON *.* TO 'xiumao'@'%' IDENTIFIED BY 'xiumao' WITH GRANT OPTION;        

        * 第一个xiumao表示用户名

        * %表示所有的电脑都可以连接，也可以设置某个ip地址运行连接

        * 第二个xiumao表示密码

    * 执行 flush privileges; 命令立即生效

        * flush privileges;

    * 查询数据库的用户（看到如下内容表示创建新用户成功了）

        * SELECT DISTINCT CONCAT('User: ''',user,'''@''',host,''';') AS query FROM mysql.user;

    *  修改用户密码

        * set password for root@localhost = password('123');  
