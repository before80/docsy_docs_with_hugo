+++
title = "基本站点配置"
weight = 4
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Basic site configuration - 基本站点配置 

https://www.docsy.dev/docs/get-started/basic-configuration/

​	新的 Docsy 站点的基本配置。



​	站点范围的配置细节和参数在项目的[配置文件](https://gohugo.io/getting-started/configuration/#configuration-file) (`config.toml` 或 `hugo.toml`) 中定义。这些包括你选择的 Hugo 主题（当然是 Docsy！）、项目名称、社区链接、Google Analytics 配置和 Markdown 解析器参数。在[`config.toml` 的示例项目](https://github.com/google/docsy-example/blob/master/config.toml)中查看带注释的示例，了解如何添加此信息。即使你只是使用主题而不是复制整个 Docsy 示例站点，**我们建议复制此 `config.toml` 并进行编辑**，因为它包括了许多参数的默认值，你需要设置这些参数才能正确构建站点。

​	你可能想要立即删除或自定义复制的 `config.toml` 文件中的某些默认值：

## 国际化 

​	复制的 `config.toml` 文件定义了英语、挪威语和波斯语内容。你可以在 [多语言支持](https://www.docsy.dev/docs/language/) 中了解 Docsy 如何支持多语言内容。

​	如果你不打算翻译你的站点，可以通过从 `config.toml` 中删除以下行来删除语言切换器：

```
[languages.no]
title = "Docsy"
description = "Docsy er operativsystem for skyen"
languageName ="Norsk"
contentDir = "content/no"
time_format_default = "02.01.2006"
time_format_blog = "02.01.2006"

[languages.fa]
title = "اسناد گلدی"
description = "یک نمونه برای پوسته داکسی"
languageName ="فارسی"
contentDir = "content/fa"
time_format_default = "2006.01.02"
time_format_blog = "2006.01.02"
```

## 搜索 

​	默认情况下，Docsy 示例站点使用自己的[谷歌自定义搜索引擎](https://cse.google.com/cse/all)。要禁用此站点搜索，请删除或注释以下行：

```
# Google Custom Search Engine ID. Remove or comment out to disable search.
gcs_engine_id = "011737558837375720776:fsdu1nryfng"
```

​	要使用您自己的自定义搜索引擎，请将 `gcs_engine_id` 中的值替换为您自己搜索引擎的 ID。或[选择其他搜索选项](https://www.docsy.dev/docs/adding-content/navigation/#site-search-options)。

## 下一步是什么？ 

- [添加内容并自定义您的站点 ](https://www.docsy.dev/docs/adding-content/)
- 从我们的[示例站点](https://github.com/google/docsy-example)和其他[示例](https://www.docsy.dev/docs/examples/)中获取一些想法。 
- [发布您的站点](https://www.docsy.dev/docs/deployment/).

  
