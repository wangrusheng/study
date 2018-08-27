# Docker基本命令

## 启动Docker

```
service docker start
#centos 开机自启动
systemctl enable docker

```



## Docker镜像命令

Docker镜像检索

[hub.docker.com](/hub.docker.com)检索或者执行

```
docker search 镜像名
docker search redis  #查找redis
```

镜像下载

```
docker pull 镜像名
docker pull redis #下载redis镜像,默认版本为latest
docker pull redis:3.0.7 #下载指定版本的镜像
```

镜像列表

```
docker images
```

镜像删除

```
docker rmi image-id #删除指定镜像
docker rmi $(docker images -q) #删除所有对象
```

## Docker容器命令

运行镜像为容器的命令

```
docker run -d -p [本机端口]:[docker服务器端口] --name container-name image-name
docker run --name test-redis -d redis #运行redis
```

端口映射

```
docker run -d -p 6378:6379 --name port-redis redis 
#端口映射是通过一个-p参数来实现
docker run -d -p 5672:5672 -p 15672:15672 --name rabbitmq rabbitmq #映射多个端口就多设置一个-p参数
```

容器列表

```
docker ps #运行状态的容器
docker ps -a #运行和停止状态的容器
```

停止和启动容器

```
docker stop container-name/container-id
docker stop test-redis 
#停止名为[test-redis]的容器
docker start container-name/container-id
docker start test-redis
 #启动名为[test-redis]的容器
```

删除容器

```
docker rm container-id #删除单个容器
docker rm $(docker ps -a -q)  #删除所有容器
```

容器日志

```
docker logs port-redis #查看单个容器
docker logs port-redis　| less #翻页查看,【| less】模式下：回车键翻页，q键退出
```

登录容器

```
docker exec -it container-id/container-name bash #登录后可以在容器中进行常规的Linux系统操作命令，还可以使用exit命令退出
```


开机自动启动 docker 容器

```
 docker run -dit --restart unless-stopped redis
 #更新已存在容器支持自动启动
 docker update --restart=always xxx
```




参考：[Docker 入门教程](https://blog.csdn.net/xiaolyuh123/article/details/72528860)

