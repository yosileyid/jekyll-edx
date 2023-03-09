---
layout: page
title: Input / Output
---

## Input
Python 3.x has one function for input from user, input(). By contrast, legacy Python 2.x has two functions for input from user: input() and raw_input().

There are also very simple ways of reading a file and, for stricter control over input, reading from stdin if necessary.

### input() in Python 3.x

In Python 3.x, input() asks the user for a string of data (ended with a newline), and simply returns the string. It can also take an argument, which is displayed as a prompt before the user enters the data. E.g.
```
print(input('What is your name?'))
```
prints out
```
What is your name? <user input data here>
```
Example: to assign the user's name, i.e. string data, to a variable "x" you would type
```
x = input('What is your name?')
```
In legacy Python 2.x, the above applies to what was raw_input() function, and there was also input() function that behaved differently, automatically evaluating what the user entered; in Python 3, the same would be achieved via eval(input()).

In legacy Python 2.x, input() takes the input from the user as a string and evaluates it.

Therefore, if a script says:
```
x = input('What are the first 10 perfect squares? ')
```
it is possible for a user to input:
```
map(lambda x: x*x, range(10))
```
which yields the correct answer in list form. Note that no inputted statement can span more than one line.

`input()` should not be used for anything but the most trivial program, for security reasons. Turning the strings returned from raw_input() into Python types using an idiom such as:
```
x = None
while not x:
    try:
        x = int(raw_input())
    except ValueError:
        print('Invalid Number')
```
is preferable, as input() uses eval() to turn a literal into a Python type, which allows a malicious person to run arbitrary code from inside your program trivially.


## File Input
### File Objects
To read from a file, you can iterate over the lines of the file using open:
```
f = open('test.txt', 'r')
for line in f:
    print(line[0])
f.close()
```
This will print the first character of each line. A newline is attached to the end of each line read this way. The second argument to open can be 'r', 'w', or 'rw', among some others.

The newer and better way to read from a file:
```
with open("test.txt", "r") as txt:
    for line in txt:
        print(line)
```
The advantage is that the opened file will close itself after finishing the part within the with statement, and will do so even if an exception is thrown.

Because files are automatically closed when the file object goes out of scope, there is no real need to close them explicitly. So, the loop in the previous code can also be written as:
```
for line in open('test.txt', 'r'):
    print(line[0])
```
You can read a specific numbers of characters at a time:
```
c = f.read(1)
while len(c) > 0:
    if len(c.strip()) > 0: print(c)
    c = f.read(1)
```
This will read the characters from f one at a time, and then print them if they're not whitespace.

A file object implicitly contains a marker to represent the current position. If the file marker should be moved back to the beginning, one can either close the file object and reopen it or just move the marker back to the beginning with:

f.seek(0)

### Standard File Objects

There are built-in file objects representing standard input, output, and error. These are in the sys module and are called stdin, stdout, and stderr. There are also immutable copies of these in `__stdin__`, `__stdout__`, and `__stderr__`. This is for IDLE and other tools in which the standard files have been changed. You must import the sys module to use the special stdin, stdout, stderr I/O handles.

### `import sys`
For finer control over input, use sys.stdin.read(). To implement the UNIX 'cat' program in Python, you could do something like this:
```
import sys
for line in sys.stdin:
    print(line, end="")
```
Note that sys.stdin.read() will read from standard input till EOF. (which is usually Ctrl+D.)

### Parsing command line
Command-line arguments passed to a Python program are stored in sys.argv list. The first item in the list is name of the Python program, which may or may not contain the full path depending on the manner of invocation. sys.argv list is modifiable.

Printing all passed arguments except for the program name itself:
```
import sys
for arg in sys.argv[1:]:
  print(arg)
```
Parsing passed arguments for passed minus options:
```
import sys
option_f = False
option_p = False
option_p_argument = ""
i = 1
while i < len(sys.argv):
  if sys.argv[i] == "-f":
    option_f = True
    sys.argv.pop(i)
  elif sys.argv[i] == "-p":
    option_p = True
    sys.argv.pop(i)
    option_p_argument = sys.argv.pop(i)
  else:
    i += 1
```
Above, the arguments at which options are found are removed so that sys.argv can be looped for all remaining arguments.

