+++
title = "添加内容"
weight = 1
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Adding Content - 添加内容 

[https://www.docsy.dev/docs/adding-content/content/](https://www.docsy.dev/docs/adding-content/content/)

​	向 你的Docsy 站点添加不同类型的内容。 

​	现在你有了一个带有 Docsy 的新 Hugo 站点，是时候添加一些内容了！本页面告诉你如何使用主题来添加和组织站点内容。

## 内容根目录 

​	你可以在你的 Hugo 站点项目的内容根目录下添加站点内容 - 即 `content/` 或[语言特定的](https://www.docsy.dev/docs/language/)根目录，比如 `content/en/`。这里的主要例外是你不想构建到站点中的静态文件：你可以在下面的[添加静态内容](https://www.docsy.dev/docs/adding-content/content/#adding-static-content)中了解更多关于添加这些文件的位置。你的内容根目录中的文件通常按照站点章节和模板分组到子目录中，我们将在[内容章节和模板](https://www.docsy.dev/docs/adding-content/content/#content-sections-and-templates)中查看这些子目录。

​	你可以在[目录结构解释](https://gohugo.io/getting-started/directory-structure/#directory-structure-explained)中了解有关 Hugo 目录结构的更多信息。

## 内容章节和模板 

​	Hugo 使用你提供的内容文件和站点主题提供的任何模板来构建你的站点页面。这些模板（在 Hugo 术语中称为"layouts（布局）"）包括你的页面的页眉、页脚、导航和样式表链接：基本上除了页面的具体内容以外的一切。这些模板又可以由局部组成：用于页面元素（如页眉、搜索框等）的小型可重用 HTML 片段。

​	因为大多数技术文档站点有不同的章节来存放不同类型的内容，Docsy 主题提供了以下顶级站点章节的[模板](https://github.com/google/docsy/tree/main/layouts)：

- [docs](https://github.com/google/docsy/tree/main/layouts/docs) 用于你站点的文档章节的页面。 
- [blog](https://github.com/google/docsy/tree/main/layouts/blog) 用于你站点的博客页面。 
- [community](https://github.com/google/docsy/tree/main/layouts/community) 用于你站点的社区页面。 

​	它还提供了一种[默认的"着陆页"模板类型](https://github.com/google/docsy/tree/main/layouts/_default)，带有站点页眉和页脚，但没有左侧导航，你可以用它来作为任何其他章节的模板。在这个站点和我们的示例站点中，它用于站点[主页](https://www.docsy.dev/)和[About](https://www.docsy.dev/about/)页面。

​	你站点中的每个顶级章节都对应着站点内容根目录中的一个目录。根据内容所在的文件夹，Hugo 自动应用适当的模板来渲染该章节。例如，此页面位于站点内容根目录 `content/en/` 的 `docs` 子目录中，因此 Hugo 自动应用 `docs` 模板。你可以通过显式指定特定页面的模板或内容类型来覆盖此行为。

​	如果你复制了示例站点，则已经拥有适当命名的顶级章节目录来使用 Docsy 的模板，每个目录都有一个索引页面（ `_index.md` 或 `index.html`）供用户访问。这些顶级章节也会出现在示例站点的[顶级菜单](https://www.docsy.dev/docs/adding-content/navigation/#top-level-menu)中。

### 自定义章节

​	如果您复制了示例站点，但并不想使用提供的任何内容章节之一，只需删除相应的内容子目录即可。同样，如果您想添加一个顶级章节，只需添加一个新的子目录，但如果您想使用除默认模板之外的任何现有Docsy模板，则需要在每个页面的[前置元数据](https://www.docsy.dev/docs/adding-content/content/#page-frontmatter)中明确指定布局或内容类型。例如，如果您创建一个新目录`content/en/amazing`，并且希望该自定义章节中的一个或多个页面使用Docsy的`docs`模板，则在每个页面的前置元数据中添加`type: docs`：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "My amazing new section"
    weight: 1
    type: docs
    description: >
        A special section with a docs layout.
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "My amazing new section"
    weight = 1
    type = "docs"
    description = '''
    A special section with a docs layout.
    '''
    +++
    ```

=== "json"

    ```json
    {
      "title": "My amazing new section",
      "weight": 1,
      "type": "docs",
      "description": "A special section with a docs layout.\n"
    }
    ```

​	或者，根据现有模板，在您项目的`layouts`目录中为您的新章节创建自己的页面模板。

​	您可以在[Hugo模板](https://gohugo.io/templates/)中了解更多有关Hugo页面布局的工作原理。本页面的其余部分将告诉您如何添加内容并使用Docsy的每个模板。

### 替代站点结构

​	如上所述，默认情况下，您的站点具有主页（使用`_default`布局），`/docs/`下的文档章节，`/blog/`下的博客章节和`/community/`下的社区章节。每个章节的[类型](https://gohugo.io/content-management/types/)（确定其使用的布局）与其目录名称匹配。

​	在某些情况下，您可能希望具有不同的目录结构，但仍要利用Docsy的布局。一个常见的例子是"文档站点"，其中大多数页面（包括主页）都使用文档布局，或者您可能更喜欢将`/news/`目录视为博客布局。

​	自Hugo 0.76以来，通过使用[目标特定级联前置元数据](https://gohugo.io/content-management/front-matter/#target-specific-pages)，而不需要复制布局到您的站点或在每个页面上都指定`type: blog`，这已经变得可行。

​	例如，对于`/news/`章节，您可以在index 页面中指定以下前置元数据，这将更改该章节及其以下所有内容的类型为"blog"：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "Latest News"
    linkTitle: "News"
    menu:
      main:
        weight: 30
    
    cascade:
      - type: "blog"
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "Latest News"
    linkTitle = "News"
    
    [menu.main]
    weight = 30
    
    [[cascade]]
    type = "blog"
    +++
    ```

=== "json"

    ```json
    {
      "title": "Latest News",
      "linkTitle": "News",
      "menu": {
        "main": {
          "weight": 30
        }
      },
      "cascade": [
        {
          "type": "blog"
        }
      ]
    }
    ```



​	如果您想创建一个"docs"站点，则在顶级`_index.md`中指定类似以下内容将使所有顶级章节都被视为"文档"，除了"news"：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "My Wonderful Site"
    
    cascade:
      - type: "blog"
        toc_root: true
        _target:
        path: "/news/**"
      - type: "docs"
        _target:
        path: "/**"
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "My Wonderful Site"
    
    [[cascade]]
    type = "blog"
    toc_root = true
    
      [cascade._target]
      path = "/news/**"
    
    [[cascade]]
    type = "docs"
    
      [cascade._target]
      path = "/**"
    +++
    ```

=== "json"

    ```json
    {
      "title": "My Wonderful Site",
      "cascade": [
        {
          "type": "blog",
          "toc_root": true,
          "_target": {
            "path": "/news/**"
          }
        },
        {
          "type": "docs",
          "_target": {
            "path": "/**"
          }
        }
      ]
    }
    ```



请注意，这里增加了`toc_root`。将其设置为`true`，可以使其被视为站点的单独部分，具有自己的左侧导航菜单。

​	使用此技术的示例基于文档的站点可在[mostly docs](https://github.com/gwatts/mostlydocs/) repo中找到。

## 页面前置元数据

​	Hugo站点中的每个页面文件都有元数据前置元数据，告诉Hugo有关页面的信息。您可以在TOML、YAML或JSON中指定页面前置元数据（我们的示例站点和此站点使用YAML）。使用前置元数据指定页面标题、描述、创建日期、链接标题、模板、菜单权重，甚至包括页面使用的任何资源，如图像。您可以在[前置元数据](https://gohugo.io/content-management/front-matter/)中查看可能的页面前置元数据的完整列表。

例如，这是本页面的前置元数据：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "Adding Content"
    linkTitle: "Adding Content"
    weight: 1
    description: >
        Add different types of content to your Docsy site.
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "Adding Content"
    linkTitle = "Adding Content"
    weight = 1
    description = '''
    Add different types of content to your Docsy site.
    '''
    +++
    ```

=== "json"

    ```json
    {
      "title": "Adding Content",
      "linkTitle": "Adding Content",
      "weight": 1,
      "description": "Add different types of content to your Docsy site.\n"
    }
    ```



​	你需要提供的最基本的前置元数据是title（标题）：其他的内容都由你决定！然而，如果你没有设置页面weight（权重），你的[导航](https://www.docsy.dev/docs/adding-content/navigation)可能会有点混乱。你可能还想包括`description`，因为 Docsy 使用它来生成搜索引擎使用的mata `description` 标签。详见[搜索引擎优化（SEO）元标签](https://www.docsy.dev/docs/adding-content/feedback/#search-engine-optimization-meta-tags)。

## 页面内容和标记 

​	默认情况下，你可以像编写普通的 [Markdown 或 HTML 文件](https://gohugo.io/content-management/formats/)一样，在 Docsy 站点上创建页面并添加[页面前置元数据](https://www.docsy.dev/docs/adding-content/content/#page-frontmatter)，就像上面描述的那样。从 0.100 版本开始，[Goldmark](https://github.com/yuin/goldmark/)是 Hugo 唯一支持的 Markdown 解析器。

> #### 提示 
>
> 如果你之前使用的是在 0.60 版本之前的 Hugo 版本，使用 [BlackFriday](https://github.com/russross/blackfriday) 作为 Markdown 解析器，你可能需要对你的站点进行一些小的更改才能与当前的 `Goldmark` Markdown 解析器一起工作。特别是，如果你克隆了我们的早期示例站点的一个版本，请在 `hugo.toml`/`hugo.yaml`/`hugo.json` 中添加以下内容，以允许 Goldmark 渲染原始 HTML 和 Markdown：
>
> === "yaml"
>
>     ```yaml
>     markup:
>       goldmark:
>         renderer:
>           unsafe: true
>     ```
>
> === "toml"
>
>     ```toml
>     [markup]
>       [markup.goldmark]
>         [markup.goldmark.renderer]
>           unsafe = true
>     ```
>
> === "json"
>
>     ```json
>     {
>       "markup": {
>         "goldmark": {
>           "renderer": {
>             "unsafe": true
>           }
>         }
>       }
>     }
>     ```



​	除了标记文本，你还可以使用 Hugo 和 Docsy 的 [shortcodes](https://www.docsy.dev/docs/adding-content/shortcodes)（简码）：可重用的 HTML 片段，可以快速构建你的页面。在 [Docsy Shortcodes](https://www.docsy.dev/docs/adding-content/shortcodes) 中了解更多关于简码的内容。

> 注意
>
> ​	Hugo 也支持使用其他标记语言的[外部解析器作为辅助工具](https://gohugo.io/content-management/formats/#additional-formats-through-external-helpers)来添加内容。例如，你可以使用 `rst2html` 作为外部解析器来添加 RST 内容（尽管请注意，这不支持所有 RST 的变体，例如 Sphinx RST）。同样地，你可以使用 `asciidoctor` 来解析 Asciidoc 文件，或者使用 `pandoc` 解析其他格式的文件。
>
> ​	由于你需要安装外部解析器并运行 Hugo 来生成你的站点（例如，你将无法使用 [Netlify 的持续部署功能](https://www.docsy.dev/docs/deployment/#deployment-with-netlify)），因此外部解析器可能并不适合与所有部署选项一起使用。此外，添加外部解析器可能会导致构建较大站点时出现性能问题。
>

### 处理链接 

​	Hugo 允许你使用普通的 Markdown 语法指定链接，但请记住，你需要将链接相对于你站点的根 URL 指定，而相对 URL 在你站点生成的 HTML 中不会被 Hugo 更改。

​	或者，你可以使用 Hugo 的 helper [ref 和 relref 简码](https://gohugo.io/content-management/cross-references/)来创建解析为正确 URL 的内部链接。但是，请注意，如果用户在你生成的站点之外查看你的页面，例如在 GitHub 的 Web UI 中使用渲染的 Markdown 功能，那么你的链接将根本不会出现为链接。

​	你可以在 [Hugo Tips](https://www.docsy.dev/docs/best-practices/site-guidance) 中找到（或添加！）有关处理 Hugo 链接的技巧和提示。

### 内容样式 

​	我们不强制要求您的页面内容采用任何特定的风格。然而，如果您需要一些关于如何编写和格式化清晰、简洁的技术文档的指导，我们推荐使用[Google开发者文档风格指南](https://developers.google.com/style/)，特别是其中的[风格指南要点](https://developers.google.com/style/highlights)。

## 页面 bundles

​	您可以将站点页面创建为其所在章节或子章节目录中的独立文件，或者作为包含内容的文件夹，其中内容在文件夹的index页中。为您的页面创建一个文件夹可以让您将图像和其他资源与内容[捆绑（bundle）](https://gohugo.io/content-management/page-bundles/)在一起。

​	您可以在本站点和我们的示例站点中看到这两种方法的示例。例如，本页面的源代码只是一个独立的文件`/content/en/docs/adding-content.md`。然而，在本站点中，Docsy简码的源代码位于`/content/en/docs/adding-content/shortcodes/index.md`，该页面使用的图像资源位于同一个`/shortcodes/`目录中。在Hugo术语中，这被称为叶子bundle，因为它是一个文件夹，包含了单个站点页面的所有数据，没有任何子页面（并且使用了不带下划线的`index.md`）。

​	您可以在[页面Bundles](https://gohugo.io/content-management/page-bundles/)中找到更多有关使用Hugo捆绑管理资源的信息。

## Adding docs and blog posts

​	您最常使用的模板可能是[`docs`模板](https://github.com/google/docsy/blob/main/layouts/docs/baseof.html)（如本页面所使用的）或非常相似的[`blog` 模板](https://github.com/google/docsy/blob/main/layouts/blog/baseof.html)。这两个模板都包括：

- a left nav
- GitHub链接（从您的站点配置中获取）供读者编辑页面或创建问题 
- a page menu

以及所有站点页面都使用的常见页头和页脚。应用哪个模板取决于您是否将内容添加到`blog`或`docs`内容目录中。您可以在[导航和搜索](https://www.docsy.dev/docs/adding-content/navigation/)中了解有关如何创建导航和页面菜单的更多信息。

### 组织您的文档 

​	虽然Docsy的顶级章节允许您为不同类型的内容创建站点章节，但您可能还希望在`docs`章节内组织您的文档内容。例如，本站点的`docs`章节目录有多个子目录，用于入门、内容和自定义等。每个子目录都有一个`_index.md`（也可以是`_index.html`），它作为一个章节索引页，告诉Hugo相关目录是您的文档的子章节。

​	Docsy的`docs`布局为您提供了一个左侧导航窗格，其中包含根据您的文档文件结构自动生成的嵌套菜单。在`docs/`目录中的每个独立页面或子章节`_index.md`或`_index.html`页面都会获得一个顶级菜单项，使用页面或index中的链接名称和`weight`元数据。

​	要向子章节添加文档，只需将页面文件添加到相应的子目录中。除子章节索引页面外，您添加到子章节的任何页面都将出现在子菜单中（请查看左侧以查看实际效果！），并按页面`weight`排序。在[导航和搜索](https://www.docsy.dev/docs/adding-content/navigation/)中了解有关添加Docsy导航元数据的更多信息。

​	如果您已经复制了示例站点，则在您的`docs`目录中已经有一些建议的子目录，并提供了放置何种类型内容以及一些示例Markdown页面的指导。您可以在[组织您的内容](https://www.docsy.dev/docs/best-practices/organizing-content/)中了解更多关于使用Docsy组织内容的信息。

#### 文档章节着陆页面 

​	默认情况下，文档章节着陆页（位于章节目录中的`_index.md`或`_index.html`）使用一种布局，该布局添加了一个格式化的链接列表，其中包含章节中的页面及其前置元数据描述。本站点中的[内容和自定义](https://www.docsy.dev/docs/adding-content/)着陆页面是一个很好的例子。

​	要显示一个简单的链接条目列表，指定在着陆页面的前置元数据中`simple_list: true`：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "Simple List Page"
    simple_list: true
    weight: 20
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "Simple List Page"
    simple_list = true
    weight = 20
    +++
    ```

=== "json"

    ```json
    {
      "title": "Simple List Page",
      "simple_list": true,
      "weight": 20
    }
    ```



​	要根本不显示任何链接，请在着陆页面的前置元数据中指定`no_list: true`：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "No List Page"
    no_list: true
    weight: 20
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "No List Page"
    no_list = true
    weight = 20
    +++
    ```

=== "json"

    ```json
    {
      "title": "No List Page",
      "no_list": true,
      "weight": 20
    }
    ```



### 组织您的博客文章 

​	Docsy的`blog`布局也为您提供了一个左侧导航菜单（如`docs`布局），以及应用于`/blog/_index.md`的列表类型index 页，自动按反向时间顺序显示所有最新文章的片段。

To create different blog categories to organize your posts, create subfolders in `blog/`. For instance, in our [example site](https://github.com/google/docsy-example/tree/master/content/en/blog) we have `news` and `releases`. Each category needs to have its own `_index.md` or `_index.html` landing page file specifying the category title for it to appear properly in the left nav and top-level blog landing page. Here’s the index page for `releases`:

​	要创建不同的博客类别以组织您的文章，请在`blog/`中创建子文件夹。例如，在我们的[示例站点](https://github.com/google/docsy-example/tree/master/content/en/blog)中，我们有`news`和`releases`。每个类别都需要有自己的`_index.md`或`_index.html`着陆页面文件，指定类别标题以使其在左侧导航和顶级博客着陆页面上正确显示。这是`releases`的index 页面：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "New Releases"
    linkTitle: "Releases"
    weight: 20
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "New Releases"
    linkTitle = "Releases"
    weight = 20
    +++
    ```

=== "json"

    ```json
    {
      "title": "New Releases",
      "linkTitle": "Releases",
      "weight": 20
    }
    ```



​	要向博客文章添加作者和日期信息，请将它们添加到页面的前置元数据中：

Front matter:

=== "yaml"

    ```yaml
    ---
    date: 2018-10-06
    title: "Easy documentation with Docsy"
    linkTitle: "Announcing Docsy"
    description: "The Docsy Hugo theme lets project maintainers and contributors focus on content, not on reinventing a website infrastructure from scratch"
    author: Riona MacNamara
    resources:
      - src: "**.{png,jpg}"
        title: "Image #:counter"
        params:
        byline: "Photo: Riona MacNamara / CC-BY-CA"
    ---
    ```

=== "toml"

    ```toml
    +++
    date = 2018-10-06T00:00:00.000Z
    title = "Easy documentation with Docsy"
    linkTitle = "Announcing Docsy"
    description = "The Docsy Hugo theme lets project maintainers and contributors focus on content, not on reinventing a website infrastructure from scratch"
    author = "Riona MacNamara"
    
    [[resources]]
    src = "**.{png,jpg}"
    title = "Image #:counter"
    
      [resources.params]
      byline = "Photo: Riona MacNamara / CC-BY-CA"
    +++
    ```

=== "json"

    ```json
    {
      "date": "2018-10-06T00:00:00.000Z",
      "title": "Easy documentation with Docsy",
      "linkTitle": "Announcing Docsy",
      "description": "The Docsy Hugo theme lets project maintainers and contributors focus on content, not on reinventing a website infrastructure from scratch",
      "author": "Riona MacNamara",
      "resources": [
        {
          "src": "**.{png,jpg}",
          "title": "Image #:counter",
          "params": {
            "byline": "Photo: Riona MacNamara / CC-BY-CA"
          }
        }
      ]
    }
    ```



​	如果您已经复制了示例站点，并且不想要blog 章节，或者想链接到外部博客，只需删除`blog`子目录即可。

## Working with top-level landing pages. 使用顶级着陆页面 

​	Docsy的[默认页面模板](https://github.com/google/docsy/blob/main/layouts/docs/baseof.html)没有左侧导航，适用于为您的站点或其他"着陆"类型页面创建主页。

### 自定义示例站点页面 

​	如果你已经复制了示例站点，那么在 `content/en/_index.html` 文件中你已经有了一个简单的站点着陆页。它由 Docsy 提供的 Hugo shortcode [页面块](https://www.docsy.dev/docs/adding-content/shortcodes/#shortcode-blocks)组成。

​	要自定义大的着陆图片（在一个[封面（cover）](https://www.docsy.dev/docs/adding-content/shortcodes/#blockscover)块中），请将项目中的 `content/en/featured-background.jpg` 文件替换为你自己的图片（文件名中必须包含`background`），你可以添加或删除尽可能多的块，以及添加你自己的内容。

​	示例站点还有一个About 页面，在 `content/en/about/_index.html` 中使用相同的 Docsy 模板。同样，它由[页面块](https://www.docsy.dev/docs/adding-content/shortcodes/#shortcode-blocks)组成，包括 `content/en/about/featured-background.jpg` 中的另一个背景图片。与站点着陆页一样，你可以替换图片、删除或添加块，或者添加你自己的内容。

### 构建你自己的着陆页 

​	如果你刚刚使用了这个主题，你仍然可以使用所有 Docsy 提供的[页面块](https://www.docsy.dev/docs/adding-content/shortcodes/#shortcode-blocks)（或任何其他你想要的内容）在相同的文件位置构建自己的着陆页。

## 添加community 页面 

​	`community`着陆页模板有样板内容，自动填充项目名称和在 `hugo.toml`/`hugo.yaml`/`hugo.json` 中指定的社区链接，为你的用户提供快速访问资源的链接，帮助他们参与你的项目。同样的链接也默认添加到你的站点页脚。

Configuration file:

=== "hugo.yaml"

    ```yaml
    params:
      links:
        user:
          - name: User mailing list
            url: 'https://example.org/mail'
            icon: fa fa-envelope
            desc: Discussion and help from your fellow users
          - name: Twitter
            url: 'https://example.org/twitter'
            icon: fab fa-twitter
            desc: Follow us on Twitter to get the latest news!
          - name: Stack Overflow
            url: 'https://example.org/stack'
            icon: fab fa-stack-overflow
            desc: Practical questions and curated answers
        developer:
          - name: GitHub
            url: 'https://github.com/google/docsy'
            icon: fab fa-github
            desc: Development takes place here!
          - name: Slack
            url: 'https://example.org/slack'
            icon: fab fa-slack
            desc: Chat with other project developers
          - name: Developer mailing list
            url: 'https://example.org/mail'
            icon: fa fa-envelope
            desc: Discuss development issues around the project
    ```

=== "hugo.toml"

    ```toml
    [params.links]
    # End user relevant links. These will show up on left side of footer and in the community page if you have one.
    [[params.links.user]]
    	name = "User mailing list"
    	url = "https://example.org/mail"
    	icon = "fa fa-envelope"
            desc = "Discussion and help from your fellow users"
    [[params.links.user]]
    	name ="Twitter"
    	url = "https://example.org/twitter"
    	icon = "fab fa-twitter"
            desc = "Follow us on Twitter to get the latest news!"
    [[params.links.user]]
    	name = "Stack Overflow"
    	url = "https://example.org/stack"
    	icon = "fab fa-stack-overflow"
            desc = "Practical questions and curated answers"
    # Developer relevant links. These will show up on right side of footer and in the community page if you have one.
    [[params.links.developer]]
    	name = "GitHub"
    	url = "https://github.com/google/docsy"
    	icon = "fab fa-github"
            desc = "Development takes place here!"
    [[params.links.developer]]
    	name = "Slack"
    	url = "https://example.org/slack"
    	icon = "fab fa-slack"
            desc = "Chat with other project developers"
    [[params.links.developer]]
    	name = "Developer mailing list"
    	url = "https://example.org/mail"
    	icon = "fa fa-envelope"
            desc = "Discuss development issues around the project"
    ```

=== "hugo.json"

    ```json
    {
      "params": {
        "links": {
          "user": [
            {
              "name": "User mailing list",
              "url": "https://example.org/mail",
              "icon": "fa fa-envelope",
              "desc": "Discussion and help from your fellow users"
            },
            {
              "name": "Twitter",
              "url": "https://example.org/twitter",
              "icon": "fa-brands fa-twitter",
              "desc": "Follow us on Twitter to get the latest news!"
            },
            {
              "name": "Stack Overflow",
              "url": "https://example.org/stack",
              "icon": "fa-brands fa-stack-overflow",
              "desc": "Practical questions and curated answers"
            }
          ],
          "developer": [
            {
              "name": "GitHub",
              "url": "https://github.com/google/docsy",
              "icon": "fa-brands fa-github",
              "desc": "Development takes place here!"
            },
            {
              "name": "Slack",
              "url": "https://example.org/slack",
              "icon": "fa-brands fa-slack",
              "desc": "Chat with other project developers"
            },
            {
              "name": "Developer mailing list",
              "url": "https://example.org/mail",
              "icon": "fa fa-envelope",
              "desc": "Discuss development issues around the project"
            }
          ]
        }
      }
    }
    ```



​	如果你正在创建自己的站点，想要使用这个模板添加页面，请在你的内容根目录中添加一个 `/community/_index.md` 文件。如果你复制了示例站点，并不想要一个社区页面，请在项目存储库中删除 `/content/en/community/` 目录。

## 添加静态内容 

​	你可能想要将一些非 Hugo 构建的内容与你的站点一起提供：例如，如果你使用 Doxygen、Javadoc 或其他文档生成工具生成参考文档。

​	要添加静态内容以"原样（as-is）"提供，请在站点的 `static` 目录中添加文件夹和/或文件。在部署站点时，该目录中的内容将在站点根路径下提供服务。因此，例如，如果你在 `/static/reference/cpp/` 添加了内容，用户可以在 `http://{server-url}/reference/cpp/` 访问该内容，你可以从其他页面在 `/reference/cpp/{file name}` 上链接到该目录中的页面。

​	你还可以在该目录中使用你的项目使用的其他文件，包括图像文件。你可以在[静态文件](https://gohugo.io/content-management/static-files/)中了解更多关于提供静态文件的信息，包括配置多个静态内容目录。

## RSS 订阅 

​	Hugo 默认会为主页和任何章节创建一个 RSS 订阅。对于主 RSS 订阅，你可以通过设置 `hugo.toml`/`hugo.yaml`/`hugo.json` 中的站点参数来控制包含哪些章节。这是默认配置：

Configuration file:

=== "hugo.yaml"

    ```yaml
    rss_sections:
      - blog
    ```

=== "hugo.toml"

    ```toml
    rss_sections = ["blog"]
    ```

=== "hugo.json"

    ```json
    {
      "rss_sections": [
        "blog"
      ]
    }
    ```



​	要禁用所有RSS订阅，请在`hugo.toml`/`hugo.yaml`/`hugo.json`中添加以下内容：

Configuration file:

=== "hugo.yaml"

    ```yaml
    disableKinds:
      - RSS
    ```

=== "hugo.toml"

    ```toml
    disableKinds = ["RSS"]
    ```

=== "hugo.json"

    ```json
    {
      "disableKinds": [
        "RSS"
      ]
    }
    ```



> 注意 
>
> ​	如果您已启用我们的[打印功能](https://www.docsy.dev/docs/adding-content/print/)或以其他方式在`hugo.toml`/`hugo.yaml`/`hugo.json`中指定了章节级别的输出格式，请确保"RSS"被列为输出格式，否则您将无法获得章节级别的RSS订阅（并且您的博客章节将不会有漂亮的橙色RSS按钮）。您的`hugo.toml`/`hugo.yaml`/`hugo.json` 规范将覆盖Hugo用于章节的默认[输出格式](https://gohugo.io/templates/output-formats/)，这些格式为HTML和RSS。
>
> Configuration file:
>
> === "hugo.yaml"
>
>     ```yaml
>     outputs:
>       section:
>         - HTML
>         - RSS
>         - print
>     ```
>
> === "hugo.toml"
>
>     ```toml
>     [outputs]
>     section = [ "HTML", "RSS", "print" ]
>     ```
>
> === "hugo.json"
>
>     ```json
>     {
>       "outputs": {
>         "section": [
>           "HTML",
>           "RSS",
>           "print"
>         ]
>       }
>     }
>     ```
>
> 

## Sitemap

​	Hugo默认为您的生成站点创建`sitemap.xml`文件：例如，这是[本站的sitemap](https://www.docsy.dev/sitemap.xml)。

​	您可以在`hugo.toml`/`hugo.yaml`/`hugo.json`中配置您的sitemap更新频率、sitemap文件名和默认页面优先级：

Configuration file:

=== "hugo.yaml"

    ```yaml
    sitemap:
      changefreq: monthly
      filename: sitemap.xml
      priority: 0.5
    ```

=== "hugo.toml"

    ```toml
    [sitemap]
      changefreq = "monthly"
      filename = "sitemap.xml"
      priority = 0.5
    ```

=== "hugo.json"

    ```json
    {
      "sitemap": {
        "changefreq": "monthly",
        "filename": "sitemap.xml",
        "priority": 0.5
      }
    }
    ```



​	要为给定页面覆盖这些值，请在页面的前置元数据中指定：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "Adding Content"
    linkTitle: "Adding Content"
    weight: 1
    description: >
        Add different types of content to your Docsy site.
    sitemap:
      priority: 1.0
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "Adding Content"
    linkTitle = "Adding Content"
    weight = 1
    description = '''
    Add different types of content to your Docsy site.
    '''
    [sitemap]
    priority = 1
    +++
    ```

=== "json"

    ```json
    {
      "title": "Adding Content",
      "linkTitle": "Adding Content",
      "weight": 1,
      "description": "Add different types of content to your Docsy site.\n",
      "sitemap": {
        "priority": 1
      }
    }
    ```



​	要了解有关配置站点地图的更多信息，请参阅[Sitemap模板](https://gohugo.io/templates/sitemap-template/)。
