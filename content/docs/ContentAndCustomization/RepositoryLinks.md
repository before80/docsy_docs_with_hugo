+++
title = "代码库链接"
weight = 9
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Repository Links - 代码库链接 

https://www.docsy.dev/docs/adding-content/repository-links/

​	帮助您的用户与您的源代码库进行交互。 

​	Docsy [文档和博客布局](https://www.docsy.dev/docs/adding-content/content/#adding-docs-and-blog-posts) 包括让读者可以通过您的网站源代码仓库编辑页面或为您的文档或项目创建问题的链接。当前生成的每个文档或博客页面的链接如下：

- **View page source**：将用户带到您的文档存储库中的页面源代码。 
- **Edit this page**：将用户带到页面内容的可编辑版本，位于他们的文档库复刻中（如果有的话）。如果用户没有您的文档库的当前 fork，则在进行编辑之前，将邀请他们创建一个 fork。然后，用户可以为您的文档创建拉取请求。
- **Create child page**：将用户带到在他们的文档库 fork 中创建新文件的表单中。新文件将作为他们单击链接页面的子级位置。该表单将使用一个模板进行预填，用户可以编辑此模板以创建自己的页面。您可以通过将 `assets/stubs/new-page-template.md` 添加到您自己的项目中来更改此设置。
- **Create documentation issue**：将用户带到一个新的 issue 表单，在其中，当前页面的名称为该问题的标题。
- **Create project issue**（可选）：将用户带到项目仓库中的一个新的issue 表单。如果您有单独的项目和文档存储库，并且您的用户想要针对正在讨论的项目功能提交问题，而不是针对您的文档，那么这可能很有用。

​	此页面向您展示了如何配置这些链接。

​	目前，Docsy仅支持GitHub存储库链接。由于GitLab可以处理相同的链接方案，因此也应该有效。如果您正在使用其他存储库（例如Bitbucket）并希望生成存储库链接，请随时 [添加功能请求或更新我们的主题](https://www.docsy.dev/docs/contribution-guidelines/)。

## 链接配置 

​	在 `hugo.toml`/`hugo.yaml`/`hugo.json` 文件中，有四个变量可以配置以设置链接，同时在您的页面元数据中也有一个变量可以配置。

### `github_repo`

​	您站点的源代码仓库的URL。此链接用于生成**Edit this page**、**Create child page**和**Create documentation issue**等链接。

Configuration file:

=== "hugo.yaml"

    ```yaml
    github_repo: 'https://github.com/google/docsy'
    
    ```

=== "hugo.toml"

    ```toml
    github_repo = "https://github.com/google/docsy"
    
    ```

=== "hugo.json"

    ```json
    {
      "github_repo": "https://github.com/google/docsy"
    }
    
    ```



### `github_subdir` (可选)

​	如果您的内容目录不在仓库的根目录中，请在此指定一个值。例如，此站点位于其仓库的 `userguide` 子目录中。设置此值意味着您的编辑链接将指向正确的页面。

Configuration file:

=== "hugo.yaml"

    ```yaml
    github_subdir: 'userguide'
    
    ```

=== "hugo.toml"

    ```toml
    github_subdir = "userguide"
    
    ```

=== "hugo.json"

    ```json
    {
      "github_subdir": "userguide"
    }
    
    ```



### `github_project_repo` (可选)

​	如果您有一个单独的项目仓库，希望您的用户能够从相关的文档中创建项目issues，请在此指定一个值。只有在设置了此项后，**Create project issue**链接才会显示。

Configuration file:

=== "hugo.yaml"

    ```yaml
    github_project_repo: 'https://github.com/google/docsy'
    
    ```

=== "hugo.toml"

    ```toml
    github_project_repo = "https://github.com/google/docsy"
    
    ```

=== "hugo.json"

    ```json
    {
      "github_project_repo": "https://github.com/google/docsy"
    }
    
    ```



### `github_branch` (可选)

​	如果您希望引用其他的 github 设置（如 **Edit this page**或 **Create project issue**）的不同分支，请在此指定一个值。

Configuration file:

=== "hugo.yaml"

    ```yaml
    github_branch: 'release'
    
    ```

=== "hugo.toml"

    ```toml
    github_branch = "release"
    
    ```

=== "hugo.json"

    ```json
    {
      "github_branch": "release"
    }
    
    ```



### `path_base_for_github_subdir` (可选)

​	假设 `content/some-section` 下的所有页面的源文件来自另一个仓库，例如[git 子模块](https://git-scm.com/book/en/v2/Git-Tools-Submodules)。在该章节的索引页中添加以下设置，以便该章节中的所有页面的存储库链接均指向源 仓库：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: Some super section
    cascade:
      github_repo: https://github.com/some-username/another-repo/
      github_subdir: docs
      path_base_for_github_subdir: content/some-section
    …
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "Some super section"
    [cascade]
    github_repo = "https://github.com/some-username/another-repo/"
    github_subdir = "docs"
    path_base_for_github_subdir = "content/some-section"
    …
    +++
    ```

=== "json"

    ```json
    {
      "title": "Some super section",
      "cascade": {
        "github_repo": "https://github.com/some-username/another-repo/",
        "github_subdir": "docs",
        "path_base_for_github_subdir": "content/some-section"
      }
    }
    ```



​	例如，考虑一个位于路径 `content/some-section/subpath/some-page.md` 的页面，全局 `github_branch` 设置为 `main`。上面的索引页面设置将为 `some-page.md` 生成以下编辑链接：

```nocode
https://github.com/some-username/another-repo/edit/main/docs/subpath/some-page.md
```

​	如果您只有一个来自另一个仓库的页面，请省略 `cascade` 键，并编写与上面所示相同的顶级设置。

​	如果您希望用户也能在源仓库中创建项目问题，则还需设置 `github_project_repo`，例如：

```yaml
---
...
cascade:
  github_repo: &repo https://github.com/some-username/another-repo/
  github_project_repo: *repo
...
---
```

Front matter:

=== "yaml"

    ```yaml
    ---
    …
    cascade:
      github_repo: &repo https://github.com/some-username/another-repo/
      github_project_repo: *repo
    …
    ---
    ```

=== "toml"

    ```toml
    +++
    …
    [cascade]
    github_repo = "https://github.com/some-username/another-repo/"
    github_project_repo = "https://github.com/some-username/another-repo/"
    …
    +++
    ```

=== "json"

    ```json
    {
      "cascade": {
        "github_repo": "https://github.com/some-username/another-repo/",
        "github_project_repo": "https://github.com/some-username/another-repo/"
      }
    }
    ```



> 提示
>
> 请注意，YAML 代码片段使用了 [YAML 锚点](https://support.atlassian.com/bitbucket-cloud/docs/yaml-anchors/)。使用 YAML 锚点是可选的，但它有助于保持设置的 DRY（不重复自己）。

​	`path_base_for_github_subdir` 设置是一个正则表达式，因此即使您的站点包含 [多个语言](https://www.docsy.dev/docs/language/)，您仍然可以使用它，例如：

Front matter:

=== "yaml"

    ```yaml
    ---
    …
    path_base_for_github_subdir: content/\w+/some-section
    …
    ---
    ```

=== "toml"

    ```toml
    +++
    …
    path_base_for_github_subdir = "content/\w+/some-section"
    …
    +++
    ```

=== "json"

    ```json
    {
    …
      "path_base_for_github_subdir": "content/\w+/some-section"
    …
    }
    ```



​	在某些情况下，页面来源于具有不同名称的文件，您可以指定 `from` 和 `to` 路径重命名设置。以下是一个例子，其中一个索引文件在来源仓库中命名为 `README.md`：

Front matter:

=== "yaml"

    ```yaml
    ---
    …
    github_repo: https://github.com/some-username/another-repo/
    github_subdir: docs
    path_base_for_github_subdir:
      from: content/some-section/(.*?)/_index.md
      to: $1/README.md
    …
    ---
    ```

=== "toml"

    ```toml
    +++
    …
    github_repo = "https://github.com/some-username/another-repo/"
    github_subdir = "docs"
    
    [path_base_for_github_subdir]
    from = "content/some-section/(.*?)/_index.md"
    to = "$1/README.md"
    …
    +++
    ```

=== "json"

    ```json
    {
      …
      "github_repo": "https://github.com/some-username/another-repo/",
      "github_subdir": "docs",
      "path_base_for_github_subdir": {
        "from": "content/some-section/(.*?)/_index.md",
        "to": "$1/README.md"
      },
      …
    }
    ```



### `github_url` (可选)

> 弃用说明 
>
> 该设置已弃用。请改用 [path_base_for_github_subdir](https://www.docsy.dev/docs/adding-content/repository-links/#path_base_for_github_subdir-optional)。

​	在您的页面元数据中指定此值以设置此页面的特定编辑 URL，例如以下示例：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: Some page
    github_url: https://github.com/some-username/another-repo/edit/main/README.md
    …
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "Some page"
    github_url = "https://github.com/some-username/another-repo/edit/main/README.md"
    …
    +++
    ```

=== "json"

    ```json
    {
      "title": "Some page",
      "github_url": "https://github.com/some-username/another-repo/edit/main/README.md",
      …
    }
    ```



​	如果您的页面源文件在多个 Git 存储库中，或需要非 GitHub URL，则可以使用此选项。使用此值的页面仅具有 **Edit this page** 链接。

## 禁用链接 

​	您可以使用 CSS 有选择性地禁用（隐藏）链接。例如，将以下内容添加到 [项目的 `_styles_project.scss`](https://www.docsy.dev/docs/adding-content/lookandfeel/#project-style-files) 文件中，以从所有页面中隐藏 **Create child page** 链接：

```scss
.td-page-meta--child { display: none !important; }
```

​	每种链接类型都有一个与之关联的唯一类名 `.td-page-meta--KIND`，如下表所定义：

| 链接类型                   | 类名                           |
| -------------------------- | ------------------------------ |
| View page source           | `.td-page-meta--view`          |
| Edit this page             | `.td-page-meta--edit`          |
| Create child page          | `.td-page-meta--child`         |
| Create documentation issue | `.td-page-meta--issue`         |
| Create project issue       | `.td-page-meta--project-issue` |

​	当然，您也可以使用这些类为您的项目为仓库链接提供独特的样式。
