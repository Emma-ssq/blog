# Debug

> [调试与性能分析](https://missing-semester-cn.github.io/2020/debugging-profiling/)

## logging

[这里是一个python logger.py 文件](./Debug.assets/logger.py)，你可以运行它并查看输出。
![logger.py运行](./Debug.assets/python%20logger%E8%BF%90%E8%A1%8C.png)

## 第三方日志系统

1. Unix系统一般将日志存放在`/var/log`文件夹中，系统日志一般在system log中。大多数（但不是全部的）Linux 系统都会使用 systemd，这是一个系统守护进程，它会控制您系统中的很多东西，例如哪些服务应该启动并运行。systemd 会将日志以某种特殊格式存放于/var/log/journal，可以使用 journalctl 命令显示这些消息。或者使用log show命令。
2. 日志文件一般特别多，可以使用`lnav`这样的工具浏览日志。

## 静态检查

1. pyflakes是python的静态检查工具。大多数的编辑器和 IDE 都支持在编辑界面显示这些工具的分析结果、高亮有警告和错误的位置。 这个过程通常称为 code linting 。 在 Python 中， pylint 和 pep8 是两种用于进行风格检查的工具。对于风格检查和代码格式化，还有以下一些工具可以作为补充：用于 Python 的 black。

## debugger调试器

1. python的调试器是pdb，当然还有一些很好的IDE融合了非常直观方便的debug工具，更为推荐。
2. pdb命令：

    ```bash
    -l(list)
    -s(tep)
    -n(ext)
    -b(reak)
    -p(rint)
    -r(eturn)
    -q(uit)
    ```

3. 对于更底层的编程语言，可以了解gdb

## 性能分析

过早的优化是万恶之源，需要学习性能分析和监控工具，它们会帮助找到程序中最耗时、最耗资源的部分，这样就可以有针对性的进行性能优化。

以time为例，执行时间（wall clock time），用户时间和系统时间是不同的。

python中可以使用cProfile模块分析程序

## 可视化

对于采样分析器来说，常见的显示 CPU 分析数据的形式是 [火焰图](<https://www.brendangregg.com/flamegraphs.html>)，火焰图会在 Y 轴显示函数调用关系，并在 X 轴显示其耗时的比例。火焰图同时还是可交互的，您可以深入程序的某一具体部分，并查看其栈追踪（您可以尝试点击下面的图片）。

调用图和控制流图可以显示子程序之间的关系，它将函数作为节点并把函数调用作为边。 在 Python 中您可以使用 pycallgraph 来生成这些图片。

## 专门工具

1. 当您的程序需要执行一些只有操作系统内核才能完成的操作时，它需要使用 系统调用。有一些命令可以帮助您追踪您的程序执行的系统调用。在 Linux 中可以使用strace
2. 通用监控 - 最流行的工具要数 htop,了，它是 top的改进版。
3. 打开文件 - lsof 可以列出被进程打开的文件信息。 当我们需要查看某个文件是被哪个进程打开的时候，这个命令非常有用；
