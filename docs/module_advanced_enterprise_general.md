# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?
 In order to modularity and single responsibility the n-tier architecture divide the processing, data management, and presentation 
 functions, and order them into different modules and layers logically maybe also physically as well.

 This is a basic model, it can be more layered:
    -presentation layer: templates, template-engines
    -application layer: business logic and other application process related stuff
    -database layer: in memory or a kind of database.
 Important to mention that the separated parts should communicate with each other through well-defined APIs. 
 An implementation should depend on an interface rather than a specific implementation, and should 
 expose public methods with interface abstraction.     
 With this kind of architecture replacing modules or extending the actual structure, also testing become much easier.
 Also, allow developing and testing different parts and phases parallel.
    
#### What are microservices? Advantages and disadvantages?
 Microservices is an architecture style where the application is a collection of services. 
Even a large software project can built from loosely coupled modules, which communicate with each other.
 
 Advantages:
     - Improved fault isolation: 
     Larger applications can remain mostly unaffected by the failure of a single module.
     - Eliminate the vendor or technology lock-in: 
     Microservices provide the flexibility to try out a new technology stack on an individual service as needed. 
     - Smaller and faster deployments: 
     Smaller codebase means quicker develop, test, deployment phases. CI/CD processes gain importance
     - Scalability: 
     This is the main benefit of a microservice. A good implemented system respond for increased need of service with copies 
     of serving systems. This can save time to provide enough service at increased usage, keep up the quality of service and
     saves costs by not operating unnecessarily service.
     - Highly maintainable and testable: 
     As benefit from modular and loosely coupled design.
     - Rapid, frequent and reliable delivery:
     Even large, complex application can developed by a relatively small team.
       
 Disadvantages:
    Disadvantages coming from the main concept of the design. Complexity, as a distributed system has in many aspects.
    - Communication between services is complex: 
    Handle requests traveling between independent service modules could be very complex. 
    - More services means more resources: 
    Multiple databases and transaction management can be resource intensive.
    - Global testing is difficult: 
    Testing a microservices-based application can be cumbersome. 
    With microservices, each dependent service needs to be confirmed before testing can occur.
    - Debugging problems can be harder: 
    Each service has its own set of logs.
    - Deployment challengers: 
    Decentarlized controll.
    
#### What is Separation of Concerns?
 Design principle. Means separating a computer program into logically related parts. 
    Separated parts can work on different concerns.
    Concern can be a task, requirement or else piece of information that affect the program.
    Modularity, and hence separation of concerns, is achieved by encapsulating information inside a section of code. 
    Encapsulation interwine with the concern of information hiding together working on separation. 
    N-tier architecture also a kind of this concern (presentation layer, business logic layer, data access layer, persistence layer).

#### What is a layered design and why is it important in enterprise applications?
 n-tier architecture. separation of concern design.
    This kind of design divide the tasks into layers. Layers have one responsibility (like to provide connection to DB or to Web).
    The tasks divided into smaller parts where every part get some corresponding module to solve it.
    So layers are interfaces, modules implementing interfaces and depends on other interfaces.
    This serve the modularity because every implementation behind an interface replaceable by other implementation, 
    even possible to change parts in implementation as maybe one layer is from multiple interfaces, so some smaller 
    part also replaceable eventually.
    Interchangeability and modularity especially important at enterprise level at 
    security, maintainability, readability, stability and reusability related questions.
    Every crucial point such as security, or maintain a -server, or a -database become much easier with well-defined parts.
    Keeping everything up to date with technical improvements with replacing some module, teams can work parallel on different
    parts to keep up quality, extending or changing the profile of some part.
    Layers also can protect, at time of error, other layers from damage.
    Layers with good modularity or other design technique like microservice can provide alternative for currently unavailable
    modules.
    
#### What is Dependency Injection?
Loosely coupled design, single-responded modules providing and receiving dependencies.
    Injection done by an interface, a setter or a constructor. 
    Solutions for tasks coming across the modules instead of inherit or implement some. 
    Three players:
        - Client: who has dependencies and receive the injection.
        - Service: who provide the dependencies and so provide the injection.
        - Injector: who bound together client and service and handle the injection.
    
