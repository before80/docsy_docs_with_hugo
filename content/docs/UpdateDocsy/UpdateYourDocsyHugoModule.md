+++
title = "更新您的 Docsy Hugo 模块"
weight = 1
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Update your Docsy Hugo Module - 更新您的 Docsy Hugo 模块

[https://www.docsy.dev/docs/updating/updating-hugo-module/](https://www.docsy.dev/docs/updating/updating-hugo-module/)

​	使用 Hugo 模块更新你的 Docsy 主题至最新版本。 

​	当将 Docsy 主题作为 Hugo 模块使用时，更新主题非常简单。

​	在命令提示符中，切换到现有站点的根目录。

```bash
cd /path/to/my-existing-site
```

​	然后使用hugo的模块`get`子命令并带有`update`标志：

```bash
hugo mod get -u github.com/google/docsy
```

​	Hugo 自动拉取最新的主题版本。就是这样，你的更新完成了！

> 提示
>
> ​	如果你想将你的模块设置为 Docsy 主题库中的某个版本，只需在更新主题时指定代表此版本的标签名称，例如：
>
> ```sh
> hugo mod get -u github.com/google/docsy@v0.6.0
> ```
> 
> ​	你也可以指定一个提交哈希值，例如：
>
> ```sh
> hugo mod get -u github.com/google/docsy@6c8a3afe
> ```

