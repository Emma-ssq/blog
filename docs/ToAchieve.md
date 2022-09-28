# ToAchieve

- [Missing semester](<https://missing-semester-cn.github.io/2020/security/>)的github仓库 以及[授课老师的仓库](<https://github.com/jonhoo/flurry>)，非常整洁有序，徽章，readme，license， github actions等等，非常适合精读，学习如何写一个项目的代码仓库。寻找关于编写github仓库的CI服务譬如Jekyll
- **什么？光实现一个 Git 无法满足你？小伙子/小仙女有前途，巧的是我也喜欢造轮子，这两个 GitHub 项目 build-your-own-x 和 project-based-learning 收录了你能想到的各种造轮子教程，比如：自己造个编辑器、自己写个虚拟机、自己写个 docker、自己写个 TCP 等等等等**。

- ubuntu新建用户：
  - <https://blog.csdn.net/timothy93bp/article/details/77679000>
  - <https://101.lug.ustc.edu.cn/Ch05/#adduser>

- github徽章badge：
    1. [项目徽标](https://zhuanlan.zhihu.com/p/85370228)
    2. <https://blog.csdn.net/terrychinaz/article/details/115706200>

- curl baidu.com ====  curl: (6) Could not resolve host: www.baidu.com
  - 配置dns，宿主机与容器保持一致, vim /etc/resolv.conf, [配置dns](https://www.jianshu.com/p/179a2a67cab6)

- sudo apt-get install pip === E: Unable to locate package pip
  - 更新apt-get index库：
        1. sudo apt-get update, 出现error：Err:5 <https://mirrors.tuna.tsinghua.edu.cn/ubuntu> xenial InRelease
    Could not connect to mirrors.tuna.tsinghua.edu.cn:443 (101.6.15.130), connection timed out
            - 修改镜像源: sudo vim /etc/apt/sources.list, 删除不可使用的镜像源
    **目前未解决,打算系统学习docker,待解决问题：在docker镜像中无法实现pip安装，猜测原因如下：**
  - 可能情况一：宿主机与镜像中的dns服务，/etc/resolv.conf，网卡指定，重启镜像
  - 可能情况二：和pip版本有关，最好设置为20.
