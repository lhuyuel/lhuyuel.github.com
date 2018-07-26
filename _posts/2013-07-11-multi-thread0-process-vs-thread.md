---
layout: post
title: "Multi Thread[0]: Process vs Thread"
description: ""
category: accumulating
tags: [Multi-thread]
---
*From cracking the coding interview*
###1. Process
A process can be thought of as an instance of a program in execution. A process is an independent entity to which system resources are allocated. Each process is executed in a separate address space, and one process cannot access the variables and data structures of another process, If a process wishes to accesss anothre process's resources, inter-process communications have to be used. These include pipes, files, sockets, and other forms.

###2. Thread
A thread uses the same stack space of a process, and multiple thereads share partsof their states. Typically, one allows multiple threads to read and write the same memory. This is very different from processes, which cannot directly access the memory of another process. Each thread still has its own registers and its own stack, but other threads can read and write the stack memory.