Parsing of command-line arguments is further supported by library modules optparse (deprecated), argparse (since Python 2.7) and getopt (to make life easy for C programmers).

### Output
The basic way to do output is the print statement.
```
print('Hello, world')
```
To print multiple things on the same line separated by spaces, use commas between them:
```
print('Hello,', 'World')
```
This will print out the following: `Hello, World`

While neither string contained a space, a space was added by the print statement because of the comma between the two objects. Arbitrary data types can be printed:

```
print(1, 2, 0xff, 0777, 10+5j, -0.999, map, sys)
```
This will output the following: `1 2 255 511 (10+5j) -0.999 <built-in function map> <module 'sys' (built-in)>`

Objects can be printed on the same line without needing to be on the same line:
```
for i in range(10):
    print(i, end=" ")
```
This will output the following: `0 1 2 3 4 5 6 7 8 9`

To end the printed line with a newline, add a print statement without any objects.
```
for i in range(10):
    print(i, end=" ")
print()
for i in range(10,20):
    print(i, end=" ")
```
This will output the following:
```
0 1 2 3 4 5 6 7 8 9
10 11 12 13 14 15 16 17 18 19
```
If the bare print statement were not present, the above output would look like:

`0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19`

You can print to a file instead of to standard output:
```
print('Hello, world', file=f)
```
This will print to any object that implements write(), which includes file objects.

Note on legacy Python 2: in Python 2, print is a statement rather than a function and there is no need to put brackets around its arguments. Instead of print(i, end=" "), one would write print i,.

### Omitting newlines
In Python 3.x, you can output without a newline by passing end="" to the print function or by using the method write:
```
import sys
print("Hello", end="")
sys.stdout.write("Hello") # Or stderr to write to standard error stream.
```
In Python 2.x, to avoid adding spaces and newlines between objects' output with subsequent print statements, you can do one of the following:

Concatenation: Concatenate the string representations of each object, then later print the whole thing at once.
```
print(str(1)+str(2)+str(0xff)+str(0777)+str(10+5j)+str(-0.999)+str(map)+str(sys))
```
This will output the following:
```
12255511(10+5j)-0.999<built-in function map><module 'sys' (built-in)>
```
Write function: You can make a shorthand for sys.stdout.write and use that for output.
```
import sys
write = sys.stdout.write
write('20')
write('05\n')
```
This will output the following: `2005`
You may need sys.stdout.flush() to get that text on the screen quickly.

### Examples
Examples of output with Python 3.x:
```
from __future__ import print_function
```
Ensures Python 2.6 and later Python 2.x can use Python 3.x print function.
```
print("Hello", "world")
```
Prints the two words separated with a space. Notice the surrounding brackets, ununsed in Python 2.x.
```
print("Hello world", end="")
```
Prints without the ending newline.
```
print("Hello", "world", sep="-")
```
Prints the two words separated with a dash.
```
print("Hello", 34)
```
Prints elements of various data types, separating them by a space.
```
print("Hello " + 34)
```
Throws an error as a result of trying to concatenate a string and an integer.
```
print("Hello " + str(34))
```
Uses "+" to concatenate strings, after converting a number to a string.
```
sum=2+2; print "The sum: %i" % sum
```
Prints a string that has been formatted with the use of an integer passed as an argument. See also #Formatting.
```
print ("Error", file=sys.stderr)
```
Outputs to a file handle, in this case standard error stream.

Examples of output with Python 2.x:
```
print "Hello"
print "Hello", "world"
```
Separates the two words with a space.
```
print "Hello", 34
```
Prints elements of various data types, separating them by a space.
```
print "Hello " + 34
```
Throws an error as a result of trying to concatenate a string and an integer.
```
print "Hello " + str(34)
```
Uses "+" to concatenate strings, after converting a number to a string.
```
print "Hello",
```
Prints "Hello " without a newline, with a space at the end.
```
sys.stdout.write("Hello")
```
Prints "Hello" without a newline. Doing "import sys" is a prerequisite. Needs a subsequent "sys.stdout.flush()" in order to display immediately on the user's screen.
```
sys.stdout.write("Hello\n")
```
Prints "Hello" with a newline.
```
print >> sys.stderr, "An error occurred."
```
Prints to standard error stream.
```
sys.stderr.write("Hello\n")
```
Prints to standard error stream.
```
sum=2+2; print "The sum: %i" % sum
```
Prints a string that has been formatted with the use of an integer passed as an argument.
```
formatted_string = "The sum: %i" % (2+2); print formatted_string
```
Like the previous, just that the formatting happens outside of the print statement.
```
print "Float: %6.3f" % 1.23456
```
Outputs "Float: 1.234". The number 3 after the period specifies the number of decimal digits after the period to be displayed, while 6 before the period specifies the total number of characters the displayed number should take, to be padded with spaces if needed.
```
print "%s is %i years old" % ("John", 23)
```
Passes two arguments to the formatter.

### File Output
Printing numbers from 1 to 10 to a file, one per line:
```
file1 = open("TestFile.txt","w")
for i in range(1,10+1):
  print(i, file=file1)
file1.close()
```
With "w", the file is opened for writing. With "file=file1", print sends its output to a file rather than standard output.

Printing numbers from 1 to 10 to a file, separated with a dash:
```
file1 = open("TestFile.txt", "w")
for i in range(1, 10+1):
  if i > 1:
    file1.write("-")
  file1.write(str(i))
file1.close()
```
Opening a file for appending rather than overwriting:
```
file1 = open("TestFile.txt", "a")
```
In Python 2.x, a redirect to a file is done like print >>file1, i.

See also Files chapter.

### Formatting

Formatting numbers and other values as strings using the string percent operator:
```
v1 = "Int: %i" % 4               # 4
v2 = "Int zero padded: %03i" % 4 # 004
v3 = "Int space padded: %3i" % 4 #   4
v4 = "Hex: %x" % 31              # 1f
v5 = "Hex 2: %X" % 31            # 1F - capitalized F
v6 = "Oct: %o" % 8               # 10
v7 = "Float: %f" % 2.4           # 2.400000
v8 = "Float: %.2f" % 2.4         # 2.40
v9 = "Float in exp: %e" % 2.4    # 2.400000e+00
vA = "Float in exp: %E" % 2.4    # 2.400000E+00
vB = "List as string: %s" % [1, 2, 3]
vC = "Left padded str: %10s" % "cat"
vD = "Right padded str: %-10s" % "cat"
vE = "Truncated str: %.2s" % "cat"
vF = "Dict value str: %(age)s" % {"age": 20}
vG = "Char: %c" % 65             # A
vH = "Char: %c" % "A"            # A
```
Formatting numbers and other values as strings using the format() string method, since Python 2.6:
```
v1 = "Arg 0: {0}".format(31)     # 31
v2 = "Args 0 and 1: {0}, {1}".format(31, 65)
v3 = "Args 0 and 1: {}, {}".format(31, 65)
v4 = "Arg indexed: {0[0]}".format(["e1", "e2"])
v5 = "Arg named: {a}".format(a=31)
v6 = "Hex: {0:x}".format(31)     # 1f
v7 = "Hex: {:x}".format(31)      # 1f - arg 0 is implied
v8 = "Char: {0:c}".format(65)    # A
v9 = "Hex: {:{h}}".format(31, h="x") # 1f - nested evaluation
```
Formatting numbers and other values as strings using literal string interpolation, since Python 3.6:
```
int1 = 31; int2 = 41; str1="aaa"; myhex = "x"
v1 = f"Two ints: {int1} {int2}"
v2 = f"Int plus 1: {int1+1}"      # 32 - expression evaluation
v3 = f"Str len: {len(str1)}"      # 3 - expression evaluation
v4 = f"Hex: {int1:x}"             # 1f
v5 = f"Hex: {int1:{myhex}}"       # 1f - nested evaluation
```