# Nginx服务器安装SSL证书教程

观看以下视频，快速了解如何在Nginx服务器上安装SSL证书。



## 相关命令

|命令|说明|视频中首次出现的时间点|
|--|--|-----------|
|`netstat -nplt |grep <port>`|查询服务器网络监听状态。将`<port>`替换成80、443，查询80、443端口是否开启了监听。

|2分48秒|
|`nginx -t`|校验配置文件的语法。|3分50秒|
|`nginx -s reload`|重启Nginx服务。|4分14秒|
|`firewall-cmd --state`|查询服务器的防火墙状态。|4分32秒|
|`firewall-cmd --list-ports`|查询防火墙放行的端口。|4分38秒|
|`firewall-cmd --zone=public --add-port=443/tcp --permanent`|在防火墙中添加443端口。|4分52秒|
|`firewall-cmd --reload`|重启防火墙。|4分56秒|
|`echo | openssl s_client -connect 127.0.0.1:443 -servername <your_domain_name> 2>/dev/null`|在服务器上模拟客户端，检查本地443端口加载的HTTPS服务以及证书是否正常。将`<your_domain_name>`替换成您的域名。

|5分12秒|
|`rewrite ^(.*)$ https://$host$1;`|配置HTTP强制跳转HTTPS。|6分11秒|

