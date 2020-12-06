# Programming Basics questions

## Computer science

### Data structures

#### What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!
A list is a "container" for collection of data, an abstract data type. <br>
The elements can be any predefined data type, like numbers, characters or objects.<br>
List is ordered in the meaning that elements construct a sequence and this isn't change without direct modification.<br> 
Every piece of the list has its index (starting usually from 0), and a place to store the value or the reference for it. 
Elements can be accessed through this index number.<br>
List can be traversed through iteration (sequentially steps over the elements).

Methods for example:
> - append()
> - extend()
> - pop()
> - remove()
> - count()
> - sort() 

#### What is the difference between a list/array and a set?
The list can contain the same value more than once, but they can still be distinguished.<br>
Set is a data structure where items are unique.

#### What is the purpose and methods of a dictionary/map data structure?
The purpose is making a structured key-value pair. 

- A value can be reached directly through the key:<br> 
`dictionary_name.get(name, default_value)`<br>
`dictionary_name[key]`

- the keys and/or values can be reached through:<br>
`dictionary_name.items()`<br>
`dictionary_name.keys()`<br>
`dictionary_name.values()`

```python
my_dict = {"key": "value"}
a_value = my_dict["key"]
b_value = my_dict.get("key")

for key, value in my_dict.items():
    print("key: ", key, " value: ", value)

keys = my_dict.keys()    
values = my_dict.values()
```

### Algorithms

#### Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
```python
    def fibonacci_seq(n):
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
array = [1, 2, 3, 4, 5, 6, 7, 8]
max_ = 0

for element in array:
    if max_ < element:
        max_ = element
```

#### How do you find the average of values in a list/array if you can’t use any built-in functions?
```python
total = 0
array_length = 0
array = [1, 2, 3, 4, 5, 6, 7, 8]

for element in array:
    total += element
    array_length += 1

average = total/array_length
```

#### What do we call an *in-place* sort?
If don't need the order of the original array, we can use a method whereas the elements of the array are only be 'swapped', <br>
the method will replace the array, therefore use just a little extra memory no matter how large is the array.

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
Call stack is a stack data structure (kind of collection) that stores information about the active subroutines (or tasks) of a computer program. 
New method calls, variables, references etc... are placed on the top of the stack, execution order is LIFO, 
the top of the stack will be executed.

#### What is “Stack overflow”?
When the number of tasks to be performed is larger than the call stack size, that stack overflow will occur, the program will crash.
This can be happened easily during a recursive execution.

#### What are the main parts of a function?

> - "def" keyword
> - "name" of the function
> - "[parameter(s)]:"
> - "[body]" and/or
> - ["return" value] (default is None)
> 
```python

#function definition:
def name(parameter):
    body(=statements)
    "do something"
    return value

#and function call:

return_value = name(arguments)
```

### Programming languages - Python  
#### How do you use a dictionary in Python?
It is readable for both key, value items or just key or value. <br>
Keys are unique and immutable.

#### What does it mean that an object is immutable in Python?
Not modifiable. If required to modify: be modified on the copy of it.

#### What is conditional expression in Python?
An expression what need to be fulfilled by a statement.

#### What are different types of arguments in Python?
Keyword- or positional argument.

#### What is variable shadowing? (context: variable scope)
If there are more than one variable with same name address, python will shadow it within the scope. <br>
The variable in the inner scope will be executed first then the others.

#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
If we delete from, or add to a list while iterating over it the method might fail, <br>
because we changed the number of elements in the list, and with this, the indexes too.

#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
Scope determines the accessibility of our variables, and what values do they hold.<br>
LEGB stands for **Local, Enclosed, Global, Built-in**. It is the hierarchy in which python looks for variables and functions.<br> 
Variables have different lifetimes, depending on their definition.<br> 
For example a local variable exists only within the function, and when that function's execution is finished the variable does not reachable more.<br>
"Golden rules": A variable should be only accessible where we use that certain variable: <br>
Using as much local variables as we can, and avoid global variables.

#### If you need to access the iterator variable after a for-loop, how would you do it in Python?
Create a variable to save the return value into or for example: append it to a list during the iteration.
```python
a_list = ["characters", "or", "strings", "in", "a", "list"]

variable = ""
for elem in a_list:
    variable = elem

print(variable)
#>>>list
```

#### What type of elements can a list contain in Python?
Numeric (int), text sequence (str) and any other object (Object or even another list or set).

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
`+` between lists to join them <br>
```python
a_list = ["this", "is"]
b_list = ["a", "long", "list"]

joined_list = a_list + b_list
print(joined_list)
#>>>this is a long list
```

