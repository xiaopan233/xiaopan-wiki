# requests



# 解决返回乱码的问题：

```
r.encoding = r.apparent_encoding
```

其中。r.apparent_encoding 表示的是网页的真实编码，把encoding设置为网页的编码，就会不乱码啦。