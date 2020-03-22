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



## 安装：

```
pip3 install nmap
pip3 install python-nmap
```

直接用不行的，会报错：

```
module 'nmap' has no attribute 'PortScanner'
```

然后要去pypi上，下载包，运行下setup.py就行了

https://pypi.org/project/python-nmap/

```
sudo python3 setup.py install
```

（过几天回来后）。。还是么得，发现只要是那个pypi上 下下来的包，在那个包的目录下就可以正常用nmap，脱离的就不行。。那就，把这个包和项目放一起吧。。。