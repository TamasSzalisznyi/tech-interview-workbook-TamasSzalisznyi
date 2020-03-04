# Programming Basics questions

## Computer science

### Data structures

#### What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!
Lists are "container" for ordered data. <br>The elements can be any data type.<br> 
Can be sliced, and reach the elements with index numbers. Mutable and ordered<br>

Methods for example:
> - append()
> - extend()
> - pop()
> - remove()
> - count()
> - sort() 

#### What is the difference between a list/array and a set?
List is an ordered data structure, can containing an item multiple times. <br>
Set is an unordered data structure, items are unique

#### What is the purpose and methods of a dictionary/map data structure?
The purpose is making a structured key-value pair. The values can be reached through the keys, <br> 
the keys can be reached through the values and the key-value pairs can be also reached.

```python
mydict = {"key": "value"}
mydict["value"] = key
```
methods are: 

```python
key_value = mydict.items()
keys = mydict.values()
values = mydict.keys()
```

### Algorithms

#### Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
```python
    def fibo_seq(n):
    a = 0
    b = 1
    t = 0
    lst = []
    while t != n:
        c = a + b
        a = b
        b = c
        t += 1 
        lst.append(c)
    return lst
```
#### How do you find a max value in a list/array if you can’t use any built-in functions?
```python
max_ = 0
for elements in array:
    if max_ < elements:
        max_ = elements
```
#### How do you find the average of values in a list/array if you can’t use any built-in functions?
```python
    total = 0
    array_lenght = 0

    for elements in array:
        total += elements
        array_lenght += 1

    average = total/array_lenght
```
#### What do we call an *in-place* sort?
If don't need the original array, we can use a method whereas the elements of the array are only be 'swapped', <br>
the method overwrite the array don't copy it, therefore use just a little extra memory no matter how large is the array.

Sorting without copying the array.
#### Explain an algorithm which sorts a list!
```python
lst = [33,1,4,5,6,12,14,9,2,3,7,44,8]

len_list = 0
""" this iteration replace the built in 'len' function, determine the lenght of a list"""
for l in lst:
  len_list += 1

""" this iteration 'looking' for the maximum value in the list, then swap it with the actual index positioned item. 
Iterate over the list on each element for each element"""
for i in range(len_list):
  for j in range(i):
    if lst[i] > lst[j]:
      lst[i], lst[j] = lst[j], lst[i]
```

### Programming paradigms - procedural

#### What is the call stack?
Call stack is a stack data structure that stores information about the active subroutines of a computer program. 
#### What is “Stack overflow”?
When the called data is larger than the call stack memory, that is the stack owerflow, the program will crash.
#### What are the main parts of a function?

> - "def" keyword
> - "name" of the function
> - "[parameter(s)]:"
> - "[body]" and/or
> - ["return" value] (default is None)
```python
    def name(parameter):
        body(=statements)
        "do something"
        return value
```
and the fuction call:
```python
    name(arguments)
```
### Programming languages - Python  
#### How do you use a dictionary in Python?
It is readable for both key, value items or just key or value. <br>
Keys are unique and immutable.
#### What does it mean that an object is immutable in Python?
Not changable. If required to modify: be modified on the copy of it.
#### What is conditional expression in Python?
An expression what need to be fullfilled by a statement.
#### What are different types of arguments in Python?
Keyword- or positional argument.
#### What is variable shadowing? (context: variable scope)
If there are more than one variable with same name address, python will shadow it within the scope. <br>
The variable in the inner scope will be executed first then the others.
#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
If we delete/drop/add to a list while iterating over it the method might fail, <br>
because we changed the number of elements in the list, and with this the index values also.
#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
Scope determines the accessibility of our variables, and what values do they hold.<br>
LEGB stands for Local, Enclosed, Global, Built-in. It is the hierarchy in which python looks for variables<br>
(and functions as well). 
Variables have different lifetimes, depending on their definition. For example a local variable exists only <br> 
within the function, and when that function's execution is finished it doesn't exist anymore.<br>
"Golden rules": A variable should be only accessible where we use that certain variable: <br>
Using as much local variables as we can, and using global variables as little as we can.