#### What is the DAO pattern? When and how to implement?
 Data Access Object.
    DAO is used at DB connection. Database layer is one or more interface and DAO implement it with connection to the DB.
    So the application can access through the interface the DAO, then the DAO
    translate the demand, connect to the DB, start query and send back the response to the sender.
    Here the layer have a task: to provide data for caller. 
    DAO model achieve this with a 
        - public reachable interface, hopefully the methods of that interface are easy to use (verbose in name, coherent functionality),
        - and with a set of different implementation.
    Implementations than share the task with dividing into smaller parts, where every task should have a single responded module, 
    and every single step should have a single responded method, but the point is, every complex business logic can be hidden
    under the hood while exposing a common API. 

#### What is SOA? When to use?
 Service Oriented Architecture. 
  Another architectual sytle. Have some important similarity with microservices in modularity and reusability too.
  The design aim to create a system, with a central core modul and service clusters. Members communicating each other
  with a common protocol.   
  
### Testing
#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?
Unit test. The most basic building block of the test architecture. Made by developers (mostly).
Integration test. A much bigger scope for running test over a workflow, examine multiple module or component behavior together.
Regression test. The biggest scope of running tests by, this aim the whole system behavior.
Acceptance test. The final test, done by real user to validate the application successness.

Major difference: unit-, integration- and regression tests are done by developers or testers and can be automated, 
but acceptance done by user(or user view) and (mostly) manual test.

#### What is code coverage? Why is it used? How you can measure?
This is a metric that should reflect the percentage or exact number of lines which was executed during a test.
It can inform easily the executor about which code block was not executed.
There are lot of tools for this purpose, actually I using IntelliJ built-in coverage tool.

#### What does mocking mean? How would you do it 'manually' (i.e. without using any fancy framework)?
Mocking used in unit test (mostly). Mocking mean to test an object and replace it's dependencies with a "fake" object
(say, place an object in a "fake" environment/system) to simulate the object- or system-under-test behaviour and state
without involving the whole system and all it's component's. 
Mocking use behavioral verification. (how the component work, different test case would be necessary to test state: what have changed by the object).

I should make a class which is written like to respond to the test object calls.

e.g.: I like to show some system, where an order placed and sent to a warehouse. In this representative we are not interested to
examine the warehouse exact behaviour, so we put expected reactions in the class, but we wan to know if the unit work as it is expected.
With that equipped we can say after the test how the warehouse reacted to the unit call, and not that what is the state after the execution.

```java
    class UnitTestClass {
        
    // unit under test is an object to represent some order. mock object representing a warehouse
    static UnitUnderTest unit = new UnitUnderTest();
    static MockObject mockWarehouse = new MockObject();

    @BeforeAll
    public static void setUpExercise() {
        mock.add(stuff);
    }

    @Test
    void objectUnderTest_againstMockObject() {
        unit.makeOrder(mockWarehouse);
        assertTrue(mockWarehouse.hasDoneWithOrder());
    }    
}

    class MockObject {
    
    List<Stuff> stuffs = new ArrayList();
    boolean isDoneWithOrder = false;

    void add(Stuff stuff) {
        this.stuffs.add(stuff);        
    }
    
    void getOrder(Stuff stuff) {
        if (stuffs.contain(stuff)) stuffs.remove(stuff);
        isDonewithOrder = true;    
    }

    boolean hasDoneWithOrder() {
        return isHasDoneWithOrder;        
    }
}
```

"Dummy objects -> are passed around but never actually used. Usually they are just used to fill parameter lists.
Fake objects -> actually have working implementations, but usually take some shortcut which makes them not suitable for production (an in memory database is a good example).
Stubs -> provide canned answers to calls made during the test, usually not responding at all to anything outside what's programmed in for the test.
Spies -> are stubs that also record some information based on how they were called. One form of this might be an email service that records how many messages it was sent.
Mocks -> are what we are talking about here: objects pre-programmed with expectations which form a specification of the calls they are expected to receive." Meszaros Gerard.

#### What is a test case? What is an assertion? Give examples!
Test case is collection of test methods, a class, which is runed by the test software.
Assertion is the actual comparison of the expected data with the actual data. 
Actual data come from the test method like the return value, expected data can come from many places:
excel, csv, hard code, magic number etc...

