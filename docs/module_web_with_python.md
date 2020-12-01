# Web with Python questions

## Software design

### Clean code

#### Point out 5 suggestions, how to format an SQL query!
 1. descriptive, related ,different and consequent database and table names
 Breaking down long queries into smaller pieces with:
 2. creating code blocks with logical steps in new lines
 3. code blocks intended after keywords
 4. separating language elements from parameters and table, column/names with usage of
 upper case letters and lower case letters
 5. using comments to explain steps
  
  ```postgresql
/*Get the list of every student who failed or was absent on exam*/
 
SELECT name, 
      student_group,
FROM course_marks
WHERE points &amp;lt; 300 OR points IS NULL; 
--student fails when gets 300 or less points.
--When student was absent, instead of points there is NULL in column
```
-->

#### What layers can you name in a simple web application?
Layered architecture is a client–server architecture
 - presentation
 - application processing
 - data management functions<br>

<b>layer</b> and <b>tier</b>: layer is a logical-, tier is a physical structuring.

### Error handling
#### What error can occur, when an array does not have an element on the requested index?
Index error.

#### What is the “finally” block, and how would you use it?
Finally-block, is a block that is used to execute important code. E.g.: closing connection. <br>
This block is always executed whether try was successful or not. <br>
Finally block follows try, and catch block.

#### Why should we catch special exception types?
In general, an exception breaks the normal flow of execution and executes a pre-registered exception handler.

The point to using an exception handler is to keep running the code in cases which are "minor" problems from a view <br>
of the program:
 - to avoid a bad input that can broke the consistency of the code
 - to avoid an index error with limiting the steps for the user

Or to prevent some mayor problem. For example: important sequences should properly given for the program.
 - misspelling or
 - harmful injections

can be handled with exception forcing the user to retry the input or breaking the code in early stage.

### Security
#### What is SQL injection? How to protect an application against it?
SQL Injection (SQLi) is a type of injection attack, that makes it possible to execute malicious SQL statements.<br>
To protect the application, one can:

**- Prevent SQL Injection attacks** <br> with input validation and parameterized queries with prepared statements: <br>
 to prevent the use of input directly.

**-** or **sanitizing all input** e.g.: remove potential malicious code elements such as single quotes and other special characters. 

-Turning off the visibility of database errors on presentation layer. 

#### What is XSS? How to protect an application against it?
Cross-site script injection.
Most of all:
 - Context-sensitive server side output encoding <br>
and:
 - Input validation or data sanitization.
 - Using safe JavaScript APIs
-->

#### How to properly store passwords?
In at least hashed form. Or hashed and salted.

#### What is HTTPS?
Hyper Text Transfer Protocol Secure. Encrypted HTTP connection basically.

#### What is encryption and decryption?
Encrypting something is 'hiding'. Decrypting is revealing the secret content.

#### What is hashing?
To transform a given character collection (data) to a fixed length character collection (value) with a mathematical algorithm, 
where the hashed output should be the same with every time from the same input. One way encryption.
 
#### What is the difference between encryption and hashing? When would you use which?
**Encrypting** is:
 - done by a key. Reversible; with the same key it can be decrypted. <br>
 - length hangs from the source length.
 - used in cases when the content is also important and needed, possible to transfer it in secure way.<br>

**Hashing** is :
 - irreversible, one way transformation
 - the length of the hashed object usually shorter than the origin, and fixed by the algorithm.
 - Used when knowing or using the source - AKA the content - isn't in focus. 
     - data tables indexing performance improvement: 
        - the shorter, hashed version is faster than comparing with longer key
        - comparing fixed-length keys allows the algorithm to operate more reliably and safely
    - storing passwords in hashed form prevent the reveal of the original password even if the database is corrupted
     
#### What encryption methods do you know?
Symmetric and asymmetric.

Symmetric: AES (Rijndael), DES (TripleDes), Twofish (Blowfish)
s-box. cycles.

Asymmetric: RSA, SHA
modulus, big primes
-->

#### What hashing methods do you know?
Division reminder, folding, radix transformation, digit rearrangement.

#### How/where would you store sensitive data (like db password, API key, ...) of your application?
Hided from publicity, separate from other datas.

