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
> 该OJ已开源，详见 [https://oj.geekpie.club/about](https://oj.geekpie.club/about )  <del>顺便求star</del>



## 0x01 服务器架构

出于轻量化和弹性化的考虑，我们社团的服务器集群管理用的是 Rancher 1.6 ，所有的服务是纯docker的，我们会分装到docker里，上传到代码托管平台，由CI服务自动build完放到私有registry里，再通过rancher提供给其它服务器使用。



所有的服务器通过 zerotier 组成内网，通过 zerotier 内网访问。




之前，我们一共有三台Azure + 若干台其它server <del>所有服务器都用算法命名</del>

- Azure-CN-E2-0 【brent﻿】           64G        负责跑 Rancher 1.6  服务
- Azure-CN-E2-1 【prim﻿】             64G       因为服务器在海外，负责 Jenkins自动docker构建和 registry 服务
- Azure-CN-E2-2 【kruskal﻿】        64G        负责跑大多数的服务，拥有大量数据库
- etc



叠镜赞助了我们四台服务器：

- 3台上海阿里云 硬盘为 30G
- 1台香港阿里云



现在的工作是将 Azure 迁移至 Aliyun ，并保证所有服务都可用。



## 0x02 阿里云官方迁移工具

我们首先查阅了这篇文档

> [Azure虚拟机迁移至阿里云ECS]( https://help.aliyun.com/document_detail/100959.html )



由于阿里云提供了官方的迁云工具，所以这一步稍显简单。



我下载了[迁云工具](https://help.aliyun.com/document_detail/62394.html?spm=a2c4g.11186623.2.18.6c1d7f90FuSH6T#section-twq-sxz-jfb)，解压后首先运行`./Check/client_check --check`命令检查，没有问题，然后配置` user_config.json `。

我的配置是这样的：

```json
{
    "access_id": "YourAccessKeyID",
    "secret_key": "YourAccessKeySecret",
    "region_id": "cn-hangzhou",
    "image_name": "Azure-CN-E2-2",
    "system_disk_size": 70,
    "platform": "Ubuntu",
    "architecture": "x86_64",
    "data_disks": [],
    "bandwidth_limit": 0
}
```

为了确保容量不会有什么问题，我特意做了些冗余，将64G(实际占用54G)的系统盘**做成了70G的快照(image)**。



### 坑点一    系统盘容量问题

大家是否还记得，阿里云的系统盘只开了30G [ QwQ ] 这样做会在快照恢复的时候提示需要多交100多块软妹币将30G系统盘升级到70G。本着**勤俭节约的精神**，我做了如下尝试： 



#### 尝试方案

想利用30G的数据盘，将docker放到数据盘上(docker是大头)：

```json
{
	"access_id" : "YourAccessKeyID",
	"bandwidth_limit" : 0,
	"data_disks" : 
	[
		{
			"data_disk_index" : 1,
			"data_disk_size" : 28,
			"src_path" : "/var/lib/docker"
		}
	],
	"image_name" : "Azure-CN-E2-2-1",
	"platform" : "Ubuntu",
	"region_id" : "cn-shanghai",
	"secret_key" : "YourAccessKeySecret",
	"system_disk_size" : 28
}

```

**结果：** 不明原因失败



#### 解决方案 

某天周五放学去了离学校只有10分钟走路程的叠境，用叠镜的钱加了系统盘，顺便配置了一下防火墙。

<del>然后发现迁移过程中烧掉的流量钱可以扩好几次硬盘了</del>

<del>原来叠境离学校这么近，果然我们是叠境附属学院</del>

<del>贫穷限制了我的想象</del>




## 0x03 Rancher的启动与Zerotier

