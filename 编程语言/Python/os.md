# os

包含着普遍的操作系统功能：

路径分隔符，linux下为 / ；windows下为 \\

	os.sep

显示当前平台，如果是windows返回nt，如果是linux返回posix

	os.name

获取当前工作目录：

	os.getcwd()

获取一个环境变量：

	os.getenv(环境变量名)


设置一个环境变量：

	os.putenv(环境变量名, 值)

返回指定目录下的所有文件名和目录：

	os.listdir(路径)

删除一个文件：

	os.remove(文件路径)

执行系统命令：

	os.system("系统命令")

给出当前平台使用的行终止符，windows使用 '\r\n'，Linux使用 '\n'，Mac使用 '\r'：

	os.linesep

改变工作目录：

	os.chdir(目录)

