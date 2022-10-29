# UCB CS61A: Structure and Interpretation of Computer Programs

强调抽象，让学生掌握用程序来解决实际问题，而不关注底层的硬件细节。此外，抽象将是这门课的一大主题，你将学习到函数式编程、数据抽象、面向对象等等知识来让你的代码更易读，更模块化。课程主要分为 video， Q&Avideo，Discussion，Homework， Lab，和[Textbook (SICP for python)](<http://composingprograms.com/pages/11-getting-started.html>)。此 Textbook非常推荐。

由于我们没有ucb的邮箱，所以我们是没有办法使用ok系统来测试我们代码的正确性，可以查看[最新的61A课程](https://cs61a.org/)，上面会发布solutions，但是有可能
你的学习速度快于最新课程发布的速度（因为你有可能使用过往学期的videoes），另外可以去github上寻找资料。

关于这个课程的内容介绍与总结 转移至 我的Github另一个仓库 [UCB CS61A](https://github.com/Emma-ssq/UCB-CS61A){:target="_blank"}

下面只是介绍一些使用python时的小技巧。

## 代码规范

vscode中一般使用pep8，yapf来格式化python代码，除此之外还需要一些其他的规范。

1. 编写docstring和pytest， 使用`python3 -m doctest -v test.py`命令运行。

```python
def divde_exact(n,d):
    # 函数编写docstring，（编写pytest文件）
    """Return the quotient and remainder of dividing N by D.
    >>> q, r = divide_exact(2013, 10)
    >>> q
    201
    >>> r
    3
    """
    return n // d, n % d

```

## 帮助help

1. python自带了help函数，进入python后直接输入help会提示如何查询object的信息。
2. [python docs官方教程](https://docs.python.org/3/)也提供了查询功能。

## 关于print函数

1. 合理使用参数`end`, `print("hi number", end="") print(2)` 是更好的选择，相比于`print("hi number",2)`

## 运行命令

1. `-i` 交互模式
2. pytest:

## 一些好用的函数

### assert

`assert 3<2, "Math is broken"`: AssertionError
