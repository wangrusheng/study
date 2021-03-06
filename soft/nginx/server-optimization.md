# nginx 服务器优化

**查看、修改linux系统的最大链接数限制、文件描述符限制、端口范围限制等**

**一、修改最大连接数**

**1、查看当前文件描述符的限制数目的命令：**

ulimit -n

**2、修改文件描述符的限制数目**

**2.1 临时改变当前会话：**

ulimit -n 65536

**2.2 永久变更需要下面两个步骤：**

**1) 修改/etc/security/limits.conf 文件**，如下：

vi /etc/security/limits.conf

***    soft    nofile    65536**

***    hard    nofile    65536**

***    soft    noproc    65536**

***    hard    noproc    65536**

保存退出后重新登录，其最大文件描述符已经被永久更改了；但是需要经过下面的步骤2）之后才能生效。

**2) 重新加载库：**

打开文件：

vi /etc/pam.d/login

在最后加上：

session  required /lib64/security/pam_limits.so

即可

 vi /etc/systemd/system.conf

DefaultLimitNOFILE=1024000      #这里需要修改 #DefaultLimitAS= #DefaultLimitNPROC= DefaultLimitNPROC=1024000   #这里也需要修改

修改普通用户 max user processes 

vim /etc/security/limits.d/20-nproc.conf

***    soft    nofile    65536**

***    hard    nofile    65536**

***    soft    noproc    65536**

***    hard    noproc    65536**

**二、修改端口限制**

主要是对内核参数sysctl.conf的优化，/etc/sysctl.conf 是用来控制linux网络的配置文件，对于依赖网络的程序(如web服务器和cache服务器)非常重要，RHEL默认提供的最好调整。推荐配置(把下面内容添加进去)：

**fs.file-max = 6553560**

**net.ipv4.ip_local_port_range= 32768     61000**

**net.core.rmem_max=16777216**

**net.core.wmem_max=16777216**

**net.ipv4.tcp_rmem=4096 87380 16777216**

**net.ipv4.tcp_wmem=4096 65536 16777216**

**net.ipv4.tcp_fin_timeout = 10**

**net.ipv4.tcp_tw_recycle = 1**

**net.ipv4.tcp_timestamps = 0**

**net.ipv4.tcp_window_scaling = 0**

**net.ipv4.tcp_sack = 0**

**net.core.netdev_max_backlog = 30000**

**net.ipv4.tcp_no_metrics_save=1**

**net.core.somaxconn = 65535**

**net.ipv4.tcp_syncookies = 0**

**net.ipv4.tcp_max_orphans = 262144**

**net.ipv4.tcp_max_syn_backlog = 262144**

**net.ipv4.tcp_synack_retries = 2**

**net.ipv4.tcp_syn_retries = 2**

　　这个配置参考于cache服务器varnish的推荐配置和SunOne 服务器系统优化的推荐配置。这里有个对端口范围的限制如果不做修改原始的返回只有2.8万个port区间。

对上述内存参数的具体操作命令示例：

**1）查看端口范围：**

[root@slave2 sub_client]# sysctl -a | grep range

net.ipv4.ip_local_port_range = 1024 65000

**2）修改内核参数sysctl.conf,打开该文件**，

vi /etc/sysctl.conf

如果文件中有参数net.ipv4.ip_local_port_range的配置，则将其修改为：

net.ipv4.ip_local_port_range = 1024 65000

否则，直接加上这句话。

**3）让配置立即生效：**

sysctl -p

另外，端口范围参数net.ipv4.ip_local_port_range不要超过1024和65535，1024以下系统使用，65535以上设置会会提示失败：

error: "Invalid argument" setting key "net.ipv4.ip_local_port_range"

修改linux系统参数。vi /etc/security/limits.conf 添加

*　　soft　　nofile　　65536

*　　hard　　nofile　　65536

修改以后保存，注销当前用户，重新登录，执行ulimit -a ,ok ,参数生效了：

修改后要重启

yum install net-tools