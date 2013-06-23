---
layout: post
title: "LeetCode[13]: Longest Common Prefix"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Write a function to find the longest common prefix string amongst an array of strings.
</blockquote>
###2. My solution：
{% highlight cpp linenos %}

   string longestCommonPrefix(vector<string> &strs) {
      
      int stringNum = strs.size();
      if( stringNum == 0 ) return "";
      
      int lenMin = INT_MAX;//max
      for(int i = 0; i < stringNum; ++i)
          lenMin = strs[i].size() < lenMin ? strs[i].size(): lenMin;           
      if( lenMin == 0 )  return "";
    
      int pos = 0;
      for( int i = 0; i < lenMin; ++i)
      {
          char currentChar = strs[0][i]; 
          for(int j=1;j< stringNum;++j)
          {  
            if( strs[j][i] != currentChar )
               return ( strs[0].substr(0,pos) );
          }
          ++pos;
      }
      return( strs[0].substr(0,pos) );
    }
{% endhighlight %}
###3. Notes:
if后面多了个分号，看了好半天才改对。
