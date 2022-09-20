# mkdocs

## 参考教程

1. [MkDocs中文文档](https://mkdocs.zimoapps.com/){:target="_blank"}
2. [中文配置material主题](https://yiruru.com/6%E4%BB%A3%E7%A0%81%E5%A6%82%E8%AF%97/%E4%BA%91%E5%BB%BA%E7%AB%99/Material%E4%B8%BB%E9%A2%98%E8%AE%BE%E7%BD%AE/){:target="_blank"}
3. [中文实践](https://cyent.github.io/markdown-with-mkdocs-material/){:target="_blank"}

## mkdoc.yml文件

**具体请参考[此博客仓库的mkdoc.yml](https://github.com/Emma-ssq/blog/blob/master/mkdocs.yml){:target=“_blank"}**

### 基本配置

1. site，repo相关用来配置网站内容和链接github仓库。

### theme:material

选用material主题，排版简洁，左右各有目录，便于阅读。

1.

## gitcus配置博客评论系统

> [如何使用 GitHub 讨论作为您博客的聊天系统_杭州程序员张张的博客-CSDN博客_github上如何私信](https://blog.csdn.net/duninet/article/details/125280107)

**gitcus是一个由Github Discussion支持的评论系统。它可以让你把仓库中的讨论整合到你的博客中。** 读者在博客上留下评论，这些评论会同时出现在你的代码库的讨论区中。

1. 首先设置仓库是 **public** 的，并开启 **discussion** 权限（在repo的settings中进行设置）。

2. **[安装 giscus应用程序]([Installed GitHub App - giscus](https://github.com/settings/installations/29422562))**。并对选定的代码库开启权限。

3. 进入 **[giscus主界面]([giscus](https://giscus.app/zh-CN))**，选定语言，仓库，映射关系（选择URL或者title），Discussion分类，特性（一般选择启用主帖子上的反应，评论框放在评论上方，懒加载评论），主题。 然后 **复制下面的html代码。**

4. **在mkdoc.yml文件的custom_dir变量配置了用于覆盖原配置的文件夹，eg：我设置了`custom_dir:overrides`，因此在overrides文件夹下新建main.html文件。在main.html文件中一定要设置`{% extends "base.html %"}`。** 下面是我的main.html文件。

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
