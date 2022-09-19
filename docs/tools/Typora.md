# Typora

Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档。

Typora是一款编辑markdown文件的极其实用的工具，免费（直接下载1.0版本之前的，1.0版本之后的收费），拥有令码农痴迷的 **实时显示** 功能，同时还可以 **直接拉取图像，自动生成插入图像的md格式代码** ，界面非常 **简洁** ，唯一不好的缺点在于没有代码自动格式化的功能，推荐在大致编辑好自己的markdown文件后，使用 **vscode中的markdownlint插件对文本进行自动格式化** 之后再上传公开。
910a415aec03fb6505408fe021c3b79c
下面就主要介绍常用的指令。

## Typora+Gitee图床+PicGo

[下载安装配置Typora](https://mp.weixin.qq.com/s/OluefwPTsU3Oz4FhZegaZw) 使之可以图片上传到Gitee仓库上便于外部访问，同时这个链接中还记录常见的指令。 我目前的配置是图片“本地存放”，在需要上传时一次性将文件中的图片全部上传。

## 网站，文件，段落链接

1. 在文本中插入链接直接指向文件夹中的文件：例如

```markdown
[Google C++代码规范的参考书籍](./Google C++ Style Guide中文.pdf)
```

## 图片

1. **推荐最简单的方式：**

   ```markdown
   ![链接失效时显示的名称](./文件夹/Utools.png "title可选鼠标移动显示的名称")
   ```

2. 在网页端显示，目前 **需要将图片上传到云端** ，不能是本地图片。

   ```html
   1. <div align="center"><img src="图片链接"  alt="图片名称1"  width="200" height="200"></img></div>
   2. <div align="center"><img src="图片链接" alt="图片名称2" style="zoom=50%"></img></div>
   3. 
   <center>
    <img style="border-radius: 20px;"
         src="Typora.assets/baymax.jpg" 
         alt="baymax"
         width="688" >
   </center>
   ```

## 字体

### 加粗

1. 使用双`**`号，但是请注意一定是在加粗字符串前面 **留有空格**。
2. 使用`<strong></strong>`将字符括起来。

### 斜体

1. `*斜体*`，*斜体示例*`

## 分割线

1. 三个或三个以上的 `*` 或者 '-'

## emoji表情

1. 使用冒号`:emoji:`，Typora会给出提示。实例：:e-mail:
