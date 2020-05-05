# linux常用维护命令
查看核心数
cat /proc/cpuinfo |grep "processor"|sort -u|wc -l
查看内存
cat /proc/meminfo
free -h
系统磁盘使用情况
df -h
当前目录磁盘占用情况
du -sh *
查询文件
find . -name "*.jpg"
查询文件并删除
find . -name "*.dcm" -exec rm -f {} \;
端口占用情况
netstat -nat|grep -i 80|wc -l
查看某个应用占用多少线程
获取tomcat进程pid
ps -ef|grep tomcat
10090
统计该tomcat进程内的线程个数
ps -Lf 10090|wc -l