---
layout: post
title: Bioinformatics Programming using Python, Chapter2
---

**Chapter 2 - NAMES, FUNCTIONS, AND MODULES**

***Outline:***

* naming values
* defining new functions
* incorporating optional software from the Python library

Python name consists of an arbitrary numbers of letter, underscores, and digits. 

* only restriction - first character can’t be number (because Python would interpret the digit as the beginning of a number)
* name is used to refer to something; a primitive value, a function, or any of a number of other possibilities
* name is not the same as string- online string it is not enclosed by quotes
* giving a name to a value is called binding

***Assigning Names***

- An assignment statement bind a name to an object. Assignment is denoted by a single equals sign :
     name = value
- Assignment statements may be chained together. This is primarily used to bind several names to some initial value:
     a=b=c=d=0
- Assignment statements is a bit of shorthand for arithmetic updates:
     a = a+1 # Python provides shorthand a +=1 —> augmented assignment statements


***Defining Functions***

- New functions are defined with function definition statements.
- Definition is a compound statement, meaning it comprises more than one line of code
- Definition statements have the general form: 
      def name (prameter-list):
            body // can be one or more statement and it is indented by four spaces from the def
- One function can call another
- Some functions are intended to return a value and some aren’t 


* For those that are, we use return statement 
        return value
- The pass statement
       pass // does nothing, it is used as a placeholder in compound statements

***Function Parameters***

- When a function is called, python evaluates each f the call’s argument expressions, then it assigns the first parameter to the first value, and so on if more than one —> when they are all assigned, the statements in the function body are executed

Example: A simple function for recognizing a binding site

```
def recognition_site(base_seq, recognition_seq):
      return base_eq.find(recognition_seq)
```

Example - Some function definition details

```
def validate_base_sequence(base_sequence):
# begins the definition of a function called validate_base_sequence that has parameter base_seqeunce
       seq = base_sequence.upper() 
# assigns the name seq to the result of calling the method upper on the value of base_sequence
       return len(seq) == (seq.count(’T’) + seq.count(‘C’) +   
                           seq.count(‘A’) + seq.count(‘G’))  
# compare the length of the sequence string to the sum of the number of Ts, As, Cs, and Gs in the sequence string - If the length is equal to that sum, the function return True, otherwise False
```

```
      >>> seq = ‘AAAT’
      >>> validate_base_sequence(‘tattattat’)
```
     

True


```
      >>> seq
```


‘AAAT’

In the previous example, within the return statement, we saw that the parentheses were opened on one line and closed on other line, that is fine, because Python will keep processing after the opening (right bracket) until it does not comes to closing (left bracket)

* another way to continue a long line without using parentheses is to end the line with a backslash- this will tell python that the current line is continued to the next. 

Block in python ends with the first line that is indented less than the first line of the block (the one that follows the “def” line which ends with a colon)

Comments and Documentation

- The # character tells to python to ignore the rest of the line 
* This convention can be used for a short comment following the line of code
- To explain the defined function python uses feature called docstring, which is simply a string that begins the function definition ( three quotes are used to characterize it)

Example: 

```
 def validate_base_sequence(base_sequence)
       “ “ “ Return True if the string base_sequence contains only 
      upper- or lowercase T, C, A, and G characters, otherwise False “ “ “
```

- Doctoring are different from comments - comments disappear when python runs the code, but doctoring remain, they have greater utility than comments
- The help function looks at the doctoring of a user-define function together with its parameter list to generate a help description.

Example: 


```
          >>> help(validate_base_sequence)
```
 

Help on function validate_base_sequence in module __main__:

```
          validate_base_sequence(base_sequence)
```


Return True if the string base_sequence contains only
upper- or lowercase T, C, A, and G characters, otherwise False


*Function definitions contain only statements. A string by itself is a statement because it is a value, a value is an expression, and an expression is a statement. However, docstrings are the only place where a freestanding string would have any effect.*

Example: Compute the GC content of a given DNA sequence represented as a string.

> GC content - genomes of different species — and regions within a genome — vary with respect to the proportion of Gs and Cs in their DNA opposed to Ts ad As.



