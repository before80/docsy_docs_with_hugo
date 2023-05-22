+++
title = "导航和搜索"
weight = 3
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Navigation and Search - 导航和搜索 

[https://www.docsy.dev/docs/adding-content/navigation/](https://www.docsy.dev/docs/adding-content/navigation/)

​	为您的 Docsy 站点自定义站点导航和搜索。 

## 顶层菜单 

​	顶层菜单（出现在整个站点的顶部导航栏中）使用您站点的[主菜单（`main` menu）](https://gohugo.io/content-management/menus/)。所有的 Hugo 站点都有一个主菜单（`main` menu）项数组，可以通过 `.Site.Menus` 站点变量进行访问，通过页面前置元数据或您站点的 `hugo.toml`/`hugo.yaml`/`hugo.json` 进行填充。

​	要将页面或章节添加到此菜单中，请将其添加到站点的主菜单（`main` menu）中，无论是在 `hugo.toml`/`hugo.yaml`/`hugo.json` 中还是在目标页面的前置元数据中（在 `_index.md` 或 `_index.html` 中作为章节着陆页面）。例如，这里是我们如何将 Documentation 章节着陆页添加到该站点的主菜单中的示例：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "Welcome to Docsy"
    linkTitle: "Documentation"
    menu:
      main:
        weight: 20
        pre: <i class='fa-solid fa-book'></i>
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "Welcome to Docsy"
    linkTitle = "Documentation"
    
    [menu.main]
    weight = 20
    pre = "<i class='fa-solid fa-book'></i>"
    +++
    ```

=== "json"

    ```json
    {
      "title": "Welcome to Docsy",
      "linkTitle": "Documentation",
      "menu": {
        "main": {
          "weight": 20,
          "pre": "<i class='fa-solid fa-book'></i>"
        }
      }
    }
    ```



​	该菜单按页面`weight`从左到右排序。例如，页面`weight: 30` 的章节索引或页面将出现在菜单中的 Documentation 章节之后，而`weight: 10`的页面将出现在它之前。

​	如果要将外部站点的链接添加到此菜单中，请在 `hugo.toml`/`hugo.yaml`/`hugo.json` 中添加，指定`weight`。

Configuration file:

=== "hugo.yaml"

    ```yaml
    menu:
      main:
        - name: GitHub
          weight: 50
          url: 'https://github.com/google/docsy/'
    ```

=== "hugo.toml"

    ```toml
    [[menu.main]]
        name = "GitHub"
        weight = 50
        url = "https://github.com/google/docsy/"
    ```

=== "hugo.json"

    ```json
    {
      "menu": {
        "main": [
          {
            "name": "GitHub",
            "weight": 50,
            "url": "https://github.com/google/docsy/"
          }
        ]
      }
    }
    ```



### 将图标添加到顶层菜单 

​	如 [Hugo 文档](https://gohugo.io/content-management/menus/#add-non-content-entries-to-a-menu)中所述，您可以使用站点的 `hugo.toml`/`hugo.yaml`/`hugo.json` 或页面前置元数据中定义的主菜单项的 `pre` 和/或 `post` 参数为顶层菜单项添加图标。例如，以下配置将 GitHub 图标添加到 GitHub 菜单项，并添加 `New!` 警报以指示这是菜单的新添加。

Configuration file:

=== "hugo.yaml"

    ```yaml
    menu:
      main:
        - name: GitHub
          weight: 50
          url: 'https://github.com/google/docsy/'
          pre: <i class="fa-brands fa-github"></i>
          post: <span class='alert'>New!</span>
    ```

=== "hugo.toml"

    ```toml
    [[menu.main]]
        name = "GitHub"
        weight = 50
        url = "https://github.com/google/docsy/"
        pre = "<i class="fa-brands fa-github"></i>"
        post = "<span class='alert'>New!</span>"
    ```

=== "hugo.json"

    ```json
    {
      "menu": {
        "main": [
          {
            "name": "GitHub",
            "weight": 50,
            "url": "https://github.com/google/docsy/",
            "pre": "<i class="fa-brands fa-github"></i>",
            "post": "<span class='alert'>New!</span>"
          }
        ]
      }
    }
    ```



​	您可以在[FontAwesome文档](https://fontawesome.com/icons?d=gallery&p=2)中找到完整的图标列表。Docsy主题默认包含免费的FontAwesome图标。

### 添加版本下拉菜单 

​	如果在`hugo.toml`中添加了一些`[params.versions]`，Docsy主题将在顶级菜单中添加一个版本选择器下拉菜单。

​	您可以在[版本控制指南](https://www.docsy.dev/docs/adding-content/versioning/)中了解更多信息。

### 添加语言下拉菜单 

​	如果在`hugo.toml`中配置了多种语言，Docsy主题将在顶级菜单中添加一个语言选择器下拉菜单。选择语言将带用户到当前页面的翻译版本，或给定语言的主页。

​	您可以在[多语言支持](https://www.docsy.dev/docs/language/)中了解更多信息。

## 章节菜单 

​	章节菜单位于`docs`章节的左侧，自动从`content`树中构建。与顶级菜单一样，按页面或章节索引`weight`（或按页面创建`date`，如果未设置`weight`）排序，页面或索引的`title`或`linkTitle`（如果不同）作为菜单中的链接标题。如果一个章节子文件夹除了`_index.md`或`_index.html`之外还有其他页面，那么这些页面将作为子菜单出现，再次按`weight`排序。例如，这是这个页面的元数据，显示它的`weight`和`title`：

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "Navigation and Search"
    linkTitle: "Navigation and Search"
    date: 2017-01-05
    weight: 3
    description: >
        Customize site navigation and search for your Docsy site.
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "Navigation and Search"
    linkTitle = "Navigation and Search"
    date = 2017-01-05T00:00:00.000Z
    weight = 3
    description = '''
    Customize site navigation and search for your Docsy site.
    '''
    +++
    ```

=== "json"

    ```json
    {
      "title": "Navigation and Search",
      "linkTitle": "Navigation and Search",
      "date": "2017-01-05T00:00:00.000Z",
      "weight": 3,
      "description": "Customize site navigation and search for your Docsy site.\n"
    }
    ```



​	要从左侧导航菜单中隐藏页面或章节，请在前置元数据中设置`toc_hide: true`。

​	要从[文档章节着落页](https://www.docsy.dev/docs/adding-content/content/#docs-section-landing-pages)的章节摘要中隐藏一个页面，请在该页面的前置元数据中设置`hide_summary: true`。如果您想从目录菜单和章节摘要列表中隐藏一个页面，您需要在该页面的前置元数据中将`toc_hide`和`hide_summary`都设置为`true`。

Front matter:

=== "yaml"

    ```yaml
    ---
    title: "My Hidden Page"
    weight: 99
    toc_hide: true
    hide_summary: true
    description: >
        Page hidden from both the TOC menu and the section summary list.
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "My Hidden Page"
    weight = 99
    toc_hide = true
    hide_summary = true
    description = '''
    Page hidden from both the TOC menu and the section summary list.
    '''
    +++
    ```

=== "json"

    ```json
    {
      "title": "My Hidden Page",
      "weight": 99,
      "toc_hide": true,
      "hide_summary": true,
      "description": "Page hidden from both the TOC menu and the section summary list.\n"
    }
    ```



### 章节菜单选项 

​	默认情况下，章节菜单完全展开显示当前章节。对于大型站点，这可能会使左侧导航过长，难以扫描。尝试在`hugo.toml`中设置站点参数`ui.sidebar_menu_compact = true`。

​	使用紧凑菜单（`.ui.sidebar_menu_compact = true`），只显示当前页面的祖先、同级和直接后代。您可以使用可选参数`.ui.ul_show`来设置所需的菜单深度始终可见。例如，使用`.ui.ul_show = 1`将始终显示第一级菜单。

​	除了完全展开和紧凑的菜单选项，您还可以通过在`hugo.toml`中设置站点参数`ui.sidebar_menu_foldable = true`来创建折叠菜单。折叠菜单让用户通过在菜单中的父节点旁边切换箭头图标来展开和折叠该菜单章节。

​	在大型站点上（默认情况下：>2000页），该章节菜单不会为每个页面生成，而是为整个章节进行缓存。然后使用JS设置标记活动菜单项（和菜单路径）的HTML类。您可以使用可选参数`.ui.sidebar_cache_limit`调整激活缓存的章节菜单的限制。

​	下面的选项卡窗格列出了您可以在项目[配置文件](https://gohugo.io/getting-started/configuration/#configuration-file)中定义的菜单章节选项。

Configuration file:

=== "hugo.yaml"

    ```yaml
    params:
      ui:
        sidebar_menu_compact: true
        ul_show: 1
        sidebar_menu_foldable: true
        sidebar_cache_limit: 1000
    ```

=== "hugo.toml"

    ```toml
    [params.ui]
    sidebar_menu_compact = true
    ul_show = 1
    sidebar_menu_foldable = true
    sidebar_cache_limit = 1000
    ```

=== "hugo.json"

    ```json
    {
      "params": {
        "ui": {
          "sidebar_menu_compact": true,
          "ul_show": 1,
          "sidebar_menu_foldable": true,
          "sidebar_cache_limit": 1000,
        }
      }
    }
    ```



### 向章节菜单添加图标 

​	您可以通过在页面前置元数据中设置`icon`参数（例如`icon: fa-solid fa-screwdriver-wrench`）向侧边栏中的章节菜单添加图标。

​	您可以在[FontAwesome文档](https://fontawesome.com/icons?d=gallery&p=2)中找到要使用的所有图标的完整列表。Docsy默认包含免费的FontAwesome图标。

​	开箱即用，如果您想使用图标，您应该为同一菜单级别上的所有项定义图标，以确保适当的外观。如果该图标以不同的方式使用，则可能需要进行个别CSS调整。

### 向章节菜单添加手动链接 

​	默认情况下，章节菜单完全是从您的章节页面生成的。如果您想在此菜单中添加手动链接，例如链接到外部站点或你站点中的不同章节中的页面，则可以通过在doc层次结构中创建具有适当权重和一些特殊参数的占位符页面文件（frontmatter）来实现这一点，以指定链接详细信息。

​	要创建占位符页面，请按通常方式在要在该菜单中显示链接的目录中创建一个页面文件，并将`manualLink`参数添加到其元数据中。如果一个页面在其元数据中具有`manualLink`，则Docsy会为此页面在章节菜单和章节索引中（章节在着陆页面上的子页面列表中 —— 请参见[Docsy文档中的描述](https://www.docsy.dev/docs/adding-content/content/#docs-section-landing-pages)）生成链接，但该链接目标会被替换为`manualLink`的值。该链接文本是您的占位符页面的`title`（如果设置了`linkTitle`，则是`linkTitle`）。您还可以使用`manualLinkTitle`参数设置链接的`title`属性以及使用`manualLinkTarget`设置链接目标 —— 例如，如果您希望一个外部链接在新选项卡中打开，则可以将其链接目标设置为`_blank`。Docsy会自动将`rel=noopener`添加到打开新标签页的链接中，作为安全最佳实践。

​	您还可以使用`manualLink`将其他现有站点页面的附加交叉引用添加到站点中。对于内部链接，您可以选择使用`manualLinkRelref`参数而不是`manualLink`来使用内置的Hugo函数[relref](https://gohugo.io/functions/relref/)。如果`relref`无法在您的站点中找到唯一页面，则Hugo会抛出错误消息。

> #### 注意
>
> ​	尽管基于您的占位符文件生成的所有菜单和着陆页链接都根据参数 `manualLink` 或 `manualLinkRelref` 设置，但 Hugo 仍会为该文件生成一个常规的 HTML 站点页面，尽管没有生成的链接指向该页面。为避免用户意外着陆到生成的占位符页面时产生混淆，我们建议在该页面的正常内容和/或页面描述中指定外部链接的 URL。

## 面包屑导航 

​	默认情况下，面包屑导航链接出现在每个页面的顶部。要禁用面包屑导航，请在`hugo.toml`中设置站点参数`ui.breadcrumb_disable = true`。

​	分类结果页面上的每个项（例如，单击一个分类标签，例如：标签/类别）也会显示面包屑导航链接。可以通过在`hugo.toml`中设置站点参数`ui.taxonomy_breadcrumb_disable = true`来禁用这些面包屑。

​	下面的选项卡窗格列出了您可以在项目[配置文件](https://gohugo.io/getting-started/configuration/#configuration-file)中定义的面包屑导航选项。

Configuration file:

=== "hugo.yaml"

    ```yaml
    params:
      ui:
        breadcrumb_disable: true
        taxonomy_breadcrumb_disable: true
    ```

=== "hugo.toml"

    ```toml
    [params.ui]
    breadcrumb_disable = true
    taxonomy_breadcrumb_disable = true
    ```

=== "hugo.json"

    ```json
    {
      "params": {
        "ui": {
          "breadcrumb_disable": true,
          "taxonomy_breadcrumb_disable": true
        }
      }
    }
    ```



## 站点搜索选项 

​	Docsy提供多个选项，让您的读者搜索您的站点内容，因此您可以选择适合您需求的选项。您可以选择以下选项：

- [Google自定义搜索引擎](https://www.docsy.dev/docs/adding-content/navigation/#configure-search-with-a-google-custom-search-engine)（GCSE），默认选项，使用Google的公共站点索引生成搜索结果页面。 
- [Algolia DocSearch](https://www.docsy.dev/docs/adding-content/navigation/#configure-algolia-docsearch)使用Algolia的索引和搜索机制，并在读者使用搜索框时提供组织良好的下拉式搜索结果列表。 Algolia DocSearch对公共文档站点是免费的。 
- [使用Lunr进行本地搜索](https://www.docsy.dev/docs/adding-content/navigation/#configure-local-search-with-lunr)，它使用JavaScript对您的站点进行索引和搜索，而无需连接到外部服务。此选项不需要将您的站点公开。 

​	如果你在项目的[配置文件](https://gohugo.io/getting-started/configuration/#configuration-file)中启用了这些搜索选项，那么一个搜索框将显示在你的顶部导航栏右侧。默认情况下，在左侧导航窗格的章节菜单顶部也会显示一个搜索框，如果你愿意，或者如果你使用的搜索选项仅适用于顶部搜索框，你可以禁用它。

​	请注意，如果您在项目[配置文件](https://gohugo.io/getting-started/configuration/#configuration-file)中意外启用了多个搜索选项，您可能会得到意外的结果（例如，如果您添加了Algolia DocSearch的`.js`文件，如果启用了GCSE搜索但忘记禁用Algolia搜索，则会得到Algolia的结果）。

### 禁用侧边栏搜索框 

​	默认情况下，搜索框会显示在顶部导航栏和侧边栏左侧导航窗格的顶部。如果您不想要侧边栏搜索框，请在`hugo.toml`/`hugo.yaml`/`hugo.json`中设置`sidebar_search_disable`为`true`。

Configuration file:

=== "hugo.yaml"

    ```yaml
    sidebar_search_disable: true
    ```

=== "hugo.toml"

    ```toml
    sidebar_search_disable = true
    ```

=== "hugo.json"

    ```json
    {
      "sidebar_search_disable": true
    }
    ```



## 使用 Google 自定义搜索引擎配置搜索 

​	默认情况下，Docsy 使用 [Google 自定义搜索引擎](https://cse.google.com/cse/all) (GCSE) 搜索您的站点。要启用此功能，您首先需要确保已构建并部署了[您站点的生产版本](https://www.docsy.dev/docs/deployment#build-environments-and-indexing)，否则您的站点将无法被爬取和索引。

### 设置站点搜索 

1. 在[Custom Search page](https://cse.google.com/cse/all)上点击**New search engine**，按照说明为已部署的站点创建一个 Google 自定义搜索引擎。记下您的新搜索引擎的 ID。
2. 使用**Edit search engine**选项添加您想要的任何其他配置到您的搜索引擎中。特别是您可能需要执行以下操作：
   - 选择**Look and feel**。将默认的**Overlay**布局更改为**Results only**，因为这个选项意味着您的搜索结果被嵌入到搜索页面中，而不是出现在单独的框中。单击**Save**以保存更改。 
   - 编辑默认的结果链接行为，使来自您站点的搜索结果不会在新标签页中打开。要执行此操作，请选择**Search Features** - **Advanced** - **Websearch Settings**。在**Link Target**字段中键入"_parent"。单击**Save**以保存更改。 

> 提示
>
> ​	您的站点搜索结果应该会在几天内显示。如果需要更长的时间，你可以[通过 Google 搜索控制台提交站点地图](https://support.google.com/webmasters/answer/183668?hl=en)来手动请求索引。

### 添加搜索页面 

​	一旦您设置好搜索引擎，就可以将此功能添加到您的站点：

1. 确保在 `content/en/search.md` 中有一个 Markdown 文件 (如果需要，其他语言也需要一个) 来显示您的搜索结果。它只需要一个`title`和`layout: search`，如以下示例：

   Front matter:

=== "yaml"

	```yaml
	   ---
	   title: Search Results
	   layout: search
	   ---
	```

=== "toml"

	```toml
	   +++
	   title = "Search Results"
	   layout = "search"
	   +++
	```

=== "json"

	```json
	   {
	       "title": "Search Results",
	       "layout": "search"
	   }
	```

   


2. 将您的 Google 自定义搜索引擎 ID 添加到 `hugo.toml`/`hugo.yaml`/`hugo.json` 的站点参数中。如果需要，您可以针对每种语言添加不同的值。

   Configuration file:

=== "hugo.yaml"

	```yaml
	   gcs_engine_id: '011737558837375720776:fsdu1nryfng'
	   
	```

=== "hugo.toml"

	```toml
	   gcs_engine_id = "011737558837375720776:fsdu1nryfng"
	```

=== "hugo.json"

	```json
	   {
	     "gcs_engine_id": "011737558837375720776:fsdu1nryfng"
	   }
	```

   




### 禁用 GCSE 搜索 

​	如果您未为您的项目指定 Google 自定义搜索引擎 ID 并且未启用任何其他搜索选项，则搜索框将不会出现在您的站点中。如果您正在使用示例站点中的默认 `hugo.toml` 并想禁用搜索，请注释或删除相关行。

## 配置 Algolia DocSearch 

​	作为 GCSE 的替代方案，您可以使用此主题的 [Algolia DocSearch](https://docsearch.algolia.com/)。Algolia DocSearch 对于公共文档站点是免费的。Docsy 支持 Algolia DocSearch v3。

> 注意
>
> ​	Docsy 以前支持 Algolia DocSearch v2，现在已被弃用。如果您是现有的 Algolia DocSearch v2 用户并想使用最新版本的 Docsy，请按照 DocSearch 文档中的[迁移说明](https://docsearch.algolia.com/docs/migrating-from-v2)更新您的 DocSearch 代码片段。
>

### 注册 Algolia DocSearch 

​	在 [https://docsearch.algolia.com/apply/](https://docsearch.algolia.com/apply/ ) 上完成表单。

​	如果您被接受to the program，您将通过电子邮件收到从Algolia获取的用于添加到您的文档站点的代码。

### 添加Algolia DocSearch

1. Configuration file:

   在`hugo.toml`/`hugo.yaml`/`hugo.json`中启用Algolia DocSearch。

=== "hugo.yaml"

	```yaml
	algolia_docsearch: true
	   
	```

=== "hugo.toml"

	```toml
	algolia_docsearch = true
	   
	```

=== "hugo.json"

	```json
	{
	     "algolia_docsearch": true
	   }
	   
	```

   


2. 移除或注释掉`hugo.toml`/`hugo.yaml`/`hugo.json`中的任何GCSE ID，并确保将本地搜索设置为`false`，因为您只能启用一种类型的搜索。请参阅[禁用GCSE搜索](https://www.docsy.dev/docs/adding-content/navigation/#disabling-gcse-search)。

4. 在`hugo.toml`/`hugo.yaml`/`hugo.json`中禁用侧边栏搜索，因为目前它不支持Algolia DocSearch。请参阅[禁用侧边栏搜索框](https://www.docsy.dev/docs/adding-content/navigation/#disabling-the-sidebar-search-box)。

4. 按照[Add code to head or before body end](https://www.docsy.dev/docs/adding-content/lookandfeel/#add-code-to-head-or-before-body-end)中的说明，在站点的每个页面的head和body中添加用于使用Algolia的CSS和JS。

   - 在`head-end.html`中添加DocSearch CSS：

     ```html
     <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@docsearch/css@3" />
     ```

   - 在`body-end.html`中添加DocSearch脚本，用从 Algolia 获取的代码段替换 `docsearch` 的详细信息（下面的示例是Algolia自己的站点索引！）。您必须提供`#docsearch`作为`container`值，因为那是 Docsy 布局中提供的 `div` 的 ID：

     ```html
     <script src="https://cdn.jsdelivr.net/npm/@docsearch/js@3"></script>
     <script type="text/javascript">docsearch({
       container: '#docsearch',
       appId: 'R2IYF7ETH7',
       apiKey: '599cec31baffa4868cae4e79f180729b',
       indexName: 'docsearch',
       });</script>
     ```


​	您可以在Algolia DocSearch V3 [Getting started](https://docsearch.algolia.com/docs/DocSearch-v3)中了解有关如何配置DocSearch的更多信息。

​	当你完成这些步骤后，Algolia搜索就应该在你的站点上启用了。搜索结果会显示在一个弹窗中，因此你不需要添加任何搜索结果页面。

## 配置Lunr本地搜索

​	[Lunr](https://lunrjs.com/) 是一种基于 Javascript 的搜索选项，它可以让您对站点进行索引并进行搜索，无需外部服务器端搜索服务。这是一个特别适合较小或非公共站点的好选择。

​	要将Lunr搜索添加到您的Docsy站点中：

1. 在`hugo.toml`/`hugo.yaml`/`hugo.json`中启用本地搜索。

=== "hugo.yaml"

	```yaml
       offlineSearch: true
       
	```
   
=== "hugo.toml"
   
	```toml
       offlineSearch = true
       
	```
   
=== "hugo.json"
   
	```json
       {
         "offlineSearch": true
       }
       
	```
   
   
   
2. 在 `hugo.toml`/`hugo.yaml`/`hugo.json` 中删除或注释掉任何 GCSE ID，并确保 Algolia DocSearch 设置为 `false`，因为您只能启用一种类型的搜索。请参阅 [禁用 GCSE 搜索](https://www.docsy.dev/docs/adding-content/navigation/#disabling-gcse-search)。


​	完成这些步骤后，本地搜索已在您的站点上启用，搜索结果会在您使用搜索框时以下拉列表形式出现。

> 提示 
>
> ​	如果您正在使用Hugo的本地服务器功能进行[本地测试](https://www.docsy.dev/docs/deployment/#serving-your-site-locally)，则需要首先通过运行 `hugo` 来构建您的 `offline-search-index.xxx.json` 文件。如果您在构建 `offline-search-index.xxx.json` 文件时已经运行Hugo服务器，则可能需要停止服务器并重新启动才能看到您的搜索结果。

### 更改本地搜索结果摘要长度 

​	您可以通过在 `hugo.toml`/`hugo.yaml`/`hugo.json` 中设置 `offlineSearchSummaryLength` 来自定义摘要长度。

Configuration file:

=== "hugo.yaml"

    ```yaml
    offlineSearch: true
    offlineSearchSummaryLength: 200
    ```

=== "hugo.toml"

    ```toml
    #Enable offline search with Lunr.js
    offlineSearch = true
    offlineSearchSummaryLength = 200
    ```

=== "hugo.json"

    ```json
    {
      "offlineSearch": true,
      "offlineSearchSummaryLength": 200
    }
    ```



### 更改本地搜索的最大结果数 

​	您可以通过在 `hugo.toml`/`hugo.yaml`/`hugo.json` 中设置 `offlineSearchMaxResults` 来自定义最大结果数。

Configuration file:

=== "hugo.yaml"

    ```yaml
    offlineSearch: true
    offlineSearchMaxResults: 25
    ```

=== "hugo.toml"

    ```toml
    offlineSearch = true
    offlineSearchMaxResults = 25
    ```

=== "hugo.json"

    ```json
    {
      "offlineSearch": true,
      "offlineSearchMaxResults": 25
    }
    ```



### 更改本地搜索结果弹出窗口的宽度 

​	搜索结果弹出窗口的宽度将根据内容自动扩展。

​	如果您想限制宽度，请将以下 scss 添加到 `assets/scss/_variables_project.scss`。

```scss
.td-offline-search-results {
  max-width: 460px;
}
```

### 排除页面不出现在本地搜索结果中 

​	要将一些页面排除在本地搜索结果之外，请在这些页面的每个页面的前置元数据中添加 `exclude_search: true`：

front matter:

=== "yaml"

    ```yaml
    ---
    title: "Index"
    weight: 10
    exclude_search: true
    ---
    ```

=== "toml"

    ```toml
    +++
    title = "Index"
    weight = 10
    exclude_search = true
    +++
    ```

=== "json"

    ```json
    {
      "title": "Index",
      "weight": 10,
      "exclude_search": true
    }
    ```

