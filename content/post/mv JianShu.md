---
title: "Move some notes from JianShu"
date: 2019-04-11 
weight: 70
keywords: ["linux","base"]
description: "Move some notes from JianShu"
tags: [ "tools"]
categories: ["Projects_SMU"]
author: "KennaNing"
---

# tmux
```markdown
brew install tmux
tmux new -s demo   新建名为demo的session
tmux a -t demo     attach
tmux d             detache
tmux ls
ctrl_b_,           修改window name
ctrl_b_c           新建window
ctrl_d             退出
```

# 关于显卡
` nvidia-smi `              查看显卡
` CUDA_VISIBLE_DEVICES=i`   指定i显卡

# virtual_env
```markdown
#用python创建
python -m venv unet_venv
source public/Unet/unet_venv/bin/activate
deactivate
# 用conda创建(fish 和 conda 不兼容)
conda create -n unet_venv python=3.6   装在默认路径
conda create --prefix=public/NingFang/unet_venv python=3.6 
source activate /public/Unet/unet_venv
deactivate
```
# path
```markdown
vim ~/.config/fish/conf.d/xxx.fish
set PATH(你想要加的路径) PATH
重启fish
```
# deb-package install
```markdown
cd xxx/xxx/
sudo dpkg -i deb_filename
发生依赖性错误时-> sudo apt-get install -f
sudo dpkg -l    查看已安装的软件
sudo dpkg -r    卸载
```
# shadowsocks
```markdown
sudo service shadowsocks status
sudo service shadowsocks start
```




