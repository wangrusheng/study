# Docker基本命令

## 启动Docker

```
service docker start
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

容器列表

```
docker ps #运行状态的容器
docker ps -a #运行和停止状态的容器
```

停止和启动容器

```
docker stop container-name/container-id
docker stop test-redis #停止名为[test-redis]的容器
docker start container-name/container-id
docker start test-redis #启动名为[test-redis]的容器
```









