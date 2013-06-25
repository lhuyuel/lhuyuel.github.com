---
layout: post
title: "LeetCode[24]: Remove Duplicates from Sorted Array"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.Do not allocate extra space for another array, you must do this in place with constant memory.<br>
For example,<br>
Given input array A = [1,1,2],<br>
Your function should return length = 2, and A is now [1,2].<br>
</blockquote>
###2. My solution：
The idea is to count the number of current different elements, and copy the following different element to the A[count] postion.
{% highlight cpp linenos %}
    int removeDuplicates(int A[], int n) 
    {
            int count=0;
            int j;
            if (n<=1) 
		return n;
        
            for( j = 1; j < n; ++j )
            {            
                if( A[j] != A[count] )
                {                
                    A[++count]=A[j];
                }
            }
            return i+1;
    }
{% endhighlight %}