```java
    @Test
    void i_test_assertion_for_workbook_if_green_then_ok() {
        int expectedNumber = 42;
        SomeClass sc = new SomeClass();
        int veryMysteriousNumber = sc.doSomethingVeryUsefulAndComplex;
        Assertions.assertEquals(expectedNumber, veryMysteriousNumber)
    }
``` 

#### What is TDD? What are the benefits?
Test Driven Development. 
A software development process. Relies on the repetition of a very short development cycle: 
    - red: requirements turned into test cases   
    - green: after develop tests will pass                   
    - refactor: code refactoring                 

This is opposed to most of the other software development processes, where development take first place.
Benefits:

- test are designed before any line of code has written, from requirements. 
The acceptance criteria and assertion designed first, after part by part components construction develop to make them pass, 
not after product done tailoring test for it. That case test can be well suited for a particular system, 
producing not correct results.

- Earliest stage of testing where it can interweave with development.
Test are done at the very first stage in software development lifecycle. That save time in designing tests for an application
by being already cnstructed or a conception for it with the clear requirements based test design.

- Test are highly accurate and reliable.  
    - tests bring information about the object from the beginning, may help a lot in develop 
    - test bring more accurate and precise results as they designed to retrive a specific information or
    observe a particular behaviour etc.

- CI/CD processes gaining place.
This test-made skeletal-construct model make perfect match with CI offered tools, like orchestration of automated regression test
or running time or resource costly test processes remotely and paralell.   

#### What are the unit testing best practices? (Eg. how many assertions should a test case contain?)
Unit tests are should follow the main programming principles:
single responsibility
readability
maintainability
isolated

Mostly one assertion per method.

#### What is arrange/act/assert pattern?
A pattern for arranging and formatting code in Unit test methods:

Arrange: all necessary preconditions and inputs.
Act: on the object or method under test.
Assert: that the expected results have occurred.

separated by blank lines.

```java
@Test
void i_test_assertion_for_workbook_if_green_then_ok() {
    int expectedNumber = 42;
    SomeClass sc = new SomeClass();

    int veryMysteriousNumber = sc.doSomethingVeryUsefulAndComplex;

    Assertions.assertEquals(expectedNumber, veryMysteriousNumber)
}
``` 

### DevOps
#### What is continuous integration? Why is CI important?
A practice of merging all developers working copies to a shared mainline several times a day. (wiki)
In my words: CI is a repository's super shepperd. Every member who have access to the repository (like github)
can work together remotely without to much worrying about the existing codebase integrity.
CI can be configured to listen to the repository (hook) and on code change (push) it will execute the preconfigured
action (jenkins file, pipeline) on the selected branch(es) on remote (virtual) machines. Usually this is a regression test, system test or system-integrity test.
This cooperation between all developer, repository and CI tool results in a stable codebase where every integration problem
coming on surface very quickly whereas in the meantime the contributors can work locally and still keep up with the whole project.
  
#### Why are tests important in the CI workflow?
Because the tests will reveal if there any integration or else related problem, so it can ensure that the product did not lose
from the quality.

#### Name some software that help the CI workflow!
Jenkins, Bamboo, CircleCI, TeamCity, GitLab

#### What is Continuous Delivery?
Based on CI, the same process but extended with a deploy stage. If the CI phase ended with tests passed 
(or any other acceptance criteria has passed) the CI tool (which is usually can be extended to CD) start the 
deploy stage (configured through pipeline).
With this technique a version of the software always reachable in a releasable state. 

#### What is Continuous Deployment?
Difference between continuous deployment and continuous delivery actually that the deploy is also automatic, if all test
passed a good configured pipeline take care of automatic deployment.

#### What is DevOps?
A set of practices that combines software development (Dev) and IT operations (Ops). 
Those who practice this methodology using more tools to shorten the systems development life cycle and provide 
continuous delivery with high software quality.

Tools:
Coding – code development and review, (source code management tools), code merging. -> code repo
Building – (continuous integration tools), build status. -> CI 
Testing – (continuous testing tools) that provide quick and timely feedback on business risks. -> CI
Packaging – (artifact repository), application pre-deployment staging. -> ??
Releasing – change management, release approvals, (release automation). -> CD
Configuring – infrastructure configuration and management, infrastructure as code tools. -> CD
Monitoring – applications performance monitoring, end-user experience.

