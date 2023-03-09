---
layout: page
title: Problem Set 0
---

# 6.00: Introduction to Computer Science and Programming
##### Handed out: Thursday, September 4, 2008
* * *
## Problem Set 0

<p>&nbsp;</p>

#### Introduction

This problem set will introduce you to the programming environment IDLE and to programming
in Python, as well as to our general problem set structure. In this problem set, you will install
IDLE, write a simple Python program, and hand it in. Be sure to read this problem set
thoroughly, especially the sections of Collaboration and the Handin Procedure.

#### Collaboration

You may work with other students. However, each student should write up and hand in his or her
assignment separately. Be sure to indicate with whom you have worked. For further detail,
please review the collaboration policy as stated in the syllabus.

#### Installing Python and IDLE

Follow the steps in the Getting Started: Python and IDLE handout for installing Python and IDLE
onto the machine you plan to be using this term. You may skip the installation step if you are
working on an Athena machine.

Familiarize yourself with Python and IDLE using the exercises given in the handout. Once you
are ready, proceed to the programming part of this assignment. 

* * *
#### A Very Simple Program: Entering and Printing Your Name

Write a program that does the following in order:

1. Asks the user to enter his/her last name.
2. Asks the user to enter his/her first name.
3. Prints out the user’s first and last names in that order. 
<div class="alert alert-danger">
An example of an interaction with your program is shown below (the words printed after the <code>$</code> are from the computer, based on your commands, the words with a <code>**</code> are a user’s input):
</div>

```
$~:Enter your last name:
**Grimson
$~:Enter your first name:
**eric
$~:eric
Grimson
```

<div class="alert alert-warning">
<h3>HINTS:</h3>
To see how to use the command, you may find it convenient to look at the input and
output section of the Python Wikibook. This will show you how to use statements to
print out values of strings.
<p></p>
To see how to read input from a user’s console into the Python environment, you may find
it convenient to look at the same section (see for example the function).
<p></p>
Remember that if you want to hold onto a value, you need to store it in a variable (i.e., give
it a name to which you can refer when you want that value). You may find it convenient to
look at the variables and strings section of the Python Wikibook.
</div>
### Hand-In Procedure

1. **Save** - Save your code in ps0.py . Do not ignore this step or save your file(s) with different names.
2. **Time and Collaboration Info** - At the start of each file, in a comment, write down the number of hours (roughly) you spent on the problems in that part, and the names of the people you collaborated with.

<p></p>
<div class="alert alert-info">
<h3>NOTE:</h3>
Since this problem is asking for input be sure to select "INTERACTIVE" in the IDE below, otherwise you get a traceback error
</div>
* * *

{% doodle %}
#!/usr/bin/env python

""" Working with User input.
DESCRIPTION = We are going to ask the user for a LAST name and then a FIRST name, and then print out the FIRST name first, and LAST name last.
"""

__author__    = "Yosi Leyid"
__copyright__ = "Copyright 2023, $HASIDIC_DEV_GROUP"
__date__      = "2023/03/08"
__email__     = "yosi@hasidic.dev"
__license__   = "MPL-2.0"
__version__   = "0.0.1"
# Problem Set 0
# Name: Your Name
# 
# Time: 3:00
#
#----your code goes below----
{% enddoodle %}