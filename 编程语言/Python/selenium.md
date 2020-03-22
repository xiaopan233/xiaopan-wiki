# selenium

一个 浏览器自动化测试框架，可用来做网页截图



# 安装：

```
pip3 install selenium
```



下载一个[ChromeDriver - WebDriver for Chrome](https://sites.google.com/a/chromium.org/chromedriver/)，需要梯子。

下载好后，给chromedriver一个环境变量：

```
vim ~/.bashrc
最底下添加一行：
export PATH=/usr/local/src/chromedriver:$PATH
```

然后我需要重启才能正常使用，就算打了 source ~/.bashrc 在python下也用不得。。重启就好了。



# 基本使用

引用：

```
from selenium import webdriver
```



初始化chrome浏览器实例：

```
driver = webdriver.Chrome()
```



设置超时：

```
driver.set_page_load_timeout(2)
```



请求一个网页：

```
driver.get("http://www.sohu.com")
```



截图保存：

```
driver.get_screenshot_as_file(r"xxx.png")
```



退出dirver

```
driver.quit()
```



# root下使用：



直接用会报错，需要改个配置：

```
vim /usr/bin/google-chrome
将 exec -a "$0" "$HERE/chrome" "$@"  改为
exec -a "$0" "$HERE/chrome" "$@" --user-data-dir --no-sandbox
```

