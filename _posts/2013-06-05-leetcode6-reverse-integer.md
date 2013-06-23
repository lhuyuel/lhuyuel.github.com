---
layout: post
title: "LeetCode[6]: Reverse Integer"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Reverse digits of an integer.<br>
<br>
Example1: x = 123, return 321<br>
Example2: x = -123, return -321
</blockquote>
###2. My solution：
这是最开始想到的代码：
{% highlight cpp linenos %}

int reverse(int x) 
{
        vector<int> r;
        int reslt = 0;
        while( x >= 1 || x<=-1 )
        {
               r.push_back( x % 10 );
               x /= 10;
        }
        
	for(int i=0; i < r.size(); ++i )
        {
            reslt += r[i]*( pow(10, r.size()-i-1 ) );
        }

        return reslt;
}
{% endhighlight %}
就一个整数反转还用了两个循环,指数pow和一个vector，太丧失了，得改。<br>
于是变成了这样：

{% highlight cpp linenos %}
int reverse(int x)
{
    	int reslt = 0;

    	while(x != 0) 
	{
        	reslt = reslt*10 + x % 10;
        	x /= 10;
    	}
    	return reslt;
}
{% endhighlight %}


###3. Notes：
别忘了负数
