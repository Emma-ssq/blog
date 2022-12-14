# Make

> [metaprogramming](https://missing-semester-cn.github.io/2020/metaprogramming/)

"metaprogramming" 是有关于流程的任务，是操作程序的程序，我们需要学习构建系统，代码测试，依赖管理等方面的知识。

一般来说我们需要定义依赖、目标和规则。必须告诉构建系统具体的构建目标，系统的任务则是找到构建这些目标所需要的依赖，并根据规则构建所需的中间产物，直到最终目标被构建出来。理想的情况下，如果目标的依赖没有发生改动，并且我们可以从之前的构建中复用这些依赖，那么与其相关的构建规则并不会被执行。幸运的是，有很多工具可以帮助我们完成这些操作。

make是最常见的构建系统的工具，对于中小型项目来说，他已经足够好了。当执行 make 时，它会去参考当前目录下名为 Makefile 的文件。所有构建目标、相关依赖和规则都需要在该文件中定义。

## make 基本语法

```makefile
paper.pdf: paper.tex plot-data.png
 pdflatex paper.tex 

plot-%.png: %.dat plot.py
 ./plot.py -i $*.dat -o $@
```

当项目中的文件进行修改后重新make，make只会对依赖改动文件部分的命令重新执行完成修改。

## 依赖管理

大多数的依赖可以通过某些软件仓库来获取，这些仓库会在一个地方托管大量的依赖，我们则可以通过一套非常简单的机制来安装依赖。例如 Ubuntu 系统下面有Ubuntu软件包仓库，您可以通过apt 这个工具来访问， RubyGems 则包含了 Ruby 的相关库，PyPi 包含了 Python 库， Arch Linux 用户贡献的库则可以在 Arch User Repository 中找到。

版本号：如果我们发布了一项和安全相关的升级，它并没有影响到任何公开接口（API），但是处于安全的考虑，依赖它的项目都应该立即升级，那应该怎么做呢？这也是版本号包含多个部分的原因。一个相对比较常用的标准是语义版本号，这种版本号具有不同的语义，它的格式是这样的：主版本号.次版本号.补丁号。相关规则有：

- 如果新的版本没有改变 API，请将补丁号递增；
- 如果您添加了 API 并且该改动是向后兼容的，请将次版本号递增；
- 如果您修改了 API 但是它并不向后兼容，请将主版本号递增。

使用依赖管理系统的时候，您可能会遇到锁文件（lock files）这一概念。锁文件列出了您当前每个依赖所对应的具体版本号。通常，您需要执行升级程序才能更新依赖的版本。

## 持续集成系统

随着您接触到的项目规模越来越大，您会发现修改代码之后还有很多额外的工作要做。您可能需要上传一份新版本的文档、上传编译后的文件到某处、发布代码到 pypi，执行测试套件等等。或许您希望每次有人提交代码到 GitHub 的时候，他们的代码风格被检查过并执行过某些基准测试？如果您有这方面的需求，那么请花些时间了解一下持续集成。

持续集成，或者叫做 CI 是一种雨伞术语（umbrella term，涵盖了一组术语的术语），它指的是那些“当您的代码变动时，自动运行的东西”，市场上有很多提供各式各样 CI 工具的公司，这些工具大部分都是免费或开源的。比较大的有 Travis CI、Azure Pipelines 和 GitHub Actions。它们的工作原理都是类似的：您需要在代码仓库中添加一个文件，描述当前仓库发生任何修改时，应该如何应对。目前为止，最常见的规则是：如果有人提交代码，执行测试套件。当这个事件被触发时，CI 提供方会启动一个（或多个）虚拟机，执行您制定的规则，并且通常会记录下相关的执行结果。您可以进行某些设置，这样当测试套件失败时您能够收到通知或者当测试全部通过时，您的仓库主页会显示一个徽标。

本课程的网站基于 GitHub Pages 构建，这就是一个很好的例子。Pages 在每次master有代码更新时，会执行 Jekyll 博客软件，然后使您的站点可以通过某个 GitHub 域名来访问。对于我们来说这些事情太琐碎了，我现在我们只需要在本地进行修改，然后使用 git 提交代码，发布到远端。CI 会自动帮我们处理后续的事情。

## 测试简介

多数的大型软件都有“测试套件”。您可能已经对测试的相关概念有所了解，但是我们觉得有些测试方法和测试术语还是应该再次提醒一下：

1. 测试套件：所有测试的统称。
2. 单元测试：一种“微型测试”，用于对某个封装的特性进行测试。
3. 集成测试：一种“宏观测试”，针对系统的某一大部分进行，测试其不同的特性或组件是否能协同工作。
4. 回归测试：一种实现特定模式的测试，用于保证之前引起问题的 bug 不会再次出现。
5. 模拟（Mocking）: 使用一个假的实现来替换函数、模块或类型，屏蔽那些和测试不相关的内容。例如，您可能会“模拟网络连接” 或 “模拟硬盘”。
