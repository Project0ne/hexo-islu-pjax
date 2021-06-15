---
title: Maven课堂笔记
author: BufferC
img: 'https://files.islu.cn/article/20210605231219.png'
top: false
toc: true
mathjax: false
categories: Maven
tags:
  - Maven
keywords: 'Maven,Maven入门,Maven配置命令'
essay: false
summary: 'Maven的入门介绍、环境配置及开发工具创建Maven项目,Maven的操作及Maven中的pom.xml配置文件'
abbrlink: 48247
date: 2021-06-05 23:14:58
---

![](https://files.islu.cn/article/20210605231219.png)



## Maven

### 概述

#### 简介

Apache Maven 是一个软件项目管理和依赖管理工具。基于项目对象模型 (POM：Project Object Model) 的概念，Maven 可以从一个中心信息块管理项目的构建、报告和文档。

无论是小型的开源类库项目，还是大型的企业级应用;无论是传统的瀑布式开发，还是流行的敏捷开发，Maven都能大显身手。

>官方网址
>
>```http
>http://maven.apache.org/
>```

#### 核心功能【重点】

>1. 依赖管理（依赖管理指的就是使用 Maven 来管理项目中使用到的 jar 包，Maven 管理的方式就是“自动下载项目所需要的jar包，统一管理jar包之间的依赖关系)
>2. 项目构建（清理、编译、单元测试、打包、安装、部署、运行）
>3. 约定大于配置，解决不同的ide文件目录不一致的问题

### Maven 环境配置

#### 下载 Maven

```http
http://maven.apache.org/download.cgi
```

