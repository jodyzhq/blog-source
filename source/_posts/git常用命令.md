---
title: git常用命令
date: 2016-06-11 14:11:32
categories: 
  - 技术
  - Git
tags: Github

---

隔一断时间不提交代码就忘记命名了，
好记性不如敲敲键盘，做做笔记
<!-- more -->
#### 本地项目托管到github服务器 这几个常用的，先记到前面吧
git init
git add .
git commit -m "first commit"
git remote add origin https://github.com/yourId/repoName.git
git push -u origin master


生成密钥
ssh-keygen -t rsa -C "user@domain"
id_rsa 密钥
id_rsa.pub 公钥

初始化
git init

克隆
git clone [url]
会在跟目录下创建一个 .git 的文件夹

设置忽略文件
touch .gitignore  //创建一个 .gitignore 文件

添加新文件到版本库
git add .  //添加到当前目录所有文件到版本库
git add *.txt //添加当前目录下所有 txt 格式的文件到版本库
git add so mefile.txt //添加单个文件到版本库

git commit -am "本次修改内容，写上一个大概的意思" //将本次提交加入到本地环境
// branch 是版本分支名称
git pull origin [branch]  //获取服务器上最新的源码
git push origin [branch]  //将本地的 commit 推送到服务器 

检测本地文件修改状态
git status

分支管理
git branch  //查看本地分支 // 带 * 号的是当前分支名称
git branch -a  //查看所有分支
git branch -r //查看远程分支

创建分支
git branch [branchName]

切换分支
git checkout [branchName]

删除远程分支
$ git push --delete origin [branchName]

重命名本地分支
git branch -m [branchName] [new branchName]

提交
git commit -am "some msg"  //提交所有修改
git commit -m "some msg" mefile.txt  //提交单个文件

获取服务器最新数据
git pull <远程主机名> <远程分支名>
git pull origin master

推送本地最新数据到远程主机
git push <远程主机名> <远程分支名>
git push origin master

日志
git log //查看所有提交日志
git log -n  //  只显示最前面的几行日至   n 是一个正整数

显示修改的行数统计
git log --stat -n
git log -p -n      //同上，显示信息更全

合并分支

git merge master --no-ff

git merge master 

取消合并

 reset --hard HEAD

暂时保存当前分支

git stash

重置

git reset 


// git 下删除node_modules
rm -rf name



