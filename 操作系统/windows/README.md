# windows

做shift后门时，直接替换不得，没有权限，需要修改权限。

右键文件，转到安全选项卡，选择高级：
（仅做演示，shift后门的文件位sethc.exe）

![](./windows/1.png)

切换到所有者选项卡，点击编辑，将所有者更换为Administrator后点击确定

![](./windows/2.png)

然后退出去，就能发现可以更改Administrator对于这个文件的操作权限了。

![](./windows/3.png)

此时就可以删除文件，替换文件什么的了。