![](https://files.islu.cn/article/20210605230835.png)

#### Maven 库目录

>【注意】不要在中文路径下解压

| 目录                                | 描述                                   |
| ----------------------------------- | -------------------------------------- |
| bin                                 | 包含 mvn 的一些可执行程序              |
| boot                                | 包含 plexus-classworlds 类加载器的框架 |
| config                              | 包含 settings.xml 在内的配置文件       |
| lib                                 | Maven 运行时所需要的 Java 类库         |
| LICENSE.txt、NOTICE.txt、README.txt | 简要介绍                               |

#### 配置 Maven 环境变量

1、此电脑[右键] --> 属性

![](https://files.islu.cn/article/20210605230812.png)

2、选择高级系统设置

![](https://files.islu.cn/article/20210605230841.png)

3、选择高级下面的环境变量

![](https://files.islu.cn/article/20210605230846.png)

4、找到系统变量下的 Path

![](https://files.islu.cn/article/20210605230854.png)

5、将 Maven 的 bin 目录添加到环境变量中，点击确定

![image-20210106120942322](https://files.islu.cn/article/20210605230901.png)

6、一路确定即可

#### 配置 Maven 仓库

Maven 使用仓库管理各种 jar 包和插件。

Maven 仓库分为：本地仓库（local）、远程仓库（remote）两大类

##### 本地仓库

> 本地电脑中的仓库。默认位置为：
>
> ```
> ${user:home}/.m2/repository
> ```
>
> 【注意】一般需要修改此位置为非C盘

##### 远程仓库

远程仓库又包括：中央仓库 + 私服 + 其它公共远程仓库 （比如阿里、163等）

###### 中央仓库

中央仓库是maven自带的远程仓库，默认地址：https://repo.maven.apache.org/maven2，由于默认中央仓库的服务器在国外，下载会比较慢，一般需要配置使用国内的公共远程仓库作为中央仓库镜像。注意配置了中央仓库镜像就不再走默认中央仓库。。

###### 私服

私服是架设在本机或者局域网中的一种特殊的远程仓库，通过私服可以方便的管理其它所有的外部远程仓库。

- 节省自己的外网带宽
- 加速maven构建
- 部署第三方控件
- 提高稳定性
- 降低中央仓库的负荷

##### 修改配置

在 maven 的 conf 目录中找到 settings.xml 文件

```xml
<!--第一个位置在根节点settings下添加本地仓库位置-->
<localRepository>F:/m2/repository</localRepository>

<!--第二个位置，在mirrors节点下添加 中央仓库镜像-->
<mirror>
	<id>alimaven</id>
	<name>aliyun maven</name>
    <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
	<mirrorOf>central</mirrorOf>
</mirror>

<!--第三个位置，在 profiles 节点下添加 jdk 版本全局配置，因为默认为1.5-->
<profile>
    <id>jdk-1.8</id>
    <activation>
    	<activeByDefault>true</activeByDefault>
    	<jdk>1.8</jdk>
    </activation>
    <properties>
   		<maven.compiler.source>1.8</maven.compiler.source>
    	<maven.compiler.target>1.8</maven.compiler.target>
    	<maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
    </properties>
</profile>
```

检索顺序：先检索本地仓库 --> 再检索远程公共仓库 --> 最后检索中央仓库

![](https://files.islu.cn/article/20210605231523.png)

### Maven入门

#### Maven 程序目录结构

> 约定大于配置：能使用约定好的方式，就不要配置。

##### 手动创建目录结构：

```
maven_project_name
	--src
		--main
			--java
				--com
					--fc
						Hello.java
			--resources
			--webapp
				--WEB-INF
					--web.xml
		--test
	--pom.xml
```

目录说明

| 参数               | 描述                  |
| ------------------ | --------------------- |
| maven_project_name | maven 项目名          |
| src                | java 源文件目录       |
| main               | 项目主体目录          |
| java               | 源代码目录            |
| resources          | 资源目录              |
| webapp             | web 项目目录          |
| test               | 项目测试目录          |
| pom.xml            | maven项目核心配置文件 |

pom.xml 配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!--组织id：公司名-->
    <groupId>com.fc</groupId>
    <!--项目名或者模块名-->
    <artifactId>testmaven</artifactId>
    <version>1.0-SNAPSHOT</version>
    <!--打包形式 jar包-->
    <packaging>jar</packaging>
    <!--依赖-->
    <dependencies>
        <!--junit单元测试-->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```

##### 使用命令创建（了解）

```
mvn archetype:generate -DgroupId=com.qf.maven -DartifactId=maven02 -DinteractiveMode=false -DarchetypeCatalog=internal
```

#### Maven常见命令

Maven 的另一个核心功能是项目构建。

构建包括：清理、编译、测试、打包、安装、部署、运行等。这些过程都可以使用Maven命令来完成。

每个maven命令都可以通过对应的插件来完成。

##### clean

```cmd
// 清理（删除）编译的文件
mvn clean
```

> 使用插件
>
> ```
> maven-clean-plugin:2.5:clean
> ```

##### compile

```cmd
// 编译主目录的文件
mvn compile
```

>使用插件
>
>```
>maven-resources-plugin:2.6:resources
>maven-compiler-plugin:3.1:compile
>```

##### test

```cmd
// 编译并运行test目录的代码
mvn test
```

>使用插件
>
>```
>maven-resources-plugin:2.6:resources
>maven-compiler-plugin:3.1:compile
>maven-resources-plugin:2.6:testResources
>maven-compiler-plugin:3.1:testCompile
>maven-surefire-plugin:2.12.4:test
>```

##### package

```cmd
// 打包项目,jar包或war包
mvn package
```

>使用插件
>
>```
>maven-resources-plugin:2.6:resources
>maven-compiler-plugin:3.1:compile
>maven-resources-plugin:2.6:testResources
>maven-compiler-plugin:3.1:testCompile
>maven-surefire-plugin:2.12.4:test
>maven-jar-plugin:2.4:jar
>```

##### install

```cmd
// 安装到仓库
mvn install
```

>使用插件
>
>```
>maven-resources-plugin:2.6:resources
>maven-compiler-plugin:3.1:compile
>maven-resources-plugin:2.6:testResources
>maven-compiler-plugin:3.1:testCompile
>maven-surefire-plugin:2.12.4:test
>maven-jar-plugin:2.4:jar
>maven-install-plugin:2.4:install
>```

##### 其他命令

```cmd
// 部署，部署到私服
mvn deploy

// 运行
mvn tomcat:run
```

#### Maven 构建生命周期

```
1. Clean：项目构建前的清理操作
2. Default（Build）：核心生命周期核心过程：编译，测试，运行，打包等等
3. Site：项目站点文档创建。
```

#### Maven POM 文件

>POM( Project Object Model，项目对象模型 ) 是 Maven 工程的基本工作单元。pom.xml是Maven的核心配置文件，包含了项目的基本信息，用于描述项目如何构建，声明项目的 jar 包依赖等等。
>
>每一个项目都有一个 POM 文件。POM 文件即 pom.xml，应该放在项目的根目录下。一个项目如果分为多个子项目，一般来讲，父项目有一个 POM 文件，每一个子项目都有一个POM文件。在这种结构下，既可以一步构建整个项目，也可以各个子项目分开构建。
>
>执行任务或目标时，Maven 会在当前目录中查找 POM。它读取 POM，获取所需的配置信息，然后执行目标。
>
>POM 中可以指定以下配置：
>
>- 项目依赖
>- 插件
>- 执行目标
>- 项目构建 profile
>- 项目版本
>- 项目开发者列表
>- 相关邮件列表信息

基本的 pom.xml 配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!--组织id：公司名-->
    <groupId>com.fc</groupId>
    <!--项目名或者模块名-->
    <artifactId>testmaven</artifactId>
    <!--版本号-->
    <version>1.0-SNAPSHOT</version>
    <!--打包形式 jar包-->
    <packaging>jar</packaging>

</project>
```

 >【注意】所有 POM 文件都需要 project 元素和三个必需的标签：groupId，artifactId，version。这个必须元素叫做坐标（GAV）

#### Maven 引入外部依赖

>Maven 仓库
>
>```http
>https://mvnrepository.com/
>```

引入多个依赖只需在 dependencies 标签下声明对应的 dependency 标签即可

```xml
<!--依赖-->
<dependencies>
    <!--junit单元测试-->
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```

>【注意】Scope依赖范围：
>
>- compile（编译范围） compile是默认的范围，会被打包。 
>- provided（已提供范围） provided依赖只有在当JDK或者一个容器已提供该依赖之后才使用。它们不是传递性的，也不会被打包。
>- runtime（运行时范围） runtime依赖在运行和测试系统的时候需要，但在编译的时候不需要。
>- test（测试范围）只有在测试编译和测试运行阶段可用。
>- system（系统范围）必须显式的提供一个对于本地系统中JAR文件的路径。注意该范围是不推荐使用。

### 使用开发工具创建Maven项目

#### Eclipse配置Maven（了解）

1. 安装插件

   Eclipse使用Maven的前提要安装m2e插件，目前Eclipse已集成，不需要安装。

2. 配置Maven

   1、进入首选项

   ![](https://files.islu.cn/article/20210605230924.png)

   2、添加 Maven 仓库

   ![](https://files.islu.cn/article/20210605230929.png)

   3、配置 Maven

   ![](https://files.islu.cn/article/20210605230933.png)

   4、配置 xml 文件

   ![](https://files.islu.cn/article/20210605230938.png)

3. Eclipse 创建 Maven 工程

   ![](https://files.islu.cn/article/20210605230943.png)

   ![](https://files.islu.cn/article/20210605230951.png)

#### Idea配置Maven

1. 安装插件

   Idea 自带 Maven 插件，不需要安装

2. 配置Maven

   ![](https://files.islu.cn/article/20210605230956.png)

   ![](https://files.islu.cn/article/20210605231000.png)

   ![](https://files.islu.cn/article/20210605231006.png)

3. Idea创建Maven工程

   1、创建项目

   ![](https://files.islu.cn/article/20210605231011.png)

   2、选择 Maven

   ![](https://files.islu.cn/article/20210605231015.png)

   >【注意】这里不要使用骨架！

   3、声明项目名

   ![](https://files.islu.cn/article/20210605231021.png)

   4、选择项目的存放路径

   ![](https://files.islu.cn/article/20210605231027.png)

### 在 Maven 项目中使用 Web 组件

1、选中 main

![](https://files.islu.cn/article/20210605231032.png)

2、点击打开文件下的项目架构

![](https://files.islu.cn/article/20210605231039.png)

3、选择模板，添加 Web 组件

![](https://files.islu.cn/article/20210605231044.png)

4、修改部署路径

![](https://files.islu.cn/article/20210605231048.png)

5、注意此路径为 web.xml 的存放路径

![](https://files.islu.cn/article/20210605231054.png)

6、将 web.xml 的路径放在项目下的 src 下的 main 下的 webapp 下的 WEB-INF 下即可

![](https://files.islu.cn/article/20210605231116.png)

7、点击编辑 Web 资源路径

![](https://files.islu.cn/article/20210605231119.png)

8、选择目录

![](https://files.islu.cn/article/20210605231124.png)

9、选择 main 下面的 webapp 目录

![](https://files.islu.cn/article/20210605231128.png)

10、点击 OK

![](https://files.islu.cn/article/20210605231132.png)

11、打开 pom.xml 文件并添加打包方式为 war

![](https://files.islu.cn/article/20210605231138.png)

```xml
<packaging>war</packaging>
```

12、添加 Servlet-api 的 jar 包依赖

![](https://files.islu.cn/article/20210605231143.png)

```xml
<dependencies>
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>3.1.0</version>
        <!--声明此jar包的作用域为编译期-->
        <scope>provided</scope>
    </dependency>
</dependencies>
```

>【注意】必须声明作用域，否则会报错！

13、添加 Tomcat 插件

![](https://files.islu.cn/article/20210605231149.png)

```xml
<build>
    <!--添加插件-->
    <plugins>
        <!--添加Tomcat插件-->
        <plugin>
            <groupId>org.apache.tomcat.maven</groupId>
            <artifactId>tomcat7-maven-plugin</artifactId>
            <version>2.2</version>
            <!--Tomcat相关配置-->
            <configuration>
                <port>8080</port>
                <!--编码集-->
                <uriEncoding>UTF-8</uriEncoding>
                <!--访问路径-->
                <path>/testMaven</path>
            </configuration>
        </plugin>
    </plugins>
</build>
```

>【注意】此方法使用 Maven 自带 Tomcat 插件，也可以使用本地 Tomcat

14、启动 Tomcat 服务器

![](https://files.islu.cn/article/20210605231157.png)

>【注意】不要反复启动 Tomcat 服务器

### Maven Web 项目结构

![](https://files.islu.cn/article/20210605231203.png)

### Maven 操作

![](https://files.islu.cn/article/20210605231208.png)

### pom.xml 配置文件【重点】

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.fc</groupId>
    <artifactId>maven_project</artifactId>
    <version>1.0-SNAPSHOT</version>
    <!--因为是web项目，所以打包方式声明为war-->
    <packaging>war</packaging>

    <!--添加jar包依赖-->
    <dependencies>
        <!--Servlet-api-->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>3.1.0</version>
            <!--声明此jar包的作用域为编译期-->
            <scope>provided</scope>
        </dependency>
    </dependencies>

    <build>
        <!--添加插件-->
        <plugins>
            <!--添加Tomcat插件-->
            <plugin>
                <groupId>org.apache.tomcat.maven</groupId>
                <artifactId>tomcat7-maven-plugin</artifactId>
                <version>2.2</version>
                <!--Tomcat相关配置-->
                <configuration>
                    <!--端口-->
                    <port>8080</port>
                    <!--编码集-->
                    <uriEncoding>UTF-8</uriEncoding>
                    <!--访问路径-->
                    <path>/testMaven</path>
                </configuration>
            </plugin>
        </plugins>
        
        <resources>
            <!--需要设置打包的文件 特别是非java文件-->
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.xml</include>
                    <include>**/*.properties</include>
                </includes>
            </resource>
        </resources>
    </build>
</project>
```

>【注意】使用时直接复制粘贴，修改groupId、artifactId、path等参数即可

### Maven 相关命令【了解】

| 命令                | 描述                                                   |
| ------------------- | ------------------------------------------------------ |
| mvn version         | 显示当前版本信息                                       |
| mvn compile         | 编译源代码                                             |
| mvn test-compile    | 编译测试代码                                           |
| mvn test            | 运行测试                                               |
| mvn site            | 生成site                                               |
| mvn eclipse:eclipse | 生成eclipse项目                                        |
| mvn idea:idea       | 生成idea项目                                           |
| mvn clean           | 清除产生的项目                                         |
| mvn package         | 打包                                                   |
| mvn jar:jar         | 只打jar包                                              |
| mvn source:jar      | 源码打包                                               |
| mvn tomcat7:run     | 在tomcat容器中运行web应用                              |
| mvn jetty:run       | 调用Jetty插件的Run目标在Jetty Servlet容器中启动web应用 |

