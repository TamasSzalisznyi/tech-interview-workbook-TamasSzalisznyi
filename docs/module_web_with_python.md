# Web with Python questions

## Software design

### Clean code

#### Point out 5 suggestions, how to format an SQL query!
 1. descriptive related but different database and table names
 2. keywords and expressions are aligned into separate columns
 3. indented new line after every logical step
 - query parameters indented to create a block like body
 - commas are at the end of the line

#### What layers can you name in a simple web application?
Layered architecture is a client–server architecture
 - presentation
 - application processing
 - data management functions<br

<blayer</b and <btier</b: layer is a logical-, tier is a physical structuring.

### Error handling
#### What error can occur, when an array does not have an element on the requested index?
Index error.
#### What is the “finally” block, and how would you use it?
Finally block is a block that is used to execute important code. E.g.: closing connection. <br
Finally block is always executed whether exception is handled or not. <br
Finally block follows try or catch block.

#### Why should we catch special exception types?
In general, an exception breaks the normal flow of execution and executes a pre-registered exception handler.

To point to using an exception handler is to keep running the code in cases which are "minor" problems from a view <br
of the program:
 - to avoid a bad input that can broke the consistency of the code
 - to avoid an index error with limiting the steps for the user

Or to prevent some mayor problem. For example: important sequences should properly given for the program.
 - misspelling or
 - harmful injections

can be handled with exception in the case that the code can not accept just the right one.

### Security
#### What is SQL injection? How to protect an application against it?
SQL Injection (SQLi) is a type of an injection attack that makes it possible to execute malicious SQL statements.
Prevent SQL Injection attacks with input validation and parametrized queries with prepared statements: do not use the input directly.
Also sanitizing all input e.g.: remove potential malicious code elements such as single quotes and other special characters. 
Turning off the visibility of database errors on production sites. 

#### What is XSS? How to protect an application against it?
Cross-site script injection.
Most of all:
 -   Context-sensitive server side output encoding<br>
and:
 -   Input validation or data sanitization.
 - Using safe JavaScript APIs

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
<b>Encrypting</b> is done by a key, reversible; with the same key it can be decrypted. Length hang from the source length.
Used in cases when the content is also important and needed, possible to transfer it in a secure way.<br>
<b>Hashing</b> is irreversible, one way transformation, the lenght is fixed by the algorithm.
Used when knowing or using the source - AKA the content - isn't in focus.
  
#### What encryption methods do you know?
Symmetric and asymmetric.

#### What hashing methods do you know?
Division reminder, folding, radix transformation, digit rearrangement.

#### How/where would you store sensitive data (like db password, API key, ...) of your application?
Hided from publicity.

## Computer science

### Algorithms

#### What is the difference between Stack and Queue data structure?
Stack data structure have just one pointer, adding operation (push) or removing operation (pop) take place from the <br
top of the list, where the pointer is.
Principle: LIFO (Last In First Out)

Queue have two pointers. One for each side of the list. The front side can take a new operation (enqueue), <br> 
to remove (dequeue) an operation the pointer should use the the rear side.
Principle: FIFO (First In First Out) 

#### What is BubbleSort? Describe the main logic of this sorting algorithm.
BubbleSort is a sorting method. Starting from the first element, comparing it with the next. If the next element 
higher then the previous move to the next. Else swap them. And so on till the last index.

#### Explain the process of finding the maximum and minimum value in a list of numbers!
Moving along the collection (iterate). Set the first as highest/lowest. Then comparing each next element with the
firts and replace it with the first accordingly.

#### Explain the process of calculating the average value in an array of numbers!
Adding each element value together and dividing it with the the total element count.
 
#### What is Big O complexity? Explain time and space complexity!
Big O Notation is to describe the complexity of an algorithm. How long an algorithm takes to run. 
It is to compare the efficiency of different approaches to a problem. Big O express the runtime as it grows relative to the input, 
as the input gets larger.

#### Explain the process of calculating the average value in a linked list of numbers!
Similar to the average counting of an array. We have to move along each nodes and adding together the values, than
dividing them with the total nodes count.

### Procedural
#### How the CASE condition works in SQL?
CASE is a program-flow controlling structure, like the ```if```  in other programming language.

#### How the switch-case condition works in JavaScript?
```Switch``` is the expression which is compared with the ```case``` clause(s). Optional an else branch can also be implemented.
This is an ```if-else``` construction, the right side of comparison is not repeated over and over.

#### How to achieve a switch-case-like structure in Python?
With a dictionary. After implemented the expression should be the key, with the
 ```dictionary.get(expression, default_returning_value)``` dictionary method and the values are the clauses.
The default  returning value role as else branch.

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

#### How the “ternary expression” looks like in Python?
`a += 1 if b % 2 else 2`
See below:
`statement | true ? false`

#### How the ternary expression looks like in JavaScript?
`statement | true ? false`

#### How to import a function from another module in Python?
With the ```[from module] import module_name``` than calling the function with ```module_name.function_name```

