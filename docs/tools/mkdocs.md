# mkdocs

## 参考教程

1. [MkDocs中文文档](https://mkdocs.zimoapps.com/){:target="_blank"}
2. [中文配置material主题](https://yiruru.com/6%E4%BB%A3%E7%A0%81%E5%A6%82%E8%AF%97/%E4%BA%91%E5%BB%BA%E7%AB%99/Material%E4%B8%BB%E9%A2%98%E8%AE%BE%E7%BD%AE/){:target="_blank"}
3. [中文实践](https://cyent.github.io/markdown-with-mkdocs-material/){:target="_blank"}

## 第一个mkdocs项目

安装MkDocs，系统上需要安装python以及包管理器pip。

```bash
#安装mkdocs
pip install mkdocs
#mkdocs创建第一个文件
mkdocs new blog
cd blog
# 实时编译，用于在本地先写博客调试
mkdocs serve
# 文件目录
- blog
  - mkdocs.yml
  - docs
    - index.md
# 打包编译成网页在/site文件夹中
mkdocs build
```

### 上传到github-pages

1. 在github上创建一个新仓库，设置为 **public** ,关联本地博客仓库。
2. 配置远程仓库settings中的pages界面，build and deployment处设置为 **branch:gh-pages, /root** ，保存。
3. 配置github-actions中的workflow，创建新的工作流，存储在[.github/workflows/autoPublish.yml](https://github.com/Emma-ssq/blog/blob/master/.github/workflows/autoPublish.yml){:target="_blank"}中，具体内容如下：

  ```yaml
  name: autoPublish
  on:
    push:
      branches:
        - master
        - main

  jobs:
    deploy:
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v2
          with:
            fetch-depth: 0

        - uses: actions/setup-python@v2
          with:
            python-version: 3.x

        - run: pip3 install -U -r requirements.txt
        - run: mkdocs gh-deploy --force
  ```

## mkdoc.yml文件

**具体请参考 [我的这个博客仓库的mkdoc.yml](https://github.com/Emma-ssq/blog/blob/master/mkdocs.yml){:target="_blank"}**

### 基本配置

site，repo相关用来配置网站内容和链接github仓库。

### theme，md-extensions，plugins等

选用material主题，排版简洁，左右各有目录，便于阅读。格式大致如下：

```yaml
theme:
  name: material
  font: #字体
  icon: #github
    repo: fontawesome/brands/github
  custom_dir: overrides # # 在该文件夹下修改部分配置，覆盖父主题
  features: #设定整体布局特性
  palette: #阅读模式，白天或黑夜

markdown_extensions: #推荐配置Markdown基本语法及其扩展
extra_javascript: #为md文件显示在网页端提供一些必要的js或css文件。
extra: #其他，譬如配置页脚，数据分析。
plugins: #插件，譬如添加搜索栏，关联github最后更新时间。
```

### nav导航

设置左侧目录：描述以及对应的markdown文件。

```yaml
nav:
  - 前言: "index.md"
  - 代码规范: "代码规范/代码规范.md"
  - 实用工具:
      - 科学上网: "tools/科学上网.md"
```

## giscus配置博客评论系统

> [如何使用 GitHub 讨论作为您博客的聊天系统_杭州程序员张张的博客-CSDN博客_github上如何私信](https://blog.csdn.net/duninet/article/details/125280107){:target="_blank"}

**gitcus是一个由Github Discussion支持的评论系统。它可以让你把仓库中的讨论整合到你的博客中。** 读者在博客上留下评论，这些评论会同时出现在你的代码库的讨论区中。

1. 首先设置仓库是 **public** 的，并开启 **discussion** 权限（在repo的settings中进行设置）。

2. **[安装 giscus应用程序](https://github.com/settings/installations/29422562){:target="_blank"}**。并对选定的代码库开启权限。

3. 进入 **[giscus主界面](https://giscus.app/zh-CN){:target="_blank"}**，选定语言，仓库，映射关系（选择URL或者title），Discussion分类，特性（一般选择启用主帖子上的反应，评论框放在评论上方，懒加载评论），主题。 然后 **复制下面的html代码。**

4. **在mkdoc.yml文件的custom_dir变量配置了用于覆盖原配置的文件夹，eg：我设置了`custom_dir:overrides`，因此在overrides文件夹下新建main.html文件。在main.html文件中一定要设置`{% extends "base.html %"}`。** 下面是我的[main.html](https://github.com/Emma-ssq/blog/blob/master/overrides/main.html){:target="_blank"}文件。

   ```html
   {% extends "base.html" %} 
   {% block giscus %}
   <script src="https://giscus.app/client.js" data-repo="Emma-ssq/blog" data-repo-id="R_kgDOIAA20A"
           data-category="Announcements" data-category-id="DIC_kwDOIAA20M4CRiD-" data-mapping="title" data-strict="0"
           data-reactions-enabled="1" data-emit-metadata="0" data-input-position="top" data-theme="light" data-lang="zh-CN"
           data-loading="lazy" crossorigin="anonymous" async>
           </script>
   {% endblock %}
   ```
