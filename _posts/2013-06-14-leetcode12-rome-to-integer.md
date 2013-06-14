---
layout: post
title: "LeetCode[12]: Rome to Integer"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Given a roman numeral, convert it to an integer.
<br>
Input is guaranteed to be within the range from 1 to 3999.
</blockquote>
###2. My solution：
{%highlight cpp linenos%}
int romanToInt(string s) 
{
        int reslt = 0;
        int deci;
        int deci_pre=4000;//max

        for( int i = 0; i < s.size(); ++i )
        {
            switch (s[i])
            {
                 case 'M': deci = 1000;
                 break;
                 case 'D': deci = 500;
                 break;
                 case 'C': deci = 100;
                 break;
                 case 'L': deci = 50;
                 break;
                 case 'X': deci = 10;
                 break;
                 case 'V': deci = 5;
                 break;
                 case 'I': deci = 1;
                 break;
            }
            reslt += deci;
            if( deci_pre < deci )
                reslt -= deci_pre*2;
            deci_pre = deci;     
        }

        return reslt;     
}
{%endhighlight%}
