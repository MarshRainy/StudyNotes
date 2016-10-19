# Git原理

---

## 前面的话

本文摘自git官方文档. 参考: [Git-Book](https://git-scm.com/book/zh/v2 "https://git-scm.com/book/zh/v2")

## 简述

### 分布式版本控制

客户端提取的是所有的代码库

### git描述

git对待数据更像是一个快照流. 每一个版本都对应各个文件的一个版本, 而不是保存的增量. 所以git系统跟像是一个小型文件系统.

因为git仓库在本地, 所以很多操作都可以在本地进行.

git以SHA-1散列值(hash值)作为内容的引用. 是个40位的十六进制字符.

只要将数据添加到git中, 数据很难丢失.

### git三种状态

所有文件都处于以下三种状态: 已提交(committed), 已修改(modified), 已暂存(staged). 已提交表明已经保存到本地数据库中, 已修改表示修改了文件, 但还没保存到数据库. 已暂存表示对已修改的文件的当前版本做了标记, 使之可以在下次提交时提交.

由此, git中存在三个区域: Git仓库, 工作目录, 暂存区域.

基本工作流程如下:

-   在工作目录中修改文件
-   暂存文件, 将文件快照放入暂存区域
-   提交更新, 快照永久存储到git仓库目录

### 安装

自己想法吧.

### git配置

可以使用命令`git config`来控制git的外观和行为. 这些变量存储的位置如下:

-   /etc/gitconfig. 带有参数`-- system`选项读写此文件.
-   ~/.gitconfig 或 ~/.config/git/config. 只针对当前用户. 带有参数`-- global`选项读写此文件.
-   当前使用仓库的目录中的config文件(.git/config). 针对此仓库.

在windows系统中, Git会查找$HOME目录下(一般情况下是 C:\Users\$USER)的.gitconfig文件. Git同样也会寻找/etc/gitconfig文件, 但只限于MSys的根目录下,即安装Git时所选的目标位置. 

### 用户信息

```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

### 文本编辑器

```
$ git config --global core.editor emacs
```

### 检查配置

检查所有配置

```
$ git config --list
```

检查某一项配置

```
$ git config <key>
```

### 获取帮助

```
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
```

## git基础

状态转移图:
![状态转移图](./source/StatusChange.png)

### 获取一个仓库

可以初始化一个仓库

进入一个目录执行初始化

```
$ git init 
```

可以克隆现有仓库

URL可以是`https://`协议, 也可以是`git://`协议, 也可以是SSH传输协议. name字段可以没有.

```
$ git clone [url] [name]
```

### 记录每次更新到仓库

工作目录下所有的文件都有两种状态: 已跟踪或未跟踪. 进入跟踪状态的文件有三种状态: 已提交, 已修改, 已暂存. 已提交和未修改意义是一样的.

查看哪些文件处于什么状态

```
$ git status # 状态
$ git status -s # 状态简览
```

暂存已修改的文件

```
$ git add <file>
```


