
---
title: "About git"
date: 2019-04-03 
weight: 70
keywords: ["branch","commit"]
description: "learning git"
tags: [ "tools"]
categories: ["projects_SMU"]
author: "KennaNing"
---


# git 简介

目前世界上最先进的版本控制系统
## 创建版本库

`ls -ah` 可以看见隐藏的命令\
初始化 git repo：`git init`\
添加文件到 git repo：

1. `git add < file >` 把文件添加到暂存区(stage)
2. `git commit -m < message >` 把 stage 中的所有内容提交到分支(branch)

# 时光穿梭机

1. 掌握工作区的状态：`git status`
2. 查看修改内容：`git diff` 退出（q）

## 版本回退

1. 查看提交历史，确定回退到哪个版本：`git log `
2. 查看命令历史，确定回到未来哪个版本：`git reflog` 
3. 指向当前版本 `HEAD`，指向上一百个版本： `HEAD -100`  `git reset  --hard coommit_id`

## git 的管理修改

git 跟踪并管理的是修改，并非文件，每次修改，如果不`git add` 到stage，就不会加入到`commit`中

## 撤销修改

incase you add stupid boss to your working directory,what you should do

1. 还未 `git add`：`git checkout --file`
2. 已 git add：`git reset HEAD <file>` 回到第一步，按第一步操作
3. 已 `git commit`:参考版本回退一节

## 删除文件

1. 删错了，版本库中还有：`git checkout -- test.txt`
2. 确定删掉：`git rm test.txt` & `git commit -m 'remove test.txt'`

# 远程仓库
## 添加远程仓库

1. 关联：`git remote add origin git@server-name:path/repo-name.git`
2. push: `git push -u origin master` or `git push origin master`

## 从远程库克隆

`git clone git@github.com:michaelliao/gitskills.git`

# 分支管理
## 创建与合并分支

1. 查看分支：`git branch`
2. 创建分支：`git branch <name>`
3. 切换分支：`git checkout <name>`
4. 创建+切换分支：`git checkout -b <name> ` 
5. 合并某分支到当前分支：`git merge <name>`
6. 删除分支：`git branch -d <name>`

## 解决冲突

1. 当git无法自动合并分支时，必须首先手动解决confict，再 add，commit。
2. `git log --graph`可以看到分支合并图

## 分支管理策略

1. 实际开发中，`master`仅用来发布新版本，不能在上面干活，干活都在`dev`分支上
2. `git merge --no-ff`表示用普通模式合并，即能看出来曾经做过合并

## Bug分支

1. master有bug，但是目前仍在dev：将dev刚写的部分代码stash`git stash`，以dev分支为基础创建issue-101，debug后，merge到master,删掉`issue-101`分支
2. 回到dev，继续干活`git stash pop`

## feature 分支

1. 添加新功能，创建新分支：`git checkout -b feature-vulcan`
2. 丢弃一个未合并的分支：`git branch -D <name>`

## 多人协作

1. 查看远程库信息：`git remote -v`
2. 从本地推送分支`git push origin branch-name`，如果push失败，先`git pull`，再提交
3. 在本地创建和远程对应的分支：`git checkout -b branch-name origin/branch-name`
4. 建立本地分支和远程分支的关联：`git branch --set-upstream branch-name origin/branch-name`

## Rebase

rebase操作把本地未push的分叉提交历史整理成直线，使得查看历史提交变化时更容易

# 标签管理

标签🏷️是版本库的一个快照，跟某个commit绑定在一起

## 创建标签

1. `git tag <tagname>`用于新建一个标签，默认为`HEAD` ，也可以通过 `git log`找到你想加tag的 commit id
2. 指定标签信息:`git tag -a <tagname> -m "babalabala"`
3. 查看所有标签:`git tag`

## 操作标签

1. push本地的标签：`git push origin <tagname>`or `git push origin --tags`
2. 如果标签已推送到远程，则先删除本地标签：`git tag -d <tagname`
3. 再删除远程标签：`git push origin :refs/tags/<tagname>`

# github

如果想参与一个开源项目比如bootstrp，点Fork就在自己的账号下克隆了一个bootstrap仓库，然后从自己的账号下clone`git clone git@github.com:KennaNing/bootstrap;.git`，才能推送修改，否则没有权限。

# 码云(gitee.com)

一个本地库如何既关联码云，又关联github呢？（add时给不同的远程库加上名字）

1. `git remote rm origin`
2. `git remote add github git@github.com:KennaNing/learngit.git`
3. `git remote add gitee git@gitee.com:KennaNing/learngit.git`
3. `git remote -v`查看远程库的信息
4. 推送时：`git push github master`or `git push gitee master`

# 自定义git
## 忽略特殊文件(.gitignore)
## 配置别名

1. `git config --global alias.st status` & co,ci,br
2. 撤销修改是把暂存区的修改撤销掉（unstage），重新返回工作区，即是一个unstage操作，可以`git config --global alias.unstage reset HEAD`
3. `git config --global alias.last log -1`

# 搭建git or Gitolite
目前用不到😄



---

用了一天时间学习git，弄懂了之前自己不懂git命令时，强行cp，ts，报错时却不知道为什么，学完后感觉常用到的也就add，commit，pull，push之类，其他的一些在最开始配置好就问题不大。
这是在搭建hugo个人网站后的第一篇笔记，可能我的主题跟已往学习的markdown语法稍有不同，也花了一些时间在尝试语法，总之，学到新东西，并且在自己搭的喜欢的blog下记录，很开心，很有成就感的吖！





