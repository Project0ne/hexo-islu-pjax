---
title: Linux安装Docker
author: 闲花手札
img: 'https://files.islu.cn/article20210522225044.jpeg'
top: false
toc: true
mathjax: false
categories: Docker
tags:
  - Docker
  - Linux
keywords: 'Docker,Linux,Linux安装Docker,Docker入门,Docker常用命令,Docker简介,Docker安装'
essay: false
summary: Linux系统安装Docker容器服务,配置阿里云镜像并使用简单命令操作Docker
abbrlink: 38496
date: 2021-05-22 22:45:06
---



# Linux系统Docker安装及软件安装

## Docker简介

Docker 是一个开源的应用容器引擎，基于 [Go 语言](https://www.runoob.com/go/go-tutorial.html) 并遵从 Apache2.0 协议开源。

Docker 可以让开发者打包他们的应用以及依赖包到一个轻量级、可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。

容器是完全使用沙箱机制，相互之间不会有任何接口（类似 iPhone 的 app）,更重要的是容器性能开销极低。

Docker 从 17.03 版本之后分为 CE（Community Edition: 社区版） 和 EE（Enterprise Edition: 企业版），我们用社区版就可以了。

## Docker安装

官方链接 [传送门](https://docs.docker.com/engine/install/centos/)

### 1、卸载旧版本

```shell
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

由于我第一次安装，运行后显示如下图

![清空docker原有组件](https://files.islu.cn//articledocker-rm-rf.png)

### 2、安装Docker

1. 安装必要的依赖包设置存储库

   ```shell
   # 安装必要依赖包
   $ sudo yum install -y yum-utils
   
   $ sudo yum-config-manager \
       --add-repo \
       https://download.docker.com/linux/centos/docker-ce.repo
   ```

2. #### 安装Docker引擎

   ```shell
   $ sudo yum install docker-ce docker-ce-cli containerd.io
   ```

   启动Docker

   ```shell
   $ sudo systemctl start docker
   ```

## Docker简单命令

### 查询Docker安装是否成功

```shell
# 使用命令查询Docker是否安装成功(查询Docker安装版本)
$ docker -v
```

![docker-v](https://files.islu.cn//articleimage-20210513165916127.png)

### 查看Docker下载的镜像

```shell
$ sudo docker images
```

![docker-image](https://files.islu.cn//articleimage-20210513165944639.png)

### 设置Docker开机自启动

```shell
$ sudo systemctl enable docker
```

![docker](https://files.islu.cn//articleimage-20210513170033264.png)

### Docker镜像加速

阿里云镜像源 [传送门](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)

登陆后，左侧菜单选中镜像加速器就可以看到你的专属地址了

```shell
$ sudo mkdir -p /etc/docker

$ sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["专属加速地址"]
}
EOF

$ sudo systemctl daemon-reload

$ sudo systemctl restart docker
```
