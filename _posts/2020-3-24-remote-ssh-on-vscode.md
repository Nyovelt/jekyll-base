---
title: Remote-SSH:我的开发环境
date: 2020-3-24 9:00:59 +0800
category: Technology
tags: Monthly-Report
excerpt: 让surface真正好用起来
---

# Remote-SSH: 我的开发环境

Visual Studio Code 在之前发布了插件 remote-ssh 和 remote-wsl 作为vsc的远程开发套件。我目前的主力设备是HP-OMEN 2 (i5-6300HQ) 和 Surface Pro 6 (i5) 。为了用上好用的包管理器，我都是装了Arch的Windows Subsystem Linux 作为日常开发。

在最近，随着天气转暖，以及经手了几个稍微复杂的项目部署，wsl相对于cpu的占用率达到了50%左右，明显感受到了性能瓶颈，外加hyper的内存泄漏，，<del>让我周一的python 在线 quiz雪上加霜</del>。更不用说surface贫弱的性能和移动性，不适合在本地跑大项目。

在半年前我刚上大学的时候，xa学长就向我推荐了remote-ssh 。利用阿里云学生机 9.9 块的羊毛，外加原生的 linux 在编译速度上玄学的快于 windows ( 在编译TeX时，有明显的感觉 )。所以在最近我将开发环境转移到了阿里云。经过了一周的试用，我认为这是目前最适合我的使用场景的开发环境。首先，它解决了代码多设备同步的问题；其次，它分担了 surface 的压力 ；最后， surface 因此成为了我的便携式个人电脑。

## Set-UP

首先，**颜值既是生产力**。因此首先在Linux主机上安装并配置oh-my-zsh。

运行命令安装 zsh :

```shell
sudo apt install zsh
```

之后再安装 oh-my-zsh :

curl 安装 :

```shell
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

wget安装 :

```shell
sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

设置 zsh 为默认shell :

```shell
# 为root用户修改默认shell为zsh
chsh -s /bin/zsh root
# 为当前用户修改默认shell为zsh
chsh -s /bin/zsh
```

这是 oh-my-zsh 的配置文件路径: `~/.zshrc`

然后更改配置以更换主题: 

```shell
nano ~/.zshrc
```

更换主题:

```json
#如果是服务器我推荐：
ZSH_THEME="sorin"
#如果是个人电脑我推荐：
ZSH_THEME="agnoster"
# agnoster 需要安装 powerline 字体以正确显示
```



## 参考

[Oh My Zsh，安装，主题配置方法](https://zhuanlan.zhihu.com/p/35283688)