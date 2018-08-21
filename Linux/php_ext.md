# PHP扩展安装



- 下载tgz文件 例如 `wget http://pecl.php.net/get/mongo-1.5.1.tgz`

- `tar zxvf mongo-1.5.1.tgz` # 解压

- `cd mongo-1.5.1`

- `/usr/local/php/bin/phpize`

- `./configure --with-php-config=/usr/local/php/bin/php-config`

- `make && make install` # 编译安装

- `vim /usr/local/php/etc/php.ini`  #编辑，在最后一行添加下面的代码

- `extension="mongo.so"`

- `:wq!` #保存退出

- `service php-fpm reload` #重新加载php-fpm

- `phpinfo()` # 查看扩展安装是否成功