`*` for list, and an integer to copy and concatenate it
```python
a_list = ["a", "b", "c"]
multiplied_list = a_list * 4

print(multiplied_list, sep=' -> ')
#>>>a b c -> a b c -> a b c -> a b c
```

#### What is the purpose of the in and not in membership operators in Python?
It returns a boolean value whether the left side value the is in/not in, in a string, list, dictionary and so on.

#### What does the + operator mean when used with strings in Python?
Concatenates the strings.

```python
str1 = "we are happy "
str2 = "with CC"
print(str1 + str2)
>>> "We are happy with CC"
```
#### Explain f strings in Python?
Allow embedding variables in a string.

```python
variable = "Sentence with"
other_variable = "by f-string."

print(f"{variable} some string stuff {other_variable}")

#>>>Sentence with some string stuff by f-string.
```

#### Name 4 iterable types in Python!
set, list, dictionary, tuple

#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?
In an object returned by the generator expression, we cannot access an element by its index but the next element<br>
with the `next()` method call. The returned object is an iterator.
Values from generators not stored in memory, only times reachable.

Using comprehension does not change the type of the object it is just a different write mode.
Also, the collection is stored in memory, the values are reachable while the containing collection exist.

The List comprehension is enclosed in square brackets [] while the <br>
Generator expression is enclosed in plain parentheses ().
```python
l = [n*2 for n in range(1000)] # List comprehension

print(l[1])
#>>>2

print(l[1])
#>>>2

value = 0
g = (n*2 for n in range(1000))  # Generator expression

while value < 1000:
    print(next(g))

#>>>0, 2, 4, 6, 8...
 ```

#### Does the order of the function definitions matter in Python? Why?
Only the function calls matter in the execution order.
Functions are not executed before the call.

#### What does unpacking mean in Python?    
We can pass more than one parameter to a function, packed in a list or in a dictionary. <br>
Passing them via *args (a collection) or **kwargs (a dictionary) mean the function can unpack them.
Working with args and kwargs give more flexibility over passing parameters.

```python
def func_for_unpack(*args, **kwargs):
    # Iterating over the args
    for x in args:
        print(x, end='')
    # Iterating over the Python kwargs dictionary
    print()
    for value in kwargs.values():
        print(value, end='')
    return 

func_for_unpack(1, 2, 3, a="Python ", b="is ", c="great ", d="!")
#>>> 1 2 3 Python is great !
```

#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?
It will have a 'None' value.

## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
> - step in
> - step out
> - step over
> - continue
> - watching expressions, variables and the state of the call stack.

#### What does step over, step into and step out mean, while using the debugger?
We can:
- step over a function and let being executed, <br>
- step in a function to examine it line by line or 
- step out to continue the process.

#### How can you start to debug a program from a certain line using the debugger?
Placing breakpoints to the certain line.

### Version control

#### What are the advantages of using a version control system?
Help the teamwork:

 - easy to share with others
 - allows working on the same project in the same time from different places/machines 
 - help track back the code:
    - with the commits everybody can track back the changes
    - can restore the broken parts with the saved ones
 - keep in a safe place the code, like a cloud store the data

#### What is the difference between the working directory, the staging area and the repository in git?
A working directory (or working tree):<br> 
    - the structure that containing the .git file
Staging area:<br> 
    - hold the files which are tracked by git and can be committed
Repository:<br>
    - local: the workdir or project folder
    - remote: files whose are already committed and pushed to Github.

### What is a remote repository?
Remote repository store the files in the git server.

#### Why does a merge conflict occur?
A merge conflict happens when two branches both modify the same region of a file and are subsequently merged.
Changing the same line in a file, or for example: one developer deleted a file while another developer was modifying it.

#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
```shell
git add [file_name | .]
git commit -m "message"
git push
```

#### What does it mean atomic commits and descriptive commit messages?
To be atomic: commit every upgrade/change/progress one-by-one, with a descriptive message what is short but clear and self explaining.

#### What’s the difference between git and GitHub?
Git is a version control software, that is used for tracking changes in the code.<br>
Github is a website used for hosting git repositories in the cloud.

## Software design

### Clean code

#### What does clean code mean?
Easy to read, easy to understand, easy to maintain, has no dead code, repetition, clutter. <br>
Clear, tight, readable, maintainable. <br> 
Dry. Don't Repeat Yourself.

#### What steps do we usually do during a clean code refactoring?
Revisiting variable names, functions, if they're not enough explicit; rename those. <br>
Removing magic numbers, global variables. 
Extract repeating lines into functions. Simplifying functions to do one task instead multi tasking.

