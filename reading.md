---
layout: page
title: Reading List
---

# {{page.title}}

Below, you’ll find a set of online resources designed to accompany the 6.00 lectures. We’ve found that the readings are generally more effective when done after the lecture, though you are of course welcome to read them at any time.

## General References

A textbook for 6.00 is now available. The book and the course lectures parallel each other, though there is more detail in the book about some topics. The book is NOT required. We will not be referring to it in assignments or depending upon it to cover holes in the lectures.

<pre>
Author: Guttag, John 
Introduction to Computation and Programming Using Python
MIT Press, 2013
ISBN: 9780262519632
</pre>

An updated version of the textbook is also available:

<code>
Author: Guttag, John
Introduction to Computation and Programming Using Python: 
"With Application to Understanding Data"
MIT Press, 2016
ISBN: 9780262529624
</code>

If you choose not to purchase this book, you will probably find it useful to buy or borrow another book that covers Python. You might check your local public library’s resources, or search online for a free Python text, such as How to Think Like a Computer Scientist or An Introduction to Python.

# Python Programming

## The Python Tutorial

### Lectures 1-3

- Chapter 1: [The Way of the Program](/books/compSci/chpt-1-the-way)
- Chapter 2: [Variables and statements](/books/compSci/chpt-2-variables)
- Strings: [Variables and strings](/books/pyProgramming/strings)
- "names": [Other languages have “variables](/books/pythonista/variables)
- For PS0: [Input/output](/books/pyProgramming/io)
- Chapter 4: [Conditionals](/books/compSci/chpt-4-conditionals)
- Iteration: [Loops](/books/pyProgramming/loops)
- Tuples: [Tuples](/books/pyTutorial/tuples)
- More on [traversing and slicing strings](/books/compSci/chpt-7-slicing)

### Lecture 4

- Chapter 3: [Functions](/books/compSci/chpt-3-functions)
- Chapter 5: [Fruitful Functions](/books/compSci/chpt-5-fruitful)
- Chapter 4: [Recursion](/books/compSci/chpt-4-conditionals)

### Lecture 5

- [Numbers](/books/pyTutorial/numbers)
- [Successive approximation](https://en.wikipedia.org/wiki/Newton-Raphson_method) Wikipedia article on Newton’s method

### Lecture 6

- Chapter 8: [Lists](/books/compSci/chpt-8-lists)
- Chapter 10: [Dictionaries](/books/compSci/chpt-10-dicts)
- As a reference: the Python Tutorial section on [lists and dictionaries](https://docs.python.org/3/tutorial/datastructures.html) (feel free to skip 5.1.3 and 5.1.4)

### Lectures 7-8

- Asymptotic notation: Section 3 from the Spring 2005 6.042 lecture notes on OCW [(PDF)](https://ocw.mit.edu/courses/6-00-introduction-to-computer-science-and-programming-fall-2008/resources/l11_sums2/)
- [Order of growth](/books/thinkcomplex/graphs)
- Binary search: [Wikipedia](https://en.wikipedia.org/wiki/Binary_search#Implementations)

### Lectures 9-10

- Selection sort: [Wikipedia](http://en.wikipedia.org/wiki/Selection_sort)
- Insertion sort: [Wikipedia](http://en.wikipedia.org/wiki/Insertion_sort)
- Merge sort: [Wikipedia](http://en.wikipedia.org/wiki/Merge_sort)

### Lecture 12

The [knapsack problem](#the-knapsack-problem) and [dynamic programming](#dynamic-programming)

### Lectures 14-16

Lots of reading on classes:

- Chapter 12: [Classes & Objects](/books/compSci/chpt-12-objects)
- Chapter 13: [Classes & Functions](/books/compSci/chpt-13-classes)
- Chapter 14: [Classes & Methods](/compSci/chpt-14-methods)
- Chapter 15: [Sets of Objects](/compSci/chpt-15-obj-sets)
- Chapter 16: [Inheritance](/compSci/chpt-16-inheritance)

### Lectures 17-19

- [Random walks](http://195.134.76.37/applets/AppletSailor/Appl_Sailor2.html) applet
- [Matplotlib/pylab](https://matplotlib.org/) reference

### Lecture 20

Monte Carlo method: [Wikipedia article](http://en.wikipedia.org/wiki/Monte_Carlo_method) on the Monte Carlo method

***

### Resources:

##### The Knapsack Problem

Let's apply what we're learned so far to a slightly more interesting problem. You are an art thief who has found a way to break into the impressionist wing at the Art Institute of Chicago. Obviously you can't take everything. In particular, you're constrained to take only what your knapsack can hold — let's say it can only hold W pounds. You also know the market value for each painting. Given that you can only carry W pounds what paintings should you steal in order to maximize your profit?

First let's see how this problem exhibits both overlapping subproblems and optimal substructure. Say there are n paintings with weights w1, ..., wn and market values v1, ..., vn. Define A(i,j) as the maximum value that can be attained from considering only the first i items weighting at most j pounds as follows.

Obviously A(0,j) = 0 and A(i,0) = 0 for any i ≤ n and j ≤ W. If wi > j then A(i,j) = A(i-1, j) since we cannot include the ith item. If, however, wi ≤ j then A(i,j) then we have a choice: include the ith item or not. If we do not include it then the value will be A(i-1, j). If we do include it, however, the value will be vi + A(i-1, j - wi). Which choice should we make? Well, whichever is larger, i.e., the maximum of the two.

Expressed formally we have the following recursive definitionKnapsack function

This problem exhibits both overlapping subproblems and optimal substructure and is therefore a good candidate for dynamic programming. The subproblems overlap because at any stage (i,j) we might need to calculate A(k,l) for several k < i and l < j. We have optimal substructure since at any point we only need information about the choices we have already made.

The recursive solution is not hard to write:
```
def A(w, v, i,j):
    if i == 0 or j == 0: return 0
    if w[i-1] > j:  return A(w, v, i-1, j)
    if w[i-1] <= j: return max(A(w,v, i-1, j), v[i-1] + A(w,v, i-1, j - w[i-1]))
```
Remember we need to calculate A(n,W). To do so we're going to need to create an n-by-W table whose entry at (i,j) contains the value of A(i,j). The first time we calculate the value of A(i,j) we store it in the table at the appropriate location. This technique is called memoization and is one way to exploit overlapping subproblems. There's also a Ruby module called memoize which does it for Ruby.

To exploit the optimal substructure we iterate over all i <= n and j <= W, at each step applying the recursion formula to generate the A(i,j) entry by using the memoized table rather than calling A() again. This gives an algorithm which takes O(nW) time using O(nW) space and our desired result is stored in the A(n,W) entry in the table.

##### Dynamic Programming

- The Needleman-Wunsch algorithm, used in bioinformatics.
- The CYK algorithm which is used the theory of formal languages and natural language processing.
- The Viterbi algorithm used in relation to hidden Markov models.
- Finding the string-edit distance between two strings, useful in writing spellcheckers.
- The D/L method used in the sport of cricket.