#### If you need to access the iterator variable after a for loop, how would you do it in Python?
Create a variable to save the return value into or for example: append it to a list during the iteration.
#### What type of elements can a list contain in Python?
string, integer, list, dictionary, tuple, set
#### What is slice operator in Python and how to use?
Syntax:
```python
>[start:stop:step]
    
    """-start: is the first index from the slice
    -stop: is the last index from the slice, exclude the item
    -step: is n, the slice will containing every n-th element"""

lst = [1,2,3,4,5,6]
lst[0:5:2]
>>> 2, 4
```
#### What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
```+``` between lists to join them <br>
```*``` for list and integer to multiply it
#### What is the purpose of the in and not in membership operators in Python?
It returns a boolean value whether the left side value the is in/not in, in a string, list, dictionary and so on.
#### What does the + operator mean when used with strings in Python?
Contacenates the strings.
```python
str1 = "we are happy"
str2 = "with CC"
print(str1 + str2)
>>> "We are happy with CC"
```
#### Explain f strings in Python?
This allow to bedding variables in a string.
```python
variable = "Sentence with"
other_variable = "by f-string."

print(f"{variable} some string stuff {other_variable}")

>>>Sentence with some string stuff by f-string.
```
#### Name 4 iterable types in Python!
set, list, dictionary, tuple
#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?

In an object returned by the generator expression, we cannot access an element by index.

The List comprehension is enclosed in square brackets [] while the <br>
Generator expression is enclosed in plain parentheses ().
```python
l = [n*2 for n in range(1000)] # List comprehension
g = (n*2 for n in range(1000))  # Generator expression
 ```

#### Does the order of the function definitions matter in Python? Why?
If the function calls are in the right place; no.
#### What does unpacking mean in Python?    
We can pass more than one parameters to a function, packed in a list or in a dictionary. <br>
Passing them via *args or **kwargs mean the function can unpack them.
```python
def func_for_unpack(*args, **kwargs):
    return 
```
#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?
It will have a 'None' value
## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
> - step in
> - step out
> - step over
> - continue
> - watching expressions, variables and the state of the call stack.
#### What does step over, step into and step out mean while using the debugger?
We can step over a function and let being executed, <br>
step in a function to examine it line by line or step out to continue the process.
#### How can you start to debug a program from a certain line using the debugger?
Placing breakpoints to the certain line.
### Version control

#### What are the advantages of using a version control system?
Help the teamwork:

> - easy to share with others
> - allows to work on the same project in the same time 
> - help tracking back the code:
> - with the commits everybody can track back the changes
> - can restore the broken parts with the saved ones
> - keep in a safe place the code, like a cloud store the data
#### What is the difference between the working directory, the staging area and the repository in git?
Working directory (or working tree) is the structure what containing the .git file, <br>
staging area hold the files which are tracked by git and can be commit. <br>
Repository store the files whose are already commited and pushed to Github.
### What is remote repository?
Remote repository store the files in the git server.
#### Why does a merge conflict occur?
A merge conflict happens when two branches both modify the same region of a file and are subsequently merged.
Changing the same line in a file, or for example: one developer deleted a file while another developer was modifying it.
#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
```
touch newfile
git add newfile
git commit -m "message"
git push
```
#### What does it mean atomic commits and descriptive commit messages?
To be atomic: commit every upgrade/change/progress one-by-one, with a descriptive message what is describe the step.
#### What’s the difference between git and GitHub?
Git is a version controll software, that is used for tracking changes in the code.<br>
Github is a website used for hosting git repositories in the cloud.

## Software design

### Clean code

#### What does clean code mean?
Easy to read, easy to understand, easy to maintain, has no dead code, repetition, clutter. <br>
Clear, tight, readable, maintainable. <br> 
Dry. Dont't Repeat Yourself.
#### What steps do we usually do during a clean code refactoring?
Revisiting variable names, functions, if they're not enough explicit; rename those. <br>
Removing magic numbers, global variables. 
Extract repeating lines into functions. Simplifying functions to do one task instead multi tasking.

### Error handling

