# Chapter 7：浅谈python 中的FTP模块

先看一下FTP的流程。
1.连接到服务器。
2.登录。
3.发出服务请求（希望能得到响应）。
4.退出。
在Python中使用FTP，需要导入**ftplib**模块，并实例化一个ftplib.FTP类对象。所有的FTP操作（如登录、传输文件和注销等）都要使用这个对象完成。
举例：

```python
self.ftp.login(self.uname, self.pwd)
```

cwd()----获取当前工作目录

pwd(path)----把当前工作目录设置为path所示的路径

retrbinary(cmd,cb[]）----下载

storbinary(cmd,f[,bs=8192])--上传
