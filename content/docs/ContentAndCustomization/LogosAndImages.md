+++
title = "Logo和图片"
weight = 6
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Logos and Images - Logo和图片 

https://www.docsy.dev/docs/adding-content/iconsimages/

​	在您的项目中添加和自定义logo、icon和图片。 

## 添加您的logo 

​	默认情况下，Docsy在导航栏的开头即极左处显示一个站点logo。将您的项目的SVG logo放在`assets/icons/logo.svg`中。这将覆盖主题中默认的Docsy logo。

​	如果您不希望在导航栏中出现logo，则在您的项目配置中将`navbar_logo`设置为`false`：

Configuration file:

=== "hugo.yaml"

    ```yaml
    navbar_logo: false
    
    ```

=== "hugo.toml"

    ```toml
    navbar_logo = false
    
    ```

=== "hugo.json"

    ```json
    {
      "navbar_logo": false
    }
    
    ```



​	有关样式化您的logo的信息，请参见[样式化您的项目logo和名称](https://www.docsy.dev/docs/adding-content/lookandfeel/#styling-your-project-logo-and-name)。

## 使用 icons

​	Docsy 默认包含了免费的 FontAwesome 图标，其中包括 GitHub 和 Stack Overflow 等网站的logo。您可以在 [FontAwesome 文档](https://fontawesome.com/icons/) 中查看所有可用的图标，包括 FontAwesome 版本以及该图标是否可供免费使用。检查 Docsy 的 [`package.json`](https://github.com/google/docsy/blob/main/package.json) 和发行说明，了解 Docsy 当前包含的 FontAwesome 版本。

​	您可以在 [顶级菜单](https://www.docsy.dev/docs/adding-content/navigation/#adding-icons-to-the-top-level-menu)、[章节菜单](https://www.docsy.dev/docs/adding-content/navigation/#add-icons-to-the-section-menu) 或文本的任何位置添加 FontAwesome 图标。

## 添加您的favicon 

​	最简单的方法是通过 [http://cthedot.de/icongen](http://cthedot.de/icongen)（允许您从单个图像创建各种图标大小和选项）和/或 [https://favicon.io](https://favicon.io/) 来创建一组网站图标，然后将它们放在站点项目的 `static/favicons` 目录中。这将覆盖本主题的默认图标。

​	请注意，[https://favicon.io](https://favicon.io/) 并不像 Icongen 那样创建范围广泛的尺寸，但它可以让您快速从文本创建 favicon：如果您想创建文本 favicon，则可以使用该站点生成它们，然后使用 Icongen 从生成的 `.png` 文件中创建更多尺寸（如果需要）。

​	如果您有特殊的网站图标要求，可以创建自己的 `layouts/partials/favicons.html` 文件并添加相应的链接。

## 添加图像 

### 着陆页面

​	Docsy 的 [**blocks/cover** 简码](https://www.docsy.dev/docs/adding-content/shortcodes/#blockscover) 可以方便地向你的 着陆 pages 中添加大型封面图片。这个 简码 在 landing page 的 [Page Bundle](https://gohugo.io/content-management/page-bundles/) 中查找一个名字中带有"background"的图片——例如，如果你复制了本示例站点，则 `content/en/_index.html` 中的 landing page 图片是 `content/en/featured-background.jpg`。

​	你可以使用块的 `height` 参数指定 cover 块容器（及其图片）的首选显示高度。对于全视口高度，请使用 `full`：

```html
\{\{\< blocks/cover title="Welcome to the Docsy Example Project!" image_anchor="top" height="full" \>\}\}
...
\{\{\< /blocks/cover \>\}\}
```

​	对于较短的图片，例如本示例站点的 About 页面，请使用 `min`、`med`、`max` 或 `auto`（实际图片的高度）之一：

```html
\{\{\< blocks/cover title="About the Docsy Example" image_anchor="bottom" height="min" \>\}\}
...
\{\{\< /blocks/cover \>\}\}
```

### 其他页面 

​	要向其他页面添加内联图片，请使用 [imgproc 简码](https://www.docsy.dev/docs/adding-content/shortcodes/#imgproc)。或者，如果你喜欢，只需使用常规的 Markdown 或 HTML 图像，并将你的图像文件添加到你的项目的 `static` 目录中。你可以在[添加静态内容](https://www.docsy.dev/docs/adding-content/content/#adding-static-content)中了解更多关于使用此目录的信息。

## 在本站点中使用的图片 

​	本站点中用作背景图片的图像属于[公共领域](https://commons.wikimedia.org/wiki/User:Bep/gallery#Wed_Aug_01_16:16:51_CEST_2018)，可以自由使用。示例网站中的粥图像由[iha31](https://pixabay.com/users/iha31-560629/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=531209)提供，来自[Pixabay](https://pixabay.com/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=531209)。
