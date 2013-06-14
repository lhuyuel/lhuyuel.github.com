---
layout: post
title: "LeetCode[11]: Integer to Rome"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Given an integer, convert it to a roman numeral.
<br>
Input is guaranteed to be within the range from 1 to 3999.
</blockquote>
###2. My solution：
{% highlight cpp linenos %}
    string intToRoman(int num) 
    {
        string rm[] = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
        int deci[]={1000,900,500,400,100,90,50,40,10,9,5,4,1};
        string reslt;
        int i = 0;
        while( num > 0 )
        {
            int times = num / deci[i];
            for( int j = 0; j < times; ++j )
            {
                reslt.append( rm[i] );
            }
            num -= times* deci[i];
            ++i;
        }
        return reslt;
    }
{% endhighlight %}
