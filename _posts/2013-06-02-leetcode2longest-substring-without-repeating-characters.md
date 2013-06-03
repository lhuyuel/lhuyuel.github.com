---
layout: post
title: "LeetCode[2]:Longest Substring Without Repeating Characters"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. 问题：
<blockquote>
Given a string, find the length of the longest substring without repeating characters. For example, the longest substring without repeating letters for "abcabcbb" is "abc", which the length is 3. For "bbbbb" the longest substring is "b", with the length of 1.
</blockquote>
###2. 我的代码:
Brute Force.
Complexicty: O(n^2)
{% highlight cpp linenos %}
int lengthOfLongestSubstring(string s) {
        int maxlen = 0;
        if( s.size() == 0 )
            return 0;
        if( s.size() == 1 )
            return 1;
        
        for(int i = 0; i < s.size()-1; ++i)
        {
            int counter = 0;
            int j = i+1;
            for(;j<s.size();)
            {
                int k = i;
                for(; k < j; ++k )
                {
                  if( s[k] == s[j] )
                  {   
                        counter = j - i;
                        break;
                  }      
                }
                if( j==k ) j++;
                else
                    break;
            }
            if( counter > maxlen )
                maxlen = counter;
            
            if( j == s.size() )//don't need to check the else since it reach the end
            {
                counter = j - i;
                if(counter >maxlen) maxlen = counter;
                break;
            }
        }
        return maxlen;
    }
{% endhighlight %}

###3.题后唠叨：
依然没能完杀。  
		1. 首先是题目没看清楚。。。  
		2. 然后是逻辑没有想清楚。。。  
以至于改了半个小时。		
很是凌乱  
完成总时间：60分10秒



