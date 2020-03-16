# pxssh

## 引用： ##

	from pexpect import pxssh

## 实例化一个对象： ##


	s = pxssh.pxssh()

## 登录： ##
如果登录失败，会throw一个报错，若作为暴力破解使用，需要加上try except

	s.login(host, username, password)

## 执行命令：##


	s.sendline("whoami")

## 获取回显： ##

	s.prompt()                #每次获取都需要加上s.prompt，不然获取的就不是回显
	print(s.before)            