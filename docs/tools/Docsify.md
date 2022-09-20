# Docsify

 [Docsify](https://jingping-ye.github.io/docsify-docs-zh/#/) 是一个轻量级快速文档生成器，非常适合编写技术文档。
访问 [Docsify中文文档快速上手](https://jingping-ye.github.io/docsify-docs-zh/){:target="_blank"}

## 安装

`npm i docsify-cli -g`

## 创建第一个docsify文档

0. 使用 **tldr查看常用命令**

1. 初始化：`docsify init ./文件夹名称`，初始化目录结构：

2. 预览网站：`cd 文件夹`，`docsify serve` 或者 一个命令 `docsify serve 文件夹名称`，在本地某端口打开预览网页。

   ```markdown
   |-- docs
        |-- index.html 入口
        |-- README.md 主页
        |-- .nojekyll 防止Github忽视下划线开头文件
   ```

## 腾讯云cloudbase静态网站托管

1. [腾讯云](https://cloud.tencent.com/){:target="_blank"} 为个人提供存储空间，可以配置静态网站托管服务，参考 [此链接](https://mp.weixin.qq.com/s/Noe90mhVssuBcySyb6TTNA){:target="_blank"}
2. 通过腾讯云界面上传文件：将index.html和README.md文件上传，进入到设置页，使用默认域名即可访问到我们的文档网站啦！ **默认会读取我们上传的index.html文件进行展示** ，也可以自己修改索引文档。
3. 借助cloudbase cli命令行上传网站文件：

    ```bash
    #安装
    npm install -g @cloudbase/cli
    #登录
    cloudbase login
    #上传文件，-r gz表示广州地区
    cloudbase hosting deploy . -e 环境ID -r gz
    ```

## 经典的博客网站

1. 适合个人博客：
    - [有很多插件](https://notebook.js.org/){:target="_blank"}
    - [有右侧目录](https://mouday.github.io/coding-tree/){:target="_blank"}
    - [目录超多](https://bytesfly.github.io/blog){:target="_blank"}
2. 适合技术文档：
    - [推荐：书籍文章](http://ddia.vonng.com/){:target="_blank"}
    - [豆瓣影音](https://hanxueqing.github.io/Douban-Movie){:target="_blank"}
3. **目前我的选择是使用mkdocs编写博客，使用docsify编写技术文档。**

## 搭建个人博客

1. 首先配置github-pages
2. 配置首页：_coverpage.md文件
3. 配置右侧目录
4. 配置全局
   1. index.html文件
