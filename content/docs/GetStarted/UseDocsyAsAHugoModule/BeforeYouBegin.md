+++
title = "开始之前"
weight = 1
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Before you begin - 开始之前

https://www.docsy.dev/docs/get-started/docsy-as-module/installation-prerequisites/

​	使用 Docsy 作为 Hugo 模块构建站点的先决条件。

​	本页面描述了构建使用 Docsy 作为 Hugo 模块的站点的先决条件。

## 安装 Hugo 

​	为了本地构建和预览使用 Docsy 的站点（比如这个示例站点），需要安装[最新的扩展版 Hugo](https://github.com/gohugoio/hugo/releases)（我们推荐使用版本 0.73.0 或更高版本）。如果从发布页面进行安装，请确保获取的是支持 [SCSS](https://sass-lang.com/documentation/file.SCSS_FOR_SASS_USERS.html)的扩展版（`extended`） Hugo；你可能需要滚动到发布列表的末尾才能找到它。

​	有关全面的 Hugo 文档，请参阅 [gohugo.io](https://gohugo.io/)。

### 在 Linux 上 

​	谨慎使用 `sudo apt-get install hugo` 命令进行安装，因为它[不能为所有 Debian/Ubuntu 版本](https://gohugo.io/getting-started/installing/#debian-and-ubuntu)提供扩展版 Hugo，也可能不是最新的版本。

​	如果你已经安装了 Hugo，请检查其版本：

```bash
hugo version
```

​	如果结果是 `v0.73` 或更早版本，或者看不到 `Extended` 字样，那么你需要安装最新版本。在 [Install Hugo](https://gohugo.io/getting-started/installing/#linux) 页面中，可以查看完整的 Linux 安装选项。以下是从发布页面安装 Hugo 的方法：

1. 前往 [Hugo releases](https://github.com/gohugoio/hugo/releases) 页面。

3. 在最新版本中，向下滚动直到找到扩展版 Hugo 的列表。

5. 下载最新的扩展版 Hugo（`hugo_extended_0.1XX_Linux-64bit.tar.gz`）。

4. 创建一个新目录：

   ```bash
   mkdir hugo
   ```

9. 将下载的文件解压到 `hugo` 目录中。

6. 切换到新的目录：

   ```bash
   cd hugo
   ```

7. 安装 Hugo：

   ```bash
   sudo install hugo /usr/bin
   ```


### 在 macOS 上 

​	使用 [Brew](https://gohugo.io/getting-started/installing/#homebrew-macos)安装 Hugo。

### 作为 `npm` 模块 

​	你可以使用 `hugo-bin` 将 Hugo 安装为 `npm` 模块。这将把 `hugo-bin` 添加到你的 `node_modules` 文件夹中，并将依赖项添加到 `package.json` 文件中。要安装 Hugo 的扩展版：

```bash
npm install hugo-extended --save-dev
```

​	有关用法详细信息，请参阅[hugo-bin文档](https://www.npmjs.com/package/hugo-bin)。

## 安装Go语言 

​	Hugo的模块管理命令需要在系统上安装Go编程语言。检查`go`是否已安装：

```console
$ go version
go version go1.19.2 windows/amd64
```

​	确保您正在使用版本1.12或更高版本。

​	如果`go`语言尚未安装在您的系统上，或者您需要升级它，请前往Go站点的[下载区域](https://go.dev/dl/)，选择适合您系统架构的安装程序并执行它。之后，检查是否成功安装。

## 安装Git VCS客户端 

​	Hugo的模块管理命令需要在系统上安装`git`客户端。检查您的系统上是否已存在`git`：

```bash
$ git version
git version 2.39.1
```

​	如果您的系统上尚未安装`git`客户端，可以前往[Git站点](https://git-scm.com/)，下载适合您系统架构的安装程序并执行它。之后，检查是否成功安装。

## 安装PostCSS 

​	要构建或更新站点的CSS资源，您还需要[PostCSS](https://postcss.org/)来创建最终的assets。如果您需要安装它，则必须在您的计算机上安装最新版本的[NodeJS](https://nodejs.org/en/)，以便您可以使用`npm`，即Node包管理器。默认情况下，`npm`会在您运行`npm install`的目录下安装工具：

```bash
npm install -D autoprefixer
npm install -D postcss-cli
```

​	从[postcss-cli的8版本](https://github.com/postcss/postcss-cli/blob/master/CHANGELOG.md)开始，您还必须单独安装`postcss`：

```bash
npm install -D postcss
```

​	请注意，如果[全局](https://flaviocopes.com/npm-packages-local-global/)安装了`PostCSS`的版本大于5.0.1，则不会加载`autoprefixer`，您必须使用本地安装。

## 安装/升级Node.js 

​	为了确保您可以正确构建站点而不仅仅是执行`hugo server`，您必须安装[最新的长期支持（LTS）版本的Node.js](https://nodejs.org/en/about/releases/)。如果您没有最新的LTS版本，则可能会看到以下错误之一：

```
Error: Error building site: POSTCSS: failed to transform "scss/main.css" (text/css): Unexpected identifier
#OR
/home/user/repos/my-new-site/themes/docsy/node_modules/hugo-extended/postinstall.js:1
import install from "./lib/install.js";
       ^^^^^^^

SyntaxError: Unexpected identifier
    at Module._compile (internal/modules/cjs/loader.js:723:23)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)
    at Function.Module.runMain (internal/modules/cjs/loader.js:831:12)
    at startup (internal/bootstrap/node.js:283:19)
    at bootstrapNodeJSCore (internal/bootstrap/node.js:623:3)
```

​	您可以通过运行`node -v`来检查当前的Node.js版本。如果您需要安装新版本，请参阅以下说明：

- [基于Debian和Ubuntu的发行版](https://github.com/nodesource/distributions/blob/master/README.md#installation-instructions)

  tl;dr:

  ```bash
  # Using Ubuntu
  curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
  sudo apt-get install -y nodejs
  
  # Using Debian, as root
  curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
  apt-get install -y nodejs
  ```

- [基于企业Linux的发行版](https://github.com/nodesource/distributions/blob/master/README.md#installation-instructions-1)

  tl;dr:

  ```bash
  # As root
  curl -fsSL https://rpm.nodesource.com/setup_18.x | bash -
  
  # No root privileges
  curl -fsSL https://rpm.nodesource.com/setup_18.x | sudo bash -
  ```

## 接下来呢？ 

​	在安装完所有必要的前提条件之后，选择如何开始你的新Hugo站点

- [从预设的站点开始（适合初学者） ](https://www.docsy.dev/docs/get-started/docsy-as-module/example-site-as-template/)
- [从头开始创建站点（适合专家）](https://www.docsy.dev/docs/get-started/docsy-as-module/start-from-scratch/)
