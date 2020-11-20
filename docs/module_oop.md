# OOP questions

## Software design

### Error handling

#### What does 'fail fast' mean in terms of exception handling? Why is it a good practice?
Fail fast is a programming design; a code tries to fail as soon as possible at variable or object initialization. 

When exception occur it is not handled silently or with default values 
because there is a chance then that the error will show up later when harder to trace back.

It should decreases the internal software entropy, and reduces debugging effort.
    
## Computer Science

### Data structures

#### How to find the middle element of singly linked list in O(n)?
n = number of elements / 2.
If we know the size of the linked list (e.g.: the number of elements it holding) then we should step (iterate) size / 2 times.
Other approach should be using two pointer: one slower pointer who step one, and a faster pointer who step two. 
If the faster pointer reach the last element, the slower one should be on the middle.
    
#### Given an array of integers going from 1 to 100 (both inclusive) there is a duplicated entry. How to find it?
Store the first element in a temporary variable then iterating over the array, if there is no match, 
begin the process with the second element and so on till an equality comparison return true.
    
#### What is a linked list? How to find if a linked list has a loop?
Linked list is a data structure which hold the values in a field and a pointer to the next element 
(and optionally a pointer to the previous).
Floyds cycle say: 
starting with two pointers, one is faster than the other, if they met, there is a loop in the list.
    
#### What is the Big O time complexity of the common operations in an ArrayList, LinkedList, HashMap? And of a bubble sort, quicksort, finding items in a Binary Search tree?
ArrayList: get O(1), search O(n), insert O(n), delete O(n)
LinkedList: get O(n), search O(n), insert O(1), delete O(1) (without search) 
HashMap: average case: O(log n), worst case: O(n)
 
As I understand: HashMap values stored in a LinkedList until the elements are less then 8, after that become a binary search tree.
 
Average time:
- bubble sort: O(n^2)
- quick sort: O(n log(n))
- binary search tree: O(log n)

#### How does HashMap work?
It's mixture from an array and a linked list. 
The keys are hashed, stored in the array, and the value stored in the linked list, in buckets, in the same order as the array containing them.
To get the value from the linked list we know where is it exactly from the index of the array.
    
#### Why is it important for keys in a map to have an immutable type? (Consider String for example.)
Because to find an element we need the hash code of the key and it must not change at time.
    
### Other

#### What is a garbage collector, in a nutshell?
The garbage collector is an autamated subroutine to free up space from the heap memory. It's designed to remove entries
what are doesn't have pointer assigned to any variable.
(Algorithms inspect the memory from time to time for dead, weak or other reference
traces and recycling the memory allocated or let them as they are)
    
## Programming paradigms

### Procedural

#### What is casting? What is the difference between up vs downcasting?
Casting is changing the type of a data.	
    
Upcasting cast the object to it's supertype. (e.g.: int to float)
Downcasting is possible to cast the object to it's sub class in the object hiearchy and explicit because of the 
possible data losing by primitive types. (e.g.: from double to int)
     
#### Which order should we catch the exceptions? Why?
We should cath most precise exception becaus exception can be from
many different exception classes. (e.g.: ArrayIndexOutOfBoundsException, NullPointerException...)

Different exceptions needed to handle in different ways and this is easier with specifik exception and easier to debug.

### Object-oriented

#### What is a class?
Encapsulated form of a bunch of data.
Classes are blueprints for objects. 
We use them to hold and define the attributes for the object and/or for itself if it static. 

#### What is an object?
Object is an entity with atributes, created with the new keyword from a class constructor.
     
#### What is a constructor?
A constructor is a special type of method called with new keyword in order to create an object.
    
#### Do we require parameter for constructors?
A constructor can have zero or more parameter, even can be overloaded.
    
#### What is an interface?
Is a model for data hiding in OO, the outer scope can access an object attributes with through the interface(s) methods, 
which is(are) implemented by the class.
In its most common form, an interface is a group of related methods with empty bodies. (JavaDoc)

As I understand: interface is a common "entry point" for different classes which are implementing the interface, so
the invoker can handle all the different classes through one interface.

