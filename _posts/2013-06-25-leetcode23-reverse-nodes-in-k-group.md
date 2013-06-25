---
layout: post
title: "LeetCode[23]: Reverse Nodes in K Group"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem：
<blockquote>
Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.<br>
If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.<br>
You may not alter the values in the nodes, only nodes itself may be changed.<br>
Only constant memory is allowed.<br>
<br>
For example,<br>
Given this linked list: 1->2->3->4->5<br>
For k = 2, you should return: 2->1->4->3->5<br>
For k = 3, you should return: 3->2->1->4->5 <br>
</blockquote>
###2. My solution：
My idea is that, keep a fast pointer go ahead to check if there are enough nodes(k) left. Use a pointer called  subEnd to remember the end of the previous sub linked list, and a pointer called subHead to remember the head of current sub-linked list.<br> 
If not enough nodes left, just return current result.<br>
else, reverse the current sub linked list(nodes between current subHead and fast pointer).<br>

It looks like this, suppose k=3: 
{% highlight cpp linenos %}
            subEnd subHead     fast
	        |   |           |
	3   2   1   4   5   6   7   8   9
	            |   |   |
	           pre cur nxt
{% endhighlight %}
####Code:
{% highlight cpp linenos %}
    ListNode *reverseKGroup(ListNode *head, int k) 
    {
        if( !head || !head->next || k == 1 ) 
            return head;

        ListNode* fast = head;
        ListNode* subHead = head;
        ListNode* subEnd = NULL;  
        ListNode* pre, *cur, *nxt;

        while(fast)
        {   //check if there are enough nodes left
            for(int i = 0; i < k; ++i )
            {
                if( !fast ) 
                    return head;
                fast = fast->next;
            }
            
            pre = subHead;
            cur = subHead->next;
            nxt = cur->next;

            //reverser the sub linked list
            while( cur != fast )
            { 
                pre->next = nxt;
                cur->next = subHead;
                subHead = cur;
                if( subEnd == NULL )
                    head = subHead;
                else
                    subEnd->next = subHead;
                
                cur = nxt;
                if( cur )
                    nxt = cur->next;       
            }
            subHead = fast;
            subEnd = pre;
        }
        
        return head;    
  }
{% endhighlight %}
