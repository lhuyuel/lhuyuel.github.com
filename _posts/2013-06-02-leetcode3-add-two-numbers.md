---
layout: post
title: "LeetCode[3]: Add Two Numbers"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}

###1. 问题：
<blockquote>
You are given two linked lists representing two non-negative numbers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.<br>
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)<br>
Output: 7 -> 0 -> 8
</blockquote>
###2. 我的代码：
和别人的比起来显得好冗长啊。。。
{% highlight cpp linenos %}
ListNode *addTwoNumbers(ListNode *l1, ListNode *l2) {
	ListNode *p1 = l1;
	ListNode *p2 = l2;
	ListNode *l3 = NULL;//mark the head of l3
	ListNode *p3 = NULL;
	ListNode *tmp;
	bool carryFlag = false;
	while( p1!=NULL && p2!=NULL )
	{
		tmp = new ListNode(0);
		if( ( p1->val + p2->val + carryFlag) >= 10 )
		{
			tmp->val= ( p1->val + p2->val + carryFlag) - 10;
			carryFlag = true;
		}
		else
		{
			tmp->val = ( p1->val + p2->val+ carryFlag ); 
			carryFlag = false;
		}
		//p3->next = &tmp;
		if(l3 == NULL)
		{// head
			l3 = tmp;
			p3 = tmp;
		}
		else
		{	p3->next = tmp;
			p3 = p3->next;
		}
		
		p1 = p1->next;
		p2 = p2->next;
	}//end of while

	while(p1)
	{//deal with the remaining part of l1
		tmp= new ListNode(0);
		if( ( p1->val + carryFlag) >= 10 )
		{
			tmp->val = ( p1->val + carryFlag) - 10; 
			carryFlag = 1;
			tmp->next = NULL;
		}
		else 
		{
			tmp->val = ( p1->val + carryFlag ); 
			carryFlag = 0;
			tmp->next = NULL;
		}
		p3->next = tmp;
		p3 = p3->next;
		p1= p1->next;
	}

	while(p2)
	{//deal with the remaining part of l2
		tmp= new ListNode(0);
		if( ( p2->val + carryFlag) >= 10 )
		{
			tmp->val = ( p2->val + carryFlag) - 10; 
			carryFlag = 1;
		}
		else 
		{
			tmp->val = ( p2->val + carryFlag ); 
			carryFlag = 0;
		}
		tmp->next = NULL;
		p3->next = tmp;
		p3 = p3->next;
		p2 = p2->next;
	}

	if( p1 == NULL &&p2 == NULL && carryFlag == 1 )
	{
		tmp = new ListNode(0);
		tmp->val = 1;
		p3->next = tmp;
		p3 = p3->next;
	}

	return l3;
    }
{% endhighlight %}

贴一个比较喜欢的版本：
{% highlight cpp linenos %}
ListNode *addTwoNumbers(ListNode *l1, ListNode *l2) {
	ListNode *s = new ListNode(0);
	ListNode *c = s;
	bool f1 = (NULL != l1);
	bool f2 = (NULL != l2);
	while(1) {
		if(f1) {
			c->val += l1->val;
			l1 = l1->next;
			f1 = (NULL != l1);
		}
		if(f2) {
			c->val += l2->val;
			l2 = l2->next;
			f2 = (NULL != l2);
		}
		bool carry = c->val / 10;
		c->val %= 10;
		if(f1 || f2 || carry) {
			c->next = new ListNode(carry);
			c = c->next;
		} else
			break;
	}
	return s;
}
{% endhighlight %}
	
###3. 题后唠叨：
改了很久才改对。<br>
问题出在最开始使用“ListNode tmp(0);” 创建对象,出现runtime error。<br>
new出来的存储在堆上，而是用类名创建的存储在栈上。<br>
前者是运行时分配空间，需要自己释放；后者在运行前就已经分配好空间，函数结束后会自动释放。<br>
具体可以看这篇。<br>
