+++
title = "打印支持"
weight = 7
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Print Support - 打印支持 

https://www.docsy.dev/docs/adding-content/print/

​	更容易地打印整个文档章节。 

​	大多数浏览器中的个别文档页面都可以很好地打印，因为布局已经被设计成从打印输出中省略导航界面。

​	在一些站点上，启用"打印整个章节"功能可能很有用（就像在本用户指南中所看到的）。选择此选项将使用适合打印的格式呈现当前顶级章节（例如此页面的Content 和Customization）的所有子页面和子章节，并附带该章节的目录。

​	要启用此功能，请在站点的`hugo.toml`/`hugo.yaml`/`hugo.json`文件中为"section"类型添加"print"输出格式：

Configuration file:

=== "hugo.yaml"

    ```yaml
    outputs:
      section:
        - HTML
        - RSS
        - print
    ```

=== "hugo.toml"

    ```toml
    [outputs]
    section = [ "HTML", "RSS", "print" ]
    
    ```

=== "hugo.json"

    ```json
    {
      "outputs": {
        "section": [
          "HTML",
          "RSS",
          "print"
        ]
      }
    }
    ```



然后，站点应在右侧导航中显示一个"打印整个章节"的链接。

## 进一步的定制 

### 禁用目录 

​	要在可打印视图中禁用目录，请在页面前置元数据或`hugo.toml`/`hugo.yaml`/`hugo.json`中将`disable_toc`参数设置为`true`：

Front matter:

=== "yaml"

    ```yaml
    ---
    …
    disable_toc: true
    …
    ---
    ```

=== "toml"

    ```toml
    +++
    …
    disable_toc = true
    …
    +++
    ```

=== "json"

    ```json
    {
      …,
      "disable_toc": true,
      …
    }
    ```



或配置文件： 

=== "hugo.yaml"

    ```yaml
    params:
      print:
        disable_toc: true
    ```

=== "hugo.toml"

    ```toml
    [params.print]
    disable_toc = true
    ```

=== "hugo.json"

    ```json
    {
      "params": {
        "print": {
          "disable_toc": true
        }
      }
    }
    ```



## 布局钩子 

​	有一些布局的partial和hook被定义用于自定义打印格式。它们可以在`layouts/partials/print`中找到。

​	Hook可以按类型定义。例如，您可能想自定义"blog"页面和"docs"页面的标题布局。可以通过创建`layouts/partials/print/page-heading-<type>.html`来实现，例如`page-heading-blog.html`。它默认使用页面title 和description 作为标题（heading）。

​	类似地，每个页面的格式可以通过创建`layouts/partials/print/content-<type>.html`进行自定义。
