# Docker基本命令

启动Docker

```
service docker start
```

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



