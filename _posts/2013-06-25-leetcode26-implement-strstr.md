---
layout: post
title: "LeetCode[26]: Implement strStr()"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Implement strStr().<br>
<br>
Returns a pointer to the first occurrence of needle in haystack, or null if needle is not part of haystack.
</blockquote>
###2. My solution：
####1). Brute Force:
{% highlight cpp linenos %}
    char *strStr(char *haystack, char *needle) 
    {
        if( *needle == '\0')
            return haystack;
          
        char *curPos = haystack;
        char *p_hs = haystack;
        char *p_nd = needle;
            
        while( *p_hs != '\0' )
        {
            while(  *p_hs !='\0' && *p_nd != '\0' && *p_hs== *p_nd )
            {
                p_hs++;
                p_nd++;
            }
            
            if( *p_nd == '\0' )//reach the end of needle
                return curPos;
            if( *p_hs =='\0' )//Didn't finish the needle but reach the end of str
                return NULL;
          
            ++curPos;
            p_hs = curPos;
            p_nd = needle;  
        }
        
        return NULL; 
    }
{% endhighlight %}
Missed a "*" in the 3rd line, and the condition when *p_hs=='\0', spent a lot of time to figure out...Still not sure why missing the line if( *p_hs =='\0' ) can cause problem...
####2). Rabin–Karp algorithm and else
I know the algorithm but I don't think I could write correct code within a time limit. It took me a long time even to get the brute force solution work...<br>
<b>Other string searching algorithm: </b><br>
+ [Rabin–Karp algorithm](http://en.wikipedia.org/wiki/Rabin-Karp_algorithm)
+ [KMP(Knuth–Morris–Pratt algorithm)](http://en.wikipedia.org/wiki/Knuth-morris-pratt_algorithm)
+ [Boyer-Moore algorithm](http://en.wikipedia.org/wiki/Boyer_moore_algorithm)



