# Crash Course Computer Science

A new level of abstraction.

科普向系列视频: [Crash Course: Computer Science](https://www.bilibili.com/video/BV1EW411u7th/?vd_source=9dd0fcc3d5398236875800270d02049a) 生动且全面的科普了关于计算机科学的方方面面。

1. 电子开关：继电器，三极真空管，晶体管（计算时代2.0，其中包含半导体材料，Santa Clara Valley, 旧金山和圣荷西之间）。

2. ALU，计算与编码：
    - 二进制，布尔代数。
    - 字节Byte=8位
    - 浮点数标准IEEE 754：625.9 = + .6259 * 10^3
    - 字母编码：ASCII 美国信息交换标准代码；Unicode统一编码标准，一般16位。
    - 同样，mp3音频，视频，图片也使用类似字母编码的方式。
    - ALU 算术逻辑单元：an arithmetic unit & a logic unit

3. 寄存器与内存与存储器：
    - RAM内存：Random Access Memory ，可以随时访问任何位置，在有电的时候存储东西。
    - 存储器：非易失性的。

4. CPU：excute programs，时钟频率控制着中央处理器一步步执行指令，一般制造商会留有超频空间。同时为了提高处理程序的速度，现代处理器设计了专门电路来处理图形操作，解码压缩视频等程序  。

    - ![CPU](Crash%20Course%20Computer%20Science.assets/CPU.png)
    - CACHE，CPU空等数据：![CPU-Cache](Crash%20Course%20Computer%20Science.assets/CPU%20Cache.png)
    - 流水线处理程序，超标量流水线（一个clk内完成多条指令，一般通过设计多个ALU等部件实现），多核处理器，多CPU处理器

5. 编程：
    - 早期的编程方式：打孔纸卡，插线板，存储程序计算机。
    - 冯诺依曼结构：CPU+数据寄存器+指令寄存器+指令地址寄存器+内存（指令+数据）。
    - 汇编语言：助记符 --> 编译器
    - 高级语言：Fortran，BASIC，PASCAL，C，C++，Python，Java，Go
    - 核心概念：模块化编程。

6. 阿兰图灵：1912-1954
    - 可判定性问题：是否存在一种算法，输入正式逻辑语句，输出准确的“是”或“否”答案？
    - 图灵机：一种将人的计算行为抽象化的数学逻辑机，其更抽象的意义为一种计算模型，可以看作等价于任何有限逻辑数学过程的终极强大逻辑机器。图灵完备。图灵欺骗。
    - 停机问题是无法解决的。
    - 丘奇和图灵证明了计算是有极限的。

7. 软件工程：
    - 面向对象编程：隐藏复杂度，选择性的公布内容。对于大型程序，将函数分层打包，将相关代码放在一起组成“对象”。
    - API：Application Programming Interface 程序编程接口。用于不同团队之间合作。
    - Documentations are important.
    - 版本控制（源代码管理），QA测试。

8. 集成电路IC，印刷电路板PCB，光刻机。它们的出现是为了减少电路中的电线数量，减少分立元件的个数。计算时代3.0。 后来，超大规模集成VLSI软件用来自动生成芯片设计，计算4.0。

9. 摩尔定律。目前障碍：光波很难再变小；量子力学。

10. 操作系统：
    - 软件与硬件之间的媒介，os提供API来抽象硬件。
    - 并发执行（多任务程序）多个程序，以免CPU不断等待I/O。
    - 虚拟内存，隐藏实际物理地址，高层抽象化便于上层使用。内存分区，内存保护。
    - 分时操作系统（Multics），Bell实验室 Unix，其中Unix主要两部分，1是内核，包括内存管理，多任务，I/O处理；2是一堆有用的工具。

11. 文件系统：
    - 文件格式
    - 分层文件系统：目录+分配块，->碎片化fragmentation
