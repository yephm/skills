# 运行Visdom出现的问题

## 1.启动visdom服务后长时间无反应

```cmd
Microsoft Windows [版本 10.0.18363.657]
(c) 2019 Microsoft Corporation。保留所有权利。

C:\Users\UserName>python -m visdom.server
D:\Anaconda3\lib\site-packages\visdom\server.py:39: DeprecationWarning: zmq.eventloop.ioloop is deprecated in pyzmq 17. pyzmq now works with default tornado and asyncio eventloops.
  ioloop.install()  # Needs to happen before any tornado imports!
Checking for scripts.
Downloading scripts, this may take a little while
```

### 解决方法：

1.找到`visdom`模块的安装位置，其位置位于`python`或`anaconda`安装目录下面`\Lib\site-packages\visdom`

文件目录结构：

```
├─static
│  ├─css
│  ├─fonts
│  └─js
├─__pycache__
├─__init__.py
├─__init__.pyi
├─py.typed
├─server.py
└─VERSION
```

2.修改文件`server.py` 修改函数`download_scripts_and_run`，注释`download_scripts()` 该函数位于全篇末尾，1917行，如下图所示：

```python
def download_scripts_and_run():
    # download_scripts()
    main()


if __name__ == "__main__":
    download_scripts_and_run()
```

3.下载新的`static`文件  将文件整体覆盖`\Lib\site-packages\visdom\static`

static



