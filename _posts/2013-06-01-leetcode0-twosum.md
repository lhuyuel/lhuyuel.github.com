---
layout: post
title: "LeetCode[0]: TwoSum"
description: ""
category: 练习题
tags: [C++, LeetCode, 刷题]
---
###1. Problem:

<blockquote>
Given an array of integers, find two numbers such that they add up to a specific target number.
<br>
The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.<br>
You may assume that each input would have exactly one solution.<br>
Input: numbers={2, 7, 11, 15}, target=9<br>
Output: index1=1, index2=2
</blockquote>
###2. Solusion:
{% highlight cpp linenos %}
 vector<int> twoSum(vector<int> &numbers, int target)
 {
        vector<int> rslt;
        int index1,index2;
	for( int i = 0; i < numbers.size()-1; ++i )
	{
		int x = numbers[i];
		int y = target - x;

		for( int j = i+1; j < numbers.size(); ++j )
		{
			if( numbers[j] == y )
			{
				index1 = i;
				index2 = j;
				rslt.push_back(index1+1);
				rslt.push_back(index2+1);
				return(rslt);
			}
		} 
	}
}
{% endhighlight %}

###3. Notes：
1. *zero-based* , means Index count from 1 not 0  
