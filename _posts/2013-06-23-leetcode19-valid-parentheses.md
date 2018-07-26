---
layout: post
title: "LeetCode[19]: Valid Parentheses"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
###1. Problem：
<blockquote>
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.<br>
The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.
</blockquote>
###2. My solution：
{% highlight cpp linenos %}
    bool isValid(string s) {
    
    if( s.size()%2 != 0 )
        return false;
    
    stack<char> stk;
    for( int i = 0; i < s.size(); ++i )
    {
         if( s[i] == '{' ||s[i] == '[' || s[i] == '(' )
            stk.push( s[i] );
         else
         {
             if( stk.empty() )
                return false;
             
             if( (s[i]==')' && stk.top()=='(') ||
                 (s[i]==']' && stk.top()=='[') ||
                 (s[i]=='}' && stk.top()=='{') )
            {
                stk.pop();
            }       
         }
    }
    return stk.empty();
}
{% endhighlight %}
