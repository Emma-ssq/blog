# 打开远程服务器端的tensorboard

> <https://blog.csdn.net/Leon1997726/article/details/118498462>

1. 远程端启动tensorboard并指定端口, **注意必须在log文件夹的上一级**，`tensorboard --logdir ./ --port 6006`
2. 本地端ssh远程连接服务器，`ssh -p 35009 -L 16006:127.0.0.1:6006 sunshuqing@202.38.88.88`，其中16006制定了本地端口
3. 本地浏览器输入 <http://127.0.0.1:16006/> 即可访问tensorboard
