## docker

### 官网文档

> https://docs.docker.com/

### 参考资料

    sudo yum install -y yum-utils   device-mapper-persistent-data   lvm2
    sudo yum-config-manager     --add-repo     https://download.docker.com/linux/centos/docker-ce.repo
    sudo yum-config-manager --enable docker-ce-edge
    sudo yum-config-manager --enable docker-ce-test
    sudo yum-config-manager --disable docker-ce-edge
    sudo yum install docker-ce -y
    sudo systemctl start docker


    $ curl -L https://github.com/docker/machine/releases/download/v0.12.0/docker-machine-`uname -s`-`uname -m` > /tmp/docker-machine
    $ chmod +x /tmp/docker-machine
    $ sudo mv /tmp/docker-machine /usr/local/bin/docker-machine


    linux virtualbox
    https://www.cnblogs.com/wangshuyi/p/6927113.html