#### How to import a function from another module in JavaScript?
With 
```javascript
import name from "module-name";
import { member } from "module-name";
import "module-name";
````
than calling the function with ```module_name.function_name```

### Functional
#### What is recursion?
Recursive in functions mean: that the function call itself again at the end of the execution with value(s) what is/are defined by itself.
Can be other meanings too, e.g.: copying or deleting a folder in a recursive way will delete/copy the sub folders too.

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
- normal functions can be called directly
- class methods
- generator functions
- arrow functions
    
#### What is an event listener? How to attach one?
Event listeners give functionality to the application. Trough them can be triggered a function by the user.
Locating the target, attaching a listener function and in the callback handling the event with an event handler function.
    
- Locating:
    - object: `window` or `document`
    - methods: `getElementById` ,`getElementsBy[TagName, .ClassName]`, <br> `querySelector`, `querySelectorAll`
    
- Attaching:
    - method: `addEventListener`    
    - event listener: a string named event listener type
    - event handler: a callable function
    
#### How to trigger an event in JavaScript?
Event listeners have a target, which for they listen. It can be triggered by:
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
For phyton we can use the psycopg2 module api's to connect an application with psql database.

#### When do you use the DISTINCT keyword in SQL?
DISTINCT clause is used in the SELECT statement to remove duplicate rows from a result set. 

#### What are aggregate functions in SQL? Give 3 examples.
An aggregate function performs a calculation on a set of values, and returns a single value.
- MAX()
- SUM()
- AVG() 

#### What kind of JOIN types do you know in SQL? Could you give examples?
- (INNER) JOIN:
    - return the corresponding values if each table have the connection point.
- LEFT (OUTER) JOIN / RIGHT (OUTER) JOIN:
    - return the corresponding values if one of tables (corresponding) have the connection point
    
#### What are the constraints in sql?
Constraints are defining what value type can accepted by the column.

#### What is a cursor in SQL? Why would you use one?
A cursor allows us to encapsulate a query (the string we defined with parameters), process it each individual row at a time. 
And return with the values as a query-result. 
We use cursors when we want to divide a large result set into parts 
and process each part individually. 

#### What are database indexes? When to use?
To faster reach of a database table values, we can create an index.
The index containing a field value and point to the row which hold the column.
Index is sorted and acting like a placeholder to a faster search:
no need the look up all the columns in the rows for the data.

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

#### You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?
`SELECT * FROM table WHERE city = 'Miskolc'`

#### How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?
With the `RETURNING` keyword at the end of the query string as a readable noteback from the operation.

### HTML & CSS

#### What’s the difference between XML, XHTML and HTML?
XML --- eXtensible Markup Language
XHTML - eXtesnsible Hypertext Markup Language
HTML -- Hypertext Markup Language
SGML -- Standard Generalized Markup Language

HTML is SGML based, developed to parse data written in a serialized language (tags are predefined) and display it from the point of user or UI. 
Media or object can also be a part of the document.

XML is mostly for parsing data and transfer it between sites or to communicate different applications with each other.
Tags are not predefined and strict in closing tags but not in case. 

XHTML is XML based, composing the two other attributes. Parsed as an HTML document but allowing XML specifications. 

#### How to include a JavaScript file in a web page?
Between a ```script``` tag, along with the ```type```, ```rel``` and ```src``` attributes.

#### How to include a CSS file in a web page?
Between a ```link``` tag, along with the ```type```, ```rel``` and ```src``` attributes.

#### How to select an element using its id in CSS?
With selectors. Selectors can be ```tag_name {}```, ```.class_name {}``` and ```#id_name {}```.

#### How to select elements using their class in CSS?
```.class_name {}```

#### How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?
With chaining the class selectors: `.alpha.beta {}`

#### How to select all list items in all ordered lists on the page in CSS?
```ol > li {}```

#### How to select elements using their attributes in CSS?
Square brackets for the attributes with the element selector. E.g.: `selector[attribute_name] {}`

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
JS is a scripting language designed to control web page content.

#### When to use AJAX? Bring examples of its usage.
AJAX - Asynchronous Javascript and XML
Using asynchronous data transfer for operations to be done without reloading the whole page, operating just with he target content. 
E.g.: loading and displaying some data part in a table and those rest part in a separate place or in a new modal without touching 
the previous element or reload the page.

#### What is DOM and how to manipulate it from Javascript?
DOM - Document Object Model
DOM is representative displaying for the according html document, and those objects can modified.
- Creating, removing or replacing an element 
- Modifying an element's text and/or HTML content
- Get an element content and work with it

#### What are events and how/why to use them in Javascript?
JavaScript's interaction with HTML is handled through events that occur when the user or the browser manipulates a page.
With event listeners to catch them and with event handlers to react for them.
Using for make a site interactive, informative or any other UX, UI purpose.

#### What is event bubbling/capturing? How would you use it?
They are the direction of the execution on a node tree. Determine the action starting object and the direction it flow through.
<br><b>Capturing</b> when an event should be handled on the target ancestors first, then come the target node. 
<br><b>B>ubbling</b> is opposite, the target node is the first object, then comes the parents.

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
Remote exists on the git server. Local files are the copy of them on my disk.

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
Application Programming Interface.A set of functions and procedures allowing the creation of applications 
that access the features or data of an operating system, application, or other service.

#### What is REST API?
REST - Representational State Transfer. Software architectural style.
With it's API directed to manage http methods for getting or sending data, payload etc.

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
