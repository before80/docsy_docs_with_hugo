+++
title = "不使用 Hugo 模块更新 Docsy"
weight = 2
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Update Docsy without Hugo Modules - 不使用 Hugo 模块更新 Docsy

[https://www.docsy.dev/docs/updating/updating-submodules/](https://www.docsy.dev/docs/updating/updating-submodules/)

​	使用子模块或 `git pull` 更新 Docsy 主题至最新版本。 

​	如果你不使用 Hugo 模块，根据你在现有站点上安装 Docsy 的方式，使用以下两个程序之一来更新你的主题。

> 提示 
>
> ​	如果你打算更新你的站点，请考虑[将你的站点转换为 Hugo 模块](https://www.docsy.dev/docs/updating/convert-site-to-module/)。转换后，更新 Docsy 就更简单了！ 

## 更新 Docsy 子模块 

​	如果你在项目中将 [Docsy 主题作为子模块](https://www.docsy.dev/docs/get-started/other-options/#option-1-docsy-as-a-git-submodule)使用，则按如下方式更新子模块：

1. 导航到本地项目的根目录，然后运行：

   ```bash
   git submodule update --remote
   ```

2. 将更改添加到项目中并提交更改：

   ```bash
   git add themes/
   git commit -m "Updating theme submodule"
   ```

3. 将提交推送到项目存储库。例如运行：

   ```bash
   git push origin master
   ```


## Route 2：更新 Docsy 克隆版 

​	如果你将 [Docsy 主题克隆](https://www.docsy.dev/docs/get-started/other-options/#option-2-clone-the-docsy-theme)到项目的 `themes` 文件夹中，则使用 `git pull` 命令：

1. 导航到本地项目的 `themes` 目录：

   ```bash
   cd themes
   ```

2. 确保 `origin` 设置为 `https://github.com/google/docsy.git`：

   ```bash
   git remote -v
   ```

3. 更新本地克隆版：

   ```bash
   git pull origin master
   ```


​	如果你对克隆主题进行了任何本地更改，则必须手动解决任何合并冲突。
