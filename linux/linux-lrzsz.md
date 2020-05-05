# linux lrzsz

通常linux服务器是通过ssh客户端来进行远程登录和管理的。

然而如何方便的实现客户端与linux服务器端的文件交互呢？这就需要用到rz（上传）、sz（下载）工具。

在Ubuntu 10.10下安装rz、sz有2个方法，分述如下：

**方法1：自动安装**

1.1 在终端中，输入命令：

sudo apt-get install lrzsz

**方法2：手动安装**

2.1 下载

地址：http://www.ohse.de/uwe/software/lrzsz.html

下载到一个压缩包文件：lrzsz-0.12.20.tar.gz

2.2 解压

tar -xzf lrzsz-0.12.20.tar.gz

2.3 安装

cd lrzsz-0.12.20

./configure --prefix=/usr/local/lrzsz

sudo make

sudo make install

2.4 创建连接

cd /usr/bin

sudo ln -s /usr/local/lrzsz/bin/lrz rz

sudo ln -s /usr/local/lrzsz/bin/lsz sz