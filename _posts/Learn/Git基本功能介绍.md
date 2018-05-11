---
title: Git基本功能介绍
date: 2018-04-24 16:45:22
categories: [工具]
tags: [Git]
author: 马少良 0027009163
---

## 相关链接
* [廖雪峰的Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
* [Git官网](https://git-scm.com/)
* [TortoiseGit工具下载](https://tortoisegit.org/)

## Git v.s. SVN
* Git/SVN都是常用的版本控制工具, Git相对于SVN来说最大的特色是**去中心化**, 去中心化的结果最大的好处是提交的话可以**不依赖于网络**, 即`commit`时提交在本地, 不在需要一个中心服务器
* Git借助于开源大趋势有很多出名的基于Web的管理平台, 最出名的是[Github](https://github.com/)和[Gitlab](https://about.gitlab.com/)平台, 还有[码云](https://gitee.com/), SVN好像没有很出名的平台
* Gitlab相对于Github来说增加了CI的远程支持, Github则需要借助于第三方的平台

## 为什么选择Git
* 其实对于基本的功能Git和SVN都差不多, Git是开源时代的产物, 还是Linux之父Linus的作品, 用的人比较多, 很多开发工具也原生对Git进行了支持
* Git在打分支时很快, 和SVN对比，就相当于C++中指针和对象的区别
* 方便的Web管理平台, 操作方便, 使用门槛低

## Git安装
* Linux
```bash
sudo apt-get install git   # ubuntu
sudo yum install git       # CentOS
```

* Windows
按照最上边的链接在git官网下载git安装即可, 注意官网安装的没有像TortoiseSVN那种方便的图形界面工具, 安装了官网的git工具之后可以安装TortoiseGit工具

## Git常用概念
* Git工作区, 对应于本地文件
* Git暂存区stage/index, Git多了一个正式commit之前可以保存的暂存区, 对应`git add`命令(不同于`svn add`, svn只是标记受控, git是每次修改都需要add)
* Git远程库, 使用版本控制只在本地用的情况很少, 这是就用到了类似于SVN服务器的的远程库, 对应于`git clone`, `git pull`, `git push`等命令

## git常用命令
* 安装之后的必备配置
```bash
ssh-keygen -t rsa -C "youremail@example.com" # 生成密钥, 用于远程库权限验证, SVN的权限管理比Git要更精准一点
git config --global user.name "Your name"
git config --global user.email "Your email"
git config --global core.editor vim
```

* 基本操作命令
```bash
git init
git clone
git add
git commit -m "commit message"
git pull
git push
git log
```

* 配置查看及删除
```bash
git config --list   # view all configurations
git config <key>    # view specific configuration
git config --global --unset http.proxy
```

* 设置别名
```bash
git config --global alias.st status
git config --global alias.last 'log -1 HEAD'
```

* 设置多个远程repo
```bash
git remote set-url --add --push origin git://original/repo.git
git remote set-url --add --push origin git://another/repo.git
git remote -v
```

* .gitignore中添加一些已经在库里的文件
```bash
git rm --cached file_name_not_ignored_by_gitignore
```

* git设置socks5代理
[参考这个链接进行设置](http://www.afox.cc/archives/404)
