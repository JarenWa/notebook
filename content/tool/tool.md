<p align="center">
   <a style="font-size:30px;"> 常用工具 </a>

</p>

# Apache Maven
Maven 是一个项目管理（统一文件结构）和构建（标准化构建流程）自动化工具，能够管理项目所有的 jar 包（仓库），并解决 jar 包的冲突问题（依赖传递）

## 生命周期

**它的构建过程是通过生命周期（Lifecycle）来管理的**。Maven 的生命周期由多个阶段（Phase）组成，每个阶段执行特定的任务。以下是 Maven 生命周期中各个键的含义：

- **clean**：这用于清理项目，删除上次构建生成的文件。
- **validate**：验证项目是否正确且所有必要的信息是否可用。
- **compile**：编译项目的源代码。
- **test**：使用适当的单元测试框架测试编译后的代码。
- **package**：将编译后的代码打包成可分发格式，如 JAR、WAR 等。
- **verify**：运行任何检查以验证包的有效性和完整性。
- **install**：将包安装到本地 Maven 仓库，以便其他项目可以使用。
- **site**：用于生成项目的站点文档。
- **deploy**：将最终的包复制到远程仓库，以便其他开发人员可以共享。

命令：
```bash
mvn clean
```

## 创建项目

### 用命令创建 maven 脚手架
```bash
mvn archetype:generate
```
groupId：（坐标）（项目包名）
artifactId：项目名称


### 在 idea 创建

# Git
> [Git 详解](https://pdai.tech/md/devops/tool/tool-git.html)

本地 Git 配置
```bash
查看
git config --global user.name
设置
git config --global user.name "Git 用户名"
git config --global user.email "xx@example.com"
```
配置 SSH 密钥
```bash
查看
ls -al ~/.ssh

确保您有一个 SSH 密钥文件（如 id_rsa 和 id_rsa.pub）。
cat ~/.ssh/id_rsa.pub

如果没有，生成 SSH 密钥
ssh-keygen -t rsa -b 4096 -C "xx@example.com"

如果您没有将公钥添加到 Git 账户，您需要复制公钥并将其添加到 Git，Settings > SSH and GPG keys，然后添加新密钥。
```

```bash
进入目录
git init
git add .
git commit -m "log"
git branch -M main
git remote add origin {url}
git push -u origin main
```

```bash
查看现有的远程仓库
git remote -v
这将列出所有远程仓库及其对应的 URL。

修改现有的远程仓库 URL
git remote set-url origin <新的远程仓库 URL>

删除现有的远程仓 origin 
git remote remove origin

添加新的远程仓库：
git remote add origin <新的远程仓库 URL>

使用不同的远程名称，如果您希望保留现有的 origin 并添加另一个远程仓库，可以使用不同的名称。例如：
git remote add upstream <新的远程仓库 URL>
这样，您就可以同时使用 origin 和 upstream
```

<br>

# npm
> [npm 使用介绍](https://www.runoob.com/nodejs/nodejs-npm.html)

<br>

# Mysql
[MySql错误 1251 - Client does not support authentication protocol requested by server 解决方案](https://blog.csdn.net/OCEAN_C/article/details/89719578)


如何查看自己本地是否装了redis

打开终端窗口（命令行窗口）。
输入以下命令来检查Redis是否已安装并运行： redis-cli ping 如果返回 "PONG"，说明Redis已经安装并运行。

<https://blog.51cto.com/u_16175504/6864238>




工具类：dbutils 是数据库简化技术  

框架-（有jar包，配置文件-（可定制化））：log4j ：日志输出技术  .info()  .error()