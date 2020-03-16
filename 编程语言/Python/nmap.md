# nmap

实例化扫描器：

	nm = nmap.PortScanner()

开启扫描：

	nm.scan(hosts="xx.xx.xx.xx-xx.xx.xx.xx",ports="1-65535",arguments="-sS -n") 
	#也可以缩写成：
	nm.scan("xx.xx.xx.xx","1-65535","-sS -n")

获取扫描命令：

	nm.command_line()

获取nmap扫描信息：

	nm.scaninfo()

返回nmap扫描的主机清单：

	nm.all_hosts()

查看扫描结果每台主机的详细信息：

	nm['xx.xx.xx.xx']