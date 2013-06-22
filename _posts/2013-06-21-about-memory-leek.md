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

###3. How can a memory leak appear?
* Pointer goes out of scope
* "Lost" pointers
* Wrong usage of new/delete<br>
{% highlight cpp %}
	double* d = new double[10];
	delete d; // delete d[0]; 
		  // must use delete [] d;
{% endhighlight %}
* Misplaced delete
{% highlight cpp %}
	int *i;
	while(someCondition)
	{
	  i = new int;
	  // some code
	}
	delete i;
{% endhighlight %}
###4.  How can I find if my program has memory leaks?
When you run your program under the debugger, '_CrtDumpMemoryLeaks()' displays memory leak information in the output window. The memory leak information looks like this:<br>

	Detected memory leaks!
	Dumping objects ->
	D:\VisualC++\CodeGuru\MemoryLeak\MemoryLeak.cpp(67) : {60} 
	normal block at 0x00324818, 4 bytes long.
	Data: <,   > 2C 00 00 00 
	Object dump complete.

If you do not use the '#define _ CRTDBG_ MAP_ALLOC' statement, defined in 'crtdbg.h', included in 'afx.h', which is by default included in your 'stdafx.h', the memory leak dump would look like this:

	Detected memory leaks!
	Dumping objects ->
	{60} normal block at 0x00324818, 4 bytes long.
	Data: <,   > 2C 00 00 00 
	Object dump complete.

Without '_CRTDBG_MAP_ALLOC' defined, the display shows: 
* The memory allocation number (inside the curly braces).
* The block type (normal, client, or CRT).
* The memory location in hexadecimal form.
* The size of the block in bytes.
* The contents of the first 16 bytes (also in hexadecimal).
<br><br>
With '_CRTDBG_MAP_ALLOC' defined, the display also shows you the file where the leaked memory was allocated. The number in parentheses following the filename (67, in this example) is the line number within the file.

###5. What is the effect of using "_CRTDBG_MAP_ALLOC" on the C++ "new" and "delete" operators?
When the '_CRTDBG_MAP_ALLOC' flag is defined in the debug version of an application, the base version of the heap functions are directly mapped to their debug versions. This flag is only available when the '_DEBUG' flag has been defined in the application.<br>
<br>
The debug versions of the C run-time library contain debug versions of the C++ 'new' and 'delete' operators. If your C++ code defines 'CRTDBG_MAP_ALLOC', all instances of new are mapped to the debug version, which records source file and line number information.<br>
<br>
If you want to use the '_CLIENT_BLOCK' allocation type, do not define 'CRTDBG_MAP_ALLOC'. Instead, you must call the Debug version of the 'new' operator directly or create macros that replace the 'new' operator in debug mode, as shown in the following example. The debug version of the 'delete' operator works with all block types and requires no changes in your program when you compile a release version.

