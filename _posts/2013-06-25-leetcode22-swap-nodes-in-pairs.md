---
layout: post
title: "LeetCode[22]: Swap Nodes in Pairs"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Given a linked list, swap every two adjacent nodes and return its head.<br>
For example,<br>
Given 1->2->3->4, you should return the list as 2->1->4->3.<br><br>
Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.
</blockquote>
###2. My solution：
At first, I didn't notice there's a line saying "You may <b>not</b> modify the values in the list, only nodes itself can be changed"...<br>
So intended to avoid mess of pointers, I came up with only swaping the val in the node. Like this:
{% highlight cpp linenos %}
    ListNode *swapPairs(ListNode *head) {
        ListNode* cur = head;
        while( cur && cur->next )
        {
            int tmp = cur->val;
            cur->val = cur->next->val;
            cur->next->val = tmp;
            cur = cur->next->next;
        }
        return head;
    }
{% endhighlight %}

But it seems that the problem expecting us to modify pointers only... <br>
After drawing three pages of nodes and pointers on paper, finally, it works.<br>
Here's my solution:
{% highlight cpp linenos %}
    ListNode *swapPairs(ListNode *head) 
    {
        ListNode* cur = head;
        if( !cur || !cur->next )
            return head;
        
        ListNode* pre = NULL;
        ListNode* nxt = cur->next;
        
        while( cur && cur->next )
        {
            if( !pre ) 
                head = cur->next;
            else
                pre->next = nxt;
                
            cur->next = nxt->next;
            nxt->next = cur;
            pre = cur;
            cur = cur->next;
            
            if(cur)
                nxt = cur->next;
            else
                nxt = NULL;         
        }
        
        return head;
        
    }
{% endhighlight %}