#### What are access modifiers?
They let the programmer to decide how the classes and objects are abstracted to the outer scope.

- private: access level is only within the class. It cannot be accessed from outside the class.
- package-private (default) : access level is only within the package. It cannot be accessed from outside the package.
- protected: access level is within the package and outside the package through child class. Without a child class, it cannot be accessed from outside the package.
- public: It can be accessed from within the class, outside the class, within the package and outside the package.
    
#### What is data hiding?
Data hiding is a software development technique specifically used in object-oriented programming (OOP) 
to hide internal object details (data members). 
Data hiding ensures exclusive data access to class members and protects object integrity by preventing unintended or intended changes
        
#### Can a static method use non-static members?
Static methods access non-static member through the object reference as parameter.
    
#### What is the difference between hiding a static method and overriding an instance method?
Static methods can not be overriden, they are initalized during compile time, 
they are not polymorh but they can be hided with an another static method.
Instance methods are late-binded, because of the polymorphism they can be overriden with an another 
instance method during run-time.

#### Define the following terms: Instantiation, Attribute, Method:
Instantiate in Java means to call a constructor of a Class which creates an instance or object, 
of the type of that class and returns a reference.

Attributes are fields and properties of the class and of the object.

Method is a collection of statements that are grouped together to perform a logical operation. 
with or without return values.

#### Could we access a static variable (or method) from a non-static method? Why?
Yes, because static fields and methods are belonging to the class and classes are initaized at compile time, 
also class members don't need any instance to be invoked. 

#### Could we access a non-static variable (or method) from a static method? Why?
Non-static fields or methods are object members, 
we can access them: calling the object with the object reference. 
 
#### How many instances you have of a static variable of a given class?
One. Everything else is a copy of that.

#### Why is it not a good practice to write a lot of static methods?
They aren't fit so in the OO principles (they more procedural):
- polymorphism not happening
- abstraction not happening as static classes can not implement interfaces, interfaces can not hav static method
    
#### What are the features of static attributes and static methods of a class? What are the benefits, when to use them?
They can be reached without an object instance because they belong to the class not to the instance.
Instances of that class sharing the same static field/method.
Static methods in Java are resolved at compile time. 
Since method overriding is part of Runtime Polymorphism, so static methods can't be overridden.
Abstract methods can't be static.
Static methods cannot use this or super keywords.

Instance methods can directly access both instance methods and instance variables.
Instance methods can also access static variables and static methods directly.
Static methods can access all static variables and other static methods.
Static methods cannot access instance variables and instance methods directly; they need some object reference to do so.

I am using them if I want a field to be shared amongs the instances.
Using static mathod should be good if they don't do anything else like a single computation depends from the
parameters, like utility or helper functions e.g.: Math class or String.format() or Arrays.asList() method.

#### What is the ‘this’ reference?
The reference to the current instance to itself or an attribute of it, where 'this' is called.

#### What are base class, subclass and superclass?
Object class is a base class (or superclass) for every other classes.
Every other class can have at most one more superclass and can have zero or more subclass.
Super- and subclasses made an inheritance hierarchy, 
Subclasses inherit the members fom the superclass allowed by the superclass. 

#### Draw an object oriented family (as entities, with relations) on the whiteboard.

#### Difference between overloading and overriding?
 Overloaded methods are in the same class, differ in parameters.
 Overriding is when an instance method will be called instead of another method with the same name but in another class(or super class).

#### What are the Object Oriented Principles? Explain the concepts with realistic examples!

OOP:

S – Single Responsibility Principle (SRP)
    one method doing one job.
O – Open Closed Principle (OCP)
    polymorphism and abstraction to build new functionality.
L – Liskov Substitution Principle (LSP)
    inherited classes can be usd without modification
I – Interface Segregation Principle (ISP)
    interfaces should be client specific
D – Dependency Inversion Principle (DIP)
    is a form of decoupling software modules

Java:

- encapsulation,
- abstraction,
- inheritance,
- polymorphism. 

Abstraction: showing only essential/necessary features of an entity/object to the outside world 
and hide the other information. 
-> getters, setters for private fields

