---
title: 一次服务器迁移的尝试
date: 2020-1-14 12:59:59 +0800
category: Technology
tags: Linux
excerpt: 踩了无数的坑...
---

## 0x00 缘起

在2019年的某天深夜，所有信院的同学的突然惊恐的发现，交作业的OJ上不去了。<del>然后欣喜的在第二天接到了ddl延期的通知</del>作为社团运维组的一员，发现罪魁祸首是...Azure欠费了。



好在作为[叠境]([https://www.dgene.com](https://www.dgene.com/)) 附属学院，金主爸爸重新赞助了一批阿里云服务器，这批新的服务器将会在2019年双十二期间划归社团。



在没有迁移到阿里云之前，社团暂时由社团经费新开了两台Azure HK，并通过快照的方式及时恢复了服务。费用为11欧/天。



> OJ为社团自建，向全校学生提供服务。 
>
> 该OJ已开源，详见 https://oj.geekpie.club/about  <del>顺便求star</del>


## 0x01 服务器架构

出于轻量化和弹性化的考虑，我们社团的服务器集群管理用的是 Rancher 1.6 ，所有的服务是纯docker的，我们会分装到docker里，上传到代码托管平台，由CI服务自动build完放到私有registry里，再通过rancher提供给其它服务器使用。



所有的服务器通过zerotier组成内网，通过zerotier内网访问。




之前，我们一共有三台Azure + 若干台其它server <del>所有服务器都用算法命名</del>

- Azure-CN-E2-0 【brent﻿】           64G        负责跑 Rancher 1.6  服务
- Azure-CN-E2-1 【prim﻿】             64G       因为服务器在海外，负责 Jenkins自动docker构建和 registry 服务
- Azure-CN-E2-2 【kruskal﻿】        64G        负责跑大多数的服务，拥有大量数据库
- etc



叠镜赞助了我们四台服务器：

- 3台上海阿里云 硬盘为 30G
- 1台香港阿里云



现在的工作是将 Azure 迁移至 Aliyun ，并保证所有服务都可用。