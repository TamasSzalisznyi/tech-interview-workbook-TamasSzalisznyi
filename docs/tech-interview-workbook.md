# OOP / General
## What is OOP?
Object Oriented Programming. Programming paradigm, meaning methods and fields (attributes) 
are encapsulated into entities: objects.
There are four principles: 
- Encapsulation, 
- Abstraction, 
- Inheritance, and 
- Polymorphism.

##Inheritance. Explain the concept with realistic example.
A class can inherit fields and attributes from its ancestor, which is a way to avoid code 
duplication and make it reusable.
```java
class ParentClass {    
    protected String aField = "this is a field at parent class";
}

class InheritingClass extends ParentClass {
    
    void showInheriting() {
        System.out.println(aField);
    }
}
```
if we call InheritingClass showInheriting method, the output will be:
```commandline
    $ this is a field at parent class
```

##Polymorphism. Explain the concept with realistic example.
Polymorphism is the ability of an object to take on many forms. 
The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object. 
Every object in Java is polymorphic in nature, as each one passes an IS-A test for itself and for Object class.

Static Polymorphism (compile time polymorphism): in Java this is method overloading. 
 -> The compiler looks at the method signature and decides which method to invoke for a particular method call at compile time.

```java
class DemoOverload{
    public int add(int x, int y){  //method 1
    return x+y;
    }

    public int add(int x, int y, int z){ //method 2
    return x+y+z;
    }
}

class Test{
    public static void main(String[] args){
    DemoOverload demo = new DemoOverload();
    System.out.println(demo.add(2,3));      //method 1 called
    System.out.println(demo.add(2,3,4));    //method 2 called
    }
}
```

Dynamic Polymorphism (dynamic binding or runtime polymorphism): A subclass can override a particular method of the superclass. 
Let’s say we create an object of the subclass and assign it to the superclass reference. 
Now, if we call the overridden method on the superclass reference then the subclass version of the method will be called.

```java
class Vehicle{
    public void move(){
    System.out.println("Vehicles can move!!");
    }
}

class MotorBike extends Vehicle{
    public void move(){
    System.out.println("MotorBike can move and accelerate too!!");
    }
}

class Test{
    public static void main(String[] args){
    Vehicle vh = new MotorBike();
    vh.move();    
    vh = new Vehicle();
    vh.move();
    }
}
```
the output will be:
```commandline
 $ MotorBike can move and accelerate too!!
 $ Vehicles can move!!
```

Polymorphism can describe a pattern in object oriented programming in which classes have different functionality 
while sharing a common interface. (see example at abstraction)

##Abstraction. Explain the concept with realistic example.
"The quality of dealing with ideas rather than events." Oxford Languages.
In my opinion this is a quite good definition which is also valid in OOP if we think about the idea as an interface, and
the event as a class.
```java
interface AnInterface {
    int getNumber();
}

class SomeClass implements AnInterface{
    
    @Override
    int getNumber() {
        return 1234;
    }
}

class OtherClass implements AnInterface {
    
    @Override
    int getNumber() {
        return 5678;
    }
}
```
then we can reach both classes via they interface as:
```java
class ShowPolymorphismClass {

    public static void main(String[] args){
        AnInterface some = new SomeClass();
        AnInterface other = new OtherClass();
        System.out.println("some class: " + some.getNumber);
        System.out.println("other class: " + other.getNumber);
    }
}
```
the output will be:
```commandline
    $ some class: 1234
    $ other class: 5678
```

It is also related to data hiding ( imho data hiding is also a form of abstraction) : 
using visibility modifiers (private, package-private, protected, public) and the standard getters/setters to hide everything 
from the outside world and abstracting just particular parts of the program.
```java
class HideAlmostEverything {

    //method is callable from everywhere -> fully abstracted
    public void imPublic() {
        System.out.println("Hello World!");
    }

    //method is callable from package -> abstracted to neighbors
    void imPackagePrivate() {
        System.out.println("Hello com.codecool.package!");
    }

    //method is callable from child -> abstracted to family    
    protected void imProtected() {
        System.out.println("Hello my Child!");
    }
    
    //method is not callable outside the class -> not abstracted at all  
    public void imPrivate() {
        System.out.println("Hello Me!");
    }
}
```
In the example above I would represent that a class can hide something but also can abstracting some parts.