```
def gc_content(base_seq):
      “ “ “ Return the percentage of G and C characters in base_seq “ “ “ 
      seq = base_seq.upper()
      return (seq.count(‘G’) + seg.count(‘C’))/ len(seq)
```


*When using meaningfully this function, a long base sequence would be requires but then it would be very difficult to say whether the result was correct. So when writing functions, it is always good to test them on small test cases for which we know the correct answer:*


```
    >>> seq50 = ‘AACCTTGG’
    >>> seq75 = ‘ATCCCGGG’
    >>> seq40 = ‘ATATTTCGCG’
    >>> gc_content(seq50)
0.5
    >>> gc_content(seq75)
0.75
    >>> gc_content(seq40)
0.4
```



***Assertions***

An assertion statement tests whether an expression is true or false, causing an error if it is false

     assert expression

*Let’s go back to our previous example with gc_content and apply assertion statement:*


```
def gc_content(base_seq):
      “ “ “ Return the percentage of G and C characters in base_seq “ “ “ 
      assert validate_base_sequence(base_eq), \
                 ‘argument has invalid characters’
      seq = base_seq.upper()
      return (seq.count(‘G’) + seg.count(‘C’))/ len(seq)
```



***Default Parameter Values*** 

Most calls to a certain function are like to include the same value for a particular parameter, frequently this value is something simple such as True, 0, or None. 

* In these cases python provides a way to assign a default value to the parameter that will be used if no explicit value is included in a cell to the function. 

Let’s go back again to one of the previous examples and make it handle RNA sequence too.

>Which simply means checking for a U instead of a T. So we will just add a second parameter whose value determines wether the function looks for Ts or Us. 


The term or syllable flag (flag) is commonly used for a Boolean value that determines which of two actions is performed. 
 We will call our new parameter RNAflag. 
 
Example:


```
def validate_base_sequence(base_seq, RNAflag):
      “ “ “ Return True if the string base_seq contains only upper — or 
            lowercase T (or U, if RNAflag), C, A, and G characters, 
            otherwise False“ “ “
      seq = base_seq.upper()
      return len(seq) == (seq.count(’T’ if RNAflag else ’T’) + seq.count(‘C’)    
                          + seq.count(‘A’) + seq.count(‘G’))

>>> validate_base_sequence(‘ATCG’, False)
True
>>> validate_base_sequence(‘ATCG’, True)
False
>>> validate_base_sequence(‘AUCG’, True)
True
```



Keyword parameters have the following properties:

* they are optional (not necessary in calls to the function)
* they are defined by specifying default values in the function’s parameter list: if the keyword does not appear in a call to the function, its default value is used
* in both the parameter list of a function definition and the argument list of its calls, all ‘positional’ (i.e., required) arguments must appear before any keyword parameters
* keyword parameters may appear in any order



***Using Modules***

A module’s contents are brought into the interpreter’s environment by an import statement



```
     import name # name is just the name of module, no path and no extension
```

First time any module is imported, python looks for it un each library directory until it is found.



***Module namespaces***

- Each module has a separate namespace associated with it.
- Module contents are accessed using the same dot notation used for method cells. (some modules have submodules, which are referenced using dot notation)
- Another form of the import statement is used to purposely bring a name from a module into the namespace in which the import appears - the interpreter or another module. 

**Selective Import***

Thus for of import statement loads a library into the Python environment but does not make its name available in the namespace from which it was loaded. Instead, it imports specific names from the module into the importing namespace.



```
     from moduleName import name1, name2, …
```

You can give the name you want to that what you are importing using the following structure:



```
      from moduleName import actualName as yourName
```

You can also import all the names from a module:



```
      from moduleName import 
```


>In general, it is best to avoid the “import all” form, because you don’t know what names you’ll be importing. Some might rebind existing names - this is called a name conflict— and lead to strange problems.



***The random module*** 

- Random module provides various ways to generate random numbers. 
- The function **random.randint** takes two integer arguments and returns a random integer in the range of the first to the second inclusive. 
 
Example:


>random.randint(1,4) will return 1,2,3,4



One good use of random.randint is to generate examples and “test cases” to use with code you are developing. 

