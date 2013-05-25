---
layout: post
title: "Fibonacci Number Problem"
description: ""
category: algorithm
tags: [algorithm]
---
{% include JB/setup %}
###1. The Nth Fibonacci number 求费氏数列第N项
====================================================
According to the definition of Fibonacci sequence, the Nth number is:
	F(n) = F(n-2)+F(n-1)
最直观的方法就是根据公式求.
So these solutions are straight forward：
####1. Recursive  递归求解
代码如下：
{% highlight cpp linenos %}
int fibonacciRecursive( int n )
{
	return n <= 2 ? 1 : fibonacciRecursive(n-2) + fibonacciRecursive(n-1);
}
{% endhighlight %}
The code above will waste time in calculating the same numbers again and again. Take f(10) for example:
                 f(10)
               /       \
            f(9)         f(8)
          /     \       /    \
       f(8)     f(7)  f(7)   f(6)
      /   \     /   \ 
   f(7)  f(6)  f(6) f(5)
可以看出，使用此递归的方法会做很多重复计算，也使得时间复杂度呈指数增长。为了避免重复计算，可以使用迭代的方法。
We could optimize this by calculate the Nth number iteratively:
####2. Iterative 迭代求解 O(n)
{% highlight cpp linenos %}
int fibonacciNonRecursive( int n )
{
	if( n <= 2 ) return 1;
	else
	{
		int a = 1;
		int b = 1;
		int c;
		while( n-- > 2 )
		{
			c = a + b;
			a = b;
			b = c;
		}
	}
	return c;
}
{% endhighlight %}
####3. Matrix form 矩阵法 O(logn)
The matrix representation gives the following closed expression for the Fibonacci numbers:
矩阵法用到了Fibonacci的数学性质，因为不太会在markdown里打公式和插图片，以后再补啦。

###Problem2: Check if N is a Fibonacci number 判断N是否属于费氏数列
==========================================
Since Fibonacci series grow very fast, store a Precomputed table for lookup seems fine to small numbers.
然后，wiki说费氏数列的数有这个性质：
```
N is a Fibonacci number if and only if (5N^2+4) or (5N^2-4) is a square number.
```
所以问题就变成了判断一个数是否是完全平方数。
代码如下：
{% highlight cpp linenos %}
bool isPerfectSquare(long n)
{
	if( n < 0 )
		return false;

	double fsqrt = sqrt(n);
	int m = fsqrt;
	return m*m == n;
}
{% endhighlight %}



-----------------------------------------------
我的Ubuntu刚装了googlepinyin，以后可以写中文啦～
这篇之前写的，后来改的所以中英混杂^^
