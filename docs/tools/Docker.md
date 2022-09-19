# Docker

![Docker](./Docker.assets/Docker.png)

> <https://docker.easydoc.net/>

Docker 是一个应用打包，分发，部署的工具。

> <https://csdiy.wiki/%E5%BF%85%E5%AD%A6%E5%B7%A5%E5%85%B7/Docker/>

Docker 使用轻量级的“容器”（container）而不是整个操作系统去支持一个应用的配置。应用自身连同它的环境配置被打包为一个个 image 可以自由运行在不同平台的一个个 container 中，这极大地节省了所有人的时间成本。

## docker desktop安装与基本配置

[桌面版安装与基本配置：参考视频链接](https://www.bilibili.com/video/BV11L411g7U1?vd_source=9dd0fcc3d5398236875800270d02049a)

## docker安装软件或系统

[docker hub](https://hub.docker.com/) 镜像查找网站

1. 一个命令跑起来redis`docker run -d -p 6379:6379 --name redis5 redis:5.0.14`
2. 使用docker-compose命令利用yml文件进行安装配置比较复杂的软件：譬如安装wordpress
