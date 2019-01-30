---
title: 在树莓派上配置Clash-linux
date:  2019-01-30 13:59:33 +0800
category: Tech
tags: 树莓派 Linux GFW 
excerpt: 描述了如何使用树莓派为整个局域网提供http代理来科学上网，让你的树莓派少吃点灰（大雾）。
---

## 前言

一直在折腾家里的路由器和相关网络设备，想提供一个较为完美的网络环境。之前在Phicomm K2p上通过Openwrt安装Luci-ssr-plus来进行国外ip的代理，但受限于简单的规则和K2p令人捉鸡的性能，体验不佳。因此萌生了使用树莓派搭建透明网关的想法。在查阅了为数不多的教程并踩了很多坑以后基本搭建完成，并且到目前还未出现问题，所以说说如何使用。

## 准备工作

- 树莓派
- 正常的网络连接
- 解决问题的能力

## Clash

> [Clash](https://github.com/Dreamacro/clash) is a rule-based tunnel in Go.

Clash 类似 IOS/Mac OS上的Surge，可以在提供SS/V2RAY代理的同时资瓷自定义的代理规则。



### 编译

虽然说[Clash](https://github.com/Dreamacro/clash)的项目主页说你可以通过

```
go get -u -v github.com/Dreamacro/clash
```

的方式构建，但是因为要去Google服务器上下载包而变得困难；项目主页的[预先构建](https://github.com/Dreamacro/clash/releases)并不支持ARM架构的树莓派，因此需要自行编译。

这里[@shinohara-rin](https://github.com/shinohara-rin) 构建了 Clash-arm (v0.10.2) ，[点击这里](https://transfer.sh/V5YQg/clash)下载。

### 配置

