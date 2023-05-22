+++
title = "在 Docker 容器中部署 Docsy"
weight = 3
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Deploy Docsy inside a Docker container - 在 Docker 容器中部署 Docsy 

https://www.docsy.dev/docs/get-started/quickstart-docker/

​	使用 Docker 镜像可以在本地运行和测试 Docsy 站点，无需安装所有 Docys 依赖项。

​	我们提供了一个 Docker 镜像，您可以使用它在本地运行和测试 Docsy 站点，而无需安装所有 Docsy 的依赖项。

## 安装先决条件 

1. 在 Mac 和 Windows 上，下载并安装 [Docker Desktop](https://www.docker.com/get-started)。在 Linux 上，安装 [Docker engine](https://docs.docker.com/engine/install/#server) 和 [Docker Compose](https://docs.docker.com/compose/install/)。

   安装可能需要您重新启动计算机以使更改生效。

2. [安装 git](https://github.com/git-guides/install-git)。


## 从 docsy-example 模板创建您的存储库

​	docsy-example 存储库提供了一个基本的站点结构，您可以将其用作创建自己的文档的起点。

1. 使用 [docsy-example 模板](https://github.com/google/docsy-example) 来 [创建自己的存储库](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template)。

2. 通过 [克隆新创建的存储库](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository) 将代码下载到本地计算机。

3. 将工作目录更改为新创建的文件夹：

   ```bash
   cd docsy-example
   ```


## 构建并运行容器 

​	docsy-example 存储库包括一个 [Dockerfile](https://docs.docker.com/engine/reference/builder/)，您可以使用它来运行您的站点。

1. 构建 Docker 镜像：

   ```bash
   docker-compose build
   ```

2. 运行该构建的镜像：

   ```bash
   docker-compose up
   ```

3. 在您的 Web 浏览器中打开地址 `http://localhost:1313` 以加载 docsy-example 主页。现在您可以对源文件进行更改，在您的浏览器中进行实时重新加载。


## Cleanup 清理

​	要清理您的系统并删除容器镜像，请按以下步骤操作。

1. 使用 **Ctrl + C** 停止 Docker Compose。

2. 删除生成的镜像

   ```bash
   docker-compose rm
   ```


## 接下来是什么？ 

- 了解 Docsy 的[基本设置和配置](https://www.docsy.dev/docs/get-started/basic-configuration/)。 
- [添加内容并自定义您的站点](https://www.docsy.dev/docs/adding-content/)
- [发布您的站点](https://www.docsy.dev/docs/deployment/).

  