## Computer science

### Algorithms

#### What is the difference between Stack and Queue data structure?
Stack data structure have just one pointer, adding operation (push) or removing operation (pop) take place from the <br>
top of the list, where the pointer is.<br>
Principle: LIFO (Last In First Out)

Queue have two pointers. One for each side of the list. The front side can take a new operation (enqueue), <br> 
to remove (dequeue) an operation the pointer should use the rear side.<br>
Principle: FIFO (First In First Out) 

#### What is BubbleSort? Describe the main logic of this sorting algorithm.
BubbleSort is a sorting method. Starting from the first element, comparing it with the next.<br>
If the next element higher than the previous move to the next. Else swap them, and so on till the last index.
The algorithm has O(n^2) complexity as the logic has to be repeated for every element for the total length of the array.
```python
    array = [8, 1, 4, 7, 2, 3, 9]
    for i in range(len(array)):
        for j in range(len(array)):
            if array[i] > array[j]:
                swap = array[j]
                array[j] = array[i]
                array[i] = swap
```

#### Explain the process of finding the maximum and minimum value in a list of numbers!
The process is:
- Moving along the collection (iterate) once. 
- Set the first as highest/lowest, say min and max.
- Then comparing each next element with the min/max value and replace it accordingly.
- Every time if the actual value higher than max, or lower than min, replacing them continuously<br>
 will find the minimum and maximum values for the end of the array.

```python
    array = [1, 2, 3, 4, 5, 6, 7, 8]
    min, max = array[0]
    for i in range(len(array)):
        if array[i] < min:
            min = array[i]
        elif array[i] > max:
            max = array[i]
```

#### Explain the process of calculating the average value in an array of numbers!
Adding each element value together and dividing it with the the total element count.
```python
    array = [1, 2, 3, 4, 5, 6, 7, 8]
    sum = 0    
    for i in range(len(array)):
        sum += array[i]
    
    average = sum / len(array)
```
 
#### What is Big O complexity? Explain time and space complexity!
Big O Notation is to describe the complexity of an algorithm. How much computation needed to perform an action, <br>
so how long an algorithm takes to run.<br> 
It is to compare the efficiency of different approaches to a problem.<br>
Big O express the runtime as it grows relative to the input, as the input gets larger.
Typicals are: O(1), O(n), O(n^2), O(log(n))

#### Explain the process of calculating the average value in a linked list of numbers!
Similar to the average counting of an array. We have to move along each nodes and adding together the values, than
dividing them with the total nodes count.

### Procedural
#### How the CASE condition works in SQL?
CASE is a program-flow controlling structure, like the ```if - else if - else```  in other programming language.
Working in a form of CASE - WHEN - THEN - ELSE

```postgresql
    CASE expression
        WHEN value_1 THEN result_1
        WHEN value_2 THEN result_2 
        [WHEN ...]
    ELSE
        else_result
    END
```
CASE is an expression, can use it with SELECT, WHERE, GROUP BY, and HAVING clause.

#### How the switch-case condition works in JavaScript?
```Switch``` is the expression which is compared with the ```case``` clause(s). Optional an else branch can also be implemented.
This is an ```if-else``` construction, the right side of comparison is not repeated over and over.

#### How to achieve a switch-case-like structure in Python?
With a dictionary. After implemented the expression should be the key, with the
 ```dictionary.get(expression, default_returning_value)``` dictionary method and the values are the clauses.
The default returning value role as else branch.

#### Explain variable scoping in Python!
According to the LEGB rule: local, enclosing, global, built-in, the look-up for the namespaces are started from the most inner scope:
which is the local. E.g.: in the body of a function.
 
#### What’s the difference between const and var in JavaScript?
```var``` is a variable, the value can be modified after all. ```const``` is a constant, 
the value is immutable, can't be reassigned  after declaration.
```var``` have a function scope, ```const```  have block scope.

#### How the list comprehension looks like in Python?
List comprehensions consist of an iterable containing an expression followed by a for clause. 
This can be followed by additional for or if clauses. Like lists it supposed to use the square brackets.

