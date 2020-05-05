**docker-compose里两种设置方式都是可以持久化的**

1. 绝对路径的

ghost:  image: ghost  volumes:    - ./ghost/config.js:/var/lib/ghost/config.js

1. 卷标的

services: mysql:    image: mysql  container_name: mysql  volumes:    - mysql:/var/lib/mysql...volumes: mysql:

第一种情况路径直接挂载到本地，比较直观，但需要管理本地的路径，而第二种使用卷标的方式，比较简洁，但你不知道数据存在本地什么位置，下面说明如何查看docker的卷标

1. 查看所有卷标

 docker volume ls 

1. 查看批量的卷标

$ docker volume ls | grep mysqllocal               vagrant_mysql

1. 查看具体的volume对应的真实地址

$ docker volume inspect vagrant_mysql[   {       "Name": "vagrant_mysql",       "Driver": "local",       "Mountpoint": "/var/lib/docker/volumes/vagrant_mysql/_data"   }]