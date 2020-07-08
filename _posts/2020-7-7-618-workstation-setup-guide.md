---
title: 618买电脑指南
date: 2020-7-7 9:00:59 +0800
category: Life
tags: Life
excerpt: Manjaro + Windows

---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script> <script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'], inlineMath: [['$','$']] } }); </script>

# 618

由于笔者的笔记本（六代标压i5 + gtx965m）已经跟不上笔者剪辑4K视频和机器学习的需求了。所以在618的时候拿到了预算，有能力购入一台新电脑。



新电脑旨在追求长期性价比，并且尽量追求边际效应最小化。笔者是计算机科学的学生，因此未来可能会写CUDA，大型编译以及双系统的需求。适逢AMD的Zen2架构和英伟达图灵显卡大降价，因此618可以算是购入电脑的一个好时机。



# 配置

[**AMD 锐龙9 3900X 处理器**](https://item.jd.com/100006391096.html)  JD 3286.33

**[华硕（ASUS）PRO WS X570-ACE 主板](https://item.jd.com/100006445338.html)** JD 2890.00

[32G ECC UDIMM DDR4 3200内存](https://item.taobao.com/item.htm?id=601069952968) TAOBAO 1100.00

[Intel/英特尔P4500 1T SSD U.2](Intel/英特尔P4500 1T SSD U.2) TAOBAO 787.50

[**利民（Thermalright） FS140 霜灵 双塔散热器**](https://item.jd.com/100010498068.html) JD 228.00

**[美商海盗船 (USCORSAIR) 额定850W RM850x 全模组电脑电源](https://item.jd.com/6757737.html)** JD 818.17

**[索泰(ZOTAC)RTX2060super霹雳版OC HA](https://item.jd.com/100007391086.html)** JD 2491.00

[先马（SAMA）黑洞 黑色 中塔式机箱](https://item.jd.com/1842778.html)  JD 247.00

U.2连接线 



**ALL 11848 ** 



## 购买理由

- 3900X 一共拥有 2 个CCD，总共十二核心，二十四线程。 每个CCD分表包含着6个核心和十二个线程 (id: 0-5, 12-17)(i: 6-11, 18-23) ，一共 64M 的三级缓存（虽然跨CCD时延迟会很大）。三级缓存对编译的提升是很大的，同时多核心更利于虚拟机。

- 华硕（ASUS）PRO WS X570-ACE 主板 是一块工作站主板，特点是支援ECC UDIMM内存， 主板用料较好， 有一个华硕自家的远程管理系统， 共有三条pcie插槽(pcie 3.0 *16*+  pcie 3.0 * 8)。

- 因为<del>上科大水电免费</del>学习需要，所以预计是24*7工作。ECC内存对于系统稳定性的提升是很大的。

- P4500, 英特尔企业级SSD，TLC颗粒， U.2接口

- 虽然各种参数上都不如猫扇（例如风压），但口碑较为不错，已经在学校内见到一个有组织的传教团队了（

- 因为会上双卡，所以上了850W的电源

- 目前，

  - 由于英伟达在CUDA领域较早的布局和在教育行业的疯狂送卡行为（一个电话连夜免费快递六块V100），AMD目前在机器学习和教育领域的生态已经落后n个身位了
  - 机器学习要求显存8G起步（测试结果来自 @murez 用openai跑历史的期末论文）
  - 同一个核心的丐版和顶级非公的性能差距不会超过5%
  - CPU更容易成为性能瓶颈
  - 2060S是20系列当前性价比较高的一张卡
  - 堆料索，走京东
  - 其它需求可以白嫖学校

  所以我决定采用索泰的丐版2060S

- 机箱随便买的



# 装机

<bilibili>



# 双系统

