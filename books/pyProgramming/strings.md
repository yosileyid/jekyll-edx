---
layout: page
title: Strings & Variables
---

### {{page.title}}
# Python Programming
### Variables

A variable is something that holds a value that may change. In simplest terms, a variable is just a box that you can put stuff in. You can use variables to store all kinds of stuff, but for now, we are just going to look at storing numbers in variables.
```
lucky = 7
print (lucky)
7
```
This code creates a variable called lucky, and assigns to it the integer number 7. When we ask Python to tell us what is stored in the variable lucky, it returns that number again.

We can also change what is inside a variable. For example:
```
changing = 3                                   
print (changing)
3 

changing = 9
print (changing)
9

different = 12
print (different)
12
print (changing)
9

changing = 15
print (changing)
15
```
We declare a variable called changing, put the integer 3 in it, and verify that the assignment was properly done. Then, we assign the integer 9 to changing, and ask again what is stored in changing. Python has thrown away the 3, and has replaced it with 9. Next, we create a second variable, which we call different, and put 12 in it. Now we have two independent variables, different and changing, that hold different information, i.e., assigning a new value to one of them is not affecting the other.

You can also assign the value of a variable to be the value of another variable. For example:
```
red = 5
blue = 10
print (red, blue)
5 10

yellow = red
print (yellow, red, blue)
5 5 10

red = blue
print (yellow, red, blue)
5 10 10
```
To understand this code, keep in mind that the name of the variable is always on the left side of the equals sign (the assignment operator), and the value of the variable is on the right side of the equals sign. First the name, then the value.

We start out declaring that red is 5, and blue is 10. As you can see, you can pass several arguments to print to tell it to print multiple items on one line, separating them by spaces. As expected, Python reports that red stores 5, and blue holds 10.

Now we create a third variable, called yellow. To set its value, we tell Python that we want yellow to be whatever red is. (Remember: name to the left, value to the right.) Python knows that red is 5, so it also sets yellow to be 5.

Now we're going to take the red variable, and set it to the value of the blue variable. Don't get confused — name on the left, value on the right. Python looks up the value of blue, and finds that it is 10. So, Python throws away red's old value (5), and replaces it with 10. After this assignment Python reports that yellow is 5, red is 10, and blue is 10.

But didn't we say that yellow should be whatever value red is? The reason that yellow is still 5 when red is 10, is because we only said that yellow should be whatever red is at the moment of the assignment. After Python has figured out what red is and assigned that value to yellow, yellow doesn't care about red any more. yellow has a value now, and that value is going to stay the same no matter what happens to red.

`Note: The interplay between different variables in Python is, in fact, more complex than explained here. The above example works with integer numbers and with all other basic data types built into Python; the behavior of lists and dictionaries (you will encounter these complex data types later) is entirely different, though. You may read the chapter on data types for a more detailed explanation of what variables really are in Python and how their type affects their behavior. However, it is probably sufficient for now if you just keep this in mind: whenever you are declaring variables or changing their values, you always write the name of the variable on the left of the equals sign (the assignment operator), and the value you wish to assign to it on the right.`

For the name of the variable, it can only consist of uppercase and lowercase letters (A-Z, a-z), digits (0-9), and the underscore character (_), and the first character of the name cannot be a digit. For example, 1abc and _#$ad are not valid variable names, while _123 and a__bc are valid variable names.

### String

A 'string' is simply a list of characters in order. A character is anything you can type on the keyboard in one keystroke, like a letter, a number, or a backslash. For example, "hello" is a string. It is five characters long — h, e, l, l, o. Strings can also have spaces: "hello world" contains 11 characters: 10 letters and the space between "hello" and "world". There are no limits to the number of characters you can have in a string — you can have anywhere from one to a million or more. You can even have a string that has 0 characters, which is usually called an "empty string."

