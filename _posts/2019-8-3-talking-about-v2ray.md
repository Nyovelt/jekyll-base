---
title: 也谈科学上网
date: 2019-08-04 21:09:35 +0800
category: Technology
tags: GFW Linux
excerpt: 这条线路又双叒叕挂了
---



### 前言
​			关于科学上网，网上的教程已经数不胜数了。从之前的SS,SSR一键脚本再到如今新兴的V2ray。俺也从原本的GoAgent到赛风再到自建再到机场一步步摸爬滚打了过来。在这里谈一谈俺的看法。



### CAUTION

- 本文具有时效性



### 为什么选择V2ray

​				评判科学上网的好坏有很多因素，延迟、速度、稳定。用到现在发现稳定其实是最重要的。在一年一度的儿童节来临之际，V2ray出人意料的坚挺，而且V2ray有很多新的特性。~~反观SS\SSR，在破娃退坑之后几乎没有新变化~~。墙会检测大流量的，通往境外的加密流量，我认为V2ray的Websocket+TLS能起到一定的伪装作用，在一定程度上避免QOS，~~虽然提速可能比较慢~~。



### 配置

俺比较懒，使用了[233boy](https://github.com/233boy)的一键脚本。

首先运行命令**（以root模式运行）**

```shell
	sudo su
	bash <(curl -s -L https://git.io/v2ray.sh)
```
接着会出现

  ```shell
    ........... V2Ray 一键安装脚本 & 管理脚本 by 233v2.com ..........
    
    帮助说明: https://233v2.com/post/1/
    
    搭建教程: https://233v2.com/post/2/
    
    1. 安装
    2. 卸载
  ```



