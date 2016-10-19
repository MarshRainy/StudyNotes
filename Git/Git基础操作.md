# Git基础操作

---

## 前面的话

本文档只列举并简单解释一些命令的作用.

## 全局操作

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
$ man git-<verb> # windows中貌似不行
```
