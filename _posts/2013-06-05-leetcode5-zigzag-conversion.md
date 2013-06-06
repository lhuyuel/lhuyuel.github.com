---
layout: post
title: "LeetCode[5]: Zigzag Conversion"
description: ""
category: 练习题
tags: [C++, LeetCode,  刷题]
---
{% include JB/setup %}
###1. 问题：
<blockquote>
 The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)<br>

P   A   H   N<br>
A P L S I I G<br>
Y   I   R<br>
<br>
And then read line by line: "PAHNAPLSIIGYIR"<br>
<br>
Write the code that will take a string and make this conversion given a number of rows:<br>
<br>
string convert(string text, int nRows);<br>
<br>
convert("PAYPALISHIRING", 3) should return "PAHNAPLSIIGYIR".<br>
</blockquote>
###2.代码：
{% highlight cpp linenos %}
/*use a flag called "down" to mark if it should go down or up.
It's very nice to use vector<char> to store lines.
Be careful when nRows=1.*/
string convert(string s, int nRows) {    
        int len = s.size();
        int i = 0;
        int row = 0;
        bool down = true;
        if( nRows == 1 ) return s;
        vector< vector<char> > matrix(nRows);
        
	while( i < len )
        {
            if(down)
            {
                if( row < nRows )
                {
                    matrix[row++].push_back( s[i++] );
                }
                else
                {
                    row -= 2;
                    down = false;
                }
            }
            else
            {
                if(row >= 0)
                {
                    matrix[row--].push_back(s[i++]);
                }
                else
                {
                    row += 2;
                    down = true;
                }
            }
        }
	
	//generate the result string
        vector<char>::iterator iter1;
        string r="";
        for(int i=0;i< nRows;++i)
        {
            iter1 = matrix[i].begin();
            for(;iter1!= matrix[i].end();++iter1)
            r += *iter1;
        }
        return r;
    }
{% endhighlight %}

###3. 题后唠叨：
都已经在注释里了，嗯。
