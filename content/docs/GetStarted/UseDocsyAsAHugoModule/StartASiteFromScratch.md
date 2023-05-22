+++
title = "创建新站点：从头开始创建新站点"
weight = 3
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Create a new site: Start a new site from scratch - 创建新站点：从头开始创建新站点 

​	使用 Docsy 作为 Hugo 模块从头开始创建新的 Hugo 站点 

​	创建 Docsy 站点的最简单方法是[复制我们的示例站点](https://www.docsy.dev/docs/get-started/docsy-as-module/example-site-as-template/)。但是，如果您是经验丰富的 Hugo 用户或者我们示例站点的站点结构不符合您的需求，您可能更喜欢从头开始创建新的站点。使用此选项，您将获得 Docsy 的外观和感觉、导航和其他功能，但您需要指定自己的站点结构。

​	这些说明仅为您的站点项目提供最小的文件结构，以便您可以逐步构建和扩展您的实际站点。第一步是将 Docsy 主题作为 [Hugo 模块](https://gohugo.io/hugo-modules/)添加到您的站点中。如果需要，您可以轻松地从 Docsy GitHub 存储库[更新](https://www.docsy.dev/docs/updating/)模块到最新版本。

## TL;DR: 专家快速设置

​	在您的命令提示符下运行以下命令：

CLI:

=== "Unix shell"

    ```bash
    hugo new site my-new-site
    cd  my-new-site
    hugo mod init github.com/me/my-new-site
    hugo mod get github.com/google/docsy@v0.6.0
    cat >> config.toml <<EOL
    [module]
    proxy = "direct"
    [[module.imports]]
    path = "github.com/google/docsy"
    [[module.imports]]
    path = "github.com/google/docsy/dependencies"
    EOL
    hugo server
    ```

=== "Windows command line"

    ```bash
    hugo new site my-new-site
    cd  my-new-site
    hugo mod init github.com/me/my-new-site
    hugo mod get github.com/google/docsy@v0.6.0
    (echo [module]^
    
    proxy = "direct"^
    
    [[module.imports]]^
    
    path = "github.com/google/docsy"^
    
    [[module.imports]]^
    
    path = "github.com/google/docsy/dependencies")>>config.toml
    hugo server
    ```

​	现在，您可以在浏览器中预览您的新站点，网址为 [http://localhost:1313](http://localhost:1313)。

## 详细设置说明 

​	将 [Docsy 主题](https://github.com/google/docsy)指定为最小站点的 Hugo 模块可为您提供所有主题的好处，但您需要指定自己的站点结构。

### 创建新的骨架项目 

​	要创建一个新的 Hugo 站点项目，然后将 Docs 主题作为子模块添加，从您的项目根目录运行以下命令。

```bash
hugo new site my-new-site
cd  my-new-site
```

​	这将创建一个最小的站点结构，包含 `archetypes`、`content`、`data`、`layouts`、`static` 和 `themes` 文件夹以及一个配置文件（默认为 `config.toml`）。

> 提示
>
> ​	在 Hugo 0.110.0 中，默认配置文件的基本文件名已更改为 `hugo.toml`。如果您使用的是 hugo 0.110 或更高版本，请考虑将 `config.toml` 重命名为 `hugo.toml`！
>

### 将 Docsy 主题模块作为站点的依赖项导入 

​	只有作为 Hugo 模块的站点才能导入其他模块。要将您的站点转换为 Hugo 模块，请在新创建的站点目录中运行以下命令：

```bash
hugo mod init github.com/me/my-new-site
```

​	这将创建两个新文件，`go.mod` 用于模块定义，`go.sum` 用于保存模块校验和。

​	接下来，将 Docsy 主题模块声明为站点的依赖项。

```bash
hugo mod get github.com/google/docsy@v0.6.0
```

​	此命令将 `docsy`主题模块添加到您的定义文件 `go.mod` 中。

### 添加主题模块配置设置 

​	在您的站点[配置文件](https://gohugo.io/getting-started/configuration/#configuration-file)（默认：`config.toml`）的末尾添加以下片段中的设置并保存文件。

Configuration file:

=== "hugo.yaml"

    ```yaml
    module:
      proxy: direct
      hugoVersion:
        extended: true
        min: 0.73.0
      imports:
        - path: github.com/google/docsy
          disable: false
        - path: github.com/google/docsy/dependencies
          disable: false
    ```

=== "hugo.toml"

    ```toml
    [module]
      proxy = "direct"
      # uncomment line below for temporary local development of module
      # replacements = "github.com/google/docsy -> ../../docsy"
      [module.hugoVersion]
        extended = true
        min = "0.73.0"
      [[module.imports]]
        path = "github.com/google/docsy"
        disable = false
      [[module.imports]]
        path = "github.com/google/docsy/dependencies"
        disable = false
    ```

=== "hugo.json"

    ```json
    {
      "module": {
        "proxy": "direct",
        "hugoVersion": {
          "extended": true,
          "min": "0.73.0"
        },
        "imports": [
          {
            "path": "github.com/google/docsy",
            "disable": false
          },
          {
            "path": "github.com/google/docsy/dependencies",
            "disable": false
          }
        ]
      }
    }
    ```



​	您可以在[Hugo模块文档](https://gohugo.io/hugo-modules/configuration/#module-config-top-level)中找到这些配置设置的详细信息。根据您的环境，您可能需要微调它们，例如添加代理以在下载远程模块时使用。

### 预览您的站点 

​	要在本地构建和预览网站：

```bash
hugo server
```

​	默认情况下，您的网站将在 [http://localhost:1313](http://localhost:1313/) 上提供。如果遇到问题，请查看 [已知问题](https://www.docsy.dev/docs/get-started/known_issues/#macos)（MacOS）。

​	当您尝试构建网站时，您可能会遇到缺少参数和值的Hugo错误。这通常是因为您缺少Docsy使用的某些配置设置的默认值 ——  一旦您添加它们，您的网站就应该可以正确构建了。您可以在[基本网站配置](https://www.docsy.dev/docs/get-started/basic-configuration/)中了解如何添加配置 —— 即使您从头开始创建网站，我们建议复制示例网站配置，因为它为许多必需的配置参数提供了默认值。

## 下一步是什么？ 

- Add some [basic configuration](https://www.docsy.dev/docs/get-started/basic-configuration/)

- 添加一些[基本配置](https://www.docsy.dev/docs/get-started/basic-configuration/) 

- [添加内容并自定义您的站点](https://www.docsy.dev/docs/adding-content/)

- 从我们的[示例站点](https://github.com/google/docsy-example)和其他[示例](https://www.docsy.dev/docs/examples/)中获得一些想法。 

- [发布您的站点](https://www.docsy.dev/docs/deployment/).

  
