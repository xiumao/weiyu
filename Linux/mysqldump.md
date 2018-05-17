# mysqldump

## 指令

> -h [IP或者域名] -u [账号] -p [密码]

## 导出命令

    mysqldump -h -u -p database_name table_name  > target.sql

## 导入命令

    mysql.exe -h -u -p database_name < /tmp/database_name.sql
