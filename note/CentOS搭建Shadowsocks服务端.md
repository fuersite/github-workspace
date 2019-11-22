# Centos 搭建Shadwosocks



## 安装

```
yum install python-setuptools
easy_install pip
pip install shadowsocks
```

## 配置

新建/etc/shadowsocks.json文件，内容如下

```
{
    "server":"服务器IP",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"密码",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}
```

## 运行

```
ssserver -c /etc/shadowsocks.json -d start
ssserver -c /etc/shadowsocks.json -d stop
```
很多新服务器 ssserver 安装没有成功导致后面无法继续，或者服务器开启了防火墙，那么就需要把端口加入防火墙允许。


## 另外一种方法，号称最快搭建

## 执行脚本

```
cd /tmp wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-libev.sh chmod +x shadowsocks-libev.sh ./shadowsocks-libev.sh 2>&1 | tee shadowsocks-libev.log
```

## 安装完是否有此界面

```
Congratulations, shadowsocks-libev install completed! Your Server IP:your_server_ip Your Server Port:your_server_port Your Password:your_password Your Local IP:127.0.0.1 Your Local Port:1080 Your Encryption Method:aes-256-cfb Welcome to visit:https://teddysun.com/357.html Enjoy it!
```


## 查看是否已经安装成功

```
ps -ef | grep ss-server | grep -v ps | grep -v grep
```
## 卸载命令

```
cd /tmp # 进入 shadowsocks-libev.sh 所在目录 ./shadowsocks-libev.sh uninstall
```

## 其他命令
```
service shadowsocks start # 启动 service shadowsocks stop # 停止 service shadowsocks restart # 重启
````