---
layout: post
title: "Learning Python"
date: 2014-06-30 21:12:58 +0800
comments: true
categories: 
---

What is Python?

Python is a modern object-oriented programming language that's well-suited for a variety of uses, from simple scripts to complex web applications. Using third-party tools, such as Py2exe or Pyinstaller, Python code can be packaged into standalone executable programs.


This Blog will be updated during my free time to share all the knowledge I learned in studing this powerful porgramming language.

Before we start make sure that you have the python installed in your computer, If you are using linux or mac chances are that you already have python preinstalled in your computer.

In this blog I'll be using python 3, and sublime as my text editor. you can use what ever text editor you like such as eclipse to help you in you coding and compiling in one development application, but I prefer the traditional way of doing it using a separate text editor and command line it running python.


I will be starting this blog by creating the traditional hello world program.

<pre>
#!/usr/bin/python3
print("Hello, World!")
</pre>

to run python, save the file first with .py extension ex. helloWorld.py then you should compile it by typing in the terminal <code>cat helloWorld.py</code> then to run the program type in <code>./helloWorld.py</code> if you got an Permission denied error type <code>chmod 755 helloWorld.py</code> to make it executable.

looking in the helloWorld.py the line <code>#!/usr/bin/python3</code> is called shebang line, in unix based operating system such as linux and mackintosh, this is the path to the python interpreter which tells the computer to use it to run the program.
while the <code>print("Hello, World")</code> is use to display the a text.


Assigning Values
<pre>
a, b = 1, 2
</pre>

1 will be assigned in "a", and 2 will be assigned in "b", so "a" will hold the value of 1 and "b" will hold the value of 2.


Conditional Statement
<pre>
a, b = 1, 2

if a < b:
	print("a ({}) is less than b ({})".format(a, b))
else:
	print("a ({}) is not less than b ({})".format(a, b))
</pre>

In python in creating conditional statement, you type the condition followed by colon then the indented code, this is how you create a block of codes in python.

<-- TO BE CONTINUED -->