---
title: Docker安装Redis
author: 闲花手札
img: 'https://files.islu.cn/article/20210524190941.png'
coverImg: /images/1.jpg
toc: true
mathjax: false
categories: Docker
tags:
  - Docker
  - Redis
keywords: 'Docker安装Redis,Docker配置Redis环境,Linux虚拟机中Redis服务'
essay: false
summary: '在Docker容器中拉去Redis镜像,远程连接Redis服务'
abbrlink: 41794
date: 2021-05-24 19:06:42
---

## Docker安装Redis

Docker镜像市场 [传送门](https://hub.docker.com/_/redis)

### 安装Redis镜像

```shell
# sudo 以超级管理员权限运行命令
# docker pull 镜像名:镜像版本
# docker pull 镜像名 即不加:版本号为默认安装最新版本镜像
$ sudo docker pull redis
```

### 查询已安装的镜像

使用命令 `sudo docker images` 查询已安装的镜像

### 创建实例并启动

运行命令 `mkdir -p /mydata/redis/conf`

再运行 `touch /mydata/redis/conf/redis.conf`

运行命令实现挂载

```shell
$ sudo docker run -p 6379:6379 --name redis \
-v /mydata/redis/data:/data/log \
-v /mydata/redis/conf:/etc/redis/redis.conf \
-d redis redis-server /etc/redis/redis.conf
```

### 设置Docker中Redis开机自启动

管理员权限运行命令 (su root)

```shell
docker update redis --restart=always
```

------

### 使用Redis客户端

运行`docker ps -a` 查询运行中的容器中是否有`redis`正在运行

![查询docker容器运行中的镜像](https://files.islu.cn/article20210521171736.png)

使用命令`docker exec -it redis redis-cli` 进行客户端连接

### 使用工具RedisDesktopManager远程连接Redis

工具下载地址 [传送门](https://github.com/uglide/RedisDesktopManager/releases/tag/0.9.3)

微云下载连接 [传送门](https://share.weiyun.com/i9rfHd7U)

安装后在linux中输入 `ip addr` 查询id地址进行登录即可