### Software Methodologies
#### What kind of software-lifecycle models do you know?
SDLC.:
Agile.
-release cycles -> each small, incremental changes --> testing --> release
-fast, continuous feedback and issue finding
-kind of lean -->
-good communication with stakeholders

Lean.
7 principles: 
    -eliminate waste, 
    -amplify learning, 
    -decide as late possible, 
    -deliver as fast as possible, 
    -empower the team, 
    -build integrity in, and 
    -see the whole.
--> emphasizes the elimination of waste as a way to create more overall value for customers    

Waterfall.
-oldest
-very straightforward, rigid
-phase to phase
--> well-known, well-planned, stable project, with no unknown requirement.

Iterative.
->phase ->iteration
implementing a set of feature -> test -> evaluate -> rinse -> repeat
-working model at early stage
-less expensive implementing changes
(-) repetition can consume resources quickly
RUP -> IBM Rational Software division 
Rational Unified Process:
    inception, when the idea for a project is set; 
    elaboration, when the project is further defined, and resources are evaluated; 
    construction, when the project is developed and completed; and 
    transition, when the product is released. 
Each phase of the project involves:
-business modeling, 
-analysis and design, 
-implementation, 
-testing, and 
-deployment.

imho --> CI/CD

Spiral.
-most flexible
-typically used at large projects
-highly customizable
-early feedback 
++risk-analysis
 spiral: -> planning -> risk-analysis -> engineering -> evaluating ->

DevOps.
-development and operation close work
-innovation and deployment oriented
-updates are small butt frequent
-continuous feedback and improvement
-automation of test processes, integration, deployment, delivery 

#### What is a UML diagram? What kind of diagram types do you know?
Unified Modelling Language
 visual documentation tool to design, analyze 
 represent business model- or 
 implementation- of a 
 software or a workpiece.

major: structure diagrams, behaviour diagram
 
Types:
 
#### What is a UML class diagram? What are the typical elements?
classes
attributes
methods
![](classBasic.svg)

extension, implementation: -> inheritance, generalization, realisation
association - aggregation - composition
multiplicity

#### What kind of design patterns do you know? Bring at least 3 examples.
singleton
dao
pom

#### What is the purpose of the Iterator Pattern?
Definition:
The essence of the Iterator Pattern is 
    -to "Provide a way to access the elements 
    of an 
    -aggregate object 
    sequentially 
    -without exposing 
    its underlying representation."

#### What do you know about the SOLID principles?
Single Responsibility. -> classes / methods responsible for single task
Open-Closed Principle. -> open for extension, closed for modification: inheritance
Liskov substitution Principle. -> objects are replaceable by their subtype instances
Interface segregation Principle. many client-specific better than one general-purpose  
Dependency Inversion Principle. -> modules, layers depends on each through interfaces for loose the coupling

#### How would you separate data storage code and business logic code (which uses stored data) in an application?
With layered architectural technique, interface, dependency injection
e.g. DAO pattern is a good solution for separating them

## Computer science

### Data Structures
#### What is the difference between Stack and Queue data structure?
Stack is a kind of queue both are a kind of a collection.

Stack: elements are added to the top of the stack and the next element also coming from the top of the stack. FILO 
Queue: elements are added to the end of the stack and the next element coming from the top. FIFO

-> polling, peeking, pushing

#### What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?
An abstract data type. A set of points (nodes) and lines connecting them (edges).

- Simple graph: where all the nodes are connected, and connected only once, with one edge.

- Directed graph: where edges associated with a direction, int hat case an edge between 
A - B is not equal to B - A.

- Weighted graph: where the edges have a label, represent a value (length, weight, price etc...) which is the cost of the edge.

#### What are trees? What are binary trees? What are binary search trees?
Tree is a special graph, directed and simple, one node representing the root,
and the rest of the nodes are children of that root.

Binary tree is a kind of tree, where every node have at least one and at most two edges.

Binary search tree is a searching algorithm which use binary tree where the data stored sorted.
The lower value from root goes to left and higher value goes to right.
Retrieving the data follow this order make it efficient the search.
  
#### How can you store graphs in programs? What are the advantages/disadvantages per each?
-Nodes as objects and edges as pointers
-A matrix containing all edge weights between numbered node x and node y
-A list of edges between numbered nodes

#### What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?
They are used for traversing the graph, they implement the logic in the graph, how the nodes are reached.
 
