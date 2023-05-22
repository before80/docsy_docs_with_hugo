+++
title = "将Docsy作为Hugo模块使用"
weight = 1
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Use Docsy as a Hugo Module - 将Docsy作为Hugo模块使用

[https://www.docsy.dev/docs/get-started/docsy-as-module/](https://www.docsy.dev/docs/get-started/docsy-as-module/)

​	学习如何通过将本主题作为 Hugo 模块使用来开始使用 Docsy。

​	在构建站点时，[Hugo 模块](https://gohugo.io/hugo-modules/)是使用 Hugo 主题（如 Docsy）的最简单和最新的方法。Hugo 使用模块机制从您选择的版本中拉取主题文件，使得在站点中轻松地保持主题最新。我们的示例站点使用 Docsy 作为 Hugo 模块。

​	要了解其他设置方法，请参阅我们的[入门](https://www.docsy.dev/docs/get-started/)概述。如果您想将现有的 Docsy 站点迁移到使用 Hugo 模块，请查看我们的[迁移指南](https://www.docsy.dev/docs/updating/convert-site-to-module/)。

## 使用 Hugo 模块的设置选项 

​	要将 Docsy 作为 Hugo 模块使用，您有以下几个选项：

 

- 复制并编辑 [Docsy 示例站点](https://github.com/google/docsy-example)的源代码。这种方法为您的站点提供了一个骨架结构，包括顶级和文档章节以及可根据需要修改的模板。示例站点使用 Docsy 作为 Hugo 模块。
- 使用 Docsy 主题构建自己的站点。在创建或更新站点时像任何其他 Hugo 主题一样指定 [Docsy 主题](https://github.com/google/docsy)。使用此选项，您将获得 Docsy 的外观和感觉、导航和其他功能，但需要指定自己的站点结构。

​	如果您是初学者，我们建议您通过复制我们的示例站点来开始。如果您已经熟悉 Hugo 或想要非常不同的站点结构，您可以按照我们的指南从头开始创建站点，这样您就可以在较高的实现努力成本下获得最大的灵活性。在两种情况下，您需要遵循我们的先决条件指南，以确保您已安装了 Hugo 和所有必要的依赖项。

------

##### [开始之前 ](https://www.docsy.dev/docs/get-started/docsy-as-module/installation-prerequisites/)

​	使用 Docsy 作为 Hugo 模块构建站点的先决条件。

##### [创建新站点：从预设的站点开始 ](https://www.docsy.dev/docs/get-started/docsy-as-module/example-site-as-template/)

​	通过使用 Docsy 示例站点的克隆作为起点，创建一个新的 Hugo 站点。

##### [创建新站点：从头开始创建新站点 ](https://www.docsy.dev/docs/get-started/docsy-as-module/start-from-scratch/)

​	使用 Docsy 作为 Hugo 模块，从头开始创建一个新的 Hugo 站点。
