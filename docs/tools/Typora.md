# Typora

一款编辑markdown文件的极其实用的工具，免费（直接下载1.0版本之前的，1.0版本之后的收费），拥有令码农痴迷的 **实时显示** 功能，同时还可以 **直接拉取图像，自动生成插入图像的md格式代码** ，界面非常 **简洁** ，唯一不好的缺点在于没有代码自动格式化的功能，推荐在大致编辑好自己的markdown文件后，使用 **vscode中的markdownlint插件对文本进行自动格式化** 之后再上传公开。

下面就主要介绍常用的指令。

## 网站，文件，段落链接

1. 在文本中插入链接直接指向文件夹中的文件：例如

```markdown
[Google C++代码规范的参考书籍](./Google C++ Style Guide中文.pdf)
```

## 图片

1. **推荐最简单的方式：**

   ```markdown
   ![Utools](./文件夹/Utools.png)
   ```

2. 在网页端显示，目前 **需要将图片上传到云端** ，不能是本地图片。

   ```html
   1. <div align="center"><img src="图片链接"  alt="图片名称1"  width="200" height="200"></img></div>
   2. <div align="center"><img src="图片链接" alt="图片名称2" style="zoom=50%"></img></div>
   ```
