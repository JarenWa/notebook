<div align="center">
    <h1>com.nowcoder.community 开发过程</h1>
</div>
 
<!-- TOC -->

- [问题记录](#问题记录)
    - [1 依赖配置](#1-依赖配置)
    - [2 Java HotSpot(TM) 64-Bit Server VM warning](#2-java-hotspottm-64-bit-server-vm-warning)
- [环境搭建](#环境搭建)
    - [本地文件管理](#本地文件管理)
    - [工具](#工具)
        - [Spring Framework](#spring-framework)
        - [Spring Boot](#spring-boot)
        - [开发时, 关闭 Thymeleaf 缓存](#开发时-关闭-thymeleaf-缓存)
        - [MYSQL](#mysql)

<!-- /TOC -->



# 问题记录
## 1 依赖配置
```
<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>
```
中的`<artifactId>spring-boot-maven-plugin</artifactId>`被标红

解决:默认版本号有问题，去<a href="https://mvnrepository.com/" target="_blank">仓库</a>找到正确的依赖，并添加版本号

## 2 Java HotSpot(TM) 64-Bit Server VM warning
项目启动：Java HotSpot（TM） 64 位服务器虚拟机警告：选项 -Xverify：none 和 -noverify 在 JDK 13 中已弃用，可能会在将来的发行版中删除。
Java HotSpot(TM) 64-Bit Server VM warning: Options -Xverify:none and -noverify were deprecated in JD

<a href="https://blog.csdn.net/qq_58341172/article/details/134626267" target="_blank">解决</a>



# 环境搭建
## 本地文件管理
项目文件：D:\MyGitProject\community<br>
新项目（全程git管理）改到了：
D:\MyGitProject\project0\community<br>
Maven本地仓库：D:\code\Maven\repo<br>
Maven：D:\Tools\Maven\apache-maven-3.6.3<br>
Maven的配置文件：D:\Tools\Maven\apache-maven-3.6.3\conf\settings.xml<br>
数据库的数据地址：D:\Tools\MySQL\mysql-8.0.15-winx64\data\<br>

## 工具
Maven 的plugin 插件：

spring initializr
https://start.spring.io/

Spring Initializr是一个用于快速生成Spring Boot项目的Web应用程序。它提供了一个用户友好的界面，让开发人员可以选择所需的项目配置和依赖项，然后生成一个基本的Spring Boot项目的初始结构。


Spring Boot 内有 tomcat服务器: Spring Boot 内部默认集成了 Tomcat 作为其内嵌的 Web 服务器。这意味着当你使用 Spring Boot 构建和运行 Web 应用程序时，它会自动包含 Tomcat 作为默认的 Web 服务器。


Dev Tools作用

自动编译重启等等...

<a href="https://www.wolai.com/v5Kuct5ZtPeVBk4NBUGBWF" target="_blank">尚硅谷SSM</a>

<a href="https://spring.io" target="_blank">sping</a>

### Spring Framework
Spring Core




### Spring Boot
功能：

起步依赖：pom.xml里一个配置引入一组依赖包<br>
自动配置：<br>
端点监控：上线后监视<br>




### 开发时, 关闭 Thymeleaf 缓存
在application.properties配置
spring.thymeleaf.cache=false

### MYSQL
1 配置文件my.ini拷贝到安装的根目录下

basedir为安装目录
```
[mysql]
default-character-set=utf8
[mysqld]
port=3306
basedir=D:\Tools\MySQL\mysql-8.0.15-winx64
max_connections=20
character-set-server=utf8
default-storage-engine=INNODB

```

2 配置环境变量

3 初始化 管理员身份打开命令行
```
C:\WINDOWS\system32>d:

D:\>cd D:\Tools\MySQL\mysql-8.0.15-winx64\bin

执行：
D:\Tools\MySQL\mysql-8.0.15-winx64\bin>mysqld --initialize --console
2023-12-04T08:30:06.493917Z 0 [System] [MY-013169] [Server] D:\Tools\MySQL\mysql-8.0.15-winx64\bin\mysqld.exe (mysqld 8.0.15) initializing of server in progress as process 11652
2023-12-04T08:30:06.503409Z 0 [Warning] [MY-013242] [Server] --character-set-server: 'utf8' is currently an alias for the character set UTF8MB3, but will be an alias for UTF8MB4 in a future release. Please consider using UTF8MB4 in order to be unambiguous.
2023-12-04T08:30:14.061522Z 5 [Note] [MY-010454] [Server] A temporary password is generated for root@localhost: Aj.WeM4wh!i*
2023-12-04T08:30:17.638963Z 0 [System] [MY-013170] [Server] D:\Tools\MySQL\mysql-8.0.15-winx64\bin\mysqld.exe (mysqld 8.0.15) initializing of server has completed
记录下临时密码

D:\Tools\MySQL\mysql-8.0.15-winx64\bin>mysqld install
Service successfully installed.

D:\Tools\MySQL\mysql-8.0.15-winx64\bin>net start mysql
MySQL 服务正在启动 ..
MySQL 服务已经启动成功。
```

3 普通方式打开命令行

```
mysql -uroot -p
修改密码
mysql> alter user root@localhost identified by '1234';
```

```
找数据地址：
mysql> SHOW VARIABLES LIKE 'datadir';
```






