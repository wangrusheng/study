# linux

ubuntu

redhat

centos



查看核心数

cat /proc/cpuinfo \|grep "processor"\|sort -u\|wc -l

查看内存

cat /proc/meminfo

free -h

查看 硬盘

删除进程

netstat -ano|findstr 1099

taskkill -f -pid 3576