---
layout: post
title: "LeetCode[25]: Remove Element"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Given an array and a value, remove all instances of that value in place and return the new length.<br>
<br>
The order of elements can be changed. It doesn't matter what you leave beyond the new length.
</blockquote>
###2. My solution：
Similar to previous post.
<b>Code:</b>
{% highlight cpp linenos %}
    int removeElement(int A[], int n, int elem) 
    {
        if(n == 0 )
            return 0;
        int count = 0;
        for( int j = 0; j < n; ++j )
        {
            if( A[j] != elem )
                A[count++] = A[j];
        }
        return count;   
    }
{% endhighlight %}
