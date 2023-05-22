+++
title = "创建新站点：从预设的站点开始"
weight = 2
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Create a new site: start with a prepopulated site - 创建新站点：从预设的站点开始

https://www.docsy.dev/docs/get-started/docsy-as-module/example-site-as-template/

​	通过使用 Docsy 示例站点的克隆作为起点来创建新的 Hugo 站点。

​	创建新 Docsy 站点的最简单方法是使用 [Docsy 示例站点](https://github.com/google/docsy-example)的源代码作为起点。这种方法为您的站点提供了一个骨架结构，包括顶层和文档章节以及您可以根据需要修改的模板。示例站点会自动作为 [Hugo 模块](https://gohugo.io/hugo-modules/)引入 Docsy 主题，因此很容易[保持最新状态](https://www.docsy.dev/docs/updating/updating-hugo-module/)。

​	如果您更喜欢从头开始创建站点，请按照"从头开始创建站点（Start a site from scratch）"的说明进行操作。

## TL;DR: 对于不耐烦的专家的设置

​	在 Unix Shell 或 Windows 命令行中运行以下命令：

```bash
git clone https://github.com/google/docsy-example.git my-new-site
cd  my-new-site
hugo server
```

​	现在，您可以在浏览器中预览 [http://localhost:1313](http://localhost:1313/) 中的新站点。

## 详细设置说明 

### 克隆 Docsy 示例站点 

​	[示例站点](https://example.docsy.dev/)为您构建文档站点提供了一个很好的起点，并且预先配置为自动引入 Docsy 主题作为 Hugo 模块。有两种不同的方法可以获取示例站点的本地克隆：

- 如果您只想创建本地副本，请选择选项1。 
- 如果您有 GitHub 帐户并希望为站点创建 GitHub 存储库，请选择选项2。 

#### 选项1：使用命令行（仅本地副本） 

​	如果您想使用除GitHub之外的远程存储库（例如[GitLab](https://gitlab.com/)、[BitBucket](https://bitbucket.org/)、[AWS CodeCommit](https://aws.amazon.com/codecommit/)、[Gitea](https://gitea.io/)），或者根本不需要远程存储库，只需直接使用`git clone`创建一个本地工作副本，将您选择的本地存储库名称（此处为`my-new-site`）作为最后一个参数即可：

```bash
git clone https://github.com/google/docsy-example.git my-new-site
```

#### 选项2：使用 GitHub UI（本地副本+关联的 GitHub 存储库） 

​	由于Docsy示例站点存储库是[模板存储库](https://github.blog/2019-06-06-generate-new-repositories-with-repository-templates/)，因此创建自己的远程GitHub克隆Docsy示例站点存储库非常容易：

1. 进入[Docsy示例站点存储库](https://github.com/google/docsy-example)，点击**Use this template**。

2. 选择新存储库的名称（例如`my-new-site`），并在**Repository name**字段中输入它。您还可以添加一个可选的**Description**。

3. 单击**Create repository from template**以创建新存储库。恭喜，您刚刚创建了远程Github克隆，现在它是您自己站点的起点！

4. 使用`git clone`创建您新创建的GitHub存储库的本地副本，并将其作为最后一个参数给出您的存储库的Web URL。

   ```bash
   git clone https://github.com/me-at-github/my-new-site.git
   ```


> 注意
>
> ​	根据您的环境，您可能需要微调`config.toml`中的[模块顶级设置](https://github.com/google/docsy-example/blob/1c7f7e300c90cd690ca5be66b43fe58713bb21c9/config.toml#L221-L228)，例如添加代理以在下载远程模块时使用。您可以在[Hugo模块文档](https://gohugo.io/hugo-modules/configuration/#module-config-top-level)中找到这些配置设置的详细信息。

​	现在，您可以对副本站点进行本地编辑并使用Hugo在本地进行测试。

### 预览您的站点 

​	要在本地构建和预览站点，请切换到克隆项目的根目录并使用Hugo的`server`命令：

```bash
cd my-new-site
hugo server
```

​	在浏览器中预览站点：[http://localhost:1313](http://localhost:1313/)。由于Hugo的实时预览功能，您可以立即看到对本地存储库源文件进行更改的影响。您可以在任何时候使用`Ctrl + c`停止Hugo服务器。[请参阅MacOS上的已知问题](https://www.docsy.dev/docs/get-started/known_issues/#macos)。

## 接下来呢？ 

- 添加一些[基本配置](https://www.docsy.dev/docs/get-started/basic-configuration/) 
- [编辑现有内容并添加更多页面](https://www.docsy.dev/docs/adding-content/) 
- [自定义您的站点](https://www.docsy.dev/docs/adding-content/lookandfeel/)
- [发布您的站点](https://www.docsy.dev/docs/deployment/)。
