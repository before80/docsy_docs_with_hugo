+++
title = "预览和部署"
weight = 4
date = 2023-05-18T17:03:08+08:00
description = ""
isCJKLanguage = true
draft = false
+++

# Previews and Deployment - 预览和部署 

[https://www.docsy.dev/docs/deployment/](https://www.docsy.dev/docs/deployment/)

​	部署你的 Docsy 站点。 

​	有多种可能的选项可用于部署 Hugo 站点，包括 Netlify、Firebase Hosting、带有 Aerobatic 的 Bitbucket 等等；您可以在 [Hosting and Deployment](https://gohugo.io/hosting-and-deployment/)中了解所有这些选项。Hugo 也可以轻松地在本地部署站点，以快速预览内容。

## 本地服务您的站点 

Depending on your deployment choice you may want to serve your site locally during development to preview content changes. To serve your site locally:

​	根据您的部署选择，您可能希望在开发过程中本地服务您的站点以预览内容更改。要本地服务您的站点：

1. 确保您从存储库克隆了最新的本地站点文件副本。
3. 确保您在本地计算机上安装了[Prerequisites and installation](https://www.docsy.dev/docs/get-started/docsy-as-module/installation-prerequisites) 中描述的工具，包括 `postcss-cli`（您需要它来在第一次运行服务器时生成站点资源）。
5. 在站点根目录中运行 `hugo server` 命令。默认情况下，您的站点将在 [http://localhost:1313](http://localhost:1313/) 上可用。

​	现在您正在本地服务站点，Hugo 将监视内容更改并自动刷新您的站点。如果您有多个本地 git 分支，则在切换 git 分支时，本地站点将反映当前分支中的文件。

## 构建环境和索引 

​	默认情况下，使用`hugo`构建（而不是在本地使用`hugo server`）的Hugo站点具有Hugo构建环境`production`。使用`production`构建的Docsy站点可以被搜索引擎索引，包括[Google定制搜索引擎](https://www.docsy.dev/docs/adding-content/navigation/#configure-search-with-a-google-custom-search-engine)。生产构建还为现场部署优化了JavaScript和CSS（例如，使用压缩后的JS而不是更易读的原始源）。

​	如果您不希望搜索引擎索引您的部署站点（例如，如果您仍在开发您的实时站点），或者如果您想构建用于离线分析的开发版本的站点，可以将Hugo构建环境设置为其他环境名称，例如`development`（在本地使用`hugo server`的默认设置），`test`或您选择的另一个环境名称。

​	设置的最简单方法是在指定或运行`hugo`命令时使用`-e`标志，如以下示例所示：

```
hugo -e development
```

## 使用 Netlify 部署 

​	我们推荐使用[Netlify](https://www.netlify.com/)作为一种特别简单的方法，从您的Git提供程序（GitHub、GitLab或BitBucket）提供您的站点，具有[持续部署](https://www.netlify.com/docs/continuous-deployment/)，在您或您的用户针对文档存储库创建拉取请求时生成的站点预览等功能。对于开源项目，Netlify是免费的，如果您需要更多支持，则有高级版。

​	在使用 Netlify 部署之前，请确保按照 [使用主题](https://www.docsy.dev/docs/get-started/docsy-as-module) 中的任何设置说明，将您的站点源代码推送到您选择的 GitHub（或其他提供者）仓库。

​	然后按照 [在 Netlify 上托管](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/) 中的说明设置 Netlify 帐户（如果您还没有帐户），并授权访问您的 GitHub 或其他 Git 提供者帐户。登录后：

1. 点击**New site from Git**。

3. 点击您选择的Git提供者，然后从您的存储库列表中选择您的站点存储库。

3. 在**Deploy settings**页面中：

   1. 指定您的构建命令。确切的构建命令取决于您选择使用Docsy的方式： 

      - 如果您将Docsy用作[Git子模块](https://www.docsy.dev/docs/get-started/other-options/#option-1-docsy-as-a-git-submodule)，请指定`cd themes/docsy && git submodule update -f --init && cd ../.. && hugo`。您需要指定这个命令，而不是只用`hugo`，以便Netlify可以使用主题的子模块。 
      - 如果您将Docsy用作[Hugo module](https://www.docsy.dev/docs/get-started/docsy-as-module/)或NPM包，您可以只指定`hugo`。 
      
   2. 点击**Show advanced**。 

   4. 在**Advanced build settings**章节，点击**New variable**。 

   6. 将`HUGO_VERSION`指定为新变量的**Key**，并将其**Value**设置为Hugo的最新版本（最低推荐版本为`0.73`）。 

   8. 在**Advanced build settings**章节，再次点击**New variable**。 

   10. 将`GO_VERSION`指定为新变量的**Key**，并将其**Value**设置为Go的最新版本（最低推荐版本为`1.18`）。 


   如果您不希望搜索引擎对您的站点进行索引，则可以在构建命令中添加环境标志来指定非production环境，如 [构建环境和索引](https://www.docsy.dev/docs/deployment/#build-environments-and-indexing) 中所述。

7. 点击**Deploy site**。


> 注意 
>
> ​	Netlify 在构建站点之前使用站点仓库的 `package.json` 文件来安装任何 JavaScript 依赖项（如 `postcss`）。如果您没有仅仅复制我们示例站点的此文件版本，请确保您已指定了我们所有的[先决条件](https://www.docsy.dev/docs/get-started/docsy-as-module/installation-prerequisites/#install-postcss)。
>
> ​	例如，如果您想使用高于 8.0.0 版本的 `postcss-cli` 版本，则需要确保您的 `package.json` 文件还单独指定了 `postcss`：
>
> ```json
> "devDependencies": {
>  "autoprefixer": "^9.8.8",
>  "postcss-cli": "^8.0.0",
>  "postcss": "^8.0.0"
> }
> ```



​	或者，您可以按照相同的说明，但在您的仓库中的 [`netlify.toml` 文件](https://docs.netlify.com/configure-builds/file-based-configuration/) 中指定您的**部署设置**，而不是在 **部署设置** 页面中指定。您可以在 [Docsy 主题仓库](https://github.com/google/docsy/blob/main/netlify.toml) 中看到一个示例（尽管请注意，此处的构建命令有点不寻常，因为 Docsy 用户指南在本主题仓库*内部*）。

​	如果您已有一个现有的部署，您可以通过在Netlify的站点列表中选择该站点，然后点击**Site settings** - **Build and deploy**来查看和更新相关信息。请确保在**Build image selection**章节中选择了**Ubuntu Xenial 16.04** - 如果您正在创建新的部署，则默认使用此镜像。您需要使用此镜像来运行Hugo的扩展版本。

## 使用Amazon S3 + Amazon CloudFront进行部署

​	使用 [Amazon Web Services](https://aws.amazon.com/) 发布您的站点有几个选项，如这篇 [博客文章](https://adrianhall.github.io/cloud/2019/01/31/which-aws-service-for-hosting/) 所述。本节介绍最基本的选项，即使用 S3 存储桶部署您的站点，并激活 CloudFront CDN（内容分发网络）以加速部署内容的传递。

1. 在您在AWS上[注册](https://portal.aws.amazon.com/billing/signup#/start)之后，创建您的S3存储桶，将其与您的域名连接，并将其添加到CloudFront CDN中。这篇[博客文章](https://www.noorix.com.au/blog/how-to/hosting-static-website-with-aws-s3-cloudfront/)提供了所有细节，并为整个过程提供了易于遵循的逐步说明。

2. 下载并安装最新版本2的AWS[命令行界面](https://docs.aws.amazon.com/cli/latest/userguide/get-started-install.html)(CLI)。然后通过发出命令`aws configure`来配置您的CLI实例(确保您随时掌握您的AWS访问密钥ID和AWS秘密访问密钥)：

   ```
   $ aws configure
   AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
   AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
   Default region name [None]: eu-central-1
   Default output format [None]:
   ```

3. 通过发出命令`aws s3 ls`检查您的AWS CLI的正确配置，这应该输出您的S3存储桶列表。

4. 在您的`hugo.toml`/`hugo.yaml`/`hugo.json`中添加一个像这样的`[deployment]`部分：

   Configuration file:

=== "hugo.yaml"

	```yaml
       deployment:
         targets:
           - name: aws
             URL: 's3://www.your-domain.tld'
             cloudFrontDistributionID: E9RZ8T1EXAMPLEID
	```

=== "hugo.toml"

	```toml
       [deployment]
       [[deployment.targets]]
       name = "aws"
       URL = "s3://www.your-domain.tld"
       cloudFrontDistributionID = "E9RZ8T1EXAMPLEID"
	```

=== "hugo.json"

	```json
       {
         "deployment": {
           "targets": [
             {
               "name": "aws",
               "URL": "s3://www.your-domain.tld",
               "cloudFrontDistributionID": "E9RZ8T1EXAMPLEID"
             }
           ]
         }
       }
	```

   

5. 运行命令`hugo --gc --minify`将站点资产渲染到您的Hugo构建环境的`public/`目录中。

6. 使用Hugo内置的`deploy`命令将站点部署到S3：

   ```bash
   hugo deploy
   Deploying to target "aws" (www.your-domain.tld)
   Identified 77 file(s) to upload, totaling 5.3 MB, and 0 file(s) to delete.
   Success!
   Invalidating CloudFront CDN...
   Success!
   ```

   正如您所看到的，发出`hugo deploy`命令会自动[使CloudFront CDN缓存失效](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Invalidation.html)。

7. 这就是您需要做的全部！从现在开始，您可以使用Hugo内置的`deploy`命令轻松地将站点部署到S3存储桶！


​	有关Hugo `deploy`命令的更多信息，包括命令行选项，请参见此[synopsis](https://gohugo.io/commands/hugo_deploy)。特别是，您可能会发现`--maxDeletes int`选项或`--force`选项(强制上传所有文件)非常有用。

> 使用 GitHub actions 自动化部署 
>
> ​	如果您的站点源代码存储在GitHub存储库中，您可以使用[GitHub Actions](https://docs.github.com/en/actions)在将更改提交到GitHub存储库时将站点部署到您的S3存储桶。此工作流程的设置在此[博客文章](https://capgemini.github.io/development/Using-GitHub-Actions-and-Hugo-Deploy-to-Deploy-to-AWS/)中有描述。

> 处理别名 
>
> ​	如果您使用[别名](https://gohugo.io/content-management/urls/#aliases)进行URL管理，则应查看这篇[博客文章](https://blog.cavelab.dev/2021/10/hugo-aliases-to-s3-redirects/)。它解释了如何在使用Amazon S3时将别名转换为正确的`301`重定向。

​	如果S3不能满足您的需求，请考虑使用AWS [Amplify Console](https://aws.amazon.com/amplify/console/)。这是一个更先进的持续部署（CD）平台，内置支持Hugo静态网站生成器。在Hugo的官方文档中可以找到一个[入门指南](https://gohugo.io/hosting-and-deployment/hosting-on-aws-amplify/)。
