# ToAchieve

- apt更改镜像源地址为科大:<https://mirrors.ustc.edu.cn/help/>
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

1. 'argon2:$argon2id$v=19$m=10240,t=10,p=8$5TryX3M8CARFhZkNiSjAtw$E+jvRI4zGeKKjW+2FnEKIdx7F1yv3xLLirrJnodIK7I'
2. /home/sunshuqing/.jupyter/jupyter_notebook_config.py
3. ssh -p 35009 -L 8888:127.0.0.1:8888 sunshuqing@202.38.88.88
4. 