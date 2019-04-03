
---
title: "About git"
date: 2019-04-03 
weight: 70
keywords: ["branch","commit"]
description: "learning git"
tags: [ "tools"]
categories: ["projects"]
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

