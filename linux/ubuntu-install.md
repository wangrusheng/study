{{>toc}}
# ubuntu安装
## 版本选择
目前有两个最新的Ubuntu版本：Ubuntu 16.04.6和Ubuntu 18.04.2
常情况下Ubuntu 18.04.2是高一级的版本，如果计算机配置跟得上的话应当选择该版本，它只是Ubuntu 18.04的第二个更新维护版本，后面还有源源不断的更新，而Ubuntu 16.04.6已经是Ubuntu 16.04的第六个更新版本了，已经达到了版本更新的顶峰，当然该版本会非常的稳定，较适合计算机配置不高的用户选用。
## ubuntu 16.04 镜像下载
1. 官方下载地址（不推荐）
   https://www.ubuntu.com/download
   
2. 官方中文
   https://cn.ubuntu.com/download
   
3. 中科大源 
   http://mirrors.ustc.edu.cn/ubuntu-releases/16.04/
   
4. 阿里云开源镜像站
   http://mirrors.aliyun.com/ubuntu-releases/16.04/
   
5. 兰州大学开源镜像站
   http://mirror.lzu.edu.cn/ubuntu-releases/16.04/
   
6. 北京理工大学开源
   http://mirror.bit.edu.cn/ubuntu-releases/16.04/
   
7. 浙江大学
   http://mirrors.zju.edu.cn/ubuntu-releases/16.04/
   
8. 不知名镜像网站
   http://mirror.pnl.gov/releases/xenial/
   
9. 各个版本下载网址：
   http://mirrors.melbourne.co.uk/ubuntu-releases/
   
   
## 安装
### VMware 新建虚拟机 
命名为：Ubuntu Server 16.04 X64
路径：D:\VMware\Ubuntu Server 16.04 X64
### 镜像放入光盘
### 选择语言
English
### 用户名、密码
username：victor
password：123456
### 选择LVM
Logical Volume Manager。 磁盘扩容技术新空间与旧空间合并。[Linux LVM](https://www.cnblogs.com/xs104/p/4642406.html)

### ssh server
空格选择，install openSSH server
### 配置镜像源
1. 阿里源地址

   http://mirrors.aliyun.com/ubuntu/

2. 查看源信息

   ```shell
   cat /etc/apt/sources.list
   ```

3. 备份源文件

   ```shell
   cp /etc/apt/sources.list /etc/apt/sources.back
   ```
4. 清空源

   ```shell
   vim /etc/apt/sources.list
   :%d
   ```

5. 修改源

   ```shell
   vim /etc/apt/sources.list
   p
   ```

```shell
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted
deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb http://mirrors.aliyun.com/ubuntu/ xenial multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-security multiverse
```

4. 更新源

   ```shell
sudo apt-get update
   ```