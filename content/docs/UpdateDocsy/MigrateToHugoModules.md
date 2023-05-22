+++
title = "迁移到Hugo模块"
weight = 3
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Migrate to Hugo Modules - 迁移到Hugo模块

https://www.docsy.dev/docs/updating/convert-site-to-module/

​	将现有站点转换为使用Docsy作为Hugo模块

## 适用于急于求成的专家

​	从命令行运行以下命令：

CLI:

=== "Unix shell"

    ```bash
    cd /path/to/my-existing-site
    hugo mod init github.com/me-at-github/my-existing-site
    hugo mod get github.com/google/docsy@v0.6.0
    sed -i '/theme = \["docsy"\]/d' config.toml
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
    cd  my-existing-site
    hugo mod init github.com/me-at-github/my-existing-site
    hugo mod get github.com/google/docsy@v0.6.0
    findstr /v /c:"theme = [\"docsy\"]" config.toml > config.toml.temp
    move /Y config.toml.temp config.toml
    (echo [module]^
    
    proxy = "direct"^
    
    [[module.imports]]^
    
    path = "github.com/google/docsy"^
    
    [[module.imports]]^
    
    path = "github.com/google/docsy/dependencies")>>config.toml
    hugo server
    ```



## 详细的转换说明

### 将Docsy主题模块作为站点的依赖项导入

​	在命令提示符下，切换到现有站点的根目录。

```bash
cd /path/to/my-existing-site
```

​	只有作为Hugo模块的站点才能导入其他Hugo模块。通过从站点目录中运行以下命令（将`github.com/me/my-existing-site`替换您的站点存储库），将现有站点转换为Hugo模块：

```bash
hugo mod init github.com/me/my-existing-site
```

​	这将创建两个新文件，`go.mod`用于模块定义和`go.sum`用于保存模块验证的校验和。

​	接下来，将Docsy主题模块声明为站点的依赖项。

```bash
hugo mod get github.com/google/docsy@v0.6.0
```

This command adds the `docsy` theme module to your definition file `go.mod`.

​	此命令将`docsy`主题模块添加到您的定义文件`go.mod`中。

​	更新您的配置文件

​	在您的 `config.toml`/`config.yaml`/`config.json` 文件中，更新该主题设置以使用Hugo模块。找到以下行：

Configuration file:

=== "config.yaml"

    ```yaml
    theme: docsy
    
    ```

=== "config.toml"

    ```toml
    theme = ["docsy"]
    
    ```

=== "config.json"

    ```json
    "theme": "docsy"
    
    ```



将此行更改为：

Configuration file:

=== "config.yaml"

    ```yaml
    theme:
      - github.com/google/docsy
      - github.com/google/docsy/dependencies
    
    ```

=== "config.toml"

    ```toml
    theme = ["github.com/google/docsy", "github.com/google/docsy/dependencies"]
    
    ```

=== "config.json"

    ```json
    "theme": [
      "github.com/google/docsy",
      "github.com/google/docsy/dependencies"
    ]
    
    ```



​	或者，您可以完全省略此行，并将其替换为以下代码段中给出的设置：

Configuration file:

=== "config.yaml"

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

=== "config.toml"

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

=== "config.json"

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



​	你可以在 [Hugo 模块文档](https://gohugo.io/hugo-modules/configuration/#module-config-top-level)中找到这些配置设置的详细信息。根据你的环境，你可能需要进行一些微调，例如添加代理以在下载远程模块时使用。

> 提示
>
> ​	在 Hugo 0.110.0 中，默认的配置基础文件名已更改为 `hugo.toml`。如果你使用的是 hugo 0.110 或更高版本，请考虑将你的 `config.toml` 重命名为 `hugo.toml`！

> 注意
>
> ​	如果你安装了多语言版本，请确保你的 `config.toml` 中的 `[languages]` 部分在带有模块导入的 `[module]` 部分之前声明。否则，你将遇到问题！

### 检查配置设置的有效性 

​	为了确保你的配置设置是正确的，请运行 `hugo mod graph` 命令，它会打印一个模块依赖项图：

```bash
hugo mod graph
hugo: collected modules in 1092 ms
github.com/me/my-existing-site github.com/google/docsy@v0.6.0
github.com/me/my-existing-site github.com/google/docsy/dependencies@v0.6.0
github.com/google/docsy/dependencies@v0.6.0 github.com/twbs/bootstrap@v5.2.3+incompatible
github.com/google/docsy/dependencies@v0.6.0 github.com/FortAwesome/Font-Awesome@v0.0.0-20230207192303-d02961b01815
```

​	确保列出了 `docsy`、`bootstrap` 和 `Font-Awesome` 的三行依赖项。如果没有，请仔细检查你的配置设置。

> 提示
>
> ​	为了清理你的模块缓存，请执行命令 `hugo mod clean`
>
> ```bash
>hugo mod clean
> hugo: collected modules in 995 ms
> hugo: cleaned module cache for "github.com/FortAwesome/Font-Awesome"
> hugo: cleaned module cache for "github.com/google/docsy"
> hugo: cleaned module cache for "github.com/google/docsy/dependencies"
> hugo: cleaned module cache for "github.com/twbs/bootstrap"
> ```



## 清理你的仓库 

​	由于你的站点现在使用 Hugo 模块，你可以按照下面的说明从`themes`目录中删除 `docsy`。首先，切换到你站点的根目录：

```bash
cd /path/to/my-existing-site
```

### 先前将 Docsy 主题安装为 Git 克隆

​	只需删除 `themes` 目录中的子目录 `docsy`：

```bash
rm -rf themes/docsy
```

### 先前将 Docsy 主题安装为 Git 子模块

​	如果您的 Docsy 主题是作为子模块安装的，请使用 git 的 `rm` 子命令删除 `themes` 目录中的子目录 `docsy`：

```bash
git rm -rf themes/docsy
```

​	现在，您可以提交更改到您的仓库中：

```bash
git commit -m "Removed docsy git submodule"
```

> 注意
>
> ​	使用 `rm -rf` 命令时请小心，确保您不会意外删除任何生产数据文件！