syntax: `[expression for item in list]`<br>

`matrix = [[x for x in range(4)] for y in range(4)]`<br>

should print:
```
[[0, 1, 2, 3]
[0, 1, 2, 3]
[0, 1, 2, 3]
[0, 1, 2, 3]]
```

#### How the “ternary expression” looks like in Python?
Conditional expression.

Syntax: `<expression1> if <condition> else <expression2>`<br>

```python
n = 5
print("Even") if n % 2 == 0 else print("Odd")
# >>> Even
```

#### How the ternary expression looks like in JavaScript?
Syntax: `statement ? true : false`

```javascript
function getFee(isMember) {
  return (isMember ? '$2.00' : '$10.00');
}

console.log(getFee(true));
// output: "$2.00"

var age = 26;
var beverage = (age >= 21) ? "Beer" : "Juice";
// output: "Beer"
```

#### How to import a function from another module in Python?
With the `import` keyword, in the form of:<br>

`[from module] import module_name` 

then the function is callable in the form of:<br>

`module_name.function_name`

#### How to import a function from another module in JavaScript?
With 
```javascript
import functionName from "moduleName"; //or

import { member } from "moduleName"; //or

import "moduleName";
````
than calling the function with:<br>
 
 ```moduleName.functionName```

### Functional
#### What is recursion?
Recursive in functions mean: that the function call itself again at a point of the execution.

#### Write a recursive function which calculates the Fibonacci numbers!
```javascript
    function fibo(limit, a=0, b=1) {
        if (b >= limit) {
            return
        }
        let c = a + b;
        console.log(c);
        return fibo(limit, b, c)
    }
    
    fibo(30);
```

#### How to store a function in a variable in Python?
With assigning it to a variable.
The returning value from a function can be stored in a variable or
the function can be called via a variable which is assigned to the function declaration.(definition)

#### List the ways of defining a callable logical unit in JavaScript!
- Normal functions can be called directly.

```javascript
function doSomething(param) {
    console.log(param)
}
doSomething("I'm called directly");
```

- As property of an Object, call it as Object method.  

```javascript
const anObject = {
    doSomething : function(param) {
        console.log(param)
    }
}

anObject.doSomething("I'm a property of anObject")
```

- Generator functions.<br>
These functions are returning with an iterator, calling this iterator `next()` method will `yield` the predefined value, <br>
and a boolean value; <br>
`{ value: ..., done: ... }` <br>
`True` until the iterator has more elements and `False` after it reached the `return` statement.<br>
Syntax is: `function*`<br>
Keyword is `yield`

```javascript
function* generatorFunction() {
    yield "This is the first return"
    console.log("First log!")
    yield "This is the second return"
    console.log("Second log!")
    return "Done!"
}

const myGenerator = generatorFunction()
myGenerator.next()
//output: 
//{value: "This is the first return", done: false}

myGenerator.next()
//output:
//First log!
//{value: "This is the second return", done: false}

myGenerator.next()
//output:
//Second log!
//{value: "Done!", done: true}
```

- Arrow functions.<br>
These functions have a wide variety to use: parentheses, method body, return statement can be omitted in particular circumstances.
A basic example:
```javascript
// Traditional Function
function (a, b){
  return a + b + 100;
}

// Arrow Function
(a, b) => a + b + 100;
```
>Arrow functions return value can be stored in variables, 
`let bob = a => a + 100;`<br>
>can be used in place to do some work or be nested under other function.
 
- As constructors.<br>
 Functions can be invoked as constructors, via the new operator.
```javascript
class Polygon {
    constructor() {
        this.name = 'I'm a Polygon';
    }
}

const polygon = new Polygon();

console.log(polygon.name);
//output: "I'm a Polygon"

