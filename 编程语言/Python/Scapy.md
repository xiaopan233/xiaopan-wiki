# Scapy

## 查看scapy常用函数的函数： ##

<font size=20px>lsc()</font>

通过计算机名计算其在NI组的地址：

	computeNIGroupAddr    

<br>

将一个列表里的数据包组合起来，如果有分片会合成一个数据包：

	defrag         


类似defrag：
             
	defragment   
   

对数据包进行分片，默认是最大的包1480：
	fragment(packet, fragsize=1480)           

<br>         

发送dhcp发现请求，并返回回复：

	dhcp_request(iface="eth0")       

<br>      

ARP攻击:

	arpcachepoison        


分片攻击（UDP）:

	fragleak(target,sport,dport,timeout,count)        


分片攻击（Unassigned）:

	fragleak2(target)                     
    

构造重叠的数据包以绕过NIPS     UDP DropTears？  :
                    
	overlap_frag(p,CD,fragsize=8,overlap_fragsize=None)   

<br>    

## 将数据包内容随机填充： ##

	fuzz(packet)        



## 探测 ##

根据指定的ip地址获取mac地址（本质就是发送了一个ARP请求）：

	getmacbyip(ip)       


检测目标是否处于混杂模式（发送ARP包，又回复就返回True，没有就返回False。相当于探测存活）：

	is_promisc(ip)           


<br>


## 网卡接口： ##

	get_if_addr("网卡名称")        查看网卡ip
	get_if_hwaddr("网卡名称")      查看网卡mac地址


## 发送数据包： ##

发送数据包的help在 scapy.layers.all 中 FUNCTIONS的下面


### 三层（即数据包中不带Ether） ###

inte&nbsp;&nbsp;&nbsp;&nbsp;发送的时间间隔


loop&nbsp;&nbsp;&nbsp;&nbsp;是否循环 1/0



count&nbsp;&nbsp;&nbsp;&nbsp;发送数量

  

return_packets&nbsp;&nbsp;&nbsp;&nbsp;是否返回返回包
 
</br>

send(x, inter=0, loop=0, count=None, verbose=None, realtime=None, return_packets=False)

sr(x,timeout)&nbsp;&nbsp;&nbsp;&nbsp;发送且接收（接收会阻塞）

sr1()&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;只接受第一个回复

sr1flood()

srflood()

srloop()

### 二层（即数据包中带有Ether，即使是 Ether()/IP()/TCP() 也是得要sendp发） ###

iface&nbsp;&nbsp;&nbsp;&nbsp;指定网卡

<br>

sendp(x, inter=0, loop=0, iface=None, iface_hint=None, count=None, verbose=None, realtime=None, return_packets=False, socket=None)

sendpfast(x)

srp(x)

srp1(x)

srp1flood(x)

srploop(x)
 
## 嗅探数据包：     ##

	sniff(count=0, store=True, offline=None, prn=None, lfilter=None, timeout=None, stop_filter=None, iface=None)

>count&nbsp;&nbsp;&nbsp;&nbsp;当捕获了指定数量的数据包后停止捕获

>store&nbsp;&nbsp;&nbsp;&nbsp;是否存储捕获的数据包

>offline&nbsp;&nbsp;&nbsp;&nbsp;离线模式，即读取pcap包

>prn&nbsp;&nbsp;&nbsp;&nbsp;处理捕获到的数据包（可以是lambda，也可以是指定一个函数名）

>filter&nbsp;&nbsp;&nbsp;&nbsp;过滤规则（小写）

>lfilter&nbsp;&nbsp;&nbsp;&nbsp;高级过滤规则（可以使用函数和lambda，return 1表示不过滤，return 0表示丢弃数据包）

>timeout&nbsp;&nbsp;&nbsp;&nbsp;指定时间停止捕获数据包

>stop_filter&nbsp;&nbsp;&nbsp;&nbsp;指定一个函数或lambda，返回true时停止捕获

>iface&nbsp;&nbsp;&nbsp;&nbsp;指定监听网卡


## 路由： #

查看当前路由，相当于linux命令 route -n

	conf.route

添加一条路由，注意指定主机用 host ，指定网段用 net：

	conf.route.add(host="172.16.11.2", gw="172.16.11.254")	
	conf.route.add(net="172.16.10.0/24", gw="172.16.10.254")

删除一条路由：

	conf.route.delt(net="172.16.10.0/24", gw="172.16.10.254")

## 编码： ##

将字符转换成ascii码

	orb('A')            

将字符串转成base64

	bytes_base64("ABCD")

将base64转成字符串

	base64_bytes("QUJDRA==")    

编码数据包

	bytes_encode(Ether()/IP()/TCP())   

字符串转十六进制

	bytes_hex("ABCD")        

十六进制转字符串

	hex_bytes("41424344")    

将基本字节对象转换为字符串

	plain_str(b'ABCD')          

将数据包转换成bytes  

	raw(x)                        


## 随机数： ##

生成长度为100的随机字符串

	RandString(size=100)

生成随机的UUID

	RandUUID()                    


## 时间： ##

显示当前时间

	strftime("%Y-%m-%d %H:%M:%S")      
  

## 读写： ##

直接读取数据包里的东西

	rdpcap("/root/test.pcap")

将数据包里的东西传给sniff，使用sniff的离线模式：

	sniff(offline="/root/test.pcap")


将数据包写入到pcap文件（重复使用会覆盖，不是追加）：

	wrpcap("temp.pcap",pkt)

## 杂项： ##

snmp探测

	snmpwalk(dst, oid='1' community='public')            