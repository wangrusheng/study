# docker-compose

docker-compose

https://github.com/docker/compose/releases

curl -L https://github.com/docker/compose/releases/download/1.25.0-rc2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose chmod +x /usr/local/bin/docker-compose

docker-compose -version                //查看版本

启动

docker-compose up -d

重启

docker-compose restart

停止

docker-compose stop

开机启动

vim /etc/rc.d/rc.local /usr/local/bin/docker-compose -f /www/docker/trace_fecshop/docker-compose.yml up -d

Redis官网

MongoDB官网

限制访问

mongodb.conf

MongoVUE

https://robomongo.org/

新建数据库

use dbname

db.createUser({

​    user: "runoob",

​    pwd: "runoob",

​    roles: [{role: "readWrite",db: "runoob"}]

})

db.dropUser('runoob')

https://github.com/wnameless/docker-oracle-xe-11g

docker run -d --privileged --name oracle  -p 1521:1521 --restart=always wnameless/oracle-xe-11g

docker  exec -it oracle /bin/bash

root@b460f21c1964:/*# sqlplus system/oracle*

echo $ORACLE_HOME

[MongoDB官网](https://www.mongodb.com/)

限制访问

[mongodb.conf](https://github.com/mongodb/mongo/blob/master/rpm/mongod.conf)

[MongoVUE](http://www.mongovue.com/)

[https://robomongo.org/](https://robomongo.org/)

--link

域名邮箱

[Redis官网](https://redis.io/)

redis4.0 远程访问

[https://www.cnblogs.com/wj5633/p/6707012.html](https://www.cnblogs.com/wj5633/p/6707012.html)

[http://www.cnblogs.com/bigben0123/p/8880940.html](http://www.cnblogs.com/bigben0123/p/8880940.html)

[https://www.cnblogs.com/trydoit/p/7129039.html](https://www.cnblogs.com/trydoit/p/7129039.html)