```

#### What is an event listener? How to attach one?
Event listeners give functionality to the application. Trough them can be triggered a function by the user.<br>
Locating the target, attaching a listener function and (in place with arrow or in the callback)<br>
handling the event with an event handler function.
    
- Locating:
    - object: `window` or `document`
    - methods: `getElementById` ,`getElementsBy[TagName, .ClassName]`, <br> `querySelector`, `querySelectorAll`
    
- Attaching:
    - method: `addEventListener`    
    - event listener: a string named event listener type
    - event handler: a callable function
        
#### How to trigger an event in JavaScript?
Event listeners have a target, which they listen for. It can be triggered by:
- mouse actions
- keyboard actions
- content load (or change) actions

#### What is a callback function? Tell some examples of its usage.
A function if passed as argument to a function, is a callback function. 
The invoking function become a higher-order function, and will control the execution of called back function
<br>
E.g.: a script can modify the content after a fetch script executed and returned the values.
    
#### What is a Python decorator? How does it work? Tell some examples of its usage.
Decorator is function, executed before the invoked function and the return value bounded with the decorated function
return value.

#### What is the difference between synchronous and asynchronous execution?
sync: being executed after the page has loaded and the script also be loaded.
async: load of the page and the script started parallel, script executed right after calling.
  
## Programming languages

### SQL

#### How can you connect your application to a database server? What are the possible ways?
I need a connection string and a connection object from the database provider to set a session with the database server.
For Python we can use the psycopg2 module's api to connect an application with psql database.

#### When do you use the DISTINCT keyword in SQL?
The keyword is used to select only **unique values** from a specified column(s) in a database table.<br>

| Car Brand | Model |	Year | Color |
:---: | :------: | --- | --- |
| Toyota | Camry XLE | 2005 | Gray |
| Honda | Accord EX | 2002 | Black |
| Lexus | ES 350 | 2008 | Gray |
| BMW |	3 Series Coupe | 2008 |	Red |

```postgresql
SELECT DISTINCT 
    Color
FROM Cars
```
resulting in:
 
| Color |
| --- |
| Black |
| Gray |
| Red |

#### Difference between WHERE and HAVING clauses.
The fundamental difference between WHERE and HAVING is this: 
    
**- WHERE** *selects input rows before groups and aggregates are computed*<br> 
- it controls *which rows go into the aggregate computation*
- the WHERE clause must not contain aggregate functions 
(it makes no sense to try to use an aggregate to determine which rows will be inputs to the aggregates.) 
    
**- HAVING** *selects group rows after groups and aggregates are computed*.<br> 
- HAVING clause always contains aggregate functions. 
- HAVING clause that doesn't use aggregates -> WHERE stage
- behaving as a filter function

#### What are aggregate functions in SQL? Give 3 examples.
An aggregate function performs a calculation on a set of values, and returns a single value.

- MAX(expression) - return the highest value from expression specified rows
- MIN(expression) - return the lowest value from expression specified rows
- SUM(expression) - return the total value from expression specified rows
- AVG(expression) - return the average value from expression specified rows
- COUNT(*) / COUNT(expression) - return the number of all rows / number of rows where expression true

#### What kind of JOIN types do you know in SQL? Could you give examples?
- `(INNER) JOIN`:
    - return the corresponding values if each table have the connection point.
- `LEFT (OUTER) JOIN` / `RIGHT (OUTER) JOIN`:
    - return the corresponding values if one of tables (corresponding) have the connection point
- `CROSS JOIN` (Cartesian-join) / `FULL JOIN`:
    - return each row from connected tables. `INNER JOIN` is a subset of `FULL JOIN`, where the `WHERE` condition is met.
    
#### What are the constraints in sql?
Constraints are defining what value type can accepted by the column or by a table.

By column:
- **NOT NULL** - Ensures that a column cannot have a NULL value
- **UNIQUE** - Ensures that all values in a column are different
- **PRIMARY KEY** - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
- **FOREIGN KEY** - Uniquely identifies a row/record in another table
- **DEFAULT** - Sets a default value for a column when no value is specified

By table:
- **CHECK** - Ensures that all values in a column satisfies a specific condition
- **INDEX** - Used to create and retrieve data from the database very quickly

#### What is a cursor in SQL? Why would you use one?
A cursor can be viewed as a pointer to one row in a set of rows.
- **can only reference one row at a time** 
- **can move to other rows of the result set as needed**
- enables the sequential processing of rows in a result set
- can perform complex logic on a single row
 
I found a few situations for using cursor, but as I understand, it is preferred to let the DB doing the work<br>
through the SQL queries with commands and clauses.<br>
This is because SQL languages are procedural-declarative, and implementations from vendors are optimised and<br>
are better in performance than using cursors.
   
One could use cursors:

- Mostly for database administration tasks like:
    - **backups**, 
    - **integrity checks**, 
    - **rebuilding indexes**
- For one-time tasks when you’re sure that possible poor performance won’t impact the overall system performance
- Calling a stored procedure a few times using different parameters.<br>
 In that case, you would get parameters from cursor variables and make calls inside the loop

#### What are database indexes? When to use?
To faster reach of a row from a database's table, we can create an index.<br>
The index containing a field value and point to the row which hold the column.<br>
Creating an index on a field in a table creates another data structure<br> 
which holds the field value, and a pointer to the record it relates to.<br> 
This index structure is then sorted, allowing Binary Searches to be performed on it.

#### What are database transactions? When to use?
A transaction is a single unit of logic or work. According to the 
ACID discipline (atomicity, consistency, isolation, durability) a database transactions should be done for all or nothing:
this is intended to keep data integrity and to maintain a consistent data set. 
Using transactions ensures that the database engine can roll back the transaction.

#### What kind of database relations do you know? How to define them?
Table connection defined by keys, which are representing the connection between the tables.
 1. one-to-one
    - if one table primary key referenced as the other table foreign key.
 1. one-to-many
    - if one table primary key referenced as more than one other table foreign key. 
 1. many-to-many
    - if more than one table key pointing to more than one table keys. For that is needed an intersection table who is controlling
the connection between the relations.

#### You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). 
#### How would you query all records related to Miskolc?
```postgresql
 SELECT * 
 FROM address_table 
 WHERE city 
 LIKE = '%Miskolc%';
