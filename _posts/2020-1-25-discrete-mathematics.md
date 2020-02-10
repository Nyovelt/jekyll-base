---
title: 离散数学定义速查
date: 2020-1-25 22:42:59 +0800
category: Education
tags: Mathematic
excerpt:  wish you luck as you begin your journey ...
---



> 教材： Discrete Mathematics andIts Applications - EighthEdition
>
> You can download it [here](https://www.academia.edu/39478917/Discrete_Mathematics_Applications_and_Its_E_i_g_h_t_h_E_d_i_t_i_o_n).
>
>其它资源： [Discrete Mathematics Notes](https://www.cl.cam.ac.uk/teaching/1920/DiscMath/DiscMathProofsNumbersSetsNotes.pdf) from others




## Chapter 1: The Foundations: Logic and Proofs

It's simply obvious.



## Chapter 2: Basic Structures: Sets, Functions, Sequences, Sums and Matrices

### 2.1 Sets

####  2.1.1 Introduction

**roster method** : 一种集合的表示法，形如 {a,b,c,d}

**set builder notation**: 集合的描述法。

**intervals**:  区间。包含开区间和闭区间。

两个集合相等当且仅当它们的元素相同。

介绍空集(empty set or null set)和单元素集(singleton set)的概念。

**Naïve Set Theory**: 朴素集合论。避免已知的各種悖论，例如理发师悖论。

#### 2.1.2 文氏圖 (Venn diagram)



![文氏图](https://4c8gpa.sn.files.1drv.com/y4moyscAEhBveEJDI-gG4J4MeFSMbByjXq44T7LFGnOA2q0-bCuXNOYPjbtITyVxzE5QMbzRraecBu8--WhT42C77XoG5HCQPwEsFgkBB76k_0o5lSgKHUPvR3F9q9Xw19v7E9COdTJrm2DL3009ZmURVN90IVouSoogwq5Qjo0ZX5brnmZueSlPh8i1qHa9IaodDYZOTGIJnKYpL7kAid6hg?width=858&height=358&cropmode=none)



#### 2.1.3 Subsets

#### 2.1.4 The Size of a Set

|S| 表示集合S中有多少个不同的元素。

2.5中将会讨论集合的势。

#### 2.1.5 Power Sets (幂集)

幂集是原集合所有子集的集合。

If a set has n elements, then its power set has 2n elements.

#### 2.1.6 Cartesian Products（笛卡儿积）

![笛卡尔积](https://4c8fpa.sn.files.1drv.com/y4mVtq-q9Gu5YQ50hy0vCEX6c6V_QuN4igytbtF-_xJmetbB5e9ogFrkgM_FZ3T1_gwjpdTqVYYQKlkHrInZHM8O9b8ZHpTqkjq9WvBYB9BnQmf6VKA4jSx4sySSj-8zSHGdhG9drn5yfrexwZBG_XS-TC70mIDc-woyFp7naTnYIQuPPY-8itiMAwfmSWd96-7SfcyPTvP2K5s3ro0686nkQ?width=1254&height=205&cropmode=none)

有点类似字典序。所以对与(AxB)来说是一个新的集合 (AxB)xC != AxBxC。

注意两集合为空集或者相等的情况。

一个有趣的例子：

![](https://4c8apa.sn.files.1drv.com/y4mUHtYhEEY7n47TLiVKNLtq6V3SxEPsAfRFMHQoJ2whWbTX-HIDoXZAXoYkrLPAVfC47y1HLeIzzIOXRy9VNDHrAv9v1aO_30eKNxXxqvxeP9ykaq2-9heXC3D4oL2x5soDrVv_nRv28oM_ZUe7gha9JKWV2g6Vt-_bOUsaLrv24pIoY2F5Ro0B0ie6LjWnNJSMLxeyegv4vKg-d4Kxb2HPw?width=1264&height=190&cropmode=none)



#### 2.1.7 Using Set Notation with Quantifiers

#### 2.1.8 Truth Sets and Quantifiers

Truth Set: 使得predict成立的元素组成的集合。

### 2.2 Set Operations

#### 2.2.1 Introduction

![](https://4c8lpa.sn.files.1drv.com/y4mdPPBiu02xoT1oqD-HXA7MqMRinqEvqp6p-Ku24y7MgKory33uoEmjIJAyI0FV1rRmBCSc0S3z7Gu2qXhcKG2Mt7ZHs5SZcvQD3FSFDH_mJSb-QgREnm15Ht6qdlr2j4d2CQzMfN_NU67Pi-52fdXBUVdIvMQdqCsyyBo-wn9Ahl68VT5Fn1k1FCsQs-cEJiQ3_Nk1f1x67DeWZKVSOYYzg?width=448&height=61&cropmode=none)



![](https://4m8epa.sn.files.1drv.com/y4ml2-SAjiNlQNS6VTBiLfB0fP86xG-Sc0ExDzo_PNK17y7ZBnEt7FAkYF8nRaFtcNUVwpM47cO6lBPGXozhbG2ULXfXvqLzWtNjpFvxS2SGiQi_qD1129iwEg0dDbm35TlWKm-JkQDjPDCzarJh9GXMR5dYEdBVIW0bwg-9qQZkPTnwZ3oGrPanBcmX6vHqe4anlhHbuyYsO7PWVE45YOKeA?width=499&height=69&cropmode=none)

![https://4m8dpa.sn.files.1drv.com/y4mnsSEPOHcaTUuj7YbgL36PEqYq6DLBD106V7VqOeh2Q6sD-42-DHjhHT67CaB7UHAVwuwHgq2XPqpop9XX10mAoa40m1fq7vT1dVNi6w6ZW1fJzhdfGnoC9fJKOIV7poEYXm6iDB2m61XbqyHXZofJ795NdQ2VfWnFV9KVUCBIoRzzHV1aZcoDdfxA8hlQ6TLrv9TEwho8wsaJZ_GaK3bfw?width=451&height=76&cropmode=none](https://4m8dpa.sn.files.1drv.com/y4mnsSEPOHcaTUuj7YbgL36PEqYq6DLBD106V7VqOeh2Q6sD-42-DHjhHT67CaB7UHAVwuwHgq2XPqpop9XX10mAoa40m1fq7vT1dVNi6w6ZW1fJzhdfGnoC9fJKOIV7poEYXm6iDB2m61XbqyHXZofJ795NdQ2VfWnFV9KVUCBIoRzzHV1aZcoDdfxA8hlQ6TLrv9TEwho8wsaJZ_GaK3bfw?width=451&height=76&cropmode=none)

（容斥原理）

![](https://4m8gpa.sn.files.1drv.com/y4m6WMuUd9Mik-ZnadA6EUNANWgHl1Br4NbIW2BJL3YoKny5AMnOHRWzhaVxn2QBnhzfrRzYpujkuCtLXS4EmXHkCtyP0ZeswSwM3MK3ruOYldMR0QaSruVflwsbOEyQ1m-gr891yDl6RB45j0u5tU6sUfKJcDIxVjZBmdbiRZ9LhsUvg-Htyk-2RGTWLkP0nrBFzeDpaz0EaRGBP6f2gZVgw?width=378&height=52&cropmode=none)

![](https://4m8fpa.sn.files.1drv.com/y4mYWRPdd9NC8islng2qnonDL2o9M4X70diAND0HzBTMZ396TociA60kQN1E-ckbQQ15kNIuCPWS_tDVHsvsa74LNTTTHWycoo-RZ83a1RgpNmDgONln1E4Q-qxXkDraNDjKKjcv_8XmzJpi90pn-b5cQ7jnYv2KcEkzdB-dl3IJNGVlLlb38Ks4_cpsx3i2-Nfj0IIxTBGIEKoW_6jPtc1Uw?width=313&height=58&cropmode=none)

（补集）

#### 2.2.2 Set Identities

![](https://4m8apa.sn.files.1drv.com/y4mslSaV21nFv4bLE13QrBsRph_ho9prIv5lzii7k5Mf-FRvsnBp3YqFetZ5vxXzIbHwGJ9MzikbaXr9EkJHxJW9PcDs2r3fqVcjwGMcxk2OZcv2j_d01XoknuWpz54YUv44RaM9eXIAyoSnGkiCDPXkqm5-kuMOuV6okg_mpzmFlT1qg-2NZ-HE4yup2t4UlGxub1pW0ZUi2xULmlviquCOg?width=651&height=918&cropmode=none)