# 开发环境

## jdk

## maven

1. [maven安装和配置](开发环境/maven安装和配置.md)

## svn

1. [TortoiseSVN](https://tortoisesvn.net/downloads.html)
2. [TortoiseSVN Language packs](https://tortoisesvn.net/downloads.html)

## Git

1. [Git](https://git-scm.com/downloads)
2. [TortoiseGit](https://tortoisegit.org/download/)
3. [TortoiseGit Language Packs](https://tortoisegit.org/download/)

## vmware

[官方](https://www.vmware.com/)

## ubuntu

1. 

## X-shell

SecureCRT

## filezilla

https://www.filezilla.cn/download

## intelj idea 

### 编码规约

1. 阿里编码规范地址

   https://github.com/alibaba/p3c

2. Alibaba JavaCoding Guidelines 安装

   打开IDEA，File-> Setteings->Plugins->Browse Repositories,在Browse Repositories搜索栏搜索Alibaba

​	lombok

​	编码规范

​	注释模板

notepad++

sublime

typora

cmder

navicat

sqlyog



postman

PowerDesiner

ProcessOn

MindManager



RedisDesktop

RoboMongo

Snipaste

ScreenToGif

screen++

snailsvnlite

## swagger

https://blog.csdn.net/u012702547/article/details/88775298

https://www.cnblogs.com/jstarseven/p/11458919.html



前端Long类型精度损问题



## Alfresco

https://alfresco.com.cn/cn



# DokuWiki 

```bash
docker run -d \
 -p 81:80 -p 443:443 --name dokuwiki \
 bitnami/dokuwiki:latest
 docker run -d -p 82:80 --name my_wiki mprasil/dokuwiki
```

```
docker run -d -p 81:80 --name dokuwiki \
    -v /dokuwiki:/dokuwiki \
    -v /dokuwiki/conf:/dokuwiki/conf \
    -v /dokuwiki/lib/plugins:/dokuwiki/lib/plugins \
    -v /dokuwiki/lib/tpl:/dokuwiki/lib/tpl \
    -v /dokuwiki/logs:/var/log \
    mprasil/dokuwiki
```



