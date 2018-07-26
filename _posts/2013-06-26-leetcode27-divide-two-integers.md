---
layout: post
title: "LeetCode[27]: Divide Two Integers"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
###1. Problem：
<blockquote>
Divide two integers without using multiplication, division and mod operator.
</blockquote>
###2.Solution：
{% highlight cpp linenos %}
int divide(long long dividend, long long divisor) 
{
     bool neg = (dividend < 0) ^ (divisor < 0);
        
     if (dividend < 0) dividend = ~dividend +1;
     if (divisor < 0) divisor = ~divisor+1;

     long long rslt = 0;
     while ( dividend >= divisor) 
     {
         long long divs = divisor;
         for( int i = 0; dividend >= divs; ++i, divs <<= 1) 
         {
             dividend -= divs;
             rslt += 1 << i;
         }
     }
        
        return neg ? (~rslt + 1) : (rslt);   
}
{% endhighlight %}
###3. Notes:
More bit manipulations see [this post](http://lhuyuel.github.io/programming/2013/06/25/bit-manipulation0/).
