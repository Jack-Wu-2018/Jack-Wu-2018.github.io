---
title: GitHub上传大文件的方法
date: 2018-05-06
categories: [工具]
tags: [Git,GitHub]
author: 马少良 0027009163
---

## 现象描述
在使用`git`往**GitHub**`push`的单个文件大小大于**_50M_**的时候会有告警, 单个文件的大小大于**_100M_**的时候会失败

## 参考链接
* [git-lfs官方文档](https://github.com/git-lfs/git-lfs/tree/v2.4.0)
* [CSDN一个博客](https://blog.csdn.net/tyro_java/article/details/53440666)
* [如何追踪整个目录 -- StackOverflow问答](https://stackoverflow.com/questions/35769330/git-lfs-track-folder-recursively)

## 步骤如下
* 安装`git-lfs`(以**Ubuntu**为例)
```bash
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
sudo apt-get install git-lfs
```

* 配置
```bash
git lfs install
```

* 使用下边的命令增加要追踪的大文件
```bash
git lfs track *.so          # 追踪某种类型
git lfs track "myfolder/**" # 遍历追踪一个目录
```

* 使用下边命令使得上边的`track`生效
```bash
git add .gitattributes     # 执行track命令之后这个文件会自动生成
```

* 剩下的步骤和正常的_git_流程是一样的(`add/commit/push`), 可以使用下边的命令来查看使用_lfs_进行管理的文件有哪些
```bash
git lfs ls-files
```

## Notes
* **GitHub**的_lfs_每个月的下载带宽只有**1GB**, 如果上传的大文件只是为了当作一个网盘用的话可以单独建一个库，不要经常的下载
