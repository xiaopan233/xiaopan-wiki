# 简易TCP端口扫描器

由于socket可以实现tcp连接和，所以我们可以用socket来进行简单的端口扫描

	import socket
	host = "1992.168.58.137"
	for i in range(1,65536):
	    try:
	        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	        s.settimeout(100)                                    #设置超时时间，防止一些防火墙直接drop掉数据包，一直阻塞
	        s.connect(("192.168.58.137", i))
	        print("[+] port %d is open"%i)
	    except:
	        pass