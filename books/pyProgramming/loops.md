---
layout: page
title: Loops
---

## While loops
This is our first control structure.The version used is 2.7. Ordinarily the computer starts with the first line and then goes down from there. Control structures change the order that statements are executed or decide if a certain statement will be run. As a side note, decision statements (e.g., if statements) also influence whether or not a certain statement will run. Here's the source for a program that uses the while control structure:
```
a = 0
while a < 5:
    a += 1 # Same as a = a + 1 
    print (a)
```
And here is the output:
```
1
2
3
4
5
```
So what does the program do? First it sees the line a = 0 and sets the variable a to zero. Then it sees while a < 5: and so the computer checks to see if a < 5. The first time the computer sees this statement, a is zero, and zero is less than 5. In other words, while a is less than five, the computer will run the indented statements.

Here is another example of the use of while:
```
a = 1
s = 0
print ('Enter Numbers to add to the sum.')
print ('Enter 0 to quit.')
while a != 0:
    print ('Current Sum: ', s)
    a = input('Number? ') #raw_input() will not work anymore.
    a = float(a)
    s += a
print ('Total Sum = ',s)
Enter Numbers to add to the sum.
Enter 0 to quit.
Current Sum: 0
Number? 200
Current Sum: 200
Number? -15.25
Current Sum: 184.75
Number? -151.85
Current Sum: 32.9
Number? 10.00
Current Sum: 42.9
Number? 0
Total Sum = 42.9
```
Notice how print 'Total Sum =',s is only run at the end. The while statement only affects the lines that are tabbed in (a.k.a. indented). The  != means does not equal so while a != 0 : means until a is zero run the tabbed in statements that are afterwards.

Now that we have while loops, it is possible to have programs that run forever. An easy way to do this is to write a program like this:
```
while 1 == 1:
    print ("Help, I'm stuck in a loop.")
```
This program will output Help, I'm stuck in a loop. until the heat death of the universe or you stop it. The way to stop it is to hit the Control (or Ctrl) button and `c' (the letter) at the same time. This will kill the program. (Note: sometimes you will have to hit enter after the Control C.)

### Examples

Fibonacci.py
```
#This program calculates the Fibonacci sequence
a = 0
b = 1
count = 0
max_count = 20
while count < max_count:
    count = count + 1
    #we need to keep track of a since we change it
    old_a = a
    old_b = b
    a = old_b
    b = old_a + old_b
    #Notice that the , at the end of a print statement keeps it
    # from switching to a new line
    print (old_a),
```
Output:
```
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181
```
Password.py
```
# Waits until a password has been entered.  Use control-C to break out without
# the password.

# Note that this must not be the password so that the 
# while loop runs at least once.
password = "foobar"

#note that != means not equal
while password != "unicorn":
    password = input("Password: ")
print ("Welcome in")
```
Sample run:
```
Password:auo
Password:y22
Password:password
Password:open sesame
Password:unicorn
Welcome in
```
### For Loops

The next type of loop in Python is the for loop. Unlike in most languages, for requires some __iterable__ object like a Set or List to work.
```
onetoten = range(1,11)
for count in onetoten:
    print (count)
```
The output:
```
1
2
3
4
5
6
7
8
9
10
```
The output looks very familiar, but the program code looks different. The first line uses the range function. The range function uses two arguments like this range(start,finish). start is the first number that is produced. finish is one larger than the last number. Note that this program could have been done in a shorter way:
```
for count in range(1,11):
    print (count)
```
Here are some examples to show what happens with the range function:
```
>>> range(1,10)
[1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> range(-32, -20)
[-32, -31, -30, -29, -28, -27, -26, -25, -24, -23, -22, -21]
>>> range(5,21)
[5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
>>> range(21,5)
[]
```
Remark: for the current version of Python, we need to pass the range function to list() to actually print a list. For instance, we need to use list(range(1,10)) to get [1, 2, 3, 4, 5, 6, 7, 8, 9].

Another way to use the range() function in a for loop is to supply only one argument:
```
for a in range(10):
    print (a)
```
The above code acts exactly the same as:
```
for a in range(0, 10):
    print (a)
```
with 0 implied as the starting point. The output is
```
0 1 2 3 4 5 6 7 8 9
```
The code would cycle through the for loop 10 times as expected, but starting with 0 instead of 1.

