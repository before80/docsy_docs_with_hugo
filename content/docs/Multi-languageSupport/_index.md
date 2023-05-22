+++
title = "多语言支持"
weight = 3
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Multi-language Support - 多语言支持 

[https://www.docsy.dev/docs/language/](https://www.docsy.dev/docs/language/)

​	在您的站点中支持多种语言。 

​	如果您想提供多种语言的站点内容，Docsy主题和Hugo可以轻松添加已翻译的内容，并使用户可以在语言版本之间导航。

## 内容和配置 

​	要添加多语言内容，您首先需要在站点配置中的`languages`部分中定义可用语言。每种语言都可以有自己的语言特定配置。例如，Docsy示例站点配置指定它提供英语和挪威语的内容，并且访问者默认看到的语言版本是英语：

Configuration file:

=== "hugo.yaml"

    ```yaml
    contentDir: content/en
    defaultContentLanguage: en
    defaultContentLanguageInSubdir: false
    …
    languages:
      en:
        title: Docsy
        description: Docsy does docs
        languageName: English
        weight: 1 # used for sorting
      'no':
        title: Docsy
        description: Docsy er operativsystem for skyen
        languageName: Norsk
        contentDir: content/no
        time_format_default: 02.01.2006
        time_format_blog: 02.01.2006
    ```

=== "hugo.toml"

    ```toml
    contentDir = "content/en"
    defaultContentLanguage = "en"
    defaultContentLanguageInSubdir = false
    ...
    [languages]
    [languages.en]
    title = "Docsy"
    description = "Docsy does docs"
    languageName ="English"
    # Weight used for sorting.
    weight = 1
    [languages.no]
    title = "Docsy"
    description = "Docsy er operativsystem for skyen"
    languageName ="Norsk"
    contentDir = "content/no"
    time_format_default = "02.01.2006"
    time_format_blog = "02.01.2006"
    ```

=== "hugo.json"

    ```json
    {
      "contentDir": "content/en",
      "defaultContentLanguage": "en",
      "defaultContentLanguageInSubdir": false,
      "languages": {
        "en": {
          "title": "Docsy",
          "description": "Docsy does docs",
          "languageName": "English",
          "weight": 1
        },
        "no": {
          "title": "Docsy",
          "description": "Docsy er operativsystem for skyen",
          "languageName": "Norsk",
          "contentDir": "content/no",
          "time_format_default": "02.01.2006",
          "time_format_blog": "02.01.2006"
        }
      }
    }
    ```



​	在`[languages]`块中未定义的任何设置都将回退到该设置的全局值。例如，上述站点所使用的内容目录将是`content/en`，除非用户选择了挪威语选项。

​	更新站点配置后，在源代码库中为每个语言版本创建一个内容根目录，例如英文文本的`content/en`，然后像平常一样添加[内容](https://www.docsy.dev/docs/adding-content/content/)。有关多语言支持的更多信息，请参阅[Hugo Docs](https://gohugo.io/content-management/multilingual)。

> 注意事项（仅在使用docsy作为hugo模块时） 
>
> ​	如果您使用的是多语言安装，请确保在模块导入的`[module]`部分之前声明配置文件中的`[languages]`部分。否则，您将会遇到麻烦！

> 提示 
>
> ​	如果您的站点可能会被翻译成其他语言，请考虑使用语言特定的子目录创建您的站点，因为这意味着如果您添加另一种语言，您不需要移动它。

​	如果要添加其他站点元素的多个语言版本，例如按钮文本，请参见下面的[国际化包](https://www.docsy.dev/docs/language/#internationalization-bundles)章节。

## 选择语言 

​	如果在[配置文件](https://gohugo.io/getting-started/configuration/#configuration-file)中配置了多个语言，则Docsy主题将在顶级菜单中添加一个语言选择器下拉菜单。选择语言会将用户带到当前页面的翻译版本，或给定语言的主页。

## 国际化  bundles

​	所有UI字符串（按钮文本、存储库链接等）都打包在主题的`/i18n`目录中，每种语言有一个`.toml`文件。

​	如果您选择的语言当前未包含在主题中，并且为所有通用UI字符串创建了自己的`.toml`文件（例如，如果您将UI文本翻译成Esperanto，并创建了一个名为`eo.toml`的`en.toml`副本），我们建议您在本主题中执行此操作而不是在自己的项目中。然后，您可以打开[pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)将您的翻译贡献给Docsy社区。

> #### Hugo提示 
>
> ​	在进行翻译工作时运行`hugo server --printI18nWarnings`，因为它会提示您缺少哪些字符串。

### 创建自定义UI字符串 

​	如果你选择的语言中 Docsy 主题的某些用户界面字符串不适合你的项目，或者你需要其他字符串来满足你的网站需求，你可以在你的项目的 `/i18n` 目录下创建一个专门的项目国际化文件。例如，如果你想覆盖 Docsy 的[英语字符串](https://github.com/google/docsy/blob/main/i18n/en.toml)中的任何内容，只需创建你自己的 `/i18n/en.toml` 文件并添加自定义字符串。你在此文件中指定的任何值都将覆盖本主题版本，而其余的字符串将来自本主题的对应国际化包。
