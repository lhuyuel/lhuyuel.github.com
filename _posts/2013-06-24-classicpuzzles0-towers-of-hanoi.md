---
layout: post
title: "ClassicPuzzles[0]: Towers of Hanoi"
description: ""
category: Classic Puzzles
tags: [Algorithm, ClassicPuzzles]
---
{% include JB/setup %}
###1. Problem:
<blockquote>
You have a stack of discs, from largest to smallest, that slide on to the first peg of a three peg board. Your goal is to move the entire stack of discs from the first peg to the third peg. However, you can only move the topmost disc of any peg, and smaller discs must always be placed on larger discs. How many moves will it take? 
</blockquote>
<br>
###2. Solution:
Suppose we have n discs in total.
+ Step1: Move the top n-1 discs from the source peg to the auxiliary peg.
+ Step2: Move the nth disc from the source peg to destination peg.
+ Step3: Move those n-1 discs from auxiliary peg to destination peg.
<br><br>
<b>Code in C++:</b>
{% highlight cpp linenos %}
void Hanoi( int n, char srcPeg, char auxPeg, char dstPeg )
{
	if( n == 1 )
		cout<<"Move disc 1 from"<<srcPeg<<"to"<<dstPeg<<endl;
	Hanoi( n-1, srcPeg, dstPeg, auxPeg );
	cout<<"Move disc"<<n<<"from"<<srcPeg<<"to"<<dstPeg<<endl;
	Hanoi( n-1, auxPeg, dstPeg, srcPeg );
}
{% endhighlight %}