Encapsulation: setting up a member data and method together into a single unit i.e. class. 
-> class, package	
    
Inheritance: the ability of creating a new class from an existing class, acquiring it's attributes and behavior. 	 
It helps to reuse, customize and enhance the existing code.
-> extend, implement

Polymorphism: means "many forms". 
A subclass can define its own unique behavior and still	share functionalities and behavior of its parent class,
but also it can have it's own behavior.
-> overloading, interface

#### What is method overloading?
Overloading is when an instance have a set method or constructor with same signature just difference
in parameter type and number.
The compiler will execute the one wich fit to the given parameter.
So the method and/or constructor can be called with different parameters.
 
#### What is method overriding?
Overriding is explicit annotated.
If also super class and subclass have a mthod with same name,
the compiler will execute the one where from the invoking come this is overriding.
    
#### Explain how object oriented languages attempt to simplify memory management for Programmers.
Some of the languages provide an automatic garbage-managment.
Java and C# are garbage-collected.
Stack, heap meta memory space also avaliable.
ArrayLst, HashMap capacity automated.
Interfaces and provided classes implemented by "java" also efficient in the way they using resources.

#### Explain the “Single Responsibility” principle!
One method should be responsible for one purpose. For one logical step or one job.
E.g.: one class created to give us a connection.
The methods are responsible to make that connection step by step, each doing their part.

#### What is an object oriented program? Explain, show.
As following OO principles, the program should contain one or several
encapsulated objects with fields to store data and procedures to access and/or
modify those fields.
These object then interact with each other and/or with the user.
	
#### How do you make a class immutable? What do you need to watch out for?
Declare the class as final so it can’t be extended.
Make all fields private so that direct access is not allowed.
Don’t provide setter methods for variables.
Make all mutable fields final so that its value can be assigned only once.
Initialize all the fields via a constructor performing deep copy.
Perform cloning of objects in the getter methods to return a copy rather than returning the 	actual object reference.

Watch out for when values passed to constructor, the deep copy technique let the
constructor to allocate a new memory space for the values in the final class,
this and the returned value by getter (as it is a copy) prevent a field modification
through refrence.
 
#### How many instances can be created for an abstract class?
Abstract class can not be instantiated diretly.

## Programming languages

### Java

#### What is autoboxing and unboxing?
Java compiler autobox primitive data types to objects from their corresponding wrapper class.
Unboxing is the reverse sequence.
    
#### If you have a variable, that shall store a positive whole number between 0 and 200, what primitive type would you use to store it?
I would use int. Maybe short.
    
#### What is the "golden rule" of variable scoping in Java? What is the lifetime of variables?
Static variables accessible from anywhere and their lifetime last as long the application running, 
whereas instance variables are accessible through the reference of that instance, and their lifetime span
from invoking them till they have refrence somewhere.
Inline or method varibles lifetime last till the enclosing brackets.
    
#### What is the purpose of the ‘equals()’ method?
To find out that two objects value are the same.
    
#### What is the difference between '==' and 'equals()'?
'==' can be used to comparing to primitive types, or comparing to objects memory location.
'equals' used to comparing objects values.
    
#### What does the ‘static’ keyword mean?
The keyword make static the 'annotated' class, method, block or variable and they are initalzed at compile time. 
They can not be instantiated because they do not belong to an object, but they belong to the class and a copy of them are used in future.
    
#### Why is the main() method declared as static? Explain.
As entry point, the JVM looking up for that exact method to start an application.
Also must not belong to an object because objects created later and stored elsewhere. 

#### What is the default access modifier in a class?
Packege-private.
    
#### What is the JVM?
The Java Virtual Machine is a virtual machine that enables a computer to run Java programs 
as well as programs written in other languages that are also compiled to Java bytecode. 
This is the feature which let the write one, run anywhere motto to come true, 
so the platform independency of java come from JVM.
    
#### What is the difference between the JRE and the JDK?
Java Runtime Enviroment responsible to run applications in java enviroment, 
Java Development Kit offer more: the JVM and JRE equipped with tools and utilities to provide an enviroment where 
coding is easier.
    
