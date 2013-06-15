---
layout: post
title: "LeetCode[15]: 3Sum Closest"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.
<br>
<br>    For example, given array S = {-1 2 1 -4}, and target = 1.

<br>    The sum that is closest to the target is 2. (-1 + 2 + 1 = 2)

</blockquote>
###2. My solution：
{%highlight cpp linenos%}
int threeSumClosest(vector<int> &num, int target) 
{        
    int n = num.size();
    int reslt = INT_MAX/2;// when use INT_MAX and target is negtive, then thre will be a overflow
           
    if( n < 3 ) 
        return INT_MAX;
    sort( num.begin(), num.end() );
        
    for(int i = 0; i < n ;++i ) 
    {
        int j = i+1;
        int k = n-1;
           
        while( j < k )
        {
            int sum3 = num[i] + num[j] + num[k];
            reslt = abs( sum3-target ) < abs( reslt-target ) ? sum3 : reslt;
            if( sum3 < target )
            {
                 ++j;
            }
            else if( sum3 > target )
            {
                 --k;
            }
            else
            {
                return sum3;
            }
        }
     }
     return reslt;
}
{%endhighlight%}
###3. Notes:
之前reslt 初始值那里fail掉了1个测试，原来用的是INT_MAX, target是负数的时候，在reslt-target那里溢出了。
