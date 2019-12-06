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

通常写程序的时候，我们会更关注于程序的代码(main.c)和最终形成的可执行文件(main)。对于程序员来说，这两个部分的确是最重要的。但是，在编译的过程中，除了你的源代码和最终的可执行程序，其它部分，也就是编译器自动帮你处理掉的那部分，也应该得到关注。事实上，有很多bug是因为忽视了编译器的运作原理而导致的。



![1575551248676.png](https://i.loli.net/2019/12/05/xXSCbpR1ckPz79W.png)	

##   この戦いが終わったら 

C作为一门不会对内存检查的语言，因此很多的操作会超出一个变量的边界去影响下一个变量，举一个例子：

![pwn](C:\Users\Nyove\Desktop\Demostration\pwn\pwn.png)

​			

我们同时输入10个A 和11个A 来康康结果：



![pwn_output](C:\Users\Nyove\Desktop\Demostration\pwn\pwn_output.png)



`buffer[10]` 开辟了10个字节的内存空间，当我们输入了10个A以后，`buffer[10]`的内存空间被用完了，而gets()函数并不会对空间的边界进行检查，所以当第11个A输入了以后，A被挤到了`(int)modified`的内存空间，所以原本是0的`modified`不再是0（实际上modified的值 是 A的askll值 `65` ）



​			 ![Big-Endian.svg](https://upload.wikimedia.org/wikipedia/commons/thumb/5/54/Big-Endian.svg/280px-Big-Endian.svg.png) 

<img src="C:\Users\Nyove\Desktop\Demostration\pwn\demo.jpg" alt="demo" style="zoom:50%;" />



##   空の上の森の中の 



所以我们可以关注一下编译器是怎么分配内存的。



一般情况下，我们可以直接调用编译器来输出汇编代码，以`helloworld.c`为例。



![hello_c.png](https://i.loli.net/2019/12/05/5kwmUpTeyH8K1tS.png)



打开终端，输入命令



```bash
$ gcc   -S helloworld.c -Og -masm=intel
```

 

-S 表示输出汇编程序   

-Og是编译器的优化等级，让编译器不要做过多的优化，随着编译技术的提升，现在编译器几乎等于已经把你的程序重新写一遍了   

-masm=intel 表示使用intel的语法，便于理解 



然后就可以得到汇编代码

![hello_s](C:\Users\Nyove\Desktop\Demostration\hello\hello_s.png)

我们关注其中的几行：

![hello_s_1](C:\Users\Nyove\Desktop\Demostration\hello\hello_s_1.png)



简单的说，



| sub  | 在内存中开辟了一段空间【栈】 （注：这里的栈和数据解构的栈是不一样的） |
| :--: | ------------------------------------------------------------ |
| lea  | `load effective address`                                     |
| call | 调用 `puts ( printf )` 输出了这段内存上所存的数据 ( 即helloworld )，，把`.LC0`地址放入`rdi` ，也就是`printf`的第一个参数。 |
| mov  | 将eax寄存器移到栈顶（0位）                                   |
|      |                                                              |



##  帰らぬ者と、待ち続けた者たち 

![20090421150228_dormirovejas](C:\Users\Nyove\Desktop\Demostration\fractorial\20090421150228_dormirovejas.jpg)



​		正如前文所指出的，C并没有边界检查，C也不是一门高精度语言，所以在做大数运算的时候会导致精度丢失，数据溢出等问题。比如上图所展示的那样，int型最高位是符号位，所以当达到int的最大值的时候符号位由表示正数的0变为表示复数的1，并且由于用补码储存的缘故，得到了如图所示的输出。

![int++](C:\Users\Nyove\Desktop\Demostration\fractorial\int++.png)

​		有时候我们会在程序中用到很大的数字，比如算组合数的时候有些程序会使用阶乘来计算。当n过大的时候，有时候阶乘算出来就不怎么准确了。



## 参考

1.  [Why 2147483647 + 1 is actually -2147483648?](https://stackoverflow.com/questions/48160580/why-2147483647-1-is-actually-2147483648)
2.  