#### What is the difference between long and Long?
long is a primitive data type, Long is a wrapped object with long value.
    
#### Can a long store bigger numbers than a Long?
Nope.
    
#### What kind of packages do you know under java.util.* ? Bring at least 3 examples.
Collections, Date, Random, Arrays.
    
#### What are the access modifiers in Java? Which one could we use for class?
They supposed to controll the abstraction level determined by the programmer.
Public or default, package-private.
    
#### Can an “enum” contain methods in Java? Explain.
Enum is a special class, but class. And as a class can hold methods as well. E.g.: enum have also constructor.
    
#### When would you use a private/protected/public attribute? What is the difference?
The difference is the abstraction level.
Personally I'm using private for all fields in objects, getter should be public, setter and other methods are package-private and 
just the top level class (while possible) have public methods, to give controll for the user.
    
#### How do you prevent developers from subclassing a class?
Static and final classes can't be subclassed.
    
#### How do you prevent developers from overriding a method in a subclass?
Static and private methods can't be overriden.
    
#### How do you prevent developers from changing the value of a variable?
Does not provided setter methods prevent the write access, final declaration prevent from changing the value and
getter method should return with a copy to prevent the modify through the reference.
    
#### Think about money ;) How would you store a currency value, that shall support decimal parts? Think it through again, and try to think outside of the box!
The variable can be at least a float, but this isn't so precise, there are classes for that purpose,
BigDecimal and Currency.
    
#### What happens if you try to call something, that you have no access to, because of data hiding?
IllegalAccessError will be thrown.
Normally this caught at compile time.
    
#### What happens if you try to delete/drop an item from an array, while you are iterating over it?
Arrays have a fixed length which is set by initalization. During iteration element or elements can be modified, but the
size of the array can not be vary. The value of the element can be null, in that way can be dropped or deleted the element. 
UnsupportedOperationException should be thrown. 
    
#### What happens if you try to delete/drop/add an item from a List, while you are iterating over it?
ConcurrentModificationException can be thrown if the implementation does not support the remove operation.
But e.g.: the list iterator support it, the arrayList implement the list iterator interface.

#### What happens if you try to add an item to the end of an array, while you are iterating over it?
UnsupportedOperationException can be thrown if the implementation does not support the add operation.
 
A structural modification is any operation that adds or deletes one or more elements, 
or explicitly resizes the backing array. Setting the value of an element is not a structural modification

#### If you need to access the iterator variable after a for loop, how would you do it?
I would store the reference in an outsider variable, which is declared and initalized before the loop.
    
#### Which interfaces extend the Collection interface in Java. Which classes?
Main interfaces are: List, Queue, Set.
Main classes are: ArrayList, LinkedList, Vector, Stack, ArrayDeque, PriorityQueue, HashSet, LinkedHashSet, TreeSet.

#### What is the connection between equals() and hashCode()? How are they used in HashMap?
If two objects are equal, then they must have the same hash code. 
If two objects have the same hash code, they may or may not be equal.
(In the native implementation, equals() comparing th objects memory addresses.)
In HashMap, the ArrayList store the key as hash code and the index of that key is the position in the linked list, which stores
the value for the key. 
By search, the given key will be hashed, than it will be comparing with the equals() method, returning true, possible 
to get the value from the bucket.
    
#### What is the difference between checked exceptions and unchecked exceptions? Could you bring example for each?
Checked exception are detected by compile-time, indicate exceptional conditions that are out of the control of the program.
e.g.: IOException, SQLException, FileNotFoundException.
Unchecked exceptions are runtime exceptions, used to indicate logical error.
e.g.: NullPointerException, ArrayOutOfBoundsException  
    
#### What is Error in Java and how does it relate to Exception?
Exceptions can be handled by try-catch blocks or throws keyword, the system may recover with proper exception handling.
Exceptions can occuring during compile-time and also at run-time.
Errors are only occuring at run-time and the system can not recover from them.
A common error is: StackOverflowError.
    
