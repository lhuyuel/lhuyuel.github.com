---
layout: post
title: "LeetCode[1]: Median of Two Sorted Arrays"
description: ""
category: 练习题
tags: [C++, LeetCode, 刷题]
---
###1. Problem：
<blockquote>
There are two sorted arrays A and B of size m and n respectively. Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).
</blockquote>
###2. My Solution:
Complexity: O( log(m+n) )  

{% highlight cpp linenos %}
double findMedianSortedArrays(int A[], int m, int B[], int n) {
        int i=0;
        int j=0;
        vector<int> C;
		
        while(i != m && j != n )
        {
            if( A[i] < B[j] )
            {
                C.push_back(A[i]);
                ++i;
            }
            else
            {
                C.push_back(B[j]);
                ++j;
            }
        }
		
        while(i!=m)
        {
            C.push_back( A[i] );
            ++i;
        }
        while(j != n)
        {
            C.push_back(B[j]);
            ++j;
        }
        
        int num = m+n;
        if( num%2 == 0 )
            return ( C[num/2]+C[num/2 - 1] )/2.0;
        else 
            return C[num/2];
    }

{% endhighlight %}

###3.Notes：  
		1. 整数除以整数得到的是整数且向下取整。    
		2. m+n是偶数求中位数时，两数相加别忘除以2。
完成总时间：19分20秒