The next line for count in onetoten: uses the for control structure. A for control structure looks like for variable in list:. list is gone through starting with the first element of the list and going to the last. As for goes through each element in a list it puts each into variable. That allows variable to be used in each successive time the for loop is run through. Here is another example to demonstrate:
```
demolist = ['life',42, 'the universe', 6,'and',7,'everything']
for item in demolist:
    print ("The Current item is: %s" % item)
```
The output is:
```
The Current item is: life
The Current item is: 42
The Current item is: the universe
The Current item is: 6
The Current item is: and
The Current item is: 7
The Current item is: everything
```
Notice how the for loop goes through and sets item to each element in the list. (Notice how if you don't want print to go to the next line add a comma at the end of the statement (i.e. if you want to print something else on that line). ) So, what is for good for? The first use is to go through all the elements of a list and do something with each of them. Here a quick way to add up all the elements:
```
list = [2,4,6,8]
sum = 0
for num in list:
    sum = sum + num
print ("The sum is: %d" % sum)
```
with the output simply being:
```
The sum is:  20
```
Or you could write a program to find out if there are any duplicates in a list like this program does:
```
list = [4, 5, 7, 8, 9, 1,0,7,10]
list.sort()
prev = list[0]
del list[0]
for item in list:
    if prev == item:
        print ("Duplicate of ",prev," Found")
    prev = item
and for good measure:
```
### Duplicate of  7  Found

How does it work? Here is a special debugging version:
```
l = [4, 5, 7, 8, 9, 1,0,7,10]
print ("l = [4, 5, 7, 8, 9, 1,0,7,10]","\tl:",l)
l.sort()
print ("l.sort()","\tl:",l)
prev = l[0]
print ("prev = l[0]","\tprev:",prev)
del l[0]
print ("del l[0]","\tl:",l)
for item in l:
    if prev == item:
        print ("Duplicate of ",prev," Found")
    print ("if prev == item:","\tprev:",prev,"\titem:",item)
    prev = item
    print ("prev = item","\t\tprev:",prev,"\titem:",item)
```
with the output being:
```
l = [4, 5, 7, 8, 9, 1,0,7,10]   l: [4, 5, 7, 8, 9, 1, 0, 7, 10]
l.sort()        l: [0, 1, 4, 5, 7, 7, 8, 9, 10]
prev = l[0]     prev: 0
del l[0]        l: [1, 4, 5, 7, 7, 8, 9, 10]
if prev == item:        prev: 0         item: 1
prev = item             prev: 1         item: 1
if prev == item:        prev: 1         item: 4
prev = item             prev: 4         item: 4
if prev == item:        prev: 4         item: 5
prev = item             prev: 5         item: 5
if prev == item:        prev: 5         item: 7
prev = item             prev: 7         item: 7
if prev == item:        prev: 7         item: 7
Duplicate of  7  Found
prev = item             prev: 7         item: 7
if prev == item:        prev: 7         item: 8
prev = item             prev: 8         item: 8
if prev == item:        prev: 8         item: 9
prev = item             prev: 9         item: 9
if prev == item:        prev: 9         item: 10
prev = item             prev: 10        item: 10
```
Note: The reason there are so many print statements is because print statements can show the value of each variable at different times, and help debug the program. First the program starts with a old list. Next the program sorts the list. This is so that any duplicates get put next to each other. The program then initializes a prev(ious) variable. Next the first element of the list is deleted so that the first item is not incorrectly thought to be a duplicate. Next a for loop is gone into. Each item of the list is checked to see if it is the same as the previous. If it is a duplicate was found. The value of prev is then changed so that the next time the for loop is run through prev is the previous item to the current. Sure enough, the 7 is found to be a duplicate.

The other way to use for loops is to do something a certain number of times. Here is some code to print out the first 9 numbers of the Fibonacci series:
```
a = 1
b = 1
for c in range(1,10):
    print (a)
    n = a + b
    a = b
    b = n
print ("")
```
with the surprising output:
```
1
1
2
3
5
8
13
21
34
```
Everything that can be done with for loops can also be done with while loops but for loops give an easy way to go through all the elements in a list or to do something a certain number of times.


### range Versus xrange

Python 3 Note: In Python 3.x, there is no function named xrange. Instead, the range function has the behaviour described below for xrange. The following applies to the legacy Python 2.

Above, you were introduced to the range function, which returns a list of all the integers in a specified range. Supposing you were to write an expression like range(0, 1000000): that would construct a list consisting of a million integers! That can take up a lot of memory.

Often, you do indeed need to process all the numbers over a very wide range. But you might only need to do so one at a time; as each number is processed, it can be discarded from memory before the next one is obtained.

To do this, you can use the xrange function instead of range. For example, the following simple loop
```
for i in xrange(0, 1000000):
    print(i)
```
will print the million integers from 0 to 999999, but it will get them one at a time from the xrange call, instead of getting them all at once as a single list and going through that.

This is an example of an iterator, which yields values one at a time as they are needed, rather than all at once. As you learn more about Python, you will see a lot more examples of iterators in use, and you will learn how to write your own.

#### The break Statement
A while-loop checks its termination condition before each entry into the loop body, and terminates if the condition has gone False. Thus, the loop body will normally iterate zero, one or more complete times.

A for-loop iterates its body once for each value returned from the iterator expression. Again, each iteration is normally of the complete loop body.

Sometimes you want to conditionally stop the loop in the middle of the loop body. An example situation might look like this:

- Obtain the next value to check
- Is there in fact another value to check? If not, exit the loop with failure.
- Is the value what I’m looking for? If so, exit the loop with success.
- Otherwise, go back to step 1.
As you can see, there are two possible exits from this loop. You can exit from the middle of a Python while- or for-loop with the break-statement. Here is one way to write such a loop:
```
found = False # initial assumption
for value in values_to_check():
    if is_what_im_looking_for(value):
        found = True
        break
# ... found is True on success, False on failure
```
The trouble with this is the asymmetry between the two ways out of the loop: one through normal for-loop termination, the other through the break. As a stylistic matter, it would be more consistent to follow this principle:

If one exit from a loop is represented by a break, then all exits from the loop should be represented by breaks.
In particular, this means that the loop construct itself becomes a “loop-forever” loop; the only out of it is via a break statement.

We can do this by explicitly dealing with an iterator yielding the values to be checked. Perhaps the values_to_check() call above already yields an iterator; if not, it can be converted to one by wrapping it in a call to the iter() built-in function, and then using the next() built-in function to obtain successive values from this iterator. Then the loop becomes:
```
values = iter(values_to_check())
while True:
    value = next(values, None)
    if value is None:
        found = False
        break
    if is_what_im_looking_for(value):
        found = True
        break
# ... found is True on success, False on failure
```
This uses the special Python value None to indicate that the iterator has reached its end. This is a common Python convention. But if you need to use None as a valid item in your sequence of values, then it is easy enough to define some other unique value (e.g. a custom dummy class) to represent the end of the list.