```

#### How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?
With the `RETURNING` keyword at the end of the query string as a readable noteback from the operation.

```postgresql
INSERT INTO a_table 
        (column_1, column_2, column_n)
VALUES ('value_1', 'value_2', 'value_n')
RETURNING column_x;
```

### HTML & CSS

#### What’s the difference between XML, XHTML and HTML?
XML --- eXtensible Markup Language
XHTML - eXtensible Hypertext Markup Language
HTML -- Hypertext Markup Language
SGML -- Standard Generalized Markup Language

**HTML** is SGML (Standard Generalized Markup Language) based,<br> 
developed to parse data written in a serialized language (tags are predefined) and<br> 
display it from the point of user or UI.<br> 
Media or object can also be a part of the document.

**XML** is mostly for parsing data and transfer it between sites or to communicate different applications with each other.<br>
Tags are not predefined, strict in closing tags, case insensitive. 

**XHTML** is XML based, composing the two other attributes.<br> 
Parsed as an HTML document but allowing XML specifications. 

#### How to include a JavaScript file in a web page?
Between a `script` tag, between the header tags, along with the `type`, `rel` and `src` attributes.

#### How to include a CSS file in a web page?
Inline - by using the `style` attribute inside any HTML elements opening tag followed by CSS properties.

Internal - by using a `<style>` element in the <head> section followed by the `type`, `rel` and `src` attributes.<br>

External - by using a `<link>` element to link to an external CSS file followed by the `type`, `rel` and `src` attributes.

#### How to select an element using its id in CSS?
Syntax: `#id`
```css
#bob {
 text-transform: uppercase;
}
```
```html
<div class="people" id="bob">Bob</div>
```

#### How to select elements using their class in CSS?
Syntax: `.class-name`
````css
.people {
    background-color: white;
}
````
```html
<div class="people" id="bob">Bob</div>
```

#### How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?
With chaining the class selectors:
 ```css
.alpha.beta {
    background-color: darkblue;
}
```

#### How to select all list items in all ordered lists on the page in CSS?
```css
ol > li {
    padding: inherit;
}
```

#### How to select elements using their attributes in CSS?
Square brackets for the attribute, optionally with the element selector and attribute value.<br> 
Syntax: `selector[attribute[[~|^*]=value] { css_property: value }` <br>
`~|^*` are wildcards for containing, starting, begins with and value contains. <br>