Breath First Search. Search through every tree level. Once finished move to the next level.
Depth First Search. Start an iteration from the root and going as far possible before tracking back and starting a new route. 

#### How does dictionary work?
Such a data structure which hold the data in key-value pairs, where value is the data and key is some "label",
with which the data is identified. Key should be unique and immutable.

#### Why is it important for keys in a hashmap to have an immutable type? (Consider string for example.)
Entries are stored as key-value pairs, if the key change, the value will be unreachable.

### Algorithms
#### What is QuickSort? Describe the main logic of this sorting algorithm.
One of the oldest sorting algorithm (Tony Hoare, 1961).
The two main strategies are: 
-the algorithm divide the array into smaller pieces
-divide it at the pivot point (pivot can be the first, the last, the middle or a random value).

The logarithm follow this logic: choosing a pivot and starting pointers from each end of the array.
The pointers will swap the values of with each other if the left pointer have higher value then pivot,
and the right pointer have less value. If the pointers cross each other or the pivot, the array will be divided into two, 
at the point of pivot.
Here the logic start again till there is no dividable array.

## Software design

### Security

#### What is OAuth2?
Open standard authentication framework, designed for HTTP protocol by IETF Community.
The main idea is: to provide access for 3rd party clients to a secured resource with the
resource owner permission without sharing credentials but using the authorization server. 
The AuthServer send access token as response for requesting token coming from
by resource owner authenticated user. 
![](oauth2flow.svg)

In the authorization server defined way the resource owner get full control access over it's resources as
configuring who and for what interval allowed to use a particular resource.
This is provided by the authorization server via tokens.  

#### What is Basic Authentication?
Basic access authentication
(wikipedia)
 In the context of an HTTP transaction, basic access authentication is a method for an HTTP user agent (e.g. a web browser) 
to provide a user name and password when making a request. 
 In basic HTTP authentication, a request contains:
  -a header field in the form of: 
  Authorization: Basic <user:pass>, 
  -where credentials is the Base64 encoding of ID and password joined by a single colon :
 
![](basicauthflow.svg)

#### What is CORS, why it’s needed in browsers?
Cross-Origin Resource Sharing.
Security policy to protect resources from malicious or uncontrolled actions.

Same-Origin allows browsers for use their resources just from the same url.
CORS allows browsers for use their resources in a controlled way, server describe who and what allowed to do.
The defined policy described in the header, with key: value 
```html
    Access-Control-Allow-Origin : [*/allowed-domain(s)]
```
Clients request put after preflight OPTION request to the server, the server will respond with it's defined access-policy.
If the options from response containing the request content the browser will execute the request, 
else will block after and correspond to the preflight response.

#### How can you initialize a CSRF attack?
Cross Site Request Forgery.

If somebody place a malicious script and stole a cookie (or different credential) then send the malicious content
from the script with the stolen cookie from a trusted site with valid identification to somewhere.

#### What is JWT used for? Where to store it on client side?
Stand for JSON Web Token. It is used to involve an authorization server, which produce a token in exchange to the credentials.
It is for secure the credentials, as using only once than go with tokens. Tokens can expire for more secure.
JWT stands from
    -header 
    -payload 
    they are stored in JSON format before signed. 
    -signature

The token is a concatenation of the base64 data of the above, delimited by a period. So, a JWT token would look like the following:

[header].[payload].[signature]

JWT should be stored in the browser memory in an encrypted form.

### Threaded programming

#### When do you need to use threads in an application?
Threads are used to achieve parallelism - this way an application can be faster by doing multiple things at the same time.
Using multiple threads can be very costly. However, there are cases when you can benefit from it, like:
- Creating asynchronous operations.
- Creating parallel operations.
- Creating continual running background operations.
- Take full advantage of CPU power (with multiple cores)
- Reducing response time. (divide a big problem to smaller chunks)
- Serve multiple clients at the same time.

#### What is a daemon thread?
We can differentiate user threads and daemon threads. User-threads are high-priority threads. 
Daemon threads has low-priority. The role of these threads are to provide services to user threads. 
Their life depends on user threads. The JVM will wait for any user thread to complete its task 
before terminating it, but daemon threads aren't supposed to prevent JVM from exiting.
In Java, there are automatically running daemon threads, like finalizer, garbage collector, etc.
They serve mostly users with memory allocation and garbage collection.

