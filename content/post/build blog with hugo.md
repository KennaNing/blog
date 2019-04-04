
---
title: "Build my blog with hugo"
date: 2019-04-04 
weight: 70
keywords: ["hugo","Travis","github"]
description: "learning own blog home"
tags: [ "experiences"]
categories: ["Projects_SMU"]
author: "KennaNing"
---

一直想找到自己喜欢的网站写自己的一些学习心得，试过onenote，简书等，onenote在linux上又只能用网页版，简书的层级布局略感粗糙，在搜寻了一阵之后，因缘巧合下得知hugo，恰好最近比较有空，就开始了又一次新的尝试。

# requirements

- [ ] Hugo
- [ ] github
- [ ] 有关git的基础知识


# About hugo

[Hugo](https://gohugo.io/)是用静态语言实现的静态网站生成器。官网有详细的安装，主题模版介绍，因为其简单，易用，高效，易部署而渐渐受到很多人的青睐。

## Install Hugo

环境：Mac 

```markdown
1. brew install hugo 
2. hugo version  #检查安装是否成功
```

## Creat a new site

```markdown
hugo new site blog  # 在blog文件夹下建一个网站
```
## check the tree categories

```markdown
tree blog   # 如果你没有安装tree，则先 brew install tree
```

## Add a theme

可以在<https://themes.gohugo.io/>选择自己喜欢的主题，本文使用简洁美观的[Leavelt themes](https://github.com/liuzc/LeaveIt)

```markdown
cd blog/themes
git init
git clone https://github.com/liuzc/LeaveIt.git
theme = "LeaveIt" # 打开config.toml 编辑文件中的theme或者使用 echo 'theme=“LeavIt” ' >> config.toml 实现相同功能
```
# Add some content

`hugo new posts/my_first_post.md`
```markdown
可以打开文章编辑内容
---                    #文章顶部的meta信息
title: "My First Post"
date: 2017-12-14T11:18:15+08:00
weight: 70
keywords: ["hugo"]
description: "第一篇文章"
tags: ["hugo", "pages"]
categories: ["pages"]
author: ""
---

这里是文章内容
```

## Start the hugo server

```markdown
▶ hugo server -D


                   | EN
+------------------+----+
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  3
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0


Total in 11 ms
Watching for changes in /Users/bep/quickstart/{content,data,layouts,static,themes}
Watching for config changes in /Users/bep/quickstart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop

```

执行命令后，可以访问 http://localhost:1313/ 查看效果

# Deploy to GitHub Pages

## github 

- 首先创建自己的guthub账号，创建两个repo，一个用来放源码repo，命名为blog，另一个用来准备发博客使用的pages repo
- 将本地的源码repo提交到github的源码repo

```markdown
git add -A
git commit -m "initial all files"
git remote add github https://github.com/<username>/blog
git push -u origin master
 ```

- 创建`<username>.github.io` repo,详情可参照 <https://pages.github.com/>
- 将 config.toml 中的`baseURL`设置为`<username>.github.io`
- 生成[Github Acess Token](https://github.com/settings/tokens/new),至少要有public_repo的权限
- 配置 Travis ：
    1. 在[Travis CI](https://travis-ci.org/)中关联自己的github账号，并激活blog repo
    2. 在blog的设置页面，除了 LImit concurrent jobs，其他的都选择ON，并把刚生成的Github Access Token 添加到环境变量
    3. `<username>.github.io`的设置页面只需要将Github Access Token 添加到环境变量
- 在blog repo 中添加 .travis.yml

```markdown
sudo: false
language: go
git:
    depth: 1
install: go get -v github.com/gohugoio/hugo
script:
    $GOPATH/bin/hugo
deploy:
    provider: pages
    skip_cleanup: true
    github_token: $GITHUB_TOKEN
    on:
        branch: master
    local_dir: public
    repo: <username>/<username>.github.io
    fqdn: <custom-domain-if-needed>
    target_branch: master
    email: <github-email>
    name: <github-username>

```


> 参考 https://gohugo.io/getting-started/quick-start/

> 参考 https://segmentfault.com/a/1190000012975914