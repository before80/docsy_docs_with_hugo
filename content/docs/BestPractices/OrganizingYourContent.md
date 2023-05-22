+++
title = "组织你的内容"
weight = 2
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Organizing Your Content - 组织你的内容 

https://www.docsy.dev/docs/best-practices/organizing-content/

​	关于如何组织你的文档站点的指导和建议。 

​	如果你查看我们的[Example Site](https://example.docsy.dev/about/)，你会看到我们将文档章节分成了多个子章节，并为每个章节提供了一些关于在该章节中应该放置什么内容的建议。

## Do I need to use this structure? 我需要使用这个结构吗？ 

​	当然不是！示例站点中的站点结构是为满足大型产品的大型文档集中的特性、潜在任务和参考元素的需要而创建的。对于一个更简单的文档集（比如这个！），只需将你的文档围绕用户需要了解的特定功能进行结构化即可。即使对于更大的文档集，你可能会发现这个结构并不是很有用，或者你并不需要使用所有的章节类型。

​	我们建议你（就像我们在这里所做的那样）至少提供以下内容：

- 产品的**概述（Overview）**（在文档着陆页或单独的概述页面上）告诉用户为什么他们应该对你的项目感兴趣。
- **入门**（**Getting Started**）页面。 
- 一些**示例**（**Examples**）。 

​	你也可能想为项目的功能创建一些任务/操作指南。如果你更喜欢这种简单的结构，可以自由地复制 Docsy 用户指南站点或只是文档章节。

> 提示 
>
> ​	如果你想复制这个指南，请注意它的[源文件](https://github.com/google/docsy/tree/main/userguide)在 Docsy 主题仓库内，因此它没有自己的 `themes/` 目录：相反，我们运行 `hugo server --themesDir ../..` 从其父目录中使用 Docsy。你可以复制该站点并[添加一个包含 Docsy 的 `themes/` 目录](https://www.docsy.dev/docs/get-started/other-options/#option-2-clone-the-docsy-theme)，或者只是将 `docs/` 文件夹复制到你现有站点的内容根目录中。

​	[了解有关 Hugo 和 Docsy 如何使用文件夹和其他文件来组织你的站点的更多信息](https://www.docsy.dev/docs/adding-content/content/#organizing-your-documentation)。

## Why this structure? 为什么要这样组织结构？

​	我们的示例站点结构基于我们自己创建（和使用）不同类型项目的大型文档集的经验和我们对一些大型站点进行的用户研究。在用户研究中，我们发现用户最关心和最迫切寻找的是"入门（Get Started）"或"快速入门（Getting Started）"章节（以便他们可以开始工作），以及一些可以探索和复制的示例，因此我们将它们作为站点的重要顶级文档章节。用户还希望找到可以轻松查找以执行特定任务并组合成自己的应用程序或项目的"食谱（recipes）"，因此我们建议你将这种内容添加为任务。其他内容类型，如概念文档、参考文档和端到端教程，对于所有文档集来说都不是很重要，特别是对于较小的项目。我们在示例站点中强调这些章节是可选的。

​	我们希望通过进一步了解用户如何与技术文档交互，特别是对于开源项目，来进一步改进示例站点结构。

## 写作风格指南 

​	本指南和示例站点仅介绍如何将文档内容组织为页面和章节。有关如何组织和编写每个页面中的内容的一些指导，请参阅[Google开发者文档风格指南](https://developers.google.com/style/)，特别是[Style Guide Highlights](https://developers.google.com/style/highlights)。
