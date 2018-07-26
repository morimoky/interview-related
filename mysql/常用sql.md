#### 1.查询某字段值唯一的记录：
```
SELECT *
FROM table_name 
group by field
having count(field) = 1
```
#### 2.插入数据（有唯一索引），如果冲突改为更新：
```
INSERT INTO 
    table_name (field1,field2,field3) 
VALUES 
    (value1,value2,value3) 
ON DUPLICATE KEY UPDATE 
    field3 = value3
```

#### 3.表中有A B C三列,用SQL语句实现：当A列大于B列时选择A列否则选择B列，当B列大于C列时选择B列否则选择C列。
```
select case when A>B then A else B end,
       case when B>C then B else C end
From test
```

#### 4.自定义排序
```
select
     *,
     case `status`
      when 8 then 1
      when 2 then 2
      when 5 then 3
      when 4 then 4
      when 1 then 5
      when 3 then 6
      when 6 then 7
      when 7 then 8 end as sort
    from
     test
    where
     `status` <> 0
    order by
     sort asc
```

#### 5.批量修改数据设置为不同的值
```
Update 
    myTable
SET 
    myField = CASE id
    		WHEN 1 THEN 'value1'
    		WHEN 2 THEN 'value2'
   		WHEN 3 THEN 'value3'
  	END,
update_time = UNIX_TIMESTAMP(NOW())
WHERE 
id IN (1,2,3)
```
#### 6.字符串替换
```
update 表名 set 字段名=REPLACE (字段名,'原来的值','要修改的值')  
```

#### 7.自定义排序
```
select * from driver_log order by field(name,'Suzi','Ben','Henry');
```
