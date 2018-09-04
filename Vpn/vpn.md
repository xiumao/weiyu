## VPN搭建

### 搭建命令

> [L2TP/IPSec一键安装脚本](https://teddysun.com/448.html)


	wget --no-check-certificate https://raw.githubusercontent.com/teddysun/across/master/l2tp.sh
	chmod +x l2tp.sh
	./l2tp.sh

### 配置DHCP

	cd /etc/sysconfig/network-scripts/ #进入网络配置文件目录
	vim ifcfg-eth0 #编辑配置文件，添加修改以下内容

	HWADDR=00:0c:29:58:27:57
	ONBOOT=yes #开启自动启用网络连接

	这里增加了第一行的mac地址，最后一行修改成了yes开启网络连接
	接下来重启网卡让网卡设置生效；

	:wq！ #保存退出
	service network restart #重启网络

	systemctl start|stop|restart|status ipsec （CentOS7 下使用）
	systemctl start|stop|restart xl2tpd （CentOS7 下使用）

	/etc/xl2tpd/xl2tpd.conf  
		local_ip = 内网IP
