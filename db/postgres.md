# Postgres

## postgres 连接数

* 查询当前连接数:

  select count(1) from pg_stat_activity;

* 查询最大连接数

  show max_connections;

* 最大连接数也可以在postgresql.conf中配置：

  max_connections = 500

* 重启PostgreSQL服务（以9.6版本为例）：
  ```bash
  在CentOS 6.x系统中
  service postgresql-9.6 restart 
  在CentOS 7系统中
  systemctl restart postgresql-9.4
  ```