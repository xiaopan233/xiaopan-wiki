# PHP

## PDO： ##

连接数据库：

	$con = new PDO($dsn, $user, $pass);
	//$dsn格式为：数据库类型:host=数据库主机;dbname=数据库名;[charset=字符集]
	//例子：
	//$dsn = 'mysql:host=localhost;dbname=test;charset=utf8'

---

执行sql语句，获取query句柄：

	$query = $con->query($sql)

取数据（一行行取，取了一行指针往下移一行，配合whlie食用更佳）：

	$query->fetch(参数)
	
//其中，参数有：
//PDO::FETCH_ASSOC
//PDO::FETCH_BOTH
//PDO::FETCH_LAZY
//PDO::FETCH_OBJ

---

全部取出：

	$query->fetchAll()