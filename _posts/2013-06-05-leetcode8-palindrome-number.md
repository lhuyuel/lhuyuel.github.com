---
layout: post
title: "LeetCode[8]: Palindrome Number"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Poblem：
<blockquote>
Determine whether an integer is a palindrome. Do this without extra space.
</blockquote>
###2. My Solution：
{% highlight cpp linenos %}
    int reverse(int x)
    {
        int reslt = 0;
        int lastdigit;
        while( x > 0)
        {
            lastdigit = x % 10;
            reslt = reslt*10 + lastdigit;
            x /= 10;
        }
        return reslt;
    }
    bool isPalindrome(int x) {
        //If the interger is a palindrome, it is equal to it's reverse
        if( x < 0 ) 
            return false;
        return (x == reverse(x) );
        
    }
{% endhighlight %}

###3. 题后唠叨：
还可以直接比较第一位和最后一位，如果一样就掐头去尾，再比第一位和最后一位，如此循环。直到一位都不剩则是回文数字。

