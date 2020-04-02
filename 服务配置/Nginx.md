# Nginx

## 安装：

依赖：

```
openssl openssl-devel
zlib zlib-devel
pcre pcre-devel
gcc
```

nginx包下载：

```
wget http://nginx.org/download/nginx-1.9.9.tar.gz  
```

重启：

```
/usr/local/nginx/sbin/nginx -s reload
```



## 反向代理配置：

找到nginx的nginx.conf文件：

```
location / {
            proxy_pass http://192.168.206.128;
            index  index.html index.htm index.php;
        }
```

其中，proxy_pass是要代理到的网站地址。