There are three ways you can declare a string in Python: single quotes ('), double quotes ("), and triple quotes ("""). In all cases, you start and end the string with your chosen string declaration. For example:
```
>>> print ('I am a single quoted string')
I am a single quoted string
>>> print ("I am a double quoted string")
I am a double quoted string
>>> print ("""I am a triple quoted string""")
I am a triple quoted string
```
You can use quotation marks within strings by placing a backslash directly before them, so that Python knows you want to include the quotation marks in the string, instead of ending the string there. Placing a backslash directly before another symbol like this is known as escaping the symbol.
```
>>> print ("So I said, \"You don't know me! You'll never understand me!\"")
So I said, "You don't know me! You'll never understand me!"
>>> print ('So I said, "You don\'t know me! You\'ll never understand me!"')
So I said, "You don't know me! You'll never understand me!"
>>> print ("""The double quotation mark (\") is used to indicate direct quotations.""")
```
The double quotation mark (") is used to indicate direct quotations.
If you want to include a backslash in a string, you have to escape said backslash. This tells Python that you want to include the backslash in the string, instead of using it as an escape character. For example:
```
>>> print ("This will result in only three backslashes: \\ \\ \\")
```
This will result in only three backslashes: \ \ \
As you can see from the above examples, only the specific character used to quote the string needs to be escaped. This makes for more readable code.

To see how to use strings, let's go back for a moment to an old, familiar program:
```
>>> print("Hello, world!")
Hello, world!
```
Look at that! You've been using strings since the very beginning!

You can add two strings together using the + operator: this is called concatenating them.
```
>>> print ("Hello, " + "world!")
Hello, world!
```
Notice that there is a space at the end of the first string. If you don't put that in, the two words will run together, and you'll end up with Hello,world!

You can also repeat strings by using the * operator, like so:
```
>>> print ("bouncy " * 5)
bouncy bouncy bouncy bouncy bouncy 
>>> print ("bouncy " * 10)
bouncy bouncy bouncy bouncy bouncy bouncy bouncy bouncy bouncy bouncy
```
The string bouncy gets repeated 5 times in the 1st example and 10 times in the 2nd.

If you want to find out how long a string is, you use the len() function, which simply takes a string and counts the number of characters in it. (len stands for "length.") Just put the string that you want to find the length of inside the parentheses of the function. For example:
```
>>> print (len("Hello, world!"))
13
```
### Strings and Variables

Now that you've learned about variables and strings separately, let's see how they work together.

Variables can store much more than just numbers. You can also use them to store strings! Here's how:
```
question = "What did you have for lunch?"
print (question)
What did you have for lunch?
```
In this program, we are creating a variable called question, and storing the string "What did you have for lunch?" in it. Then, we just tell Python to print out whatever is inside the question variable. Notice that when we tell Python to print out question, there are no quotation marks around the word question: this tells Python that we are using a variable, not a string. If we put in quotation marks around question, Python would treat it as a string, as shown below:
```
question = "What did you have for lunch?"
print ("question")
question
```
Let's try something different. Sure, it's all fine and dandy to ask the user what they had for lunch, but it doesn't make much difference if they can't respond! Let's edit this program so that the user can type in what they ate.
```
question = "What did you have for lunch?"
print (question)
answer = raw_input() #You should use "input()" in python 3.x, because python 3.x doesn't have a function named "raw_input".

print ("You had " + answer + "! That sounds delicious!")
```
To ask the user to write something, we used a function called raw_input(), which waits until the user writes something and presses enter, and then returns what the user wrote. Don't forget the parentheses! Even though there's nothing inside of them, they're still important, and Python will give you an error if you don't put them in. You can also use a different function called input(), which works in nearly the same way. We will learn the differences between these two functions later.

`Note: In Python 3.x raw_input() was renamed to input(). That is, the new input() function reads a line from sys.stdin and returns it without the trailing newline. It raises EOFError if the input is terminated prematurely (e.g. by pressing Ctrl+D). To get the old behavior of input(), use eval(input()).`

In this program, we created a variable called answer, and put whatever the user wrote into it. Then, we print out a new string, which contains whatever the user wrote. Notice the extra space at the end of the "You had " string, and the exclamation mark at the start of the "! That sounds delicious!" string. They help format the output and make it look nice, so that the strings don't all run together.

### Combining Numbers and Strings

Take a look at this program, and see if you can figure out what it's supposed to do.
```
print ("Please give me a number: ")
number = raw_input()

plusTen = number + 10
print ("If we add 10 to your number, we get " + plusTen)
```
This program should take a number from the user, add 10 to it, and print out the result. But if you try running it, it won't work! You'll get an error that looks like this:
```
Traceback (most recent call last):
  File "test.py", line 5, in <module>
    print "If we add 10 to your number, we get " + plusTen
TypeError: cannot concatenate 'str' and 'int' objects
```
What's going on here? Python is telling us that there is a TypeError, which means there is a problem with the types of information being used. Specifically, Python can't figure out how to reconcile the two types of data that are being used simultaneously: integers and strings. For example, Python thinks that the number variable is holding a string, instead of a number. If the user enters 15, then number will contain a string that is two characters long: a 1, followed by a 5. So how can we tell Python that 15 should be a number, instead of a string?

Also, when printing out the answer, we are telling Python to concatenate together a string ("If we add 10 to your number, we get ") and a number (plusTen). Python doesn't know how to do that -- it can only concatenate strings together. How do we tell Python to treat a number as a string, so that we can print it out with another string?

Luckily, there are two functions that are perfect solutions for these problems. The int() function will take a string and turn it into an integer, while the str() function will take an integer and turn it into a string. In both cases, we put what we want to change inside the parentheses. Therefore, our modified program will look like this:
```
print ("Please give me a number:",)
response = raw_input()

number = int(response) 
plusTen = number + 10

print ("If we add 10 to your number, we get " + str(plusTen))
```
`Note: Another way of doing the same is to add a comma after the string part and then the number variable, like this:`
```
print ("If we add 10 to your number, we get ", plusTen)
```
or use special print formatting like this:
```
print ("If we add 10 to your number, we get %s" % plusTen)
```
which alternative can be written this way, if you have multiple inputs:
```
plusTwenty = number + 20
print ("If we add 10 and 20 to your number, we get %s and %s" % (plusTen, plusTwenty))
```
or use format()
```
print ("If we add 10 to your number, we get {0}".format(plusTen))
```
That's all you need to know about strings and variables! We'll learn more about types later.

##### List of Learned Functions

- **print():** Print the output information to the user
- **input()** or **raw_input():** asks the user for a response, and returns that response. (Note that in version 3.x raw_input() does not exist and has been replaced by input())
- **len():** returns the length of a string (number of characters)
- **str():** returns the string representation of an object
- **int():** given a string or number, returns an integer

`Note: input and raw_input function accept a string as parameter. This string will be displayed on the prompt while waiting for the user input. The difference between the two is that raw_input accepts the data coming from the input device as a raw string, while input accepts the data and evaluates it into python code. This is why using input as a way to get a user string value returns an error because the user needs to enter strings with quotes.`
`It is recommended to use raw_input at all times and use the int function to convert the raw string into an integer. This way we do not have to bother with error messages until the error handling chapter and will not make a security vulnerability in your code.`

##### Exercises
- Write a program that asks the user to type in a string, and then tells the user how long that string was.
- Ask the user for a string, and then for a number. Print out that string, that many times. (For example, if the string is hello and the number is 3 you should print out hello hello hello .)
- What would happen if a mischievous user typed in a word when you ask for a number? Try it.

[Solution](https://en.wikibooks.org/wiki/Python_Programming/Variables_and_Strings/Solutions)