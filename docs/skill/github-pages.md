---
layout: default
title: GitHub Pages
parent: skill
---

# GitHub Pages & Jekyll
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 关于使用GitHub Pages制作网站的基础知识
* GitHub Pages 使用Jekyll来处理幕后所有文件。Jekyll 可以将您的博客文章文件转换为可以在浏览器中查看的格式良好的 HTML。
* 博客文章文件应始终使用以下格式命名：yyyy-mm-dd-your-blog-post-name.md
* 一篇写于 2022 年 4 月 24 日的帖子将被命名为2022-04-24-my-blog-post.md. 请注意不要使用未来的日期，因为该帖子不会显示。
* 文章内容是用Markdown语言写的，请参阅[Github Markdown](https://guides.github.com/features/mastering-markdown/){:target="_blank"} 以了解一些基础知识。还可以看[Markdown官方教程](https://markdown.com.cn/basic-syntax/){:target="_blank"} 来学习Markdown语法。

### 什么是Github Pages？
GitHub Pages 是一个静态网站寄主服务，换言之就是一个静态网页托管的服务。
在使用GitHub Pages时，有以下限制：
* GitHub Pages 源码仓库限制在1GB大小
* 发布GibHub Pages 网站最好不要超过1GB
* GitHub Pages网站有流量限制（每月100GB或者100,000次请求）
* GitHub Page 网站每个小时限制10次重建
* 不支持如.htaccess之类的密码验证功能，亦即不能针对gh-pages的页面设定密码保护。
* 所有的gh-pages内的页面都是公开的，表示所有的人都可存取到相关的页面。
必须bundle exec jekyll build从主分支运行，然后切换到gh-pages分支推送最新的_site，可能会很乏味。幸运的是，有一个解决方案可以让我们自动化这个过程。我们可以使用GitHub Actions，这是一项允许您根据存储库中发生的某些事件自动化工作流程的功能。例如，我们可以创建一个工作流，在我们的项目中使用相同版本的 Jekyll 和其他 gem 自动构建站点，并在每次推送到main分支时部署它。它还可以自动创建gh-pages分支。

UTF-8格式

Repository仓库

### 什么是Jekyll？
Jekyll 是用 Ruby 编写的，可以将您的纯文本转换为静态网站和博客。[Jekyll官网](https://jekyllrb.com/)
由于 Jekyll 是由GitHub的联合创始人Tom Preston-Werner构建的，因此 Jekyll 与GitHub Pages配合得非常好。

简单地说，Jekyll是一个用ruby写的解析引擎，用于从动态的组件中生成静态的网站。
Jekyll 是迄今为止最受欢迎的静态生成器，因为它由 GitHub 构建和支持，并用于流行的服务 GitHub Pages，免费用于托管个人或项目网站的静态页面。
Jekyll 拥有其他静态生成器中最大的社区，提供了大量优秀的教程、开源主题和插件。
它被视为 WordPress 在静态世界中的竞争者，许多博主已经将他们的博客从 WordPress 迁移到 Jekyll。
Jekyll 是一个静态站点生成器，内置 GitHub Pages 支持和简化的构建过程。 Jekyll 使用 Markdown 和 HTML 文件，并根据您选择的布局创建完整静态网站。 Jekyll 支持 Markdown 和 Lick，这是一种可在网站上加载动态内容的模板语言。
在 StackOverflow 中，Jekyll 的相关Q&a比 Hugo 和 Hexo 都多

### Jekyll / Hugo / Hexo等静态博客生成器对比 
[https://jamstack.org/generators](https://jamstack.org/generators)还有很多博客生成器、1如1ty

Jekyll 使用语言 Ruby GitHub 支持； 免费且开源； RubyGems 支持构建主题为 gems 方便分发； 简单便捷使用； 开箱即用的合适的默认极简主题。 Liquid 模版引擎； 基于 Gem 主题； Markdown 和 YAML 类型支持； Sass 预处理 CSS 支持； 官方插件支持 CoffeeScript。

Hugo 使用语言 Go 免费开源； 速度非常快，对构建速度做了优化； 内置支持很多功能： 动态 API 请求的内容； 无限制内容类型； shortcakes， 一个灵活的 Markdown 替代； 国际化； 别名重定向； 分页。 预制的 Go 模版和模式； 无需依赖（不用安装 Go，因为它是编译好的二进制）； 功能强大的内容模型。 主题使用 Go 模版，所以需要熟悉 Go； 没有内置默认主题； 缺少扩展性和插件（因为 Go 是编译型语言）。

Hexo 使用 Node.js 相当快速； EJS 模版引擎; 在 GitHub Pages 部署简单； 中文支持，中文社区（可能是劣势对于非中文用户）； 对于 HTML + CSS + Javascript 非常友好。 没有英文。对于非中文用户劣势




## 开始用Github Pages制作网站


### 【安装】Ruby开发环境和Jekyll
Jekyll是由Ruby脚本语言编写的，所以在运行jekyll之前，需要先安装Ruby运行环境。
* 下载[RubyInstaller for Windows (Ruby+Devkit) x64.exe](https://rubyinstaller.org/downloads/)的最新版
* 默认运行ridk install（选择3.自动下载安装msys2和mingw）必需的开发工具
* 打开cmd命令窗口，执行**gem install jekyll bundler**安装jekyll和bundler（等一会，国内访问可能比较慢）
* 查看是否正确安装了jekyll：jekyll -v
* 查看是否正确安装了bundler：bundler -v
* （查看ruby的版本：ruby -v）
* jekyll 更新到最新版本：gem update jekyll（gem install jekyll -v x.x.x ）
* 更新Bundler：gem update bundler
* 同时建网站和文件夹：jekyll new myblog  ，到文件目录下：cd myblog （建文件夹：mkdir  myblog，为当前文件夹建站：jekyll new . ）
* 安装主题：gem install just-the-docs
* 将主题添加到Jekyll站点。Gemfile文件：gem "just-the-docs"，_config.yml文件：theme: just-the-docs
* 更新主题：bundle update just-the-docs  （*Any new files or updates the theme developer has made (such as to stylesheets or includes) will be pulled into your project automatically.*）
* 全部更新：bundle update
* 启动本地网站服务：bundle exec jekyll serve。在浏览器输入<http://127.0.0.1:4000>或<http://localhost:4000>， **成功！**

如果出现bundle exec jekyll serve能启动，而jekyll serve不能启动，则删除Gemfile和Gemfile.lock重新运行jekyll serve即可。
如果端口被占用 bundle exec jekyll server --port 5000

本地hello world的html运行
jekyll serve

### 使用CSS属性自定义网站
我们只在我们极其简单的网页上使用了几个 CSS 属性，但有很多。这个来自 MDN 网络文档的 CSS 参考包含每个标准 CSS 属性的列表。如果我想知道如何做某事，我通常只是谷歌“css”和我想做的事情。例如，尝试在搜索引擎上搜索“css change font family”来了解如何更改您网站上的文本字体。
说到字体，一个很好的网站字体资源是Google Fonts。有许多免费字体可供您轻松参考并应用于您的网站。
正如我之前提到的，您可以使用Google 颜色选择器来选择网页颜色并找到它们的十六进制十进制代码。
通过引用其他人编写的代码库，我们可以轻松地应用他们的样式和布局。一个流行的框架是Bootstrap。本网站使用 Bootstrap 创建响应式布局或可根据窗口大小变化的布局。这很重要，因为您的网站需要在不同的屏幕尺寸和设备上看起来不错。最后，我建议您熟悉使用Chrome DevTools来测试您的网页并排除故障。您是否曾经在使用 Chrome 时右键单击并单击“检查”？这将打开 DevTools 窗口，您可以在其中编辑页面上的元素并实时查看更改，而无需实际编辑文件。

### 上传，Github Pages托管网站
#### 方法一、使用github desktop完成
有许多图形git软件，如GitHub Desktop，不必再辛苦地利用git指令来执行。
#### 方法二、[使用自定义GitHub Actions工作流进行发布](https://docs.github.com/cn/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#%E4%BD%BF%E7%94%A8%E8%87%AA%E5%AE%9A%E4%B9%89-github-actions-%E5%B7%A5%E4%BD%9C%E6%B5%81%E8%BF%9B%E8%A1%8C%E5%8F%91%E5%B8%83)

#### 方法三、使用代码完成Git

以仓库的远程地址（可以在github desktop看到）
~~~
「git clone https://github.com/[使用者名称]/pagedemo.github.io.git」
~~~
来取得GitHub档案库内的档案。成功执行后，在本地端会产生一个名称为「pagedemo」的工作目录。
接着，在此工作目录内执行「git branch gh-pages」指令，新建一个名称为「gh-pages」的分支。在建立分支成功后，以「git checkout gh-pages」指令切换到gh-pages分支上。在切换过后，即可在工作目录内简单地新增一个网页档（以index.html为档名）。

接着，执行「git add .」指令将此档案储存到暂存区，并利用「git commit -m "test page"」指令（其中-m参数为本次提交的说明文字）提交到本地端的档案库上。

最后，使用「git push origin gh-pages」指令将本地端档案库内的档案上传至GitHub网站上。在上传的过程中，会要求输入GitHub上所注册的帐号及密码内执行「git branch gh-pages」指令，新建一个名称为「gh-pages」的分支。

### 自己制作Jekyll Themes主题
如果您是 Jekyll 主题开发者（而不是主题消费者），您可以将您的主题打包到 RubyGems 中，并允许用户通过 Bundler 安装它。Jekyll 将帮助您使用new-theme命令构建一个新主题。jekyll new-theme（以主题名称作为参数运行）。
如果您的主题有一个/_layouts/page.html文件，并且页面在其front matter 中有layout: page，Jekyll 将首先查找站点的_layouts文件夹以查找page布局，如果不存在，将使用您的主题的page布局。
如果希望自己的主题可以让更多人看到或使用，可以上传到[jekyll主题网](http://jekyllthemes.org/)这个站点
1. 准备一张250x200的预览图
2. fork这个[JekyllThemes](https://github.com/mattvh/jekyllthemes/fork)项目源码到自己的Github仓库
3. 找到自己的Github仓库中fork的这个JekyllThemes项目
4. clone自己仓库的JekyllThemes项目到本地
5. 将预览图放到thumbnails目录，在_posts下复制一篇文章，替换为自己的主题信息
6. 执行bundle exec jekyll server本地预览效果
7. 本地调试直到网站已经添加了自己的主题
8. commit并且push添加的代码(此时代码只是提交到自己仓库的JekyllThemes项目)
9. 网页访问自己仓库的JekyllThemes项目，点击New pull request发起一个合并请求
10. 此时提交已经发送给JekyllThemes项目的管理员，等待管理员合并提交
注意：图片的规格最好一致，并且进行本地测试，否则即使提交了也很可能会被管理员拒绝合并代码


## **深入Jekyll主题**
改造自己的主题
* 加入html、css、js等需要的文件
* 提取相同的内容到_includes目录
* 需要复用的页面框架，比如post文章页，放到_layouts目录
* 一些配置字符串，放在_config.yml文件内
* 使用**Liquid语法**在页面中访问site，page等信息组织内容
* 调整html页面标签的css定制自己的Markdown样式
* 调整语法高亮的css定制自己的语法高亮颜色值
* 你可能需要一个MarkdownDemo来测试站点的样式

### Jekyll模板的结构
下面是用tree命令输出的目录结构（cmd，输入tree即可）

~~~
├── _sass      **#布局。改变颜色、字体**
│   ├── _base.scss                  # markdown对应的css
│   ├── _theme-layout.scss          # @import指令包含主题信息
│   └── _syntax-highlighting.scss   # 语法高亮对应的css
├── css
│   └── main.scss           # 其实就是css，比.css更现代
├── _includes   **#布局**
│   ├── footer.html         # 页脚html片段
│   ├── header.html         # 页头html片段
│   ├── head.html           # html片段 。添加网站logo 图标在_includes/head.html
│   ├── icon-github.html    # html片段
│   ├── icon-github.svg     # github图标
│   ├── icon-twitter.html   # html片段
│   └── icon-twitter.svg    # twitter图标
├── _data   **#布局    (Starting with version 4.3.0, Jekyll also takes into account the _data directory of themes. This allows data to be distributed across themes.)  **
│   └── navigation.yml    # 可能包含此文件 ，定义网站的导航菜单
├── _layouts   **#布局 页面框架**
│   ├── default.html        # default页面
│   ├── page.html           # page页面
│   └── post.html           # post页面
├── _posts
│   └── 2016-08-24-welcome-to-jekyll.markdown
└── _site             # Jekyll最终生成的静态网站
├── about
│   └── index.html
├── css
│   └── main.css  # 如果不喜欢上面的那堆scss，那么复制这个过去就够了
├── feed.xml
├── robots.txt
├──.gitignore  # 告诉Git 要忽略项目中的哪些文件或文件夹
├── index.html
└── jekyll
└── update
└── 2022
└── 08
└── 24
└── welcome-to-jekyll.html
├── index.md
├── about.md
├── _config.yml       # Jekyll核心配置文件，yml文件非常精确，如果您键入一个额外的空格，则会出现错误。使用 **[yaml 验证器](http://www.yamllint.com/)**验证器来检查您的 .yml 错误在哪里！
├── favicon.ico     # 32x32 px for browsers
├── Gemfile           # Github Pages本地化的文件
└── Gemfile.lock      # Github Pages本地化的文件
~~~

### 简化Jekyll模板
/assets 文件要保留：SCSS、图像、网络字体
.git 文件夹要保留
简化当前模板后得到结构：
~~~
├── index.html
├── _config.yml       # Jekyll核心配置文件
├── feed.xml
├── Gemfile           # Github Pages本地化的文件
├── Gemfile.lock      # Github Pages本地化的文件
├── css
│   └── markdown.css    # 提取上面_site/css/main.css中设置html部分
│   └── highlight.css   # 提取上面_site/css/main.css中语法高亮部分
├── _includes
├── _layouts
│   └── post.html       # 文章页框架
├── _posts
│   └── 2016-08-24-welcome-to-jekyll.markdown
~~~

要安装 Jekyll插件，需要在两个地方添加插件名称。一个在_config.yml文件的plugins部分，第二个在Gemfile文件

#### _includes目录详解
该目录下的片段是“被包含”的关系，可以是任何格式的文件，片段也可以include片段。 include的语法：{% raw %} {% include head.html %} {% endraw %}
_layouts和_includes与普通页面的关系图： ![jekyll-layout-include][jekyll-layout-include]
注意：default.html里访问index.html生成的内容是直接访问content，而不是page.content或post.content，这两者的关系大概是前者才是经过处理后的html片段，而后者是原始的文本，包含未解析的liquid语法。

### _config.yml文件详解
Jekyll站点的配置文件，可以存储数据，用于配置Jekyll的插件和运行环境

~~~
excerpt_separator: "\n\n" # you can specify your own separator here, default is "\n\n" String
permalink: /:year/:month/:day/:title.html
highlighter: rouge  # 使用rouge作为语法高亮引擎
markdown: kramdown  # 使用kramdown作为markdown的转换器
kramdown:
  input: GFM
  hard_wrap: true # a newline in markdown text would be changed to <br>
gems:
  - jemoji # 要站点支持Github表情，必须添加

# 上传到Github Pages时Github会进行配置的项，详见：Github Help With Configuring Jekyll

# Github Pages默认配置项，Jekyll的配置可以覆盖
# kramdown:
#   input: GFM
#   hard_wrap: false
# gems:
#   - jekyll-coffeescript
#   - jekyll-paginate

# Github Pages不可改变项，会覆盖Jekyll的配置
# lsi: false
# safe: true
# source: [your repo's top level directory]
# incremental: false
# highlighter: rouge
# gist:
#  noscript: false
# kramdown:
#  math_engine: mathjax

~~~

### **什么是Gems？Gems详解**
Gems 是可以包含在 Ruby 项目中的代码。Gems 封装了特定的功能。您可以跨多个项目或与其他人共享 gem。 Gems 可以执行以下操作：
* 将 Ruby 对象转换为 JSON
* 分页
* 与 GitHub 等 API 交互
Jekyll is a gem。许多 Jekyll插件也是 gem，包括 jekyll-feed、 jekyll-seo-tag和 jekyll-archives。
e.g. ~> 2.3  means "equal to 2.3 or greater than 2.3
jekyll也是一个gem，4.3.1 - October 26, 2022 (125 KB)
bundler也是一个gem，2.3.26 - November 17, 2022 (402 KB)
Bootstrap也是一个gem，5.2.2 - October 15, 2022 (160 KB)

#### **Gemsfile里frozen_string_literal: true代码**
Ruby 中冻结的对象只会创建一次，以后遇到相同的对象会复用之前创建的对象，这样可以减少对象创建次数和垃圾回收次数。Ruby 中的符号、整数、浮点数默认都是冻结的，字符串字面量目前还不是。
为了提高程序性能，在 Ruby 3 中，字符串字面量在所有文件中默认被冻结。
为了过渡，Ruby2.3 增加了一个魔法注释： frozen_string_literal: true

### Gemfile和Gemfile.lock文件详解
为什么有了 Gemfile 文件还需要一个 Gemfile.lock 文件，我知道是为了在多种场合下保持 gem 版本一致，比如在开发和部署时，或者你有多台不同的开发机器，或者项目有多人开发。但是它到底是如何保持的，一直比较迷惑。下面简要记录一下：
首先，Gemfile 文件所列的 gem 只是项目依赖的一部分，gem 本身也有自己的依赖，不同的 gem 本身可能依赖了某一 gem 不同的版本，如何让这么多不同版本的依赖相安无事，不发生冲突，这就是 bundle 的发挥作用的时候了。bundle 不仅用来安装 gem，更重要的是还负责计算出不同 gem 的依赖版本，最终生成 Gemfile.lock 文件，该文件记录了确切的 gem 名称和版本号，以及他们所依赖的 gem 的名称和版本号。
第一次运行 bundle install 时自动生成 Gemfile.lock 文件。 以后每次运行 bundle install 时,如果 Gemfile 中的条目不变 bundle 就不会再次计算 gem 依赖版本号，直接根据 Gemfile.lock 检查和安装 gem。 如果出现依赖冲突时可以通过 bundle update 更新 Gemfile.lock。

#### Gemfile里面的gemspec代码
gemspec 定义了 gem 中的内容、制作者以及 gem 的版本。它也是您访问 RubyGems.org 的界面。您在 gem 页面上看到的所有信息（例如jekyll的）都来自 gemspec。
创建页面
方式一 | **某路径**下添加xxx.html，访问地址为该路径/xxx.html 方式二 | **某路径**下添加xxx/index.html，访问地址为该路径/xxx，无需后缀

#### front matter(Yaml头信息)
每个页面都可以有自己的头信息，可以覆盖Jekyll和_config.yml里面的值
---
layout: post
title: 一步一步创建Jekyll主题
categories: [jekyll github markdown rouge]
date: 2016-9-3 15:47:05
excerpt: ""   # 覆盖清掉文章的摘要
pid: ""       # 新建一个pid的字符串变量
---

#### site变量
来自_config.yml配置文件和Jekyll内置变量，下面是常用的属性：
- site.posts	从新到旧排序的 posts 文章列表集合
- site.categories	以目录分类的文章列表 Map{cate1:[post1, post2], cate2:[post3, post4]}
- site.tags	以 tags 分类的文章列表 Map{tag1:[post1, post2], tag2:[post3, post4]}
- site.XXX	_config.yml配置文件中XXX: val的 val 值，val 可以是字符串/数组/集合

#### page变量
指代当前页面的变量，在index.html里使用page，page指的就是index.html这个页面，常用属性：
- page.content	页面源码(含有 markdown/liquid 等语句)
- page.title	页面标题
- page.excerpt	页面摘要源码，可通过_config.yml 配置摘要算法
- page.url	页面的相对路径
- page.date	页面的时间和日期
- page.categories	页面的 categories 数组，linux/ruby/_posts/ruby.md文章会把 linux 和 ruby 加入 - categories，和上面的 site.categories 不同！
- page.tags	页面的 tags 数组
- page.path	页面的实际路径(源码路径)

*注意：当前页面的 Front Matter 中设置的 xxx: val 可以通过 page.xxx 访问 val 值 另外：site.posts 数组的元素 post 和 page 具有几乎一样的属性*

#### liquid语法
Jekyll内变量操作是使用[Liquid语法](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers)

主要有：

1、显示变量的值 {{ 变量名 }}

如果要组成字符串，可以这样："字符串头部{{ 变量名 }}字符串尾部"

也可以使用 Filter：{{ "字符串头部" | append : 变量名 | append : "字符串尾部" }}

如，显示文章的标题：{{ page.title }}

2、使用变量的值进行计算 文章的标题计算 {% assign titleAndDate = page.title | append: page.date %}

assign x = y是声明一个变量并赋值，声明必须赋值！

xxx | append: "str"是 Liquid 语法中的 Filter，可以理解为管道，也可以简单理解为对象|方法:参数

Filter 可以连续执行：xxx | append: "str1" | append: "str2"

3、if 语句
~~~
{% if site.title == "" %}
{% assign title = "A" %}
{% elsif site.title == "stepbystep" %}
{% assign title = "B" %}
{% else %}
{% assign title = "C" %}
{% endif %}
~~~

4、for 语句
~~~
{% for post in site.posts %}
 {% assign title = post.title %}
 The post title is {{ title }}
{% endfor %}
~~~

5、访问 map 的 key 和 value 像site.categories其实是一个 map，访问分类是 linux 的文章集合有两种方式： 

~~~
方式一: site.categories.linux即是分类为 linux 的 posts 列表 方式二: for cate in site.categories，cate[0]是 linux，cate[1]是 posts 列表
~~~


#### Bundler详解

Bundler使用Ruby语言写的，通过跟踪和安装运行Ruby项目所需要的确切的gem和版本,为Ruby项目提供了完整的可运行环境。 Bundler跳出了复杂的环境依赖，并且确保下载你在development, staging, and productionBundler这三个阶段所需要的gem源。开始一个项目的工作只需要一个简单的命令：bundle install Bundler是一种有用的工具，它能使你更方便地跟踪某个应用程序所依赖的gem（以及这些gem的版本）。它通过安装应用程序的Gemfile中的所有gem来做到这一点。

卸载Bundler目前的版本
gem uninstall bundler
安装Bundler
gem install bundler

#### Bootstrap详解
一个用于快速开发 Web 应用程序和网站的前端框架
基于html和JavaScript、css三者开发的框架，主要用于响应式网站上的结构和布局，Bootstrap的出现主要是简化Web工作者的工作，其中还包括对JavaScript中的动态调整。
只需要写HTML标签调用它的类你就可以很快速的做一个高大上的网页，你不用担心兼容问题，提供了很多样式供你选择！

使用bootstrap框架可以响应式网站，bootstrap能使用适用pc和手机等不同分辨率的设备，我们不需要根据设备的不同而去担心显示效果。目前所有的浏览器都支持Bootstrap，所以我们在做网站的时候，也不要考虑浏览器的兼容问题。





## Q&A 常见问题

### 既然master 已经能展示页面了， gh-pages分支是什么作用呢？

通过git-add -A、git -commit -m "..." 命令把完成的项目上传到github上以后，默认的是处于master分支，这个主要用来展示项目，然后新建gh-pages分支：`git push origin gh-pages`，展示.github.io网站。
mkdir [-p] dirName mkdir -p runoob2/test 若 runoob2 目录原本不存在，则建立一个。
mkdir [-p] dirName 创建文件夹（命令 -p 确保目录名称存在，不存在的就建一个。
mkdir -p runoob2/test 若 runoob2 目录原本不存在，则建立一个。
cd .. 返回上一级目录
cls 清屏

bundle exec jekyll serve- 运行您的 Gemfile/Gemfile.lock 中指定的确切 jekyll 服务器版本。 jekyll serve- 运行某些版本的 jekyll 服务器
jekyll启动时出现的问题 bundle add webrick，添加完这段代码终于可以运行了！webrick是用Ruby写的 web server,这是因为 webrick 不再是 Ruby 3.0 中的捆绑 gem，我们需要手动添加 webrick 到 Gemfile 中作为依赖。

### 如何创建一个新的博客文章
1. 导航到GitHub 上的 _posts 上的文件夹
2. 点击 Add file > Create new file
3. 命名文件 {{ site.time | date: '%Y-%m-%d' }}-your-new-blog-post.md
4. 使用 Markdown 语法设置博客文章的标题。（第一行： ## 这是标题）
5. 单击该 Preview 选项卡，您可以预览文章。写好后提交保存即可！


### Github 如何创建一个隐藏的仓库并使用 Github Pages?
Github Pro, 一个月 4 美元, 支持私有仓库 Github Pages充钱，或者使用组织账户。
插入gjf 不要自动播放 {:data-gifffer="/img/****.gif"}
Jekyll Sitemaps生成器插件 Jekyll插件可为您的Jekyll网站静默生成与sitemaps.org兼容的站点地图

 将gem'jekyll gem 'jekyll-sitemap'添加到您站点的Gemfile并运行bundle 将以下内容添加到您网站的_config.yml : url : "[ https://example.com](https://example.com/) " # the base hostname & protocol for your site plugins : - jekyll-sitemap :light_bulb: 如果您使用的Jekyll版本低于3.5.0,请使用gems键而不是plugin



### 如何创建一个隐藏的仓库并使用Github Pages?
cdn+对象存储 或者 cloudflare page
私有仓库部署到 cloudflare pages 、Vercel，都有免费额度，相对来说 Vercel 的访问速度还是不错的

1. 源码放在私有仓库里，action 编译好 push 到.github.io 的仓库
2. 选择 gitlab, cf pages

可以写个 Action 从私有仓库拉代码 build 然后 push 到 Pages 分支

### Github换行符的问题
git如何避免”warning: the endings will be changed form LF to CRLF“提示？

假如你正在Windows上写程序，又或者你正在和其他人合作，他们在Windows上编程，而你却在其他系统上，在这些情况下，你可能会遇到行尾 结束符问题。 这是因为Windows使用回车和换行两个字符来结束一行，而Mac和Linux只使用换行一个字符。 虽然这是小问题，但它会极大地扰乱跨平台协作。Git可以在你提交时自动地把行结束符CRLF转换成LF，而在签出代码时把LF转换成CRLF。用core.autocrlf来打开此项功能， 如果是在Windows系统上，把它设置成true，这样当签出代码时，LF会被转换成CRLF：

Uinx/Linux采用换行符LF表示下一行（LF：LineFeed，中文意思是换行）；
Dos和Windows采用回车+换行CRLF表示下一行（CRLF：CarriageReturn LineFeed，中文意思是回车换行）；
Mac OS采用回车CR表示下一行（CR：CarriageReturn，中文意思是回车）。

CR为回车符，LF为换行符。Windows结束一行用CRLF，Mac和Linux用LF。
core.autocrlf
false表示取消自动转换功能。适合纯Windows
true表示提交代码时把CRLF转换成LF，签出时LF转换成CRLF。适合多平台协作
input表示提交时把CRLF转换成LF，检出时不转换。适合纯Linux或Mac

在Git中，可以通过以下命令来显示当前Git中采取哪种对待换行符的方式

$ git config core.autocrlf
此命令会有三个输出，“true”，“false”或者“input”

为true时，Git会将要提交的文件视为文本文件，将行尾（line endings）的CRLF转换为LF，而检出时会再将文件的LF格式转为CRLF格式
为false时，行尾不做任何改变，文件换行符保持其原来的格式
为input时，Git会将要提交文件行尾的CRLF转换为LF，而检出时不做处理

warning级别的警告都是可以忽略的，这个警告也是。
如果你是一个强迫症，非要去掉所有warning，也是可以。如果你可以保证你的代码不会跨平台开发，（比如你和你的合作者用不同的系统进行开发时，关掉这个自动转换的功能可能会导致代码显示异常），你可以设置关掉自动转换的功能。
当然，结合实际情况来说，你不能保证你的所有代码都不会跨平台开发，因为你不能保证你的合作者用的是跟你一样的系统，这个时候，最好就是只针对当前仓库设置，你只要保证当前仓库的代码不会跨平台开发就行。
就我现在来说，比较建议忽略这个警告。


### **常见的git指令用法：**

git init：建立管控程式用的本地端档案库，这是建立版本控制的第一个步骤。

git add：将程式加进暂存目录中，以便日后提交至档案库。

git commit：在完成开发工作后，将完整的程式提交至档案库，可利用-m参数写入本次提交的相关说明。

git rm：将档案删除掉，并移除该档案的管控。

git status：显示相关状态资讯。

git branch [分支名称]：建立分支程式。

git checkout [分支名称]：切换到该分支下。如果仅执行「git checkout」，表示退出该分支。

git push：将档案上传至远端的档案库。

git clone：从远端伺服器上完整下载某个档案库内容。

git档案状态

git会将档案状态分成以下四类，分别加以说明：

‧untracked：代表未被追踪的状态，此为在工作目录中新增档案的最初始状态，表示该档案尚未被git所追踪及管控。

‧unmodified：表示未被修改的状态，当使用者以「git add」指令将状态为untracked的档案加入追踪，就会将该档案状态从untracked更改到unmodified。另外一种情况是档案已经被提交至档案库，也会将档案的状态回复到unmodified。

‧modified：已被修改的状态，当档案被改变时便会转换到此状态。

‧staged：表示暂存的状态，通常处于这个状态的档案，即表示要准备提交到档案库上。

#### 查看Git的版本号：
打开终端—输入命令git --version



### plugins（Jekyll插件）有哪些？
要安装 Jekyll插件，需要在两个地方添加插件名称。一个在_config.yml文件的plugins部分，第二个在Gemfile文件
jekyll-titles-from-headings

### Github Desktop报错Author identity unknown，提交出现错误

~~~
Author identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: empty ident name (for <***@protonmail.com>) not allowed
~~~
或
~~~
fatal: unable to auto-detect email address (got '***o@DESKTOP***.(none)')
~~~

答：到git里面切换一下邮箱，点击软件Options——Git，确认用户名邮箱正确，点击OK即可


### 绑定Github上的个人博客到Godaddy域名
1、在网站的Github项目上，点击设置Settings，找到Custom domain，填入申请的域名www.xxx.com，并保存。
GitHub已与Let’s Encrypt合作，为Github Pages自定义域名提供官方的HTTPS 支持。

（Github项目的根目录CNAME文件，[自定义域和 GitHub 页面故障排除](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/troubleshooting-custom-domains-and-github-pages#cname-errors)。）

2、在域名解析提供商网站修改DNS
CNAME：主机记录写www(或@，@表示空)，后面记录值也是xxx.github.io，这样用www和不用www都能访问你的网站，主机记录也可以是二级域名news或blog。
（使用A记录，name写@，记录值Data是写github page里面的ip地址，但IP地址会更改导致解析不正确。）

GoDaddy的A记录的值默认为“Parked”。CNAME记录的_domainconnect不用管，是GoDaddy's implementation of the Domain Connect standard。

Github Pages的A记录
~~~
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
~~~




## **参考文档**
- [Jekyll的中文文档](http://jekyll.bootcss.com/) 
| [Jekyll的英文官方文档](http://jekyllrb.com/docs/)
| [Windows安装Jekyll教程](https://jekyllrb.com/docs/installation/windows/)
| [GitHub的官方文档之Jekyll](https://docs.github.com/cn/pages/setting-up-a-github-pages-site-with-jekyll)
- [Liquid的文档1](https://help.shopify.com/themes/liquid) 
| [文档2](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) 
| [文档3](https://shopify.github.io/liquid/)
- [语法高亮引擎rouge的文档](https://github.com/jneen/rouge) 
- [Markdown转换器kramdown的文档（支持maruku语法）](http://kramdown.gettalong.org/) 
| [Markdown转换器maruku的文档（支持TOC语法）](http://maruku.rubyforge.org/maruku.html) 
- [Emoji](https://emojipedia.org/nature/)
- [如何选择合适的静态生成器：Jekyll vs. Hugo vs. Hexo](https://www.techiediaries.com/jekyll-hugo-hexo/)

## **写在最后**
学习使我快乐，我喜欢学习新东西，GitHub Pages、Jekyll、Markdown、Ruby、HTML、CSS、Liquid、YAML、Notepad++，PowerShell