```html
<input type="checkbox" role="button" id="checkbox_one" class="top sample">
```
```css
#checkbox_one[role=button] {
    color: coral;
}
```

#### What are UX and UI?
User Experience and User Interface.

#### Please list some points that an application should fulfill to have good UX.
- Meet the users' needs
- Have a clear hierarchy
- Consistency
- Understand accessibility
- Usability

#### What is XML, XSLT, DTD?
- XML is a markup language, to create XML document in the proper way
- XSLT - Extensible Stylesheet Language Transformations is the XML stylesheet formatting language
- DTD -- Document Type Definition is for validating the XML document

#### What is the difference between HTML and XML?
<b>HTML</b>
- designed to display data & focus on how data looks
- tags are predefined.
- tags are case sensitive.
- stylesheet for HTML are optional.
- static in nature.
- is the presentational language.
- some HTML elements can be improperly nested with each other.
- it is not mandatory to close the tag.

<b>XML</b>
- used to describe data & focus on what data is
- tags are not predefined.
- tags are not case sensitive.
- it is mandatory to close the tag.
- stylesheet is needed for formatting the data.
- elements must be properly nested.
- is dynamic in nature.
- is more programming language.

### Javascript

#### What is javascript?
JS is a scripting language designed to control web page content.<br>
Event-driven, functional, imperative and dynamic typed multi-paradigm scripting language.

#### When to use AJAX? Bring examples of its usage.
AJAX - Asynchronous Javascript and XML<br>
Using asynchronous data transfer for operations to be done without reloading the whole page,<br> 
operating just with he target content. 

Usage: A modern web page may use a lot of different components. The load time may take significant amount of time.<br>
For a better UX the web page should not wait for load in all the parts together then displaying it's final content and,<br>
render it as a whole and repeat it after every interaction with the user,<br> 
instead the different parts can be loaded parallel; *asynchronously* and let be displayed immediately at the time<br> 
when the individual parts finished with loading.  

#### What is DOM and how to manipulate it from Javascript?
DOM - Document Object Model
- the data representation of the objects that comprise the structure and content of a document on the web.<br>  
- a programming interface for HTML and XML documents.<br> 
- it represents the page so that programs can change the document structure, style, and content. 
- a web page is a document, and the DOM represents the document as nodes and objects.<br> 
That way, programming languages can connect to the page.
    - Creating, removing or replacing an element 
- DOM is an object-oriented representation of the web page, which can be modified with a scripting language such as JavaScript.
- JS modify the DOM with scripts, these scripts are linked with the `<script>` tags in the HTML `<head>` section.

#### What are events and how/why to use them in Javascript?
JavaScript's interaction with HTML is handled through events that occur when the user or the browser manipulates a page.
With event listeners to catch them and with event handlers to react for them.
Using for make a site interactive, informative or any other UX, UI purpose.

#### What is event bubbling/capturing? How would you use it?
They are the direction of the execution on a node tree.<br> 
Determine the action starting object and the direction it flow through.<br> 

**Capturing**<br>
```javascript
elem.addEventListener(..., {capture: true})
``` 
The browser checks to see if the element's outer-most ancestor has an onclick event handler<br> 
registered on it for the capturing phase, and runs it if so.<br>
Then it moves on to the next element and does the same thing, then the next one,<br> 
and so on until it reaches the element that was actually selected.

**Bubbling**<br> When an event happens on an element, it first runs the handlers on it,<br> 
then on its parent, then all the way up on other ancestors.
```html
<form onclick="alert('form')">FORM
    <div onclick="alert('div')">DIV
        <p onclick="alert('p')">P</p>
    </div>
</form>
```
The alert message will be: "p", "div" and "form".

#### What is JSON and how do we use it?
JSON format is used for serializing and transmitting structured data over a network connection. 
Primarily to transmit data between a server and web application.
Through 'jsonify' a collection; structuring in a dictionary-like form.

## Software engineering

### Version control

#### What type of branching strategy would you use?
Opening a new branch for every development station (or it can mean for every team member) 
and when it's done then merge back to master so avoid conflicts or losing a good state the code.

