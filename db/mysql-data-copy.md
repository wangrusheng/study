# mysql表数据复制

## mysql insert into

当表A和表B的表结构一致时，直接插入即可。

```sql
insert into A select * from B;
```

当表结构不一致时（字段大小、类型都相同）

```sql
insert into A(col1, col2) select col1, col2 from B;
```

不插入重复数据

```sql
INSERT INTO A
SELECT * FROM B WHERE id NOT IN (SELECT id FROM A);
```

## 跨服务器查询数据

在日常的开发中经常进行跨数据库进行查询数据。
同服务器下跨数据库进行查询在表前加上数据库名就可以查询到数据。
mysql跨服务器进行查询提供了FEDERATED引擎进行映射表，然后进行查询。
mysql数据库federated引擎是关闭的，首先需要先启用该引擎。

### mysql执行show engines命令查看引擎状态

```sql
show engines;
```

federated引擎默认是关闭的

![image-20200426072515986](Untitled.assets/image-20200426072515986.png)

### 启用FEDERATED引擎

#### mysql安装目录下找到**my.ini**并编辑，在[mysqld] 下加上**federated**

![image-20200426073342069](Untitled.assets/image-20200426073342069.png)

#### 重启mysql

[运行]services.msc ,在服务中重新启动mysql服务，再查看引擎

![image-20200426073937512](Untitled.assets/image-20200426073937512.png)

#### 查看源表结构

show create table user

#### 创建远程服务器数据库中的需要映射的表

映射表名称可以随意命名，但是数据结构必要一样。

```sql
CREATE TABLE `user` (
  `id` varchar(32) NOT NULL,
  `name` varchar(20) DEFAULT NULL
  PRIMARY KEY (`id`)
) ENGINE=FEDERATED CONNECTION='mysql://root:123456@192.168.0.103:3306/db/user'; 
```

这样就可以将远程的user表数据实时映射到本地user表中，实现mysql跨服务器查询数据。