---
layout: post
title: "LeetCode[4]: Longest Palindromic Substring"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题, 重写]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Given a string S, find the longest palindromic substring in S. You may assume that the maximum length of S is 1000, and there exists one unique longest palindromic substring.
</blockquote>
###2. My solution：
每个回文序列都会有个中心。把字符串第一个字符开始的每一个字符选作中心（设index=i），检查中心两边字符是否相同（i-1 和i+1），相同则向两边展开最长子回文序列变成s.substr(i-1,i+1), 这样循环；不相同则跳出循环记录长度，选取新的中心。<br>
思路是对的，但是从思路转化成代码还是有很多问题。。。下面是别人的一段代码，很简练：<br>
Time Compelxity: O(N^2)<br>

{% highlight cpp linenos %}
string expandAroundCenter(string s, int c1, int c2) {
    int l = c1, r = c2;
    int n = s.length();
    while (l >= 0 && r <= n-1 && s[l] == s[r])
    {
        l--;
        r++;
    }
    return s.substr(l+1, r-l-1);
}

string longestPalindrome(string s) {
    int n = s.length();
    if (n == 0) return "";
    string longest = s.substr(0, 1);  // a single char itself is a palindrome
    for (int i = 0; i < n-1; i++) 
    {
        string p1 = expandAroundCenter(s, i, i);
        if (p1.length() > longest.length())
            longest = p1;

        string p2 = expandAroundCenter(s, i, i+1);
        if (p2.length() > longest.length())
            longest = p2;
    }
    return longest;
}
{% endhighlight %}
###3. Notes：
[这里](http://discuss.leetcode.com/questions/178/longest-palindromic-substring)有非常详细的解法和说明：<br>
