---
title: PIGEON OJ 配置指南（评卷机）
date: 2020-7-7 10:00:59 +0800
category: Technology
tags: Technology
excerpt: 咕咕咕咕咕

---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script> <script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'], inlineMath: [['$','$']] } }); </script>

# Pigeon OJ

Pigeon OJ 是由上海科技大学 GeekPie 社团开发的一个基于 Docker 和 Gitlab 的多文件在线评测系统。

在上学期的 CS100 后，该 OJ 已经尘封了一个学期了。 在下个学期的 SI100B 中，该 OJ 也会给新来的 20 届同学使用。在暑学期中， 该 OJ 还要为 专硕 的项目服务。 

OJ 的评卷系统是通过一个 scheduler 通过 TLS 连接 Docker API 调用 Docker 进行评卷。之前的评卷机在 CS100 课程结束后就被学校收回了。 所以现在我需要为其添加一个新的评卷机 ( Judger )



  