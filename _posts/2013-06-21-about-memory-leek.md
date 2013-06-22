---
layout: post
title: "About Memory Leek"
description: ""
category: 
tags: [C++]
---
{% include JB/setup %}
*Grab from [codeguru](http://forums.codeguru.com/showthread.php?312742-Visual-C-Debugging-How-to-manage-memory-leaks) *
###1. What is a memory leak?
The failure to properly deallocate memory that was previously allocated.<br>

###2. What are the consequences of memory leaks?
Programs that leak large amounts of memory, or leak progressively, may display symptoms ranging from poor (and gradually decreasing) performance to running out of memory completely. Worse, a leaking program may use up so much memory that it causes another program to fail, leaving the user with no clue to where the problem truly lies. In addition, even harmless memory leaks may be symptomatic of other problems.<br>



