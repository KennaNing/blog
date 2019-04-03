
---
title: "KennaNing's foot"
date: 2017-12-14T11:18:15+08:00
weight: 70
keywords: ["git"]
description: "learning git"
tags: ["hugo", "pages"]
#categories: ["pages"]
author: ""
---

# git 简介
目前世界上最先进的版本控制系统
## 创建版本库
`ls -ah` 可以看见隐藏的命令
初始化 git repo：`git init`
添加文件到 git repo：1. `git add < file >` 把文件添加到暂存区(stage)
                2. `git commit -m < message >` 把 stage 中的所有内容提交到分支(branch)
# 时光穿梭机
掌握工作区的状态：`git status`
查看修改内容：`git diff` 退出（q）
## 版本回退
查看提交历史，确定回退到哪个版本：`git log `
查看命令历史，确定回到未来哪个版本：`git reflog` 
指向当前版本 `HEAD`，指向上一百个版本： `HEAD -100`  `git reset  --hard coommit_id`
## git 的管理修改
git 跟踪并管理的是修改，并非文件，每次修改，如果不`git add` 到stage，就不会加入到`commit`中
## 撤销修改
incase you add stupid boss to your working directory,what you should do?\
1. 还未 `git add`：`git checkout --file`
2. 已 git add：`git reset HEAD <file>` 回到第一步，按第一步操作
3. 已 `git commit`:参考版本回退一节
## 删除文件
1. 删错了，版本库中还有：`git checkout -- test.txt
2. 确定删掉：`git rm test.txt` & `git commit -m 'remove test.txt'`