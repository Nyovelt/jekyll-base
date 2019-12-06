---
title: 编译时你在做什么？有没有空？可以来拯救吗？
date: 2019-11-29 12:55:35 +0800
category: Technology
tags: C/C++ 黑魔法
excerpt: 是...是神奇的黑魔法呢
---

<p align="right">— Willem...</p>
<p align="right">— What's the matter?</p>
<p align="right">— It seems that there's something wrong with Seniorious....</p>
<p align="right">— I'll have a look...</p>
![](https://codeforces.com/predownloaded/74/bf/74bf142287573c733e9196a3bf26cd8b012bc804.png)



## 太陽の傾いたこの世界で

通常写程序的时候，我们会更关注于程序的代码(main.c)和最终形成的可执行文件(main)。对于程序员来说，这两个部分的确是最重要的，甚至说90%的情况下都不用去管其它部分。现代的编译器非常智能，它们会帮你处理好一切（点名表扬 clang  [klæŋ]  ) 。但是，在编译的过程中，除了你的源代码和最终的可执行程序，其它部分，也就是编译器自动帮你处理掉的那部分，也应该得到关注。事实上，有很多bug是因为忽视了编译器的运作原理而导致的。



![1575551248676.png](https://i.loli.net/2019/12/05/xXSCbpR1ckPz79W.png)	

##   この戦いが終わったら 

C作为一门不会对内存检查的语言，因此很多的操作会超出一个变量的边界去影响下一个变量，举一个例子：

![pwn](/assets/img/2019/Workshop/pwn.png)

​			

同时输入10个A 和11个A 来康康结果：



![pwn_output](/assets/img/2019/Workshop/pwn_output.png)



`buffer[10]` 开辟了10个字节的内存空间，当我们输入了10个A以后，`buffer[10]`的内存空间被用完了，而gets()函数并不会对空间的边界进行检查，所以当第11个A输入了以后，A被挤到了`(int)modified`的内存空间，所以原本是0的`modified`不再是0（实际上modified的值 是 A的askll值 `65` ）



一般情况下，数据在计算机内部是这样存储的：

​			 ![Big-Endian.svg](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/Big-Endian.svg/280px-Big-Endian.svg.png) 

而在这个具体的例子中：内存空间（栈）是这样的：

<img src="/assets/img/2019/Workshop/demo.jpg" alt="demo" style="zoom:50%;" />





##   空の上の森の中の 

所以编译器到底在干什么？

很多人都听说了C是一种高级语言，编译器把高级语言翻译成低级语言，操作系统把低级语言翻译成机器码。

那么我们可以看一看编译器翻译后的代码，来关注一下程序到底是什么运作的。

一般情况下，我们可以直接调用编译器来输出汇编代码，以`helloworld.c`为例。



![hello_c.png](https://i.loli.net/2019/12/05/5kwmUpTeyH8K1tS.png)

打开终端，输入命令

```bash
$ gcc -S helloworld.c -Og -masm=intel
```

 

- -S 表示输出汇编程序   

- -Og是编译器的优化等级，让编译器不要做过多的优化，随着编译技术的提升，现在编译器几乎等于已经把你的程序重新写一遍了   

- -masm=intel 表示使用intel的语法，便于理解 

- 当然可以用文末的在线工具（推荐）

  

然后就可以得到汇编代码

![hello_s](/assets/img/2019/Workshop/hello_s.png)

我们关注其中的几行：

![hello_s_1](/assets/img/2019/Workshop/hello_s_1.png)

简单的说，

| sub  | 在内存中开辟了一段空间【栈】 （注：这里的栈和数据解构的栈是不一样的） |
| :--: | ------------------------------------------------------------ |
| lea  | `load effective address`                                     |
| call | 调用 `puts ( printf )` 输出了这段内存上所存的数据 ( 即helloworld )，，把`.LC0`地址放入`rdi` ，也就是`printf`的第一个参数。 |
| mov  | 将eax寄存器移到栈顶（0位）                                   |
| add | 将add的第二个参数加到第一个参数上，在这里是rsp += 8 |
| ret | 返回 |



 ![Stack Overflow website logo.png](https://upload.wikimedia.org/wikipedia/zh/9/95/Stack_Overflow_website_logo.png) 

Stackoverflow 直译过来就是堆栈溢出 XD

##  帰らぬ者と、待ち続けた者たち 

![sheep](/assets/img/2019/Workshop/sheep.jpg)

​		正如前文所指出的，C并没有边界检查，C也不是一门高精度语言，所以在做大数运算的时候会导致精度丢失，数据溢出等问题。比如上图所展示的那样，int型最高位是符号位，所以当达到int的最大值的时候符号位由表示正数的0变为表示复数的1，并且由于用补码储存的缘故，得到了如图所示的输出。

![int++](/assets/img/2019/Workshop/int++.png)

​		有时候我们会在程序中用到很大的数字，比如算组合数的时候有些程序会使用阶乘来计算。当n过大的时候，有时候阶乘算出来就不怎么准确了。

![int](/assets/img/2019/Workshop/int.png)

![int_output](/assets/img/2019/Workshop/int_output.png)

当然，你可以用尽最大的数据类型，甚至舍弃符号位，用`unsigned long long` 的数据类型（也就是夸张的0 ~ 2^64 ，八字节），但是问题实际上并没有解决。

![unsigned_ll](/assets/img/2019/Workshop/unsigned_ll.png)

![unsigned_ll_output](/assets/img/2019/Workshop/unsigned_ll_output.png)

虽然我们可以确保20以内的阶乘的值

是精确的（事实上`21!`就出现问题了，而且因为 `unsigned long long` 没有符号位的特性，和int不一样，它不是负数，而是看似正确的一个极大的正数）。但是在算组合数的依旧值得注意“`算术溢出`”的问题。
$$
C_{40}^{20} = \frac{40!}{20!20!}
$$
在运算过程中，编译器会自动进行数据类型转换，尽可能的存下这些数据，但是如果数据过大，仍然会产生溢出。



##   ただいま帰りました 

在Mid-Term中有这么一道题：

![union](/assets/img/2019/Workshop/union.png)

汇编结果是：

![union_s](/assets/img/2019/Workshop/union_s.png)

可以用动图解释：

![union](/assets/img/2019/Workshop/union.gif)

##  どうか、忘れないで 

基于本文，可以给出一下优化程序的建议：

- 关注数据类型和内存边界问题

- 由上文带来的算法优化问题，能否用算法来解决数据类型和内存大小的限制

- 其它内存相关的优化（比如考虑内存的连续性，考虑减少不必要的调用和引用）

- etc

### 设计模式

- 





## 参考

1. [Why 2147483647 + 1 is actually -2147483648?](https://stackoverflow.com/questions/48160580/why-2147483647-1-is-actually-2147483648)

2. [Understanding the Stack](https://www.youtube.com/watch?v=pOOivAJ63DM)

3.  [在线汇编编译](https://godbolt.org/ )
4.  [栈缓冲区溢出](https://zh.wikipedia.org/wiki/%E6%A0%88%E7%BC%93%E5%86%B2%E5%8C%BA%E6%BA%A2%E5%87%BA)