#### What would you do if you find a bug on the production code (master branch)?
I would open a new branch: locate and fix the bug, after testing merging it back to master.

#### How can you move changes from one branch to another in GIT?
Make and checkout to a new branch will copy the actual state of the original branch where can be rollback or set back
status. 
Rebase or merge bring changes from another branch into the current one.

#### How does a VCS help with code reviews?
With the pull request, as inviting the other members to review the developed branch.

#### What is your favorite git command? Why?
`git status` I like see the result.

#### What does remote/local mean in Git? 
Remote exists on the git server. Local files are the origin or the copy of them on my disk.

### DevOps

#### Why is it good to use a package manager software?
Easy, safe and clean install packages, modules, extensions.
 
#### Why is it good to use a virtual environment for a project?
Different dependencies can safely separated for every project. For example one project is hanging around from a while,
there is already an update for one of the module which is used by. With venv the module can be available in both versions
without any problem.
  
### Networks

#### What kind of HTTP status codes do you know
- 100–199 - Informational responses
- 200–299 - Successful responses
- 300–399 - Redirects
- 400–499 - Client errors
- 500–599 - Server errors

#### What is a API?
Application Programming Interface. A set of functions and procedures allowing the creation an interface for applications 
that access the features or data of an operating system, application, or other service.

#### What is REST API?
REST - Representational State Transfer. 
A software architectural style to provide interoperability between computer systems on the internet and to improve
*performance, scalability, simplicity, modifiability, visibility, portability and reliability.*