#### What is the difference between concurrent and parallel execution of code?
Concurrent execution: Running lots of independent things at the same time. A task doesn't have to wait for the other tasks
to finish, for it to advance. In single-core setup, suspending and alternating between threads is required 
(also called pre-emptive multithreading / task switching).

In parallel execution:
 Application breaks down a task into subtasks, and they advance simultaneously at the same time. 

In concurrent execution:
 Means that it processes more than one task at the same time, 
 
#### What is the most important problem developers are faced when using threads?
Deadlock: when two or more threads waiting for each other to lend access to a resource, so they are blocked forever.
Starvation: Occurs when a process never gains accesses to resources, never allowing the program to finish.
Race Condition: Occurs when two or more threads can access shared data, and they try to change it at the same time.
Livelock: Occurs when two threads are dependent on each other signals and are both threads 
    respond to each others signals occuring a 'while like' infinite loop.

#### In what kind of situations can deadlocks occur?
First there are locks:
A lock occurs when multiple processes try to access the same resource at the same time. One process loses out and must wait
for the other to finish.

Deadlock occurs when: Thread ‘A’ locks Resource 1, that Thread ‘B’ wants to use, and Thread ‘B’ locks Resource 3 that 
Thread ‘A’ wants to use at the same time, and they get stuck forever.

#### What are possible ways to prevent deadlocks from occurring?
When two or more process wish to use the same resource is a race condition. 
The part of the program where accessesing the shared resource is known as the critical section. 
So, to avoid a race condition, we need to synchronize access to the critical section.
Java offer a couple of solution:

- Mutex (or mutual exclusion).
The simplest type of synchronizer – it ensures that only one thread can execute the critical section of a computer program 
at a time. To access a critical section, a thread acquires the mutex, then accesses the critical section, 
and finally releases the mutex. In the meantime, all other threads block till the mutex releases. 
As soon as a thread exits the critical section, another thread can enter the critical section. Mutex is applied to the
resource with the ```synchronized``` keyword.

```java
    //an example resource
    public int getNextSequence() {
        classVarible += 1;
        return classVarible;
    }

    //and applying the mutex to ensure synchronous access
    @Override
    public synchronized int getNextSequence() {
        return super.getNextSequence();
    }
```
   
- ReentrantLock.
The thread can reenter any block of code for which it already holds the lock.

```java
...
  boolean isLocked = false;

  public synchronized void lock()
  throws InterruptedException{
    while(isLocked){                //here the mutex is implemented as spin-lock
      wait();
    }
    isLocked = true;
  }
...

private ReentrantLock mutex = new ReentrantLock();
 
    public int getNextSequence() {
        try {                               //and here, in the
            mutex.lock();                   //critical section
            return super.getNextSequence(); //the method who access the resource
        } finally {                         //the process can re-enter to the resource
            mutex.unlock();                 //while other processes are waiting
        }
    }
```

- Semaphore:
While in case of a mutex only one thread can access a critical section, 
Semaphore allows a fixed number of threads to access a critical section. 
Therefore, we can also implement a mutex by let the resources use a pool.

```java
public class SequenceGeneratorUsingSemaphore extends SequenceGenerator {
    
    private Semaphore mutex = new Semaphore(1); //the pool
 
    @Override
    public int getNextSequence() {
        try {
            mutex.acquire();                    //an access granted
            return super.getNextSequence();
        } catch (InterruptedException e) {
            // exception handling code
        } finally {
            mutex.release();                    //and returned
        }
    }
}
```

#### What does the critical section or critical region mean in the context of concurrent programming?
Parts of the program where the shared resource can be accessed is the critical section.
It cannot be executed by more than one process. Typically, the critical section accesses a shared resource, such as a 
- data structure, 
- a peripheral device, or 
- a network connection, 

For example, in networking. 
A network socket wait some ordered data. 
Let's say we have an ordering program that is able to order this data and pass to the socket. 
This part of code is the critical section, where socket get ordered data (resource) and sorting methods (processes) wish to
pass their load.  

Another example, for data structures. 
It might be that given a collection (a resource) and two or more processes 
are also a couple of method (processes) which want to read this resource. 
(for example a list. one process is running through the list, while other proccess trying to modify or delete the same resource.) 
The part of the code where any method have access to the collection is a critical section.