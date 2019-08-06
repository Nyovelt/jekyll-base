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

显然选择1

```shell
请选择 V2Ray 传输协议 [1-32]

1. TCP
2. TCP_HTTP
3. WebSocket
4. WebSocket + TLS
5. HTTP/2
6. mKCP
7. mKCP_utp
8. mKCP_srtp
9. mKCP_wechat-video
10. mKCP_dtls
11. mKCP_wireguard
12. QUIC
13. QUIC_utp
14. QUIC_srtp
15. QUIC_wechat-video
16. QUIC_dtls
17. QUIC_wireguard
18. TCP_dynamicPort
19. TCP_HTTP_dynamicPort
20. WebSocket_dynamicPort
21. mKCP_dynamicPort
22. mKCP_utp_dynamicPort
23. mKCP_srtp_dynamicPort
24. mKCP_wechat-video_dynamicPort
25. mKCP_dtls_dynamicPort
26. mKCP_wireguard_dynamicPort
27. QUIC_dynamicPort
28. QUIC_utp_dynamicPort
29. QUIC_srtp_dynamicPort
30. QUIC_wechat-video_dynamicPort
31. QUIC_dtls_dynamicPort
32. QUIC_wireguard_dynamicPort

备注1: 含有 [dynamicPort] 的即启用动态端口..
备注2: [utp | srtp | wechat-video | dtls | wireguard] 分别伪装成 [BT下载 | 视频通话 | 微信视频通话 | DTLS 1.2 数据包 | WireGuard 数据包]

(默认协议: TCP):4

```

在这里选择4

```shell
----------------------------------------------------------------

请输入 V2Ray 端口 [1-65535]，不能选择 80 或 443 端口
(默认端口: 54869): Port

```