- **Uniform Interface**<br>
defines the interface between clients and servers. It simplifies and decouples the architecture, 
which enables each part to evolve independently.
The uniform interface that any REST services must provide is fundamental to its design.
    - **Resource-Based**<br>
        - resources are identified using URIs as resource identifiers. 
        - resources are conceptually separate from the representations that are returned to the client.<br>
            > For example, the server does not send its database, but rather, some HTML, XML or JSON 
            (depending on the details of the request and the server implementation
            that represents some database records expressed, 
    - **Manipulation of Resources Through Representations**<br>
    When a client holds a representation of a resource, including any metadata attached, 
    it should have enough information to create, modify or delete the resource on the server, 
    if it has permission to do so.
    - **Self-descriptive Messages**<br>
    Each message includes enough information to describe how to process the message. 
        >For example, which parser to invoke may be specified by an Internet media type (previously known as a MIME type). 
        Responses also explicitly indicate their cache-ability.
    - **Hypermedia as the Engine of Application State (HATEOAS)**<br>
        servers provide information dynamically through hypermedia       
        - Clients deliver state via:
            - body contents, 
            - query-string parameters, 
            - request headers and the 
            - requested URI (the resource name).<br> 
        
        - Services deliver state to clients via: 
            - body content, 
            - response codes, and 
            - response headers.<br> 

- **Stateless**<br>
    - URI uniquely identifies the resource and the body contains the state (or state change) of that resource. 
    - The client must include all information for the server to fulfill the request, 
        - as part of the URI, 
        - query-string parameters, 
        - request body, or header.

    - Then after the server does it's processing, the appropriate state are communicated back to the client via:
        - headers, 
        - status and 
        - response body.
    - resending state as necessary if that state must span multiple requests.<br> 
    - **Statelessness enables greater scalability** since the server does not have to maintain, update or communicate that session state. 
        >State, or application state, is that which the server cares about to fulfill a request—data necessary for the current session or request.

- **Cacheable**<br>
Clients can cache responses. Responses must therefore, implicitly or explicitly, define themselves as cacheable, or not, 
to prevent clients reusing stale or inappropriate data in response to further requests. 
Well-managed caching partially or completely eliminates some client–server interactions, further improving *scalability* and *performance*.

- **Client-Server**<br>
The uniform interface separates clients from servers. 
    - *Portability of client code is improved.*<br> 
    clients are not concerned with resource implementation, those are remaining internal to each server<br>
    - *servers can be simpler and more scalable.*<br> 
    Servers are not concerned with the user interface or user state<br> 
    - *Servers and clients may also be replaced and developed independently*, as long as the interface is not altered.

- **Layered System**<br>
    - Intermediary servers may improve system scalability by enabling load-balancing and by providing shared caches. 
    - Layers may also enforce security policies.
    
- **Code on Demand** (optional)<br>
    Servers are able to temporarily extend or customize the functionality of a client by transferring logic to it. 
    that it can execute. Examples of this may include: 
    - compiled components such as Java applets and 
    - client-side scripts such as JavaScript.

#### What is JSON? When to use?
JavaScript Object Notation.
JSON format is used for serializing and transmitting structured data over network connection. 
It is primarily used to transmit data between a server and web applications. 

#### What is TCP/IP? What layers does it define, what are they responsible for?
<b>TCP/IP</b> - Transmission Control Protocol/Internet Protocol

<b>TCP</b> defines how applications can create channels of communication across a network. 
It also manages how a message is assembled into smaller packets before they are then transmitted over the internet 
and reassembled in the right order at the destination address.
<br><b>IP</b> defines how to address and route each packet to make sure it reaches the right destination. 
Each gateway computer on the network checks this IP address to determine where to forward the message.

#### What’s the difference between TCP and UDP?
<b>TCP</b> is a connection-oriented protocol, does error checking and also makes error recovery, acknowledgment segments. 	
Using handshake protocol. Reliable as it guarantees delivery of data to the destination router. It provides flow control and acknowledgment of data.

<b>UDP</b> is a connectionless protocol. Checks for integrity at the arrival time. It is not connection-based,so one program can send lots of packets to another.
UDP protocol has no fixed order because all packets are independent of each other.There are no tracking connections. Performs error checking, but it discards erroneous packets.
No Acknowledgment segments. No handshake protocol. The delivery of data to the destination can't be guaranteed in UDP.
UDP has just a single error checking mechanism which is used for checksums. 

#### How does an HTTP Request look like? What are the most relevant HTTP header fields?
Request headers contain more information about the resource to be fetched, or about the client requesting the resource.
Method name, target address, user agent, encodings and connection types, cookie information.

#### How does an HTTP Response look like? What are the most relevant HTTP header fields?
Response headers hold additional information about the response.
status of the response, location where it came from, its content length or MIME type.

#### What is DNS? How does it work?
DNS - Domain Name Servers
They maintain a directory of domain names and translate them to Internet Protocol (IP) addresses. 

#### What is a web server?
On the hardware side, a web server is a computer that stores web server software and a website's component files.
On the software side, a web server includes several parts (e.g. HTML documents, images, CSS stylesheets, and JavaScript files) that control how web users access hosted files, at minimum an HTTP server.

#### Explain the client-server architecture.
Each computer or process on the network is either a client or a server.<br>
<b>Clients</b> are the users whom consuming the<br> 
<b>Servers</b> provided, hosted, managed network.

#### What would you use a session for?
For conserving a temporary state about the connection and about the user. They expire after the browser closed.

#### What would you use a cookie for?
For saving locally data about the user or from the connection types or settings.

## Software Development Methodologies

#### What kind of software development methodologies do you know? What are the main features of these?
- <b>Waterfall</b> - Very simple and easy to understand or to manage. Rigid. Each phase has a review process. 

- <b>Agile</b> - Adaptive approach which is able to respond to the changing requirements of the clients. Direct communication and feedback from customer.

- <b>Scrum</b> - Decision-making is entirely in the hands of the teams, lightly controlled method, frequent updating of the progress, 
project development steps is visible. A daily meeting easily helps the developer to make it possible to measure individual productivity. 
This leads to the improvement in the productivity of each of the team members

#### What are the SCRUM roles?
- Product owner
- Scrum master
- Development team

#### What are the SCRUM ceremonies?
- Sprint planning meeting 
- Daily Scrum
- Sprint review meeting
- Sprint retrospective meeting

#### What are the SCRUM artifacts?
- Product increment
- Product backlog
- Sprint backlog

#### What is the main goal of a retrospective meeting?
To get better understanding about how the work went during the last sprint, and through this
find better ways to meet the project's goals. 

#### Explain, when would you recommend to use the waterfall methodology?
- Requirements are very well known, clear and fixed.
- Product definition is stable.
