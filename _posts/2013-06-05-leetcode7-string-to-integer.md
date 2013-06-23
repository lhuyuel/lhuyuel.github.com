---
layout: post
title: "LeetCode[7]: String to Integer"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem:
<blockquote>
Implement atoi to convert a string to an integer.
</blockquote>
###2. My solusion：
{% highlight cpp linenos %}

   int atoi(const char *str) {
        const char *p = str;
        bool neg = false;
        long long reslt = 0;
        
        if( p == NULL )
            return 0;
       
        while( *p ==' ' ) ++p;//skip the spaces
        if( *p == '-' )
        {
            neg = true;
            ++p;
        }
        else if( *p == '+' )
        {
            neg = false;
            ++p;
        }
            
        while( isdigit(*p) )
        {
            reslt = reslt*10 + *p-'0';
            ++p;
        }
        if( reslt > INT_MAX )
             neg ? reslt = INT_MAX + 1 : reslt = INT_MAX;
            
        return neg ? (-1*reslt ) : reslt;
        
    }
{% endhighlight %}

###3. Notes：
要考虑正负情况，还有极值问题。<br>
具体见[这里](http://discuss.leetcode.com/questions/192/string-to-integer-atoi).<br>
C++有一个int isdigit(int c)函数可以判断一个字符是否是十进制的数字。


