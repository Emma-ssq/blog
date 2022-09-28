# Git 版本控制系统

> [Missing-semester-git](https://missing-semester-cn.github.io/2020/version-control/)

## 基本概念

### 数据模型

Git 将顶级目录中的文件和文件夹作为集合，并通过一系列快照来管理其历史记录。在Git的术语里，文件被称作Blob对象（数据对象），也就是一组数据。目录则被称之为“树”，它将名字与 Blob 对象或树对象进行映射（使得目录中可以包含其他目录）。快照则是被追踪的最顶层的树。例如，一个树看起来可能是这样的：
![git数据结构](Git.assets/git%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84.png)

在 Git 中，历史记录是一个由快照组成的有向无环图。
![git历史提交](Git.assets/git%E5%8E%86%E5%8F%B2%E6%8F%90%E4%BA%A4.png)
Git 中的提交是不可改变的。但这并不代表错误不能被修改，只不过这种“修改”实际上是创建了一个全新的提交记录。而引用（参见下文）则被更新为指向这些新的提交。

以伪代码的形式来学习 Git 的数据模型，可能更加清晰：

```c
// 文件就是一组数据
type blob = array<byte>

// 一个包含文件和目录的目录
type tree = map<string, tree | blob>

// 每个提交都包含一个父辈，元数据和顶层树
type commit = struct {
    parent: array<commit>
    author: string
    message: string
    snapshot: tree
}
```

### 引用

Git 中的对象可以是 blob、树或提交，it 在储存数据时，所有的对象都会基于它们的 SHA-1 哈希 进行寻址。现在，所有的快照都可以通过它们的 SHA-1 哈希值来标记了。但这也太不方便了，谁也记不住一串 40 位的十六进制字符。针对这一问题，Git 的解决方法是给这些哈希值赋予人类可读的名字，也就是引用（references）。引用是指向提交的指针。与对象不同的是，它是可变的（引用可以被更新，指向新的提交）。例如，master 引用通常会指向主分支的最新一次提交。

### 仓库

最后，我们可以粗略地给出 Git 仓库的定义了：对象 和 引用。
在硬盘上，Git 仅存储对象和引用：因为其数据模型仅包含这些东西。所有的 git 命令都对应着对提交树的操作，例如增加对象，增加或删除引用。

### 暂存区

创建提交的接口的一部分，允许您指定下次快照中要包括那些改动。

## 命令

### 初始化

```bash
git init .
# 进入 .git/ 文件夹中，存在很多内容包括objects和refs
ls .git/
config  description  HEAD  hooks/  info/  objects/  refs/
# 分支状态
git status 
# 历史记录
git log
git log --all
git log --all --graph --decorate 
git log --all --graph --decorate --oneline
# 根据哈希值查看metadata，可以是历史版本的哈希值，或是tree，blob的哈希值。
git cat-file -p 5e0b
```

### add 和 commit

```bash
git add a.txt 
git add -p a.txt 
git diff --cached     
git commit  # 进入文件中写提交信息 or
git commit -m "提交信息"
```

### checkout 更新 HEAD 和目前的分支

```bash
git checkout 哈希值或者refs
# 强制转换
git chechout -f 哈希值或者refs
```

### diff 比较不同

```bash
git diff hello.txt
git diff 历史版本1  历史版本2 文件名
```  

### branch

```bash
git branch -vv
git branch 新的分支名称
```

### merge

```bash
git log
# 合并指定分支到当前分支
git merge 指定分支
# merge conflict
git merge --continue 
```

### clone

```bash
git clone <url> 本地文件夹
# 记录最近提交即可
git clone --shallow
```

## remote

```bash
git remote add 远程名称 远程url
git push <remote> <local_branch>:<remote branch>
# 设置当前本地分支关联追踪远程分支
git branch --set-upstream-to=origin/master
git branch -vv
git push
# 追踪远程变化并拉取
git fetch; git merge  # 两个命令相当于git pull
git pull 

```

### config

1. 在`~/.gitconfig` 文件中，使用`git config`命令进行配置

### .gitignore

1. .gitignore 用于指定git对哪些文件的修改隐藏略过。

## 如何写好一个Git commit

><https://www.liuxing.io/blog/how-to-write-a-good-commit/>
每次提交，commit message 都包括三个部分： Header (主题)、Body（详细描述） 和 Footer 组成，Body 和 Footer 都是可选的。

```bash
<header>
// 空一行
<body>
// 空一行
<footer>
```

![commit示例](./Git.assets/commit%E7%A4%BA%E4%BE%8B.png)

1. header行限制为50个字符，第一个字母大写，末尾不加句点。scope用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。
2. Body行宽不超过72字符，可以分行-，使用祈使句Add不是Added，Fix不是Fixed，描述目的不是具体实现
3. Footer 部分只用于两种情况。
    - 不兼容变动：如果当前代码与上一个版本不兼容，则 Footer 部分以BREAKING CHANGE开头，后面是对变动的描述、以及变动理由和迁移方法。
    - 关闭 Issue：Closes #234

### 一些有用的commit工具

> [git commit规范及自动检查工具安装小记](<https://juejin.cn/post/6844904033635794958>)
> [commitizen全局安装](<https://juejin.cn/post/7084119337375629342>)
> [anjular规范各部分含义](https://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)

1. Commitizen：并配置cz-conventional-changelog使用anjular 的规范，并且配置路径全局安装.czrc
2. 同时在vscode中安装Conventional Commits，实现commit格式检查，符合anjular规范。Visual Studio Code Commitizen Support 也可以实现在vscode窗口中编写good commits

另外还有Commitlint是一个可以帮我们检查 git commit 所提交信息是否符合conventional commit format（也就是类似上面的格式）的工具，但是我没有使用，觉得如果提交commit一直给我报错，maybe会影响心情。

又另外：如果你的所有 Commit 都符合 Angular 格式，那么发布新版本时， Change log 就可以用脚本自动生成，参见上面链接。

## 其他参考资料

- Pro Git ，强烈推荐！学习前五章的内容可以教会您流畅使用 Git 的绝大多数技巧，因为您已经理解了 Git 的数据模型。后面的章节提供了很多有趣的高级主题。[（Pro Git 中文版）](<https://git-scm.com/book/zh/v2>)；

- [Oh Shit, Git!?!](https://ohshitgit.com/) ，简短的介绍了如何从 Git 错误中恢复；

- [Git for Computer Scientists](https://eagain.net/articles/git-for-computer-scientists/) ，简短的介绍了 Git 的数据模型，与本文相比包含较少量的伪代码以及大量的精美图片；
