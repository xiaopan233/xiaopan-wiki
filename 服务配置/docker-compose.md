# docker-compose

安装 docker-compose：

```
curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose

curl -L https://raw.githubusercontent.com/docker/compose/1.23.1/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose

docker-compose --version
```



安装 docker：

```
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```



docker 启动：

```
systemctl start docker.service 
systemctl enable docker.service
```

