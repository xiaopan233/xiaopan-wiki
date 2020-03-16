# Mysql

下载地址（msi）：
[https://downloads.mysql.com/archives/installer/](https://downloads.mysql.com/archives/installer/)

MSi比较方便配置，zip好像还要配置别的东西。。。

## 报错解决 ##

### 1、ERROR 1820 (HY000): You must reset your password using ALTER USER statement###

这个是说，密码复杂度过低，不符合配置。我们把配置的密码复杂度调低即可：

>set global validate_password_policy=0;

>set global validate_password_length=0;

最后重新改下密码刷新权限即可：

>alter user 'root'@'localhost' identified by '123456';

>flush privileges



### 2、MariaDB 缺省使用 Unix_socket的问题：###

修改配置插件：

	update mysql.user set plugin='mysql_native_password' where user='root';

刷新权限后即可：

	flush privileges



## 基础 ##

查询当前用户：

```
select user();
\#或者
select current_user();
```

查看当前使用的数据库：

```
select database();
```

查看用户权限：

```
show grants for '用户名'@'%'
```



---



创建用户：



1、create user '用户名'@'主机' identififed by '密码'           # 直接创建用户



2、grant 权限 on 数据库.表 to '用户名'@'主机' identified by '密码'   # 创建用户并赋予权限，如果不加identified，就算赋予权限



权限：

  **select、insert、update、delete、create、alter、drop**、reload（flush命令）、shutdown、process、**file**、**all**

撤销授权：

```
revoke 权限 on 数据库名.表名 from '用户名'@'主机'
```

刷新权限表，（修改密码，一定要刷新权限表，不然不生效）

```
flush privileges
```

加写锁：

```
flush tables with read lock
```

解锁：

```
unlock tables
```
