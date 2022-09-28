[toc]

# Docker

![Docker](./Docker.assets/Docker.png)

> <https://docker.easydoc.net/>

Docker 是一个应用打包，分发，部署的工具。

> <https://csdiy.wiki/%E5%BF%85%E5%AD%A6%E5%B7%A5%E5%85%B7/Docker/>

Docker 使用轻量级的“容器”（container）而不是整个操作系统去支持一个应用的配置。应用自身连同它的环境配置被打包为一个个 image 可以自由运行在不同平台的一个个 container 中，这极大地节省了所有人的时间成本。

## docker快速入门

> [Docker 1小时快速上手教程，无废话纯干货](https://www.bilibili.com/video/BV11L411g7U1?vd_source=9dd0fcc3d5398236875800270d02049a)

### docker desktop安装与基本配置

[Docker 1小时快速上手教程，无废话纯干货](https://www.bilibili.com/video/BV11L411g7U1?vd_source=9dd0fcc3d5398236875800270d02049a)

### docker安装软件或系统

[docker hub](https://hub.docker.com/) 镜像查找网站

1. 一个命令跑起来redis：`docker run -d -p 6379:6379 --name redis5 redis:5.0.14`
2. 使用docker-compose命令利用yml文件进行安装配置比较复杂的软件：譬如安装wordpress

### 制作自己的镜像

1. **编写Dockerfile文件**。

   ```dockerfile
   FROM node:11
   MAINTAINER easydoc.net
   
   # 复制代码
   ADD . /app
   
   # 设置容器启动后的默认运行目录
   WORKDIR /app
   
   # 运行命令，安装依赖
   # RUN 命令可以有多个，但是可以用 && 连接多个命令来减少层级。
   # 例如 RUN npm install && cd /app && mkdir logs
   RUN npm install --registry=https://registry.npm.taobao.org
   
   # CMD 指令只能一个，是容器启动后执行的命令，算是程序的入口。
   # 如果还需要运行其他命令可以用 && 连接，也可以写成一个shell脚本去执行。
   # 例如 CMD cd /app && ./start.sh
   CMD node app.js
   ```

2. **Build**

   - 编译 `docker build -t test:v1 .`，`-t` 设置镜像名字和版本号。

   - 运行 `docker run -p 8080:8080 --name test-hello test:v1`

     ```bash
     -p 宿主机端口:容器端口
     --name 容器名称 拉取镜像名称以及版本
     ```

### 更多相关命令

`docker ps` 查看当前运行中的容器
`docker images` 查看镜像列表
`docker rm container-id` 删除指定 id 的容器
`docker stop/start container-id` 停止/启动指定 id 的容器
`docker rmi image-id` 删除指定 id 的镜像
`docker volume ls` 查看 volume 列表
`docker network ls` 查看网络列表

### 目录挂载

**现存问题**

- 使用 Docker 运行后，我们改了项目代码不会立刻生效，需要重新`build`和`run`，很是麻烦。
- 容器里面产生的数据，例如 log 文件，数据库备份文件，容器删除后就丢失了。

挂载：

1. **bind mount挂载方式**：`-v 宿主机绝对路径:容器路径`

- ```bash
  run -p 8080:8080 --name test-hello -v C:\Users\sunsh\Desktop\CS\test-docker:/app -d test_docker:v1
  ```

- 别忘了可能需要restart 容器

2. **volume方式**，只需要一个名字，容器决定创建在宿主机里，所以删除容器后不会丢失，linux系统官方推荐。`-v 文件夹名称:容器路径`

### 多容器通信

### docker-compose

### 发布和部署

阿里云，自己的仓库，发布部署

### 数据的备份和迁移

### 待续

## [USTC lug](https://101.lug.ustc.edu.cn/Ch08/)
