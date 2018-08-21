# 搭建LVS

[Linux高可用之Keepalived](https://www.jianshu.com/p/b050d8861fc1)
[Nginx+keepalived双机热备（主从模式）](https://www.cnblogs.com/kevingrace/p/6138185.html)

服务器准备(centos7)：
master(192.168.175.128)
backup(192.168.175.129)
rs01(192.168.175.130)
rs02(192.168.175.131)

```
#修改hostname
hostnamectl set-hostname master
#修改ip
vi /etc/sysconfig/network-scripts/ifcfg-网络接口名称
IPADDR=192.168.175.130
#重启
service network restart
```