#### What is exception handling?
The error what is raised by the program can be handled with a ```try\except``` block.
Another solution to avoid error to handle them with conditional constructs  . 
#### What are the basics of exception handling in Python?
The ```try\except``` statement are the basic error handling blocks. <br>
Can expand with the ```else``` and ```finally``` blocks.
#### In which case should we catch an exception? Why?
We should catch an exception if it would not allow our code to run, but not for cathching errors in a badly written code.
#### What can/should we do with an exception in the ‘except’ block?
We can tell the program how to continue executing our code, if there's an exception event in the try block.<br>
For example: Print and error message and jumping back to the try block.
#### What does the else and finally statement do in a try-except block in Python?
The ```else```branch will be executed if the ```except``` statement hasn't been fulfilled. <br>
The ```finally``` will be executed in all cases at the end of the function. 
## Software Development Methodologies

#### What is the main goal of a retrospective meeting?
Talking about the positive and negative things from previous week and getting a new goal that we can focus on on the next week.
## Programming environment

### Unix

#### What is UNIX and what is Linux?
The biggest difference between the two operating system is: <br> linux is an opensource, unix is licensed software.
#### What do we call the shell in Linux?
The shell is the command interpreter, it is a program that executes other programs. <br>
It provides a user with an interface to the Linux system.
#### What does root means in a Linux environment?
Root is the user name or account that by default has access to all commands and files on a Linux system. <br>
It is also referred to as the root account, root user and the superuser.
#### How do you access your personal files in Linux?
Under the home directory ```\home\rootuser\```
#### How can you install an application in Linux?
With package managers like: ```apt``` or ```pip```
#### What is package management in Linux, what are repositories?
Package management is a method of installing and maintaining (which includes updating and probably removing as well) <br>
software on the system.
#### How do you navigate in the filesystem with the command line?
With changing directories; ``` cd ..``` to one level up,```cd <dir_name>/more_dir_name/etc.``` into the desired directory,<br>
 ```pwd``` to print out the current directory path. 
#### What does the following commands do: mkdir, rm, cat, cp, touch?
>1. ```mkdir```: make directory
>    * **```$ mkdir <mydir>```**

>2. ```rm```: remove files and directories
>    * **```$ rm <myfile>```**

>3. ```cat```: concatenate files and print to stdout
>    * **```$ cat > file1```** <br>
>    ```$ Hello```
    
>4. ```cp:``` copy files contents from ```file1``` to ```file2``` and contents of file1 is retained
>    * **```$ cp file1 file2```**

>5. ```touch```: create a new empty file or update its timestamp.
>   * **```$ touch <filename>```**

#### How can you look up what does a command do in Linux if you have no internet connection?
```$ help``` or ```$ man <command>```
#### What does the following commands do: head, tail, more, less?
1. ```more <filename>``` : to view a text file one page at a time
>    * **```$ more <-num> <filename>```** : show the document page few lines as specified by ```-num```

2. ```$ less``` : similar to ```$ more``` command
    * can navigate the page up/down
    * can search a string in less command. (use /```$ keywordto``` search)

>    * **```$ less <filename>```**

3. ```$ head``` : displays the first ten lines of a file, unless otherwise stated.
>    * **```$ head <myfile.txt>```** : Would display the first ten lines of ```myfile.txt```
* ```$ head <-num> <myfile.txt>``` : Would display the first ```<num>``` lines of ```myfile.txt```

4. ```$ tail``` : display the last part of the file

    * ```$ tail <filename>```
    >    * **```$ tail -n <filename>```** : display the last n lines of the file

>5. **```$ cat```** : can be used to join multiple files together and/or print the result on screen
    
* **```$ cat 01.txt ```** : display the contents of ```file 01.txt```
    * **```$ cat 01.txt 02.txt```** : display the contents of both files
    * **```$ cat file1.txt file2.txt > file3.txt```** : Reads ```file1.txt``` and ```file2.txt``` and  <br>
    combines those files to make ```file3.txt```
    * **```$ cat note5 >> notes```** : attach ```note5``` to ```notes```
    * **```$ cat > file1 ```** : add additional data in ```file1```
#### How do you download a file from internet using the terminal?
```$ wget (-o)``` or ```$ curl (-o)``` for further information, ```$ man wget``` or ```$ man curl```
