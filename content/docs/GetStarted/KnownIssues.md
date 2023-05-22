+++
title = "已知问题"
weight = 5
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Known issues - 已知问题 

https://www.docsy.dev/docs/get-started/known_issues/

​	在安装 Docsy 主题时的已知问题。 

​	以下问题适用于 [MacOS](https://www.docsy.dev/docs/get-started/known_issues/#macos)和 [Windows Subsystem for Linux](https://www.docsy.dev/docs/get-started/known_issues/#windows-subsystem-for-linux-wsl)：

### MacOS

#### Errors: `too many open files` or `fatal error: pipe failed`

​	默认情况下，MacOS允许打开少量文件描述符。对于较大的网站或同时运行多个应用程序时，当您运行[`hugo server`](https://gohugo.io/commands/hugo_server/)本地预览网站时，您可能会收到以下错误之一：

- POSTCSS v7 及更早版本：

  ```
  ERROR 2020/04/14 12:37:16 Error: listen tcp 127.0.0.1:1313: socket: too many open files
  ```

- POSTCSS v8 及更高版本：

  ```
  fatal error: pipe failed
  ```


##### Workaround 解决方法 

​	为了暂时允许更多的打开文件：

1. 通过运行以下命令查看当前设置：

   ```sh
   sudo launchctl limit maxfiles
   ```

2. 通过运行以下命令将限制增加到`65535`个文件。如果您的站点文件较少，则可以选择设置较低的软（`65535`）和硬（`200000`）限制。

   ```shell
   sudo launchctl limit maxfiles 65535 200000
   ulimit -n 65535
   sudo sysctl -w kern.maxfiles=200000
   sudo sysctl -w kern.maxfilesperproc=65535
   ```


​	请注意，您可能需要为每个新的shell设置这些限制。[了解有关这些限制及如何使其永久的更多信息](https://www.google.com/search?q=mac+os+launchctl+limit+maxfiles+site%3Aapple.stackexchange.com&oq=mac+os+launchctl+limit+maxfiles+site%3Aapple.stackexchange.com)。

### Windows Subsystem for Linux (WSL)

​	如果您正在使用WSL，请确保在文件系统的Linux挂载上运行`hugo`，而不是在Windows挂载上运行，否则可能会出现意外错误。
