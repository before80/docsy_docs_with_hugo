+++
title = "其他设置选项"
weight = 2
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Other setup options - 其他设置选项

[https://www.docsy.dev/docs/get-started/other-options/](https://www.docsy.dev/docs/get-started/other-options/)

​	使用 Git 或 NPM 创建一个新的 Docsy 站点

​	如果您不想将 [Docsy 用作 Hugo 模块](https://www.docsy.dev/docs/get-started/docsy-as-module/)（例如，如果您不想安装 Go），但仍不想将主题文件复制到自己的存储库中，则可以将 Docsy 用作 [Git 子模块](https://git-scm.com/book/en/v2/Git-Tools-Submodules)。使用子模块还允许 Hugo 使用 Docsy 存储库中的主题文件，但比 Hugo 模块方法更复杂。这是在旧版本的 Docsy 示例站点中使用的方法，目前仍然得到支持。如果您正在使用 Docy 作为子模块，但想迁移到 Hugo 模块，请参阅我们的[迁移指南](https://www.docsy.dev/docs/get-started/other-options/)。

​	另外，如果您不想让 Hugo 从外部存储库获取主题文件（例如，如果您想直接自定义和维护本主题的副本，或者您的部署选择要求您在存储库中包含本主题的副本），则可以将文件直接克隆到您的站点源。

​	最后，您可以[将 Docsy 安装为 NPM 包](https://www.docsy.dev/docs/get-started/other-options/#option-3-docsy-as-an-npm-package)。

This guide provides instructions for all of these options, along with common prerequisites.

​	本指南提供了所有这些选项的说明，以及常见的先决条件。

## 先决条件

### 安装 Hugo

​	要本地构建和预览使用 Docsy 的网站（如本示例网站），您需要一个[最新的 **extended** 版本](https://github.com/gohugoio/hugo/releases)的[Hugo](https://gohugo.io/)（我们推荐使用 0.73.0 版本或更高版本）。如果您从发布页面安装，请确保获取支持 [SCSS](https://sass-lang.com/documentation/file.SCSS_FOR_SASS_USERS.html) 的`extended` Hugo 版本；您可能需要滚动列表以查看它。

​	有关全面的 Hugo 文档，请参见 [gohugo.io](https://gohugo.io/)。

#### 在 Linux 上

​	请注意，使用 `sudo apt-get install hugo` 可能[不会为所有 Debian/Ubuntu 版本提供 `extended` 版本](https://gohugo.io/getting-started/installing/#debian-and-ubuntu)，而且可能不会与最新的 Hugo 版本保持同步。

​	如果您已经安装了 Hugo，请检查您的版本：

```
hugo version
```

​	如果结果是 `v0.73` 或更早版本，或者您没有看到 `Extended`，那么您需要安装最新版本。您可以在 [安装 Hugo](https://gohugo.io/getting-started/installing/#linux) 中看到完整的 Linux 安装选项。以下是如何从发布页面安装 Hugo 的说明：

1. 转到 [Hugo 发布](https://github.com/gohugoio/hugo/releases)页面。

3. 在最新版本中，向下滚动，直到找到扩展版本列表。

5. 下载最新的扩展版本（`hugo_extended_0.9X_Linux-64bit.tar.gz`）。

4. 创建一个新目录：

   ```bash
   mkdir hugo
   ```

9. 提取您下载的文件到 `hugo`。

6. 切换到新目录：

   ```bash
   cd hugo
   ```

7. 安装 Hugo：

   ```
   sudo install hugo /usr/bin
   ```


#### 在 macOS 上

​	使用 [Brew](https://gohugo.io/getting-started/installing/#homebrew-macos)安装 Hugo。

#### 作为 NPM 模块

​	您可以使用 [hugo-extended](https://www.npmjs.com/package/hugo-extended) 将 Hugo 安装为 NPM 模块。要安装 Hugo 的扩展版本：

```
npm install hugo-extended --save-dev
```

### Node：获取最新 LTS 版本

​	如果已经安装了 Node，请检查您的 Node 版本。例如：

```sh
node -v
```

​	将您的Node版本安装或升级到[活跃的LTS版本](https://nodejs.org/en/about/releases/)。我们建议使用[nvm](https://github.com/nvm-sh/nvm/blob/master/README.md#installing-and-updating)来管理您的Node安装（显示Linux命令）：

```sh
nvm install --lts
```

### 安装PostCSS 

​	要构建或更新站点的CSS资源，您还需要[PostCSS](https://postcss.org/)。使用Node包管理器`npm`安装它。

> 重要提示：检查您的Node版本 
>
> ​	某些旧版本的Node安装的PostCSS软件包与Docsy不兼容。将您的Node版本与活动的[LTS版本](https://nodejs.org/en/about/releases/)进行对比，并在必要时进行升级。有关详细信息，请参阅[Node：获取最新的LTS版本](https://www.docsy.dev/docs/get-started/other-options/#node-get-the-latest-lts-release)。 
>

​	从您的项目根目录运行以下命令：

```sh
npm install --save-dev autoprefixer postcss-cli postcss
```

## 选项1：将Docsy作为Git子模块 

### 对于新站点 

​	要创建一个新站点并将Docsy主题作为Git子模块添加，运行以下命令：

1. 创建站点：

   ```shell
   hugo new site myproject
   cd myproject
   git init
   ```

3. [按照先前的说明](https://www.docsy.dev/docs/get-started/other-options/#install-postcss)安装postCSS。

5. 按照下面的说明为现有站点进行操作。


### 对于已经存在的站点 

​	要将Docsy主题添加到现有站点，请从项目的根目录运行以下命令：

1. 将Docsy作为Git子模块安装：

   ```sh
   git submodule add https://github.com/google/docsy.git themes/docsy
   cd themes/docsy
   git checkout v0.6.0
   ```

   要从Docsy的开发版本中进行操作（不建议），请改为运行以下命令：

   ```sh
   git submodule add --depth 1 https://github.com/google/docsy.git themes/docsy
   ```

2. 将Docsy添加为主题，例如：

   ```sh
   echo 'theme = "docsy"' >> config.toml
   ```

   > 提示 
   >
   > ​	在Hugo 0.110.0中，默认配置基础文件名更改为`hugo.toml`。如果您使用的是hugo 0.110或更高版本，请考虑将您的`config.toml`重命名为`hugo.toml`！ 


3. 获取Docsy依赖项：

   ```sh
   (cd themes/docsy && npm install)
   ```

4. （可选但建议）为了避免每次更新Docsy时都需要重复上一步操作，请考虑向项目的`package.json`文件添加以下[NPM脚本](https://docs.npmjs.com/cli/v8/using-npm/scripts)：

   ```json
   {
     "...": "...",
     "scripts": {
       "get:submodule": "git submodule update --init --depth 1",
       "_prepare:docsy": "cd themes/docsy && npm install",
       "prepare": "npm run get:submodule && npm run _prepare:docsy",
       "...": "..."
     },
     "...": "..."
   }
   ```

   每次从您的项目根目录运行`npm install`时，`prepare`脚本将获取Docsy及其依赖的最新版本。


​	从这一点开始，使用通常的Hugo命令来构建和提供您的站点，例如：

```sh
hugo serve
```

## 选项2：克隆该Docsy主题 

​	如果您不想使用子模块（例如，如果您想直接自定义和维护本主题的副本，或者您的部署选择需要在存储库中包含本主题的副本），则可以将本主题克隆到项目的`themes`子目录中。

​	将 Docsy 版本为 v0.6.0 的代码库克隆到你的项目的 `themes` 文件夹中，请在你的项目根目录下运行以下命令：

```sh
cd themes
git clone -b v0.6.0 https://github.com/google/docsy
cd docsy
npm install
```

​	如果您想要使用 Docsy 的开发版本（不建议，除非您计划将更改上游（upstream ）到 Docsy），则省略上面的克隆命令中的 `-b v0.6.0` 参数。

​	然后考虑设置一个 NPM [prepare](https://docs.npmjs.com/cli/v8/using-npm/scripts#prepare-and-prepublish)脚本，如选项 1 中所述。

​	有关更多信息，请参阅[Hugo](https://gohugo.io/)网站上的[Theme Components](https://gohugo.io/hugo-modules/theme-components/)。

## 选项 3：Docsy 作为 NPM 包 

​	您可以按以下方式使用 Docsy 作为 NPM 模块：

1. 创建您的站点，并将Docsy指定为站点主题：

   ```sh
   hugo new site myproject
   cd myproject
   echo 'theme = "docsy"' >> config.toml
   ```

2. 安装Docsy和postCSS（按照[之前的说明](https://www.docsy.dev/docs/get-started/other-options/#install-postcss)）：

   ```sh
   npm install --save-dev google/docsy#semver:0.6.0 autoprefixer postcss-cli postcss
   ```

3. 使用常规的Hugo命令构建或启动您的新站点，并指定Docsy主题文件的路径。例如，构建站点的命令如下：

   ```sh
   $ hugo --themesDir node_modules
   Start building sites …
   ...
   Total in 1890 ms
   ```

   你可以通过在站点的配置文件中添加本主题目录来删除 `--themesDir ...` 标志：

   ```sh
   echo 'themesDir = "node_modules"' >> config.toml
   ```


​	作为指定 `themesDir` 的替代方法，在某些平台上，你可以按如下方式创建指向 Docsy 主题目录的符号链接（显示了 Linux 命令，从站点根文件夹执行）：

```sh
mkdir -p themes
pushd themes
ln -s ../node_modules/docsy
popd
```

## 预览您的站点 

​	要在本地预览您的站点：

```sh
cd myproject
hugo server
```

​	默认情况下，您的站点将在 [http://localhost:1313](http://localhost:1313/) 上可用。有关MacOS上的已知问题，[请参见已知问题](https://www.docsy.dev/docs/get-started/known_issues/#macos)。

​	如果您在尝试构建站点时遇到缺少参数和值的 Hugo 错误，则通常是因为 Docsy 使用了某些配置设置的默认值而您没有它们，一旦您添加了它们，您的站点应该能够正确构建。有关如何添加配置的信息，请参见[基本站点配置](https://www.docsy.dev/docs/get-started/basic-configuration/) ——  即使您从头开始创建站点，我们建议复制示例站点配置，因为它为许多必需的配置参数提供了默认值。

## 下一步是什么？ 

- 添加一些[基本站点配置](https://www.docsy.dev/docs/get-started/basic-configuration/) 

- [添加内容并自定义您的站点](https://www.docsy.dev/docs/adding-content/)

- 从我们的[示例站点](https://github.com/google/docsy-example)和其他[示例](https://www.docsy.dev/docs/examples/)中获取一些想法。 

- [发布您的站点](https://www.docsy.dev/docs/deployment/).

  
