# pymssql


连接数据库：


	connect = pymssql.connect(host=host, user=username, password=password, [database])        #database可选


成功连接后，需要获取一个cursor，然后用这个cursor才能执行数据库命令：

	cursor = connect.cursor()


执行命令：

	cursor.execute("select name from master..sysdatabases")


若执行的命令是插入等写操作，需要加上commit

	connect.commit()


获取回显：

	cursor.fetchone()


关闭连接：

	connect.close()
