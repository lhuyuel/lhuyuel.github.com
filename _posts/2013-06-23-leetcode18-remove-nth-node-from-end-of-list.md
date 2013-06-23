---
layout: post
title: "LeetCode[18]: Remove Nth Node From End of List"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. Problem
<blockquote>
Given a linked list, remove the nth node from the end of list and return its head.<br>
For example,<br>
Given linked list: 1->2->3->4->5, and n = 2.<br>
After removing the second node from the end, the linked list becomes 1->2->3->5.<br>
Note:<br>
Given n will always be valid.<br>
Try to do this in one pass.
</blockquote>
###2. My Solution
{% highlight cpp linenos %}
    ListNode *removeNthFromEnd(ListNode *head, int n) {
 
        ListNode* fast = head;
        ListNode* slow= head;
        ListNode* pre = NULL;
        
        if( slow->next == NULL ) 
            return NULL;
        while( n > 1 )
        {
            fast = fast->next;
            --n;
        }
        while( fast->next != NULL )
        {
            pre = slow;
            slow = slow->next;
            fast = fast->next;
        }

        if(pre==NULL)//means head will be deleted
        {
            ListNode* tmp =  head;
            head = head->next;
            delete tmp;
        }
        else
        {
            pre->next = slow->next;
            delete slow;
        }  
        
        return head;
    }
{%endhighlight%}

###3. Notes:
小心head和end

