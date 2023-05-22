+++
title = "Hugo 内容提示"
weight = 1
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Hugo Content Tips - Hugo 内容提示 

[https://www.docsy.dev/docs/best-practices/site-guidance/](https://www.docsy.dev/docs/best-practices/site-guidance/)

​	适用于 Docsy 主题 Hugo 站点的内容编写技巧。 

​	Docsy 是 [Hugo](https://gohugo.io/)静态站点生成器的一个主题。如果您还不熟悉 Hugo，本页面提供了一些有用的提示和潜在的注意事项，用于添加和编辑您站点的内容。欢迎添加您自己的建议！

## Linking 链接 

​	默认情况下，Hugo不会更改链接中的常规相对URL（它们在您站点的生成HTML中仍然是相对链接），因此一些硬编码的相对链接（例如 `\[relative cross-link\]\(../../peer-folder/sub-file.md\)`）与它们在本地文件系统上的工作方式可能会有所不同。您可能会发现，使用Hugo内置的一些[链接简码](https://gohugo.io/content-management/cross-references/#use-ref-and-relref)有助于避免在生成的站点中出现损坏的链接。例如，在Hugo中，`\{\{\< ref "filename.md" \>\}\}`链接实际上会找到并自动链接到名为`filename.md`的文件。

​	但是请注意，`ref`和`relref`链接无法与`_index`或`index`文件配合使用（例如，本站的[内容着陆页](https://www.docsy.dev/docs/adding-content/)），您需要使用常规的Markdown链接到章节着陆页或其他索引页面。将这些链接相对于站点的根URL指定，例如：`/docs/adding-content/`。

​	[了解更多链接信息](https://www.docsy.dev/docs/adding-content/content/#working-with-links)。