### Error handling

#### What is exception handling?
The error what is raised by the program can be handled with a `try\except` block.
Another solution to avoid error to handle them with conditional constructs. 

#### What are the basics of exception handling in Python?
The `try\except` statement are the basic error handling blocks. <br>
Can expand with the `else` and `finally` blocks.

#### In which case should we catch an exception? Why?
We should catch an exception if it would not allow our code to run, but not for catching errors in a badly written code.

#### What can/should we do with an exception in the ‘except’ block?
We can tell the program how to continue executing our code, if there's an exception event in the try block.<br>
For example: Print and error message and jumping back to the try block.

#### What does the else and finally statement do in a try-except block in Python?
The ```else```branch will be executed if the ```except``` statement hasn't been fulfilled. <br>
The ```finally``` will be executed in all cases at the end of the function. 

## Software Development Methodologies

#### What is the main goal of a retrospective meeting?
Talking about the positive and negative things from previous time period and learning from them.<br> 
Also, defining a new goal that we can focus on for the next time period.

## Programming environment

### Unix

#### What is UNIX and what is Linux?
The biggest difference between the two operating system is: <br> linux is opensource, unix is licensed software.

#### What do we call the shell in Linux?
The shell is the command interpreter, it is a program that executes other programs. <br>
It provides a user with an interface to the Linux system.

#### What does root means in a Linux environment?
Root is the admin user or account that has access to all commands and files on a Linux system. <br>
It is also referred to as the root account, root user and the superuser.

#### How do you access your personnel files in Linux?
Under the home directory `\home\user\`

#### How can you install an application in Linux?
With package managers like: `apt` or `pip`

#### What is package management in Linux, what are repositories?
Package management is a software for installing and maintaining (which includes updating and removing as well) <br>
other softwares on the system.

#### How do you navigate in the filesystem with the command line?
With changing directories;
- `cd ~/` to home directory
- `cd ./` to root directory
- `cd ..` to one level up,
- `cd path/to/file` into the desired directory,
- `pwd` to print out the current directory path. 

#### What does the following commands do: mkdir, rm, cat, cp, touch?
>1. `mkdir` make directory
>    * **`$ mkdir <mydir>`**

>2. `rm` remove files and directories
>    * **`$ rm <myfile>`**

>3. `cat` print file(s) content to stdout
>     * **`cat hello_world_file`**<br>
        `$ Hello World!` <br>
    or make a file with content with prompting user for input after the command:
>    * **`$ cat > hello_file`** <br>
>    `>>> Hello`<br>
>    `$ cat hello_file`<br>
>    `$ Hello`
    
>4. `cp` copy file from one place to another
>    * **`$ cp file1 path/to/directory/file2`**<br>
    or rename a file:<br> 
>   * **`$ cp file1 file2`**

>5. ```touch``` create a new empty file.
>   * **```$ touch <filename>```**

#### How can you look up what does a command do in Linux if you have no internet connection?
`$ <command> --help` or `$ man <command>`

#### What does the following commands do: head, tail, more, less?
1. ```more <filename>```  to view a text file one page at a time
>    * **```$ more <-num> <filename>```** : show the document page few lines as specified by ```-num```

2. ```$ less```  similar to ```$ more``` command
    * can navigate the page up/down
    * can search a string in less command. (use /```$ keywordto``` search)

>    * **```$ less <filename>```**

3. ```$ head```  displays the first ten lines of a file, unless otherwise stated.
>    * **```$ head <myfile.txt>```**  Would display the first ten lines of ```myfile.txt```
* ```$ head <-num> <myfile.txt>```  Would display the first ```<num>``` lines of ```myfile.txt```

4. ```$ tail```  display the last part of the file

    * ```$ tail <filename>```
    >    * **```$ tail -n <filename>```**  display the last n lines of the file

>5. **```$ cat```** can be used to join multiple files together and/or print the result on screen
    
* **```$ cat 01.txt ```**  display the contents of ```file 01.txt```
    * **```$ cat 01.txt 02.txt```**  display the contents of both files
    * **```$ cat file1.txt file2.txt > file3.txt```**  Reads ```file1.txt``` and ```file2.txt``` and  <br>
    combines those files to make ```file3.txt```
    * **```$ cat note5 >> notes```**  attach ```note5``` to ```notes```
    * **```$ cat > file1 ```**  add additional data in ```file1```

#### How do you download a file from internet using the terminal?
```$ wget (-o)``` or ```$ curl (-o)``` for further information, ```$ man wget``` or ```$ man curl```
