版权声明：本文为博主原创文章，未经博主允许不得转载。 https://blog.csdn.net/u010889616/article/details/80170767

第一种方法从Ubuntu的仓库直接下载安装：

安装比较简单，这种安装的Docker不是最新版本，不过对于学习够用了，依次执行下面命令进行安装。

$ sudo apt install docker.io

1. $ sudo systemctl start docker
2. $ sudo systemctl enable docker

查看是否安装成功

1. $ docker -v
2. Docker version 17.12.1-ce, build 7390fc6

**第二种方法从Docker仓库下载安装：**

这种安装方式首先要保证Ubuntu服务器能够访问Docker仓库地址：https://download.docker.com/linux/ubuntu，如果能够访问，按照下面的操作步骤进行安装。

1. $ sudo apt update
2. $ sudo apt install apt-transport-https ca-certificates curl software-properties-common

在/etc/apt/sources.list.d/docker.list文件中添加下面内容

deb [arch=amd64] https:*//download.docker.com/linux/ubuntu bionic stable*

添加秘钥

$ curl -fsSL https:*//download.docker.com/linux/ubuntu/gpg | sudo apt-key add -*

安装docker-ce

$ sudo apt install docker-ce

查看是否安装成功：

1. $ docker --version
2. Docker version 18.03.0-ce, build 0520e24



