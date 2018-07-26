---
layout: post
title: "ClassicPuzzles[0]: Towers of Hanoi"
description: ""
category: Classic Puzzles
tags: [Algorithm, ClassicPuzzles]
---
###1. Original Problem:
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
###3. Variations:
#### Bicolor Tower of Hanoi  
<b>Solution:</b>
{% highlight cpp linenos  %}
void BicolorHanoi(int n, char srcPeg, char auxPeg, char dstPeg )
{
	Hanoi(n,srcPeg,auxPeg,dstPeg);  //Step1
	--n;
	while(n > 0)  //Step2 
	{
		Hanoi(n,auxPeg,srcPeg,dstPeg); 
		--n;
		//exchange auxPeg and dstPeg
		char temp = auxPeg;
		auxPeg = dstPeg;
		dstPeg = temp;
	}
}
{% endhighlight %}
Here's a simple illustration:  
(R=Red and Y=Yellow)   
Before:
{% highlight cpp  %}
	     |           |           |
	    R|R          |           |
	    Y|Y          |           |
	  RRR|RRR        |           |
	  YYY|YYY        |           |
	RRRRR|RRRRR      |           |
	YYYYY|YYYYY      |           |     
{% endhighlight %}

After first step:  //Hanoi(n,srcPeg,auxPeg,dstPeg);
{% highlight cpp  %}
	     |           |           |
	     |           |          R|R
	     |           |          Y|Y
	     |           |        RRR|RRR
	     |           |        YYY|YYY
	     |           |      RRRRR|RRRRR
	     |           |      YYYYY|YYYYY
{% endhighlight %}

After loop once, it looks like this:
{% highlight cpp  %}
	     |           |           |
	     |          R|R          |
	     |          Y|Y          |
	     |        RRR|RRR        |
	     |        YYY|YYY        |
	     |      RRRRR|RRRRR YYYYY|YYYYY
{% endhighlight %}

After loop2, it looks like this:
{% highlight cpp %}
	     |           |           |
	     |           |          R|R
	     |           |          Y|Y
	     |           |        RRR|RRR
	     |           |        YYY|YYY
	     |      RRRRR|RRRRR YYYYY|YYYYY
{% endhighlight %}

After loop3:
{% highlight cpp %}
	     |           |           |
	     |           |           |
	     |          R|R          |
	     |          Y|Y          |
	     |        RRR|RRR     YYY|YYY
	     |      RRRRR|RRRRR YYYYY|YYYYY
{% endhighlight %}

After loop4:
{% highlight cpp %}
	     |           |           |
	     |           |           |
	     |           |          R|R
	     |           |          Y|Y
	     |        RRR|RRR     YYY|YYY
	     |      RRRRR|RRRRR YYYYY|YYYYY
{% endhighlight %}

After loop5:
{% highlight cpp  %}
	     |           |           |
	     |           |           |
	     |           |           |
	     |          R|R         Y|Y
	     |        RRR|RRR     YYY|YYY
	     |      RRRRR|RRRRR YYYYY|YYYYY
{% endhighlight %}

#### Three color Tower of Hanoi:
Similar to Bicolor.