Example: Generating a random codon



```
from random import randint
def random_base(RNAflag = False):
      return (‘UCAG’) if RNAflag else ’TCAG’) [randint (0,3)]
def random_codon(RNAflag = False):
      return random_base(RNAflag)+random_base(RNAflag)+random_base(RNAflag)
```



Breaking the code into two separate functions, each of which does its own job, helps readability. 

Example: Naming intermediate results in a function definition 


>Shows a function that stimulates single-base mutation. It uses assignment statements to name everything along the way to the final result.




```
from random import randint
def replace_base_randomly_using_names(base_seq):
       “ “ “ Return a sequence with the base at a randomly selected position 
       of base_seq replaced by a base chosen randomly from the three bases 
       that are not at that position “ “ “
       position = randint(0, len(base_seq) -1) #-1 because len is one past end
       base = base.seq[position]
       base = ’TCAG’
       bases.replace(base, ‘ ‘)     # replace with empty string!
       newbase = bases[randint(0,2)]
       beginning = base_seq[0:position] # up to position
       end = base_seq[position+1:]      # omitting the base at position
       return beginning + newbase + end 
```


Example: The same function without intermediate result names

>Shows another version of the same function. This variation uses a com- plex expression instead of a lot of names. It does use the name position to save the value of the call to randint, because that is used in two places; if randint were called twice, it would return two different values, and the definition needs to use the same value in both places.


```
def replace_base_randomly_using_expression(base_seq): 
     position = randint(0, len(base_seq) - 1)      
     return (base_seq[0:position] + 'TCAG'.replace(base_seq[position], '')
             [randint(0,2)] + base_seq[position+1:])
```


There’s no clear-cut rule about which style to use. Sometimes naming things improves readability (even taking the place of comments) and aids debugging. Often, however, it doesn’t contribute much, especially if the value named is only used once in the def- inition. In the case of this function, something between these two extremes would probably be best. The compromise version is shown in  next Example.



Example: A function definition with some intermediate names



```
def replace_base_randomly(base_seq):     
     position = randint(0, len(base_seq) - 1)
     bases = 'TCAG'.replace(base_seq[position], '') 
     return (base_seq[0:position] + bases [randint(0,2)] 
            + base_seq[position+1:])
```



***Python Files*** 

- File that you import becomes a module just as if the file had been in python’s library. 
- Accessing any of its contents requires using the file’s name as prefix, except for a specific names imported into the interpreter’s namespace using the “from” form of the import statement. 
- Each Python file must import any modules it uses. 



Example: A python file

>Shows a file containing the functions defined in examples earlier in this chapter, along with a new one for testing the others. The test function is called at the end of the file, and that call occurs regardless of whether the file is imported or executed.



```
def validate_base_sequence(base_sequence, RNAflag = False):       
       """ Return True if the string base_sequence contains only upper- or 
       lowercase T (or U, if RNAflag), C, A, and G characters, 
       otherwise False"""    
       seq = base_sequence.upper()      
       return len(seq) == (seq.count('U' if RNAflag else 'T') + seq.count('C') 
                            + seq.count('A') + seq.count('G'))
def gc_content(base_seq):
      """Return the percentage of bases in base_seq that are C or G""" 
      assert validate_base_sequence(base_seq), \                  
            'argument has invalid characters' 
            seq = base_seq.upper()
            return (base_seq.count('G') + 
            base_seq.count('C')) / len(base_seq)
            
def recognition_site(base_seq, recognition_seq):        
      """Return the first position in base_seq where recognition_seq occurs, 
      or −1 if not found"""       
      return base_seq.find(recognition_seq)
      
def test():       
        assert validate_base_sequence('ACTG')        
        assert validate_base_sequence('')       
        assert not validate_base_sequence('ACUG')
        assert validate_base_sequence('ACUG', False)        
        assert not validate_base_sequence('ACUG', True)        
        assert validate_base_sequence('ACTG', True)
        assert .5 == gc_content(‘ACTG’)       
        assert 1.0 == gc_content(‘CCGG’)       
        assert .25 == gc_content(‘ACTT’)
        print( ‘ All tests passed.’)
test()
```



