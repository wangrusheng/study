# 将Oracle、Mysql中的表结构导出到word

## Oracle

```sql
SELECT t1.Table_Name AS "表名称", t3.comments AS "表说明",  t1.Column_Name AS "字段名称", t1.Data_Type AS "数据类型", t1.Data_Length AS "长度", t1.NullAble AS "是否为空", t2.Comments AS "字段说明", t1.Data_Default "默认值" FROM cols t1 left join user_col_comments t2 on t1.Table_name=t2.Table_name and t1.Column_Name=t2.Column_Name left join user_tab_comments t3  on t1.Table_name=t3.Table_name  WHERE NOT EXISTS ( SELECT t4.Object_Name FROM User_objects t4 WHERE t4.Object_Type='TABLE'  AND t4.Temporary='Y'  AND t4.Object_Name=t1.Table_Name ) ORDER BY t1.Table_Name, t1.Column_ID;
```

## mysql

```sql
SELECT
 COLUMN_NAME 列名,
 COLUMN_COMMENT 名称 ,
 COLUMN_TYPE 数据类型,
 DATA_TYPE 字段类型,  
 CHARACTER_MAXIMUM_LENGTH 长度,
 IS_NULLABLE 是否必填,
 COLUMN_DEFAULT 描述 
FROM
 INFORMATION_SCHEMA.COLUMNS
where
-- developerclub为数据库名称，到时候只需要修改成你要导出表结构的数据库即可
table_schema ='litchi'
AND
-- article为表名，到时候换成你要导出的表的名称
-- 如果不写的话，默认会查询出所有表中的数据，这样可能就分不清到底哪些字段是哪张表中的了，所以还是建议写上要导出的名名称
table_name  = 'tb_item'
```