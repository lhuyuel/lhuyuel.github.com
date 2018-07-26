---
layout: post
title: "Aligned Memory Allocation"
description: ""
category: Programming
tags: [CPP, Programming]
---
###1. What & Why
CPU access memory most efficiently when accessing in certain unit, it is better if the allocated memory lies in the certain unit boundary. For example, let’s assume a CPU architecture is most efficient when memory is aligned every 4 bytes. When it accesses memory located at multiples of 4 in its address space, it is much faster than when the accessed memory is at 0×03 or 0×05.<br>
The Unix malloc functions usually return aligned memory space, while Windows version doesn’t. Instead, the Windows provide _aligned_malloc().

###2. How
+ step1: allocate enough spare space;
+ step2: convert the void pointer to a char pointer;
+ step3: saves the address which points where the whole allocated memory starts.( for free() )<br>
<b>[This post](http://jongampark.wordpress.com/2008/06/12/implementation-of-aligned-memory-alloc) has detailed explanation.</b>
