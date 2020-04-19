# CentOS 7.4安装Nginx 1.14.0

 **一、安装所需环境**

　　 1、gcc 安装

  　　  yum install gcc-c++

　　 　  

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/a4583cbb2542452ca01462b71bbe0f8e/suvork5cyii%3D.png)

　　 2、PCRE pcre-devel 安装

  　　  yum install -y pcre pcre-devel

　　　  

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/e72b9ccf081a4e8588755915d9b75a33/suvork5cyii%3D.png)

​     3、zlib 安装

  　   yum install -y zlib zlib-devel

　　  　

![img](CentOS 7.4安装Nginx 1.14.0.assets/aelftksuqmcc.png)

​     4、OpenSSL 安装

  　   yum install -y openssl openssl-devel

　　  　

![img](CentOS 7.4安装Nginx 1.14.0.assets/aelftksuqmcc.png)

 

**二、官网下载nginx**

​     1、直接下载.tar.gz安装包，地址：https://nginx.org/en/download.html

　　　　

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/e2ed7398f04a43eabcd9285fb3308d4a/suvork5cyii%3D.png)

​    

　　  2、使用wget命令下载（推荐）

​        wget -c https://nginx.org/download/nginx-1.14.0.tar.gz

 

**三、解压**

​     **tar -zxvf nginx-1.14.0.tar.gz**

　   

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/7d29eade6212432f80a951283fc49f6d/suvork5cyii%3D.png)

​      

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/8d5598e45de042b5910727a516c21f68/suvork5cyii%3D.png)

 **四、配置makefile** 

　　  **为了防止** **重启nginx后** **报如下异常****：**

​          **[root@localhost sbin]# nginx: [emerg] open() "/var/run/nginx/nginx.pid" failed (2: No such file or directory 。**

​      **推荐****使用默认配置**

　　  **进入到nginx-1.14.0目录下**

​        **cd nginx-1.14.0** 

　　 **1、使用默认配置（个人** **强烈推荐****）**

  　　 **./configure**

　  　 

![img](CentOS 7.4安装Nginx 1.14.0.assets/aelftksuqmcc.png)

​     2、自定义配置（不推荐）

  　  此方法可以网上搜索查看，这里我就不列出来了。

报错时执行

/usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf

  

**五、编译安装**

　　 1、make

​    2、make install

​       

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/e04903d1726741bda1fb6f762b3ba89e/suvork5cyii%3D.png)

 

**六、防火墙开启80端口**

　　 1、开启防火墙 

​       systemctl start firewalld.service

​    2、防火墙开启80端口

  　  firewall-cmd --zone=public --add-port=80/tcp --permanent

　　    

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/9a11bb2841054d6d980961ab9569ca83/ru5erkjggg%3D%3D.png)

​    3、重启防火墙

​       firewall-cmd --reload 或者  service firewalld restart

​    4、查看端口列表

​       firewall-cmd --permanent --list-port

**七、查找安装路径**

​      whereis nginx

**八、启动nginx** 

​      cd到nginx安装目录的bin目录下启动nginx

  　 　 cd /usr/local/nginx/sbin/

  　　  ./nginx

　　  

![img](CentOS 7.4安装Nginx 1.14.0.assets/aelftksuqmcc.png)

  

**九、查询nginx进程**

​      ps aux|grep nginx

　　  

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/6b9b9c60c8244fe1ae2a918eb47ae1e0/suvork5cyii%3D.png)

**十、 验证是否安装启动成功 （前提:先启动nginx）**

　　  打开浏览器，输入安装nginx服务器的CentOS系统的IP地址，看到如下的页面时，说明安装启动成功了。

　　  

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/815af4f5e40d4d71bd83754fb500e864/ru5erkjggg%3D%3D.png)

​      

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/42da1b548b1245dd94c16df89160943b/ru5erkjggg%3D%3D.png)

 

**十一、 停止nginx**

​         ./nginx -s stop

​         ./nginx -s quit

​         附加说明：

​           ./nginx -s quit:此方式停止步骤是待nginx进程处理任务完毕进行停止。

​           ./nginx -s stop:此方式相当于先查出nginx进程id再使用kill命令强制杀掉进程。

 

**十二、设置ngnix开机自启**

　　   1、编辑 rc.local 文件

​          cd /etc/rc.d/

​          vim /etc/rc.d/rc.local

​          添加如下参数（此参数就是你的nginx启动程序所在的路径，这里根据个人安装的nginx位置而定，我的nginx是安装在了/usr/local/下）

​           增加一行 /usr/local/nginx/sbin/nginx

　 　      

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/4af26437dcee4341adf4fefd627affcf/ru5erkjggg%3D%3D.png)

　 　      

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/ec4f106ea8934572859b79c4ca23c94d/ru5erkjggg%3D%3D.png)

　　

  

​      2、设置执行权限

​         cd /etc/rc.d/

​         chmod +x rc.local

　　      

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/3080914a8a814bb7971bacf4570f523a/suvork5cyii%3D.png)

  

​      3、验证开机启动设置是否生效

​        reboot(重启系统)

　　　   

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/cba2e4e23eab4112ac84e536debb8875/suvork5cyii%3D.png)

　　　   打开浏览器，输入安装nginx服务器的CentOS系统的IP地址，显示如下图的页面，说明nginx开机自启设置已生效。

　　　   

![img](C:/Users/victor/AppData/Local/YNote/data/qq8C262E294875B99E3D4A25C7A10909A4/1b8aa34e4ca54120ad38edad8fe08a26/ru5erkjggg%3D%3D.png)

 

PS：如有问题，请留言，转载请注明出处 https://www.cnblogs.com/ascd-eg/p/9275441.html