#### When does 'finally' block run? What it is used for? Could you give an example from your projects when you would use 'finally'?
After a successfull try block or after the catch block if the try was unsuccessfull.
It is used to finalyze a logical operation, for example I would use finally after executing an SQL statement to close the connection.
 
#### What is the largest number you can work with in Java?
 2 up 64 -1 with 64bit unsigned long. But as I read, with sufficient memory in theory it's possible bigger number.
         
#### When you use method overriding, can you change the access level of the method, from protected to public? Why?
-->
#### When you use method overriding, can you change the access level of the method, from public to protected? Why?
The access level cannot be more restrictive than the overridden method’s access level.
So from protected to public yes, but traverse from public to protected no. 
  
#### Can the main method be overridden? Explain your answer!
No. As static methods are not capable for run-time polymorphis, they can not be overriden. 
And, as the main class is the only entry point for a java application, 
and thus it have the precise signature it's not allowed to have two from them.

#### When you use method overriding, can you throw fewer exceptions in the subclass than in the parent class? Why?
Yes. Overriding method should not throw checked exceptions that are new or broader than the ones declared by the overridden method.
The overriding method can throw narrower or fewer exceptions than the overridden method.
Because if a method declares to throw a given exception, the overriding method in a subclass can only declare to throw that exception or its subclass.
    
#### When you use method overriding, can you throw more exceptions in the subclass than in the parent class? Why?
No. Because if a method declares to throw a given exception, the overriding method in a subclass can only declare to throw that exception or its subclass.

#### What does "final" mean in case of a variable, method or a class?
Final mean in every case that the one which declared final can not be re-declared.
Thus final class or method can not be subclassed or overriden.
    
#### What is the super keyword?
The super keyword in Java is a reference variable which is used to refer immediate parent class object.
The keyword pointing to the immediate parent class constructor, method or a variabe as well.
    
#### What are “generics”? When to use? Show examples.
Generics could be used to develop a container that can have a type assigned at instantiation, referred to as a generic type, 
allowing the creation of an object that can be used to store objects of the assigned type. 
A generic type is a class or interface that is parameterized over types, 
meaning that a type can be assigned by performing generic type invocation, 
which will replace the generic type with the assigned concrete type. 

It is recommended to use generic interface for example, produce less interfaces or by methods if more than one parameter
or return value expected we can avoid, method overloading.
    
#### What is the benefit of having “generic” containers?
The assigned type would be used to restrict values being used within the container, 
which eliminates the requirement for casting, as well as provides stronger type-checking at compile time.
Also less code needed, without overloading we are able to handle multiple parameter or return value.
    
#### Given two Java programs on two different machines. How can you communicate between the two? What are the possible ways?
The java.net package in the Java platform provides a class, Socket, that implements one side of a two-way connection between 
your Java program and another program on the network. The Socket class sits on top of a platform-dependent implementation, 
hiding the details of any particular system from your Java program. 
By using the java.net.Socket class instead of relying on native code, 
your Java programs can communicate over the network in a platform-independent fashion.
    
Additionally, java.net includes the ServerSocket class, which implements a socket that servers can use to listen for 
and accept connections to clients.

Connect to the Web, the URL class and related classes (URLConnection, URLEncoder) are also might help, one application
can send data and the other can gather it for itself. 
URLs are a relatively high-level connection to the Web and use sockets as part of the underlying implementation. 
    
#### What is an annotation? What can be annotated and how? Show examples.
Annotation is a form of syntactic metadata that can be added to Java source code.
Classes, methods, variables, parameters and Java packages may be annotated with the @ sign.
I think the most common annotation is the @Override, which is used to order the compiler to override a method.
    
### Database

#### How can you connect your application to a database server? What are the possible ways?
I will need a driver, provided by DB providers, and a connection, provided by the driver.
The lower level is to use JDBC interface. The higher level is the JPA intetrface.
The point is to map the DB tables into java objects and to handle them as objects.
    
#### What do you know about database normalization?
Database normalization is the process of structuring a relational database in order to reduce data redundancy and improve data integrity.
There are three main reasons to normalize a database: 
- to minimize duplicate data, 
- to minimize or avoid data modification issues, 
- to simplify queries. 