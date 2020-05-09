---
title: 电路基础期中概念梳理
date: 2020-5-9 9:00:59 +0800
category: EDU
tags: EDU
excerpt: 电路基础期中概念梳理
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script> <script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'], inlineMath: [['$','$']] } }); </script>



# 电路基础

## 电路基础基础

- $i = \frac{dq}{dt}$
- $v=\frac{dE}{dq}$  , E 指电荷移动做功（功有正负之分，取决于电路中电荷移动的方向）
- $p = \frac{dE}{dt}$   单位时间内做功的能力
- $v = L \frac{di}{dt}$  L为电感，因为当$\frac{di}{dt}$不能为值无穷,所以含有电感的支路$i$不能突变v
- $i = C \frac{dv}{dt}$  C为电容，因为当$\frac{dv}{dt}$不能为值无穷,所以含有电感的支路$v$不能突变

### 理想电源

#### 非受控源

恒定的输出电压和电流

### 受控源

根据电源两端的电压或者通过电源的电流，以线性函数的形式，产生响应的电压和电流。

## 基尔霍夫定律

基尔霍夫定律分为基尔霍夫电流定律和基尔霍夫电压定律。它的本质思想是电荷不会凭空的产生和消失（电荷守恒公理），所以电流——单位时间内电荷的数量，以及电压——能使电荷移动的能力。这两者是守恒的。对于每一个形状闭合的电路，都可以有:

- 电势涨落守恒
- 电流的数量和为0 (电流为有向标量)

于是我们有方程

- $$\sum{v_i} = 0$$, $v_i$为每个电路元件所吸收/输出的电压

- $$\sum{i_j} = 0$$, $i_j$为电路上选定的任意一个点，它的每个方向上的电流