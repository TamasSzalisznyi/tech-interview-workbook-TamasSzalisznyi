# OOP questions

## Software design

### Error handling

#### What does 'fail fast' mean in terms of exception handling? Why is it a good practice?
    1. A code when tries to fail as soon as possible at variable or object initialization. 
    In object-oriented programming, a fail-fast-designed object initializes the internal state of the object in the constructor, 
    launching an exception if something is wrong (vs allowing non-initialized or partially initialized objects that will fail later due to a wrong "setter"). 
    The object can then be made immutable if no more changes to the internal state are expected. 
    In functions, fail-fast code will check input parameters in the precondition. 
    In client-server architectures, fail-fast will check the client request just upon arrival, before processing or redirecting it to other internal components, returning an error if the request fails (incorrect parameters, ...). 
    2. Fail-fast-designed code decreases the internal software entropy, and reduces debugging effort.
    Fail-fast components are often used in situations where failure in one component might not be visible until it leads to failure in another component.
    A fail-fast system that is designed to halt as well as report the error on failure is less likely to erroneously perform an irreversible or costly operation.

## Computer Science

### Data structures

#### How to find the middle element of singly linked list in O(n)?
    O(n) = LinkedList.size() / 2.
    if we know the size of the linked list (e.g.: the number of elements it holding) then we should step (iterate) size / 2 times.
    other approach should be using two pointer: one slower pointer who step one, and a faster pointer who step two. If the faster pointer reach the last element, the slower one should be on the middle.
    
#### Given an array of integers going from 1 to 100 (both inclusive) there is a duplicated entry. How to find it?
    Converting the array to a set should eliminate the duplicates.
    
#### What is a linked list? How to find if a linked list has a loop?
    Linked list is collection where the elements have at least two, at most three field. 
    One of those are the field what contains actually the data, the second containing the pointer to the next element, 
    and if it a double linked list the third field point to the previous element.
    So these fields together building a node, the list what builded up from nodes is the linked list.
    If the linked list last node has the pointer to the first node, not just null, it's acting like a ring. or loop.
    
#### What is the Big O time complexity of the common operations in an ArrayList, LinkedList, HashMap? And of a bubble sort, quicksort, finding items in a Binary Search tree?
    Big O can be O(1) which is constant time needed to perform the operation.
    O(n) where is the n are the steps what needed to be done to perform the operation.
    // TODO: O(log(n)) if the -- 
    
#### How does HashMap work?
    It's mixture from an array and a linked list. The keys are hashed, stored in the array, and the value stored in the linked list.
    As I understand: the array containing keys like an index to help retrive the value from the linked list easier than the two 
    can on it's own.

#### Why is it important for keys in a map to have an immutable type? (Consider String for example.)
    To avoid collision.
    
### Other

#### What is a garbage collector, in a nutshell?
    The garbage collector is an autamated subroutine to free up space from the heap memory. It's designed to remove entries
    what are doesn't have pointer assigned to any variable.
    
## Programming paradigms

### Procedural

#### What is casting? What is the difference between up vs downcasting?
    Upcasting can be implicit, cast the object to it's supertype. (e.g.: int to float)
    Downcasting is possible to sub classes in the object hiearchy and explicit because of the 
    possible data losing by primitive types. (e.g.: from double to int)
     
#### Which order should we catch the exceptions? Why?
    We should cath the most common exceptions with the Exception class, which is used as a common exception pool.
    If we know what exception can occur during the code lifetime, we should precisely catch that exception with the 
    many different exception classes. (e.g.: ArrayIndexOutOfBoundsException, NullPointerException...)
    The order matters because there are runtime exceptions, IOexceptions and errors.
    Different exceptions needed handle different ways.

### Object-oriented

#### What is a class?
    Classes are blueprints or templates for objects. 
    We use them to describe types of entities, 
    define the properties and operations for the object.
    
#### What is an object?
    An object is an entity which can have fields and/or methods.
    But also object also the base class for every entity, IS-A superclass
    for every object which is created by us.
     
#### What is a constructor?
    A constructor is a special type of subroutine called to create an object. 
    It prepares the new object for use, often accepting arguments that the constructor uses to set required member variables.
    
#### Do we require parameter for constructors?
    A signature can have zero or more parameter.
    
#### What is an interface?
    In its most common form, an interface is a group of related methods with empty bodies. (JavaDoc)
    As I understand: interface is a common "entry point" for different classes which are implementing the interface, so
    the exceptor can handle all the different classes through one interface.
    
#### What are access modifiers?
    - private: access level is only within the class. It cannot be accessed from outside the class.
    - package-private (default) : access level is only within the package. It cannot be accessed from outside the package.
    - protected: access level is within the package and outside the package through child class. Without a child class, it cannot be accessed from outside the package.
    - public: It can be accessed from within the class, outside the class, within the package and outside the package.
    
#### What is data hiding?
    Data hiding is a software development technique specifically used in object-oriented programming (OOP) 
    to hide internal object details (data members). 
    Data hiding ensures exclusive data access to class members and protects object integrity by preventing unintended or intended changes
        
#### Can a static method use non-static members?
    Static methods access non-static methods passing the object reference as parameter.
    Static class method can access an object method or variable through the object,
    if it's instance and reference already presence.     
    
#### What is the difference between hiding a static method and overriding an instance method?
    Overriding basically supports late binding. Therefore, it's decided at run time which method will be called. 
    It is for non-static methods.
    Hiding is for all other members (static methods, instance members, static members). 
    It is based on the early binding. More clearly, the method or member to be called or used is decided during compile time.
    
#### Define the following terms: Instantiation, Attribute, Method:
    Instantiate in Java means to call a constructor of a Class which creates an an instance or object, 
    of the type of that Class. 
    Instantiation allocates the initial memory for the object and returns a reference.
    
    Objects are instances of classes, so think in terms of classes, attributes and operations.
    Attributes are fields or properties of the class.
    
    Operations are logic exposed as methods. 
    
    A Java method is a collection of statements that are grouped together to perform an operation. 
    with or without return values.

#### Could we access a static variable (or method) from a non-static method? Why?
    Yes, because static fields and methods are belonging to the class.
    Class members don't need any instance to be invoked. 
    
#### Could we access a non-static variable (or method) from a static method? Why?
    Non-static fields or methods are object members, 
    we can access them: calling the object with the object reference name. 
 
#### How many instances you have of a static variable of a given class?
    One. Everything else is a copy of that.
    
#### Why is it not a good practice to write a lot of static methods?
    They aren't fit so in the OO principles.(they more procedural)
    Inheritance and modularity changing.
    
#### What are the features of static attributes and static methods of a class? What are the benefits, when to use them?
    They can be reached without an object instance beacause they belong to the class not to the instance.
    Instances of that class sharing the same static field/method.
    I am using them if I want a field to be shared amongs the instances.
    Using static mathod should be good if they don't do anything else like a single computation depends from the
    parameters, like utility or helper functions.
    Pure functionality e.g.: Math class or String.format() or Arrays.asList() method.

#### What is the ‘this’ reference?
    The reference to the current instance where 'this' is called.
    
#### What are base class, subclass and superclass?
    Object class is a base class (or superclass) for every other classes.
    Every other class can have at most one more superclass and can have zero or more subclass.
    super- and subclasses made an inheritance hierarchy, 
    subclasses inherit the members fom the superclass allowed by the superclass. 

#### Draw an object oriented family (as entities, with relations) on the whiteboard.
#### Difference between overloading and overriding?
     Overloaded methods are in the same class, suppossed to act in the same way, just let the compiler
	 choose from the given parameters which is fit to one of the methods.
	Overriding let one method to be called instead of an inherited method with the same name.

#### What are the Object Oriented Principles? Explain the concepts with realistic examples!

    S – Single Responsibility Principle (SRP)
    O – Open Closed Principle (OCP)
    L – Liskov Substitution Principle (LSP)
    I – Interface Segregation Principle (ISP)
    D – Dependency Inversion Principle (DIP)

	The four principles of object-oriented programming are encapsulation, abstraction,	inheritance, and polymorphism. 

    Abstraction : Abstraction is the process of showing only essential/necessary 
	features of an entity/object to the outside world 
	and hide the other irrelevant information. 
	-> getters, setters for private fields

    Encapsulation : Encapsulation means wrapping up data and member function 
	(Method) together into a single unit i.e. class. 
	Encapsulation automatically achieve the concept of data hiding 
	providing security to data by making the variable as private and expose 
	the property to access the private data which would be public.
	-> class, package	
	    
	Inheritance : The ability of creating a new class from an existing class. 
	Inheritance is when an object acquires the property of another object. 
	Inheritance allows a class (subclass) to acquire the properties and 
	behavior of another class (super-class). 
	It helps to reuse, customize and enhance the existing code.
	So it helps to write a code accurately and reduce the development time.
    -> extend, implement

	Polymorphism: Polymorphism is derived from 2 Greek words: poly and morphs. 
	The word "poly" means many and "morphs" means forms. 
	So polymorphism means "many forms". 
	A subclass can define its own unique behavior and still 
	share the same functionalities or behavior of its parent/base class. 
	A subclass can have their own behavior and share some of its behavior 
	from its parent class not the other way around. 
	A parent class cannot have the behavior of its subclass.
	-> overloading, interface

#### What is method overloading?
    Overloading is a class member set from instance methods or constructors with same name 
    but difference in parameter type and number.
    The compiler will execute the one wich fit to the given parameter.
    So the method and/or constructor can be called with different parameters.
    
     
#### What is method overriding?
    Overriding is explicit, with annotation in the subclass on the method which have the same name from the superclass.
    The compiler will execute the one annotated one with matching type from caller site.
    
#### Explain how object oriented languages attempt to simplify memory management for Programmers.
	Some of the languages provide an automatic garbage-managment.
	(Algorithms inspect the memory from time to time for dead, weak or other reference
	traces and recycling the memory allocated or let them as they are)
	Java and C# are garbage-collected.

#### Explain the “Single Responsibility” principle!
	A single function per class, also encapsulated in a class, module or function.

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
    
#### What is the purpose of the ‘equals()’ method?
    To find out two objects are the same, as they resident in the same location, 
    or two objects are the same in values which they holding. ( data, attributes, fields, methods...)
    
#### What is the difference between '==' and 'equals()'?
    '==' can be used to comparing to primitive types, but it return with memory address from objects therefore 
    'equals' used to comparing objects with the original form or with overriden own method.
    
#### What does the ‘static’ keyword mean?
    The keyword make static the 'annotated' class, method, block or variable. They can not be instantiated nor belong
    to object, they belong to the class and they allocated in memory during compile time and a copy of them are used in future.
    
#### Why is the main() method declared as static? Explain.
    The entry point must not belong to an object because it's not exist yet. 
    The complier can step in the application thrugh this method.
    
#### What is the default access modifier in a class?
    Packege-private.
    
#### What is the JVM?
    The Java Virtual Machine.
    
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
    Enum is a special class, but class. And as a class can hold methods as well.
    
#### When would you use a private/protected/public attribute? What is the difference?
    The difference is the abstraction level.
    Personally I'm using private for all fields in objects, getter setter other methods are package-private and 
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
#### When you use method overriding, can you change the access level of the method, from public to protected? Why?
    The access level cannot be more restrictive than the overridden method’s access level.
    So from protected to public yes, but traverse from publico proteted no. 
     
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