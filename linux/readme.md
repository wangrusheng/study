# linux
## Linux 简介
Linux 内核最初只是由芬兰人林纳斯·托瓦兹（Linus Torvalds）在赫尔辛基大学上学时出于个人爱好而编写的。
Linux 是一套免费使用和自由传播的类 Unix 操作系统，是一个基于 POSIX 和 UNIX 的多用户、多任务、支持多线程和多 CPU 的操作系统。
Linux 能运行主要的 UNIX 工具软件、应用程序和网络协议。它支持 32 位和 64 位硬件。Linux 继承了 Unix 以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统。

## Linux 的发行版
Linux 的发行版说简单点就是将 Linux 内核与应用软件做一个打包。目前市面上较知名的发行版有：Ubuntu、RedHat、CentOS、Debian、Fedora、SuSE、OpenSUSE、Arch Linux、SolusOS 等。
![](readme.assets/1511849829609658.jpg)

## 参考

\- [1] [百度学术](http://xueshu.baidu.com/)

```

```

[不如][1]

[GitHub Octocat][2]

[@1]

[1]:http://bruce-sha.github.io
[2]:http://github.global.ssl.fastly.net/images/modules/logos_page/Octocat.png




查看核心数

cat /proc/cpuinfo \|grep "processor"\|sort -u\|wc -l

查看内存

cat /proc/meminfo

free -h

查看 硬盘

删除进程

netstat -ano|findstr 1099

taskkill -f -pid 3576