---
layout: post
title: Bioinformatics Programming using Python, Preface and Chapter1
---




*As I mentioned in the previous post, I will be sharing different bioinformatics sources that I am folowing. So here is one of them, my current book **"Bioinformatics Programming Using Python"** - Mitchell L Model*



**PREFACE AND CHAPTER 1**

#### Bioinformatics Programming Using Python

*PREFACE*

About Bioinformatics; three main areas of bioinformatics are 

- Computational Biology
- Software development
- Life Science Research and Development

**The goal is to teach writing programs that manipulate data**


Audience for the book:

* Scientists
* Students
* Technical staff
* Programmers

Traditional programmers should reconsider Python’s syntax after performing this experiment:


1. Open a file containing some well-formatted code.
2. Delete all semicolons, braces, and terminal keywords such as end, endif, etc. 
3. Look at the result. 

Checking the version of python installed


- **python -V** or 
- if in IDE  **from sys import version**

Quit the Python interpreter on 


- command line **Unix- Ctrl-D, Windows- Ctrl-Z**
- from IDE - **Quit menu command**

Two extensive Bioinformatic references:


- **Bioinformatics and Functional Genomics**, Second Edition, by Jonathan Pevsner (Wiley-Blackwell) 
- **Bioinformatics: Sequence and Genome Analysis**, Second Edition, by David W. Mount (Cold Spring Harbor Laboratory Press) 

>Bioinformatics is a fascinating field. Python is a wonderful language. Programming is a an exciting challenge. (Bioinformatics Programming using Python)



**Chapter 1 - PRIMITIVES**

- Simple values: logical(Boolean), integer, float and string.

- Special *no-value* value called None. (None means nothing)


String Operations: in, not in, + and *

- In and Not in = whether the first string is a substring of the second one
- ‘+’  concatenation = string consisting of all the characters of the first operand followed by the all characters of the second.
- Subscription = extracts a one-character substring of a string. 
[index]
- the index can be negative, which would mean count from the end of the string
- Slicing = extracts a series of characters from a string. 
[m:n](where m and n are different indexes)
- s[::1] = reversed copy of a string



**Calls**
 
 
>Function calls - invoke a function; function name, pair of parentheses a zero or more argument expressions separated by commas. 

Function is called, does something and then returns a value. Before the function is called, the argument expressions are evaluated, and the resulting values are passed to the function to be used as input in computation in defines. An argument can be any kind of expression whose result has a type acceptable to the function. 
Python has a small number of  built-in functions. 

Frequently used are:

* **len(arg)** = Returns the number of characters in arg 
* **print(args…[, sep=seprstr][, end=endstr])** = prints the arguments, of which there may be any number, separating each by a seprstr(default ‘’) and omitting certain technical details, such as the quotes surrounding a string, and edging with an endstr(default ‘\n’)
* **input(string)** = prompts the user by printing string, reads a line of input typed by the user (which ends when the Return or Enter key is pressed), and returns the lines as a string

Common numeric functions in python:

* **abs(value)** = returns the absolute value of its argument
* **max(args…)** = returns the maximum value of its arguments
* **min(args…)** = returns the minimum value of its arguments

Types can be called a function too. They tale an argument and return a value of the type called:

* **str(arg)** = returns a string representation of its argument
* **int(arg)** = returns integer derived from its arguments
* **float(arg)** = returns a float derived from its arguments
* **bool(arg)** = returns False for None, zeros, empty strings, etc., and True otherwise, rarely used, because other types of values are automatically converted to Boolean values wherever Boolean values are expected

> Using int is the only way to guarantee that the result of a division is an integer. As noted earlier, // is the floor operator and results in a float if either operand is a float

* Help
  * **help()** = inters the interactive help facility
  * **help(x)** = prints information about X, which can be anything (value, type, function, etc)

* **isinstance(x, sometime)** = 
Returns True if X is an instance of the type (class) sometime, and False otherwise

**Methods calls**

* functions which are part of the implementation of a specific type are called methods.
* calling a method is just like calling a function, except that the first argument goes before the function name, followed by a period. 



```
           string1.count(string2[, start[, end]])
```


Returns the number of times string2 appraise in string1. If start is specified, starts counting at that position in string1; if end is also specified, stops counting before that position in string1.



```
        string1.find(string2[,start[,end]])
```


Returns the position of the last occurrence of string1; -1 means string2 was not found in string1. If start is specified, starts searching at that position in string1; if end is also specified, stops searching before that position in string1.



```
          string1.startswith(string2[, start[, end]])
```



Returns True or False according to whether string2 starts with string1. If start is specified, uses that as the position at which to start the comparison; if end is also specified, stops searching before that position in string1.





```
          string1.strip([string2])
```



Returns a string with all characters in string2 removed from its beginning and end; if string2 is not specified, all whitespace is removed.





```
          string1.lstrip([string2])
```



Returns a string with all characters in string2 removed from its beginning; if string2 is not specified, all whitespace is removed.





```
          string1.rstrip([string2])
```



Return a string with all characters in string2 removed from its end; if string2 is not specified, all whitespace is removed.




**Compound Expressions**

*Programming language incorporate operator precedence rule.*

*List of the operands mentioned, ordered from highest precedence to lowest:

- Calls
- Slicing
- Subscriptions
- Exponentiation (**)
- Unary (+, -)
- Multiplication, division, and remainder (*, /, //, %)
- Addition and subtraction (+,-)
- Comparisons (==, !=, <, <=, >, >=)
- Membership (in, not in)
- Boolean not (not)
- Boolean and (and)
- Boolean or (or)


**Chapter 1; Tips, Traps, and Tracebacks**

***TIPS***

>Don’t trust what you see! - The visible interpretation may not be what you expect, even though the internal representation is actually the result you expected.

Statements and expressions * Functions cells are both expressions and statements * Sep and end keyword arguments t print give you more control over your output * A method call is simply a function call with its first argument moved before the function name,  followed by a period * Use parentheses to indicate the order you want, if you have any doubts about it.

 Running Python interactively

 * Type **python** in the terminal; if it starts with **2.xx**, exit and type **python3** to check if there is **3.xx** version of python installed 

To quit python **quit()** or **Ctrl-D** (unix) or **Ctrl-Z** (windows)

To edit the lines; 

- **Ctrl-A** = go to the beginning of the line
- **Ctrl-E** = go to the end of the line
- **Ctrl-B** = or left arrow move one character to the left
- **Ctrl-F** = or right arrow move one character to the right
- **Backspace** = delete the preceding character
- **Ctrl-D** = delete the next character
- **Ctrl-K** = delete the rest of the line after the cursor
- **Ctrl-Y** = “Yank” the last killed text into the line at the location of the cursor
- **Ctrl-_(underscore)** = undo; can be repeated
- **Ctrl-R** = search incrementally for a preceding input line
- **Ctrl-S** = search incrementally for a subsequent input line
- **Return** = give the current line to the interpreter. 
   
***TRAPS***

* The value of a floor division // equals an integer but has the type int only if both operands were ints; otherwise, the value is a float, with a 0 after the decimal point.
* First element of a string has **index 0**, and the last one has **index -1**
* The index in string indexing expressions must be greater or equal to 0 and less than the length of the string
* In a function call with more than one argument, each of them is separated by comma, except last one. Omitting commas will cause syntax errors.
* Functions and methods without arguments must be followed by an empty pair of parentheses - not including them won’t cause a synth error but will lead to an unexpected results.

***TRACEBACKS***

Error messages:

* NameError: 

 *‘Non’ is not defined* 

>Python doesn’t recognize a name
    
  * IndexError: *string index out of range*

>For a string of length N, and index must be in the range -N<= index < N-1

  * SyntaxError *Python syntax violation*

>ZeroDivisionError:  /, //, or % with 0 as the second operand
