---
layout: post
title: "GPU[0]: CPU vs GPU"
description: ""
category: GPU
tags: [GPU]
---
{% include JB/setup %}
*grab from [here](http://blogs.nvidia.com/blog/2009/12/16/whats-the-difference-between-a-cpu-and-a-gpu/) *  
Architecturally, the CPU is composed of a only few cores with lots of cache memory that can handle a few software threads at a time. In contrast, a GPU is composed of hundreds of cores that can handle thousands of threads simultaneously. The ability of a GPU with 100+ cores to process thousands of threads can accelerate some software by 100x over a CPU alone. What’s more, the GPU achieves this acceleration while being more power- and cost-efficient than a CPU.  
<br>
GPU-accelerated computing has now grown into a mainstream movement supported by the latest operating systems from Apple (with OpenCL) and Microsoft (using DirectCompute). The reason for the wide and mainstream acceptance is that the GPU is a computational powerhouse, and its capabilities are growing faster than those of the x86 CPU.  
<br>
In today’s PC, the GPU can now take on many multimedia tasks, such as accelerating Adobe Flash video, transcoding (translating) video between different formats, image recognition, virus pattern matching and others. More and more, the really hard problems to solve are those that have an inherent parallel nature – video processing, image analysis, signal processing. The combination of a CPU with a GPU can deliver the best value of system performance, price, and power.
