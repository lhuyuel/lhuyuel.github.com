---
layout: post
title: "File Reading in C++"
description: "using ifstream and getline"
category: learning
tags: [C++]
---
{% include JB/setup %}
###Read file by line and word

Suppose we have a file named 'data.txt', which contains the following:

	It was the best of times, it was the worst of times,
	it was the age of wisdom, it was the age of foollishness,
	it was the epoch of belief, it was the epoch of incredulity

{% highlight cpp linenos %}
#include <iostream>  
#include <fstream>  
#include <string>  

using namespace std;

//输出空行 
void OutPutAnEmptyLine() 
{ 
   cout<<"\n"; 
} 
  
//读取方式: 逐词读取, 词之间用空格区分.
//read data from the file, Word By Word 
//when used in this manner, we'll get space-delimited bits of text from the file 
//but all of the whitespace that separated words (including newlines) was lost. 
void ReadDataFromFileWBW() 
{ 
    ifstream fin("data.txt"); 
    string s; 
    while( fin >> s ) 
    { 
        cout << "Read from file: " << s << endl;    
    }
}
  
//读取方式: 逐行读取, 将行读入字符数组, 行之间用回车换行区分 
//If we were interested in preserving whitespace, 
//we could read the file in Line-By-Line using the I/O getline() function. 
void ReadDataFromFileLBLIntoCharArray() 
{ 
    ifstream fin("data.txt"); 
    const int LINE_LENGTH = 100; 
    char str[LINE_LENGTH]; 
    while( fin.getline(str,LINE_LENGTH) ) 
    { 
        cout << "Read from file: " << str << endl;  
    } 
} 
  
//读取方式: 逐行读取, 将行读入字符串, 行之间用回车换行区分 
//If you want to avoid reading into character arrays, 
//you can use the C++ string getline() function to read lines into strings 
void ReadDataFromFileLBLIntoString() 
{ 
    ifstream fin("data.txt"); 
    string s; 
    while( getline(fin,s) ) 
    { 
        cout << "Read from file: " << s << endl;   
    } 
} 
  
//带错误检测的读取方式 
//Simply evaluating an I/O object in a boolean context will return false 
//if any errors have occurred 
void ReadDataWithErrChecking() 
{ 
    string filename = "dataFUNNY.txt"; 
    ifstream fin( filename.c_str()); 
    if( !fin ) 
    { 
        cout << "Error opening " << filename << " for input" << endl;     
        exit(-1);    
    }
} 
  
int main() 
{
    ReadDataFromFileWBW(); //逐词读入字符串 
    OutPutAnEmptyLine(); //输出空行
  
    ReadDataFromFileLBLIntoCharArray(); //逐行读入字符数组
    OutPutAnEmptyLine(); //输出空行
  
    ReadDataFromFileLBLIntoString(); //逐行读入字符串
    OutPutAnEmptyLine(); //输出空行
  
    ReadDataWithErrChecking(); //带检测的读取 
    return 0;
} 
{% endhighlight %}

Here is the output:

	Read from file: It 
	Read from file: was
	Read from file: the
	Read from file: best
	Read from file: of 
	Read from file: times,
	Read from file: it
	Read from file: was
	Read from file: the
	Read from file: worst
	Read from file: of
	Read from file: times,
	Read from file: it
	Read from file: was
	Read from file: the
	....	
	
	Read from file: It was the best of times, it was the worst of times,
	Read from file: it was the age of wisdom, it was the age of foollishness,
	Read from file: it was the epoch of belief, it was the epoch of incredulity

	Read from file: It was the best of times, it was the worst of times,
	Read from file: it was the age of wisdom, it was the age of foollishness,
	Read from file: it was the epoch of belief, it was the epoch of incredulity

	Error opening  dataaaaa.txt for input

	Press any key to continue



###Check if there is a newline bit
{% highlight cpp linenos %}
#include <iostream>  
#include <fstream>  
#include <string> 

ifstream fin(argv[1]); 
string word;
while( fin >> word ) 
{
	lines.push_back(word);
	if( fin.peek() == '\n' )
	{//newline detected
	}
}
{% endhighlight %}


###Check if it is the end of file
{% highlight cpp linenos %}
if( fin.peek() == EOF) 
{
	if (fin.eof())// end of file
	{//do something here
	}
}
{% endhighlight %}


