# socket

## c/s 模式： ##

学习Python的socket最好的方式，就是先从client / server 的方式学起吧。

### 服务端： ###

第一步，创建socket套接字：

	s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

若想重启监听端口的时候，不会出现监听端口被占用，可以设置一个选项：

	s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)


第二步，绑定主机和端口，传入的是元组：

	s.bind(("0.0.0.0", 7777))

第三步，设置挂起连接的最大数量，类似于排队的最大数量，并不是说这里数量是多少就是只能连接多少个：

	s.listen(1)


第四步，开启接收连接（这个时候会阻塞，有新连接过来才会继续往下执行，不然就是一直阻塞着）：

	conn, addr = s.accept()

conn是连接客户端的句柄，到时候要发送消息什么的就靠conn的句柄来实现
addr是一个元组，存放在客户端的Ip和连接端口


第五步，推送消息给客户端及接收客户端发来的信息：


	conn.send("message")

	data = conn.recv(1024)

这也是会阻塞的，只有接收到了客户端发来的信息才会继续往下执行代码
里面的值是一次性接收多少客户端发来的字节

推送和接收的顺序可以互换，主要看程序的逻辑


第七步，关闭客户端连接

	conn.close()


第八步，关闭socket监听：

	s.close()


### 客户端： ###


第一步，创建一个socket套接字：

	s = socket.socket(socket.AF_INET,socket.SOCK_STREAM)


第二步，连接主机：

s.connect((host, port))


第三步，接收服务器发来的信息及向服务器推送消息

	data = s.recv(1024)

	s.send("message")


这里的接收和推送顺序也可以互换，只要看服务端的逻辑

如果服务端是先推送再接收，那客户端就要先接收再推送
如果服务端是先接收再推送，那客户端就要先推送再接收

因为接收是阻塞的，没有接收到东西就不会执行下面的代码。为了保险起见，可以先让客户端推送，防止服务端没有响应

第四步，关闭连接：

	s.close()