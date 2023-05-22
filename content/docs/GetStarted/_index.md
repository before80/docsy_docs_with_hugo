+++
title = "入门指南"
weight = 1
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Get started - 入门指南  

[https://www.docsy.dev/docs/get-started/](https://www.docsy.dev/docs/get-started/)

​	学习如何开始使用Docsy，包括安装和使用Docsy主题的可用选项。 

​	正如我们在介绍中看到的，Docsy是一个[Hugo](https://gohugo.io/)主题，这意味着如果您想使用Docsy，您需要设置您的站点源，以便Hugo静态站点生成器可以在构建站点时找到并使用Docsy主题文件。最简单的方法是复制和编辑我们的示例站点，尽管我们也提供了将Docsy主题手动添加到新站点或现有站点的说明。

​	如果您想在本地构建和测试您的站点，您还需要能够运行Hugo本身，要么通过安装它和任何其他所需依赖项，要么使用我们提供的Docker容器。

本页面描述了Docsy的安装选项，并帮助您选择适当的设置指南以开始使用。

## 安装选项 

​	Hugo提供了多种使用主题的选项，Docsy支持所有这些选项。

- 将主题添加为Hugo模块：[Hugo模块](https://gohugo.io/hugo-modules/)是使用Hugo主题的最简单和最新的方式。Hugo使用模块机制从主Docsy仓库拉取主题文件，您可以选择版本，并且在您的站点中保持主题更新非常容易。我们的[示例站点](https://github.com/google/docsy-example)使用Docsy作为Hugo模块。 
- 将主题添加为Git子模块：将主题作为[Git子模块](https://git-scm.com/book/en/v2/Git-Tools-Submodules)添加也可以让Hugo使用主题文件，尽管比Hugo模块方法更难维护。这是Docsy示例站点旧版本中使用的方法，现在仍然受支持。 
- 克隆主题文件：如果您不想让Hugo从外部仓库获取主题文件（例如，如果您想直接自定义和维护主题的副本，或者您的部署选择需要您在仓库中包含主题的副本），您可以直接将文件克隆到您的站点源中。 

## 迁移和向后兼容性 

​	如果您有一个使用Docsy作为Git子模块的现有站点，并希望将其更新为使用Hugo模块，请遵循我们的[迁移指南](https://www.docsy.dev/docs/updating/convert-site-to-module/)。如果您还没有准备好迁移，不要担心！您的站点将继续像往常一样工作。

## 设置指南 

​	按照您选择的方法的设置指南。如果您是Docsy的新手，并不确定要按照哪个指南，我们建议按照"将Docsy作为Hugo模块使用"指南，这是一种简单且易于维护的选择。

------

##### [将Docsy作为Hugo模块使用  ](https://www.docsy.dev/docs/get-started/docsy-as-module/)

​	学习如何使用主题作为Hugo模块来开始使用Docsy。

##### [其他设置选项 ](https://www.docsy.dev/docs/get-started/other-options/)

​	使用Git或NPM创建一个新的Docsy站点。

##### [在Docker容器中部署Docsy ](https://www.docsy.dev/docs/get-started/quickstart-docker/)

​	有关如何使用 Docker 设置和运行本地 Docsy 站点的说明。

##### [基本站点配置 ](https://www.docsy.dev/docs/get-started/basic-configuration/)

​	新的 Docsy 站点的基本配置。

##### [已知问题 ](https://www.docsy.dev/docs/get-started/known_issues/)

​	安装 Docsy 主题时已知的问题。