##Encapsulation. Explain the concept with realistic example.
I would refer the examples in above to data hiding and abstraction.
Logical functions (method) and datas (variable) are wrapped (encapsulated) together into a single unit (class).
```java
class Encapsulation {
    protected int number;
    protected char character;
    protected String letters;

    public void printAttributes() {
        System.out.println(number + " " + character + " " + letters);
    }
    
    protected setNumber(int anotherNum) {
        this.number = anotherNum;
    }
//...more setters, getters
}
```
In this example the number, character, letters are encapsulated into a single class and abstracted to be printable 
but except a subclass none can modify them.

##What is a class?
An entity in OO languages. Encapsulated logic and data. Blueprint for objects.

##What is an Object?
Instantiated class.

##What is casting? What is the difference between up vs downcasting?
Values (variables, data) in programming languages have:
 -place in harddisk (bits allocated in memory) where they live
 -type (to define how those bits should be read by a program (compiler also a program) )
 and
 -reference how we can access them (because bits and memory location isn't human readable), this is the name of the variable

Furthermore,it is also possible to change attributes of a particular variable: casting stand for "change" the type.
For example an int (short -> int -> long -> float -> double) can be upcast (implicit) to its representative Object: Integer.
A class can also be casted up to its super class (see by abstraction and polymorphism) or a super class can be casted down to its subclass:
```java
class Animal {} 
...
class Dog extends Animal {}
...
Animal dog = new Dog();
```
we can write it also:
```java
((Animal)Dog)dog = new Dog();
```
Upcasting can be implicit, meaning we don't need to write extra expression for it.
```java
int num = 1;
Integer i = num;
```
Downcasting on the other hand explicit because of the possible data loss.
```java
float f = 4F;
int i = (float)f;
```

##Define a constructor?
Constructors are special methods in Java. As regular methods they can have parameters, they can be overloaded and, they have visibility modifier.
A huge difference is the return type: which is implicitly (it is not visible like void or T type) an instance of the declaring class.
Another difference is: every class have at least one constructor. It is possible to not declare explicitly a constructor, in this case
the class can be instantiated via a public, non-arg constructor.
```java
class SomeClass {

    int someVariable;
    //here compiler make magic as this is not in the code
    //public SomeClass() {)
        
    void someMethod() {}
}
``` 

##What is method overloading?
Thanks for polymorphism and late binding we can declare in Java overloaded methods. (example at polymorphism)
Overloaded methods have to have the same name but can differ in parameter list. The compiler will decide at runtime,
from the passed arguments which method will go in the stack.

##What are different types of arguments? (context: pass by value / pass by reference)
In Java, everything is passed by value. Primitive types passed directly by value, Non-primitives passed by their reference value.
Formal arguments, actual arguments. 

##What is method overriding?
Runtime (dynamic) polymorphism. This is when a method with same signature and return type declared both in super- and subclass.
The JRE will know from the type of the declared caller class which method to use. 

##What is an interface?
In Java interface is a reference type, similar to a class (imho interface is a special class, but static and abstract), 
that can contain only constants (static, final), 
method signatures (abstract, because they don't have body), 
default methods (java8+), 
static methods (java9+), 
and nested types. ("oracle docs")
Interfaces cannot be instantiated (-> spac static class) they can only be implemented by classes or extended by other interfaces. (reference type -> polymorphism)                                            

Interfaces are contracts which guarantees for the caller, that this type will contain and implement the methods whose are declared in the interface.

##What is exception handling?
Exception handling is the way, how the developer facing with problems on critical points. 
It can be fail-fast, whereas an exception, if occuring, will be thrown immediately
preventing more issue or serious damage.
It can be handled silently with try-catch block where the source of the problem will be set to a default value if it some value, 
or the program can continue the process if it was an array and so it will prevent an index out of bound exception. 
Some exception can be prevented with conditionals as well.

##Difference between overloading and overriding?
Overloaded methods live in the same class, they can be even static, the happening will happen during compile time -> static binding.
Overriding happen at runtime -> dynamic binding. Overriden and overrider method living in super- and subclass.

##What are access modifiers?
Private, protected, package-private, public.
These keywords are responsible for how a class, or an object expose itself for outside. 

##Do we require a parameter for constructors?
Not mandatory but we can have. Or not.

##Whether static method can use non static members?
If the reference from that instance passed to the static method, yes.

##What are base class, subclass and superclass?
Base class is synonymous for superclass (or can refer for every object mother, the Object class itself).
Subclass is a class which extend an another class, which is then become a superclass.

##What is data hiding?
Controlled method and property abstraction with modifier keywords.

##What is variable shadowing?
Some languages permit more than one variable with the same name, but they have to be in different scope.
In Java this can be explicitly indicated with the 'this' keyword.
```java
class Shadow {
    int i;

    Shadow(int i) {
        this.i = i;
    }

    void shadowVar() {
        int i = 1;
        System.out.println(i);
        System.out.println(this.i);
    }
}
```

##What is the difference between hiding a static method and overriding an instance method?
The purpose the same, the difference is that static method can't be overridden. 
The classes which are defining the methods are super- and subclass of each other.
The two methods have to own the same signature and return type and parameter list.
Access modifier have to be at least visible as the superclass, but exception list can be narrower. 

##Define the following terms: Instantiation, Attribute, Method
Instantiation: calling a class special method; the constructor. The return type itself the class, and the value is an instance of the class.

Attribute: a field or variable in a class. Fields holds some value type and reference. 
It can belong to the object: instance variable.
If the field marked with static keyword: static variable.
If the variable belong to a method, then it is not a field but a local variable.

Method: collection of statements that are grouped together to perform any logic.
Methods have a visibility modifier, a return type, a signature (name and parameter list) and body.
Any method can be called via the method reference (the name of it) and passing by the proper arguments.

##Explain how object oriented languages attempt to simplify memory management for Programmers.
Garbage collectors are working all the time under the hood. They can have different behavioral marks  in different languages,
but commonly they are responsible to remove finished blocks from the stack, objects from the heap without reference, and they also allocate the
memory after local variables are reached the end of the lifecycle (the method have finished the execution).

##Explain the “Single Responsibility” principle!
Everything in OOP should be responsible for one goal.
A method should be responsible just for one logical step. If more steps are need we should create more methods.
A class purpose is only one thing: fulfilling one requirement through encapsulating a bunch of method and attribute. 

##What is an object oriented program? Explain, show.
Where the program is a set of interacting objects.
Programs wish to follow OOP paradigm should fulfill that the developer organize the program into objects. 
Objects containing states and procedures, procedures can modify states or expose states to other objects with abstraction,
(using interfaces or getter methods).
The way how objects interact with each other and processing the given task achieved by the objects APIs.
API is a set of encapsulated and abstracted method references, they describe who and how can use a particular object.
In Java, classes defining APIs, they are the blueprints for the objects. 
Classes using data hiding to define how a state or procedure encapsulated and exposed to other objects. 
Procedures defined in methods, methods can have parameter and return value.
The level of exposing defined with visibility modifier keywords like public, private... 
Objects should be reusable and single responded using inheritance and polymorphism.

This example would represent:
- an encapsulated object, 
- holding some state and 
- exposing some procedure to 
    - modify, 
    - reach and 
    - use that
    
```java
    class Capsule {                                             //encapsulated
        
        private final int serial;                               //state
        int dimension = 3;                                      // in attributes
        int weight;                                             // in variables
                                                                // object
        String type = "medicin";                                // can have state
        String name;                                            // can get state
    
        public Capsule(String name, int weight) {               
            this.serial = generateSuperSecretSerialNumber();    // get as dependency injection
            this.weight = weight;
            this.name = name;                                   // get at a level of construction
        }
        
        public void setName(String newName) { name = newName; } // or at any level

        public String getName() { return name; }                // with procedure exposed state -> keyword and method
        
        protected void cutHalf() { weight /= 2; }               // limited exposion
    
        private int generateSuperSecretSerialNumber() { return SerialNumberGenerator.generate(); }
    }   

    class Pill extends Capsule {                                // inheritance
    
}
```

##Draw an object oriented family (as entities, with relations) on the whiteboard.
![]family.svg

##What does it mean an object is Immutable?
Once it's created it can't be modified.

##How do you make a class immutable? What do you need to watch out for?
Immutable is a state what cannot be varied after creation. 
To reach it I should watch out for:
- fields of the class are final. To prevent any change after initialize it.
- fields get new value or reference at the time of initialization. 
    - assigning them a copy of non-primitive types, so this will be the only reference which point to that object
    - assigning them a primitive type, so it will hold a value directly
- fields should not have setter, for preventing the ability to modify them.
- fields getters should provide a copy of the value, so it cannot be modified through reference.

##How do you prevent developers from subclassing a class?
```java
public final class ImRock {}
```
The final keyword don't allow sub-classing that class.

##How do you prevent developers from overriding a method in a subclass?
The method should be static, private or final.

##How do you prevent developers from changing the value of a variable?
It can be hided and shipped with getter, but not setter or be final.

##What are the possible uses of reflection?
As a part of reflection it is possible to map an object fields and types of those, and to map methods as well.
Those introspections can be used to modify fields or invoke methods as reflecting to the gathered information.  
For example Junit also using reflection to look for annotated classes, fields and methods and then run those.

#Java Language
##What is the JVM?
Java Virtual Machine.
A program tu run java class files.

##What is the difference between the JRE and the JDK?
Java Runtime Environment providing everything which is required to run a java application.
Java Development Kit providing everything for analyzing and developing java application.

##What is the difference between long and Long?
Every primitive type have a corresponding wrapper class. Non-primitive Long is the wrapper class for primitive long.
Wrapper classes then can be handled as every other object, possessing a state of long value.

##Can a long store longer number than Long?
No. Longer is just the wrapper round the same value.

##What is autoboxing and unboxing?
Autoboxing is the automatic conversion between primitives to their object wrapper class. E.g.: int -> Integer, long -> Long.
Unboxing is the opposite flow. E.g.: Integer -> int 

##If you have a variable, that shall store a positive whole number between 0 and 200, what primitive type would you use to store it?
A short. because it's have the closest maximum value to 200.
2 bytes. because byte have the maximum value of 127, but two bytes are equally 16bit as one short.
An unsigned int. because int have much higher maximum value than 200, but unsigned int can be just positive, whole natural number.
 
##Think about money ;) How would you store a currency value, that shall support decimal parts? Think it through again, and try to think outside of the box!
-->
-->
##What do you think, why there is no string type in Java?
Because String is a wrapper class for char. As it is an object, it can have a state of immutable array of chars.

##What is the largest number you can work with in Java?
 !!(2-2-52)·21023 the double max_value, after it come the positive infinity.
--> bigdecimal

##What happens if you try to call something, that you have no access to, because of data hiding?
IllegalAccessException will be thrown.

##What happens if you try to delete/drop an item from an array, while you are iterating over it?
Arrays have fixed length, after creation the array is immutable against structural modification, 
but it is possible to change the value for null or 0. 
ConcurrentModificationException can be thrown against structural modification   or
IndexOutOfBunds can be thrown against iterate over the array last element

##What happens if you try to delete/drop/add an item from a List, while you are iterating over it?
Different list implementations are eg. LinkedList, ArrayList
```java
    @Test
    void linkedList_separatedIteration_addElem() {                                      // there is no concurrent thread
        List<String> list = new LinkedList<>() {{add("hello"); add("world");}};         // betweem for i and list.add() method
        for (int i=0; i < list.size(); i++ ) if (i == 1) list.add("added");
        for (String word: list) System.out.println(word);   //out: hello world added    
    }
    @Test
    void linkedList_separatedIteration_addElem_atIndex() {                               // same
        List<String> list = new LinkedList<>() {{add("hello"); add("world");}};
        for (int i=0; i < list.size(); i++ ) if (i == 1) list.add(i, "added");
        for (String word: list) System.out.println(word);   //out: hello added world
    }
    @Test
    void linkedList_iteratingOver_and_addElem_withAddMethod() {
        List<String> list = new LinkedList<>() {{ add("hello"); add("world"); }};         // ConcurrentModification
        for (String word : list) list.add("added");
    }
```
During iteration ConcurrentModification can occur or IndexOutOfBounds (rarely)

##What happens if you try to add an item to the end of an array, while you are iterating over it?
Arrays are immutable, after they created the size of the array can not be changed, the capacity is fixed.
During iteration ConcurrentModification can occur or IndexOutOfBounds (rarely)

##How can you safely add/remove items to/from a List?
List implementations providing methods to add/remove/insert item into/from the list.
They are cutting the original array into two and insert an elem into a new array with 
the copy of the original half of array on each end respectively.

##What is the "golden rule" of variable scoping in Java? What is the lifetime of variables?
Variables declared static in a class (above method scope) are class variables or globals.
Globals are visible for every instance within the access modifier. The lifetime span through the entire app lifetime.

Variables declared in a class (above method scope) are instance variables.
They belong to the declaring class instantiated object. The lifetime is from instantiation as long as reference stored in a stack.

Variables declared in method body are local variables. They are further subdivided into more scope as they declared before or after:
 - decision-making statements (if-then, if-then-else, switch), 
 - the looping statements (for, while, do-while), and the 
 - branching statements (break, continue, return)    
Lifetime span till the execution done.

Globals can modify a method outcome, may occur side effect etc. Stateless approach better. 
Variables should prefer method scope instead global class scope. 
Local variables are help to reduce a state lifetime and scope.

##What is garbage collector, in a nutshell?
They are automatic workers of JVM and organizing the memory for the application. They responsible to 
 - allocate memory space as required
 - free up memory blocks out of use
They work in stack and also in heap.

##If you need to access the iterator variable after a for loop, how would you do it?
```java
int retrieveIteratorVariable() {
    int ret = 0;
    for (int i: int[]{1, 2, 3, 4}) { if (i == i) { ret = i; } }
    return ret;
}
//return value : 4
```

##What kind of packages do you know under java.util.* ? Bring at least 3 examples.
List implementation: ArrayLst, LinkedList, HashMap, HashSet, Stack
Utility: Arrays.asList(T...), Collection.singletonList(T), Optional, Random, Date

##Given two Java programs on two different machines. How can you communicate between the two? What are the possible ways?

##When you use method overriding, can you throw fewer exceptions in the subclass than in the parent class? Why?
Yes. Access modifier can be the same or higher, signature the same, but exception list can be narrower.
--> Liskov subtitution principle: the ability to refer to an object from it's super class
-> A sub class from the super class exception can be referred from it's super class

##When you use method overriding, can you throw more exceptions in the subclass than in the parent class? Why?
No. The subtypes must be substitutable for their supertype (Liskov) without ever having to modify the client code. (Open - closed) 
To be substitutable, the subtype must behave like its supertype.

##When you use method overriding, can you change the access level of the method, from protected to public? Why?
The over-rider method can be more accessible than it's subject method.
This isn't break the parent class contract: Subclass able to behave (-> reachable for others now) at least like its superclass.

##When you use method overriding, can you change the access level of the method, from public to protected? Why?
No. Beacuse it would break the Liskov principle. If some object depend from the superclass method, and if it would be accessible for
less members, then the depending class should be confronted with an IllegalAccessException in contrast for its contract.  

##Which interfaces extend the Collection interface in Java. Which classes?
i: List. c: LinkedList, ArrayList.

##Does Map extends the Collection interface? Why?
--> Map have a Collection field to the values.

No it does not, it was a design choice by the developers of Java. 
They thought that mappings are not collections and collections are not mappings, so why should map extend the collection interface.
If we think about maps as collections, we should point out what an element is. 
The only plausible answer seems to be key-value pairs, but in the end this provides a very limited and not too useful map abstraction. 
“You can't ask what value a given key maps to, nor can you delete the entry for a given key without knowing what value it maps to.”

##What is JPA? What is JDBC? Which are the advantages and disadvantages of each? When to use each?
##How does HashMap work?
##What is the connection between equals() and hashCode()? How are they used in HashMap?
##Why is it important for keys in a map to have an immutable type? (Consider String for example.)

##What is the purpose of the ‘equals()’ method?
To give space for every class to define itself how would be compared for other objects.

##What is the difference between '==' and 'equals()'?
equals() can provide a self defined way to an object to be able to compared again other objects.
'==' comparator can report about primitives equality or about memory addresses.
```java
class...
...

    @Override
    public boolean equals(Object o) {
        if (o.someAttribute)
    }
```

##What is the difference between checked exceptions and unchecked exceptions? Could you bring example for each?
Checked: methods defined throw list in declaration or with try-catch block in body handle a checked exception.
Java verify those at compile time. These representing that the program prepared against (mostly external) problems.
Subclass of Exceptions.
Common are: IOException, FileNotFoundException, SQLException.
 
Unchecked: reflects some problem in program logic. They remain hidden during and after compiler work, at run time, 
when the program reaches the particular part of the code and execute it, it will throw an exception.
Separated as sub classes of RuntimeException subclass of Exception.
Commons are: NullPointerException, ArrayIndexOutOfBoundsException, IllegalArgumentException. (pointer-, index-, arithmetic-exceptions)

“If a client can reasonably be expected to recover from an exception, make it a checked exception. 
If a client cannot do anything to recover from the exception, make it an unchecked exception.” 
Oracle

##What is Error in Java and how does it relate to Exception?
Error is also a sub class of Throwable like Exception.
Exception class represent a failure from logic or other application related problem, 
while Error represent a deeper and mostly more serious problem, coming from the system, potentially hardware related.
Commons are: StackOverflowError, OutOfMemoryError. 

##What does 'fail fast' mean in terms of exception handling? Why is it a good practice?
Methods should deliver a state or modify it. Fail fast approach is instead of silently handling exception with try-catch block, 
and continue the work with a default or null value, stop the process throwing exception.
This can prevent some unwanted and maybe bigger problem occuring later from the fail of a method. 

##When does 'finally' block run? What it is used for? Could you give an example from your projects when you would use 'finally'?
At last, after the try-, and all possible catch-block(s). The finally block will be executed independently of other blocks in every case.
I would (and did) used finally blocks at DB access, methods with a task to query and process response closed every closable as 
Connection and PreparedStatement at finally block.

##Which order should we catch the exceptions? Why?
It is recommended to start with the most specific problem. 
If multiple possible exception can occur, every exception should be listed.
The scope can be bigger if the problems tending to cluster, but precise use of exception classes can better identify the
source of the problem.

##In which case should we catch an exception? Why?
In case an interaction between user and an interface, where the user prompted for inputs, a try-catch block should 
check the input and catch the exception in at time but instead of break the program run,
allowing the smooth flow re-prompting the user for the right input.

##How can we handle exception? What can we and should we do with an exception in the 'catch' block?
Started with the most specific class of exception proceed with super classes toward the Throwable class.
If the method designed to handle the exception in place than catch block or finally block should implement the recovery
and log mechanism. Otherwise, following the same exception policy, method should throw the exception explicitly
and so, passing the opportunity to the caller to handle it. 

##What are the access modifiers in Java? Which one could we use for class?
Public and the default package-private are available also for classes at top-level.
Protected and private modifiers are on member-level, for instances.
 
##What does ‘static’ keyword mean?
Static stuff belong for class. Can apply to variable, method, class. 
Class can be static as nested class of a class.
Compiler at compile time initialize and execute static variable and code block. 
Therefore, everything what is static already present at runtime. 
Therefore, instances can reach every static variable or method. 

##Could we access static variable (or method) from a non-static method? Why?
We can. To reach and use static members, their names are enough reference, this is shared across objects in
metaspace.

##Could we access non-static variable (or method) from a static method? Why?
Non-static variables and methods can be reached and used through their reference.
Because they live in the heap, and reference for this heap location stored in the stack, and this reference can
distinguish objects for jre to execute or use value.

##Can an “enum” contain methods in Java? Explain.
Enum is a special class, where constructor and methods are allowed. Difference in construction and built-in methods, 
like values() and valueOf(String).
Most important that fields in enum always constants (public, static and final) 

##What are “checked” and “unchecked” exceptions?
Checked exception what is compiled with exception handling. On occuring can be thrown at compile time.
Unchecked exception occuring at run time and mostly some logic problem, like NullPointer or IllegalArgument.

##How many instances you have of a static variable of a given class in the JVM?
Every object instantiated from the class, where class variable were declared, get a copy of the same value.
Same objects, other objects or classes can get a copy of reference from this particular variable,
or can get a copy of the value.

##Why main() method is declared as static? Explain.
Compiler make static members firstly before instantiating objects, therefore at compile time only from those can serve
as entry point for application. Furthermore this particular:
```java
    public static void main(String[] args){
        //...  
    }
```  
form is the contract every java program to implement and be runnable.

##Why is it not a good practice to write a lot of static methods?
The process going against the object oriented approach.
In some circumstances they can cause problem or issue because they: 
- living before
- and longer than objects
- acting as globals   

##Can the main method be overridden? Explain your answer!
No. By contract the JVM expect exactly one method for that exact signature. 
The reason is to provide a common interface (entry point) for every java application with The main() method, and
in the same time to obligate every program to hold the contract, therefore leave no doubt about the first method for JVM.

##When would you use a private/protected/public attribute? What is the difference?
I would use these attributes for clearly defining the borders between abstraction levels.
From bottom to up:
I would encapsulate every field and method in class with a private modifier.
In case by design there are sub-classes planned, I would expand those with a protected keyword at variable and at method level as well.
Expanding the visibility to package members for providing inner functionality that provide the program consistence.
Defining what level are open for expansion and what remain private from all. 
Then defining a public API with a public keyword to provide an open operating surface for the program.

##What are the features of static attributes and static methods of a class? What are the benefits, when to use them?
Statics are available through the declaring class name. 
They don't need to be any instantiated object from their class to be available.
They are unique in a term that copies from static fields given to instances.
Every instantiated object allowed by access modifier can access every static member (field and method).
Also, every member who reach a static variable, are get a copy from the same variable.
Static method not available to override.

The fact that a copy from the field value or reference shared among other members and
methods are independent of any instance can be good service for a program.
Static fields can be used to register objects using unique identify process.
- using a static number field to sequentially increment it and equip the new object with a copy of value.
Static methods can serve generator or utility purpose:
- using static method to generate an identifier and pass it to the instance 
Providing such functionality what essential for the application like java.util, java.lang etc.
If the usage of some functions require (from nature so complicated or essential usage and/or implementation) to be 
available before any object and for every object. Eg.: Math library, Collection, Array, List, Map utility classes.

##What is annotation? What can be annotated and how? Show examples.
##What is a ternary operator?
-->

##How many instances can be created for an abstract class?
Abstract keyword is for preventing creating an object or defining method body.
None.

##What is ‘this’ reference?
The this keyword point to the object, in case variable shadowing it help clarify the variables hierarchy.
```java
    int num;
    ImThis(int num) {
        this.num = num;    
    }
}
```

##What does final means in case of variable, method and class?
At every case protect the subject from modification.
In case of method, method overriding no longer possible,
In case of class it prevents other classes to extend it. 

##What is the super keyword?
Similar for 'this' but point to the next base class of declaring one.
The subject of 'super' can be method and variable as well.

##What is the default access modifier in a class?
Package-private.

##Consider the following class definition and implement the solutions: ???

#Java Enterprise
##What is Java Enterprise (J2EE, JEE)? What is the major difference between the Standard edition (JSE) and Enterprise edition (JEE)?
Earlier version of JEE was Java 2 Enterprise Edition, later it simplified to Java Enterprise Edition X.
JEE designed on JSE and extended with server side target goals to develop and run network applications.
Large-scale, multi-tiered, scalable, reliable, and secure.
                                                                                  
##What is Hibernate? What are the advantages, limitations?
Advantages of hibernates:
Hibernate supports Inheritance, Associations, Collections
Hibernate supports relationships like One-To-Many,One-To-One, Many-To-Many-to-Many, Many-To-One
Also supports collections like List,Set,Map (Only new collections)
Hibernate is handling every exception as un-checked.
Hibernate has capability to generate primary keys automatically while we are storing the records into database
Hibernate has its own query language, i.e hibernate query language which is database independent
In case of hibernate, if it not found any table in the database this will create the table for us.
Hibernate supports caching mechanism by this, 
Hibernate provided Dialect classes, so we no need to write sql queries in hibernate, instead we use the methods provided by that API.
Getting pagination in hibernate is quite simple.
 
Disadvantages of hibernates:
Hibernate is little slower than pure JDBC, generate many SQL statements in run time .
Boilerplate code issue.
imho: what are advantages in good hands, can be difficulties or disadvantages at others. 
eg.: with the unchecked exception handling policy and with the table creation method it is possible to create DB structure with no intention.

##Difference between .jar and .war files
JAva Archives.
```.jar``` put datas about the project into ```META-INF``` directory, compress the ```.class``` files and any resources if there are any, and
define in ```MANIFEST.MF``` about the file goal. It can be a library, a plugin or an application. 
Building tools like Maven support ```JAR``` building and running.

Web Application aRchive or Resource.
```.war``` in similar way like JAR but specially designed for to package web applications that we can deploy on any Servlet/JSP container. 
In an additional ```WEB_INF``` folder and the ```web.xml``` file it will store static context like html template files, JS files, properties etc.
File structure is rigid and preconfigured.
Building tools like maven can build ```.war``` file, but server need to run it. 

##What is Spring?
##What is Spring Boot?
##What are the advantages of the Spring Framework?
##What are the major differences between Maven, Ant and Gradle?
##What is Maven used for?
##What does a pom.xml file contain in Maven?
##What is n-tier (or multi-tier) architecture?
##What are microservices? Advantages and disadvantages?
##What is continuous integration? Why is CI important?
##Why are tests important in the CI workflow?
##Name some software that help the CI workflow!
##What is Continuous Delivery?
##What is Continuous deployment?
##What is DevOps?

#Algorithms, Pseudo code
##Fibonacci sequences. Write a method(or pseudo code), that generates the Fibonacci sequences.

##Factorial. Write a function that, given a number as input, returns the factorial of that number. 
##...The factorial of a number ‘n’ is the product of all positive integers less than or equal to ‘n’. 
##...So, the factorial of 6 would be 6*5*4*3*2*1 = 720. The factorial of 0 is 1.

##Write a function that calculates the factorial of an integer with recursion.
##Write a function, that prints all the files in a given folder and sub-folders using recursion.
##What is “Stack overflow”? Write a code, that ends up with stack overflow.
##What is Big O complexity? Explain time and space complexity!
##What is the Big O time complexity of the common operations in an ArrayList, LinkedList, HashMap? And of a bubble sort, quicksort, finding items in a Binary Search tree?
##What is binary search tree (BST)? Write an implementation in Java.
##What is linked list? How to find if linked list has a loop?
##How to find middle element of linked list in one pass?
##In an integer array, there is 1 to 100 number, out of one is duplicate, how to find?
Derive all elements to a set -> variable able to if desired

##What is the difference between Stack and Queue data structure?
LIFO - FIFO

##What is QuickSort? Describe the main logic of this sorting algorithm.
conquer and rule

##What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?
##What are trees? What are binary trees? What are binary search trees?
##How can you store graphs in programs? What are the advantages/disadvantages per each?
##What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?

#Testing
##What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?
##What is code coverage? Why is it used? How you can measure?
##What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?
##What is a test case? What is an assertion? Give examples!
##What is TDD? What are the benefits?
##What are the unit testing best practices? (Eg. how many assertion should a test case contain?)

#Databases
##How can you connect your application to a database server? What are the possible ways?
##When do you use the DISTINCT keyword in SQL?
##What are aggregate functions in SQL? Give 3 examples.
##What do you know about database normalization?
##What kind of JOIN types do you know in SQL? Could you give examples?
##What are database transactions? When to use?
##What is a two-phase commit? Bring an example how to use?
##What kind of database relations do you know? How to define them?
##What is an ORM? What are the benefits, when to use?
##What is the difference between JDBC and JPA?
##What is the DAO pattern? When and how to implement?
##How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?
##You have a table with an “address” field which contains data like 3525, Miskolc, Régiposta 9. (postcode, city, street name and address). How would you query all records related Miskolc?

#Networking, HTTP, Web technologies
##What is the difference between HTML and XML?
##What is XSLT?
##When to use AJAX? Bring examples.
##What is SOA? When to use?
##What kind of HTTP status codes do you know?
##What is a REST API?
##What is JSON? When to use?
##What is TCP/IP? What layers does it define, what are they responsible for?
##What’s the difference between TCP and UDP?
##How does an HTTP Request look like? What are the most relevant HTTP header fields?
##How does an HTTP Response look like? What are the most relevant HTTP header fields?
##What is DNS? How does it work?

#Software Methodologies
##What kind of software-lifecycle models do you know?
##What kind of software development methodologies do you know? What are the main features of these?
##What is a UML diagram? What kind of diagram types do you know?
#xWhat is a UML class diagram? What are the typical elements?
##What kind of design patterns do you know? Bring at least 3 examples.
##What is the purpose of the Iterator Pattern?
##What do you know about the SOLID principles?
##How would you separate data storage code and business logic code (which uses stored data) in an application?
##What are the SCRUM roles? What are the SCRUM ceremonies? What are the SCRUM artifacts?
##What is the main goal of a retrospective meeting?

#Threads, Concurrency
##When do you need to use threads in an application?
##What is a daemon thread?
##What is the difference between synchronous and asynchronous execution?
##What is the difference between concurrent and parallel execution of code?
##What is the most important problem developers are faced when using threads?
##In what kind of situations can deadlocks occur?
##What are possible ways to prevent deadlocks from occurring?
##What does critical section or critical region mean in the context of concurrent programming?
##How do you execute critical code in [your favourite language]? What mechanism(s) can you use?