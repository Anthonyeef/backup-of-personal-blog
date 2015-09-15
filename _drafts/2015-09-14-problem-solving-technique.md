---
layout: post
title: "Programming and Problem solving with C++"
<!--date: 2015-09-14 16:38:46 +0800-->
comments: true
categories: 
- Life
- 2015
- Develope
- Taiwan

---

这是我在台湾阅读的第一本书。下面是一些简单的笔记和摘抄：

> Never reinvent the wheel. If a solution exists, use it. If you've solved the same or a similar problem before, just repoeat your solution.

---

> Beware when declaring two or more pointers on the same line. The * operator binds with the variable name, not the type name.

{% highlight C++ linenos%}
int* x,y,z;  //same as: int* x, int y; int z;
{% endhighlight %}

---

> This decision is consistent with C++'s general philosophy of not introducing any feature that would slow the execution of a program.

---

> int A[15][30] declares A to be an array of 30 objects, each of which is an array of 15 intergers.（二维数组）

> The name of an array is equivalent to a pointer to the array's initial element and vice versa.

> Given two arays c and d, the comparison(c == d) does not test whether the contents of the two arrays are equal. Rather it compares the address of their initial elements.

> Unlike some programming languages such as Java, C++ does not provide automatic garbage collection.（ C++ 不提供垃圾回收机制）  

---

> new 命令使用之后需要 delete 命令进行内存的回收：
{% highlight C++ lineons%}
char* buffer = new char[500];
buffer[3] = 'a';
delete [] buffer;
{% endhighlight %} 

