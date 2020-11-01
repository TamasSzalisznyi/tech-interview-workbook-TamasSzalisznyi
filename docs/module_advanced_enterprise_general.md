# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?
 the processing, data management, and presentation functions physically and/or logically separated
    -presentation layer
    -application layer
    -integration layer
    -database layer
    
#### What are microservices? Advantages and disadvantages?
 A large software project which is built from loosely coupled modules, which communicate with each other.
 
 Advantages:
     Improved fault isolation: Larger applications can remain mostly unaffected by the failure of a single module.
     Eliminate vendor or technology lock-in: Microservices provide the flexibility to try out a new technology stack on an individual service as needed. 
     There won’t be as many dependency concerns and rolling back changes becomes much easier. 
     With less code in play, there is more flexibility.
     Ease of understanding: With added simplicity, developers can better understand the functionality of a service.
     Smaller and faster deployments: Smaller codebase and scope = quicker deployments, which also allow you to start to explore the benefits of Continuous Deployment.
    Scalability: Since your services are separate, you can more easily scale the most needed ones at the appropriate times, as opposed to the whole application. When done correctly, this can impact cost savings.
 Disadvantages:
    the main negative of microservices is the complexity that any distributed system has.
    Communication between services is complex: Since everything is now an independent service, 
    you have to carefully handle requests traveling between your modules. 
    More services equals more resources: Multiple databases and transaction management can be painful.
    Global testing is difficult: Testing a microservices-based application can be cumbersome. In a monolithic approach, we would just need to launch our WAR on an application server and ensure its connectivity with the underlying database. With microservices, each dependent service needs to be confirmed before testing can occur.
    Debugging problems can be harder: Each service has its own set of logs to go through. Log, logs, and more logs.
    Deployment challengers: The product may need coordination among multiple services, which may not be as straightforward as deploying a WAR in a container.

#### What is Separation of Concerns?
Design principle. Means separating a computer program into logically related parts. Concerns.
Modularity, and hence separation of concerns, is achieved by encapsulating information inside a section of code. 
Encapsulation is a means of information hiding. 
Layered designs in information systems are another embodiment of separation of concerns (e.g., presentation layer, business logic layer, data access layer, persistence layer).

#### What is a layered design and why is it important in enterprise applications?
n-tier architecture. separation of concern design.
It's about security, maintainability, readability, modularity, stability, reusability.

#### What is Dependency Injection?
Client who has dependencies and receive the injection.
Service who provide the dependencies and so provide the injection.
Injector who is bound together client and service and handle the injection.
Injection can be done via interface, setter and constructor.
Goal is to achieve a loosely coupled design where client, service and injector all easily replaceable.

#### What is the DAO pattern? When and how to implement?
Data Access Object.
DAO is used at DB connection. DAO provide the middle layer between business layer and DB layer.
DAO implementing an interface, the application can access through the interface the DAO, then the DAO
translate the demand, connect to the DB, start query and send back the response to the sender.

When: when using DB, persistence and CRUD operations.
How: with an interface.

#### What is SOA? When to use?
Service Oriented Architecture. Similar in modularity and reusability to microservices, but in enterprise level. 
Main point is heterogeneous behave.

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

Benefits come from the basic of the TDD. First writing failing test. Then write the code to make it pass, finally refactor. 
Earliest stage of testing where it can interweave
 with development.

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
Stack is a kind of queue.
The common part is: the information flow or the execution order are one-directional, 
adding- and removing items only possible from the end of the structure.
The difference is: 
in stack: new element added to the top of the stack and also the next element coming from the top. FILO 
in queue: new element added to the end of the stack and the next element always coming from the top. FIFO
-> polling, peeking, pushing

#### What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?
An abstract data type. A set of points (nodes) and edges, where points are bounded together with edges
and those edges have at least one, at most two nodes.

Simple graph where all the nodes connected with at most one edge.

Directed graph where edges have direction (and this is represented) 
meaning that an edge between A - B is not equal to B - A.

Weighted graph where the edges have a label, represent a value (length, weight, price etc...) which is the cost of the edge.

#### What are trees? What are binary trees? What are binary search trees?
Tree is a special graph, where every two node connected with exactly one edge.
Tree must be a connected- (there are no node without edge), and a simple-graph.

Binary tree is a kind of graph, which is tree, and every node have at least one and at most two edges.

Binary search tree is a searching algorithm which use rooted binary tree to store and retrieve the data. 
BST. In BST every node represent a value. The root of the tree represent the half of the highest value. 
Nodes in the left sub-tree containing lower values as the root,
nodes are in the right sub-tree containing higher values then the root value. 
 
#### How can you store graphs in programs? What are the advantages/disadvantages per each?
As nodes and edges: like in linked list.
As a list of all nodes and edges.
As a matrix of connections.

#### What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?
They are used for traversing the graph, they implement the logic in the graph, how the nodes are reached.
 
Breath First Search. Search through every graph level (if it is a tree). Once finished move to the next level.
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
CORS allows browsers fro use their resources in a controlled way, server describe who and what allowed to do.
The defined policy described in the header, with key: value 
```html
    Access-Control-Allow-Origin : [*/allowed-domain(s)]
```
Clients request put after preflight OPTION request to the server, the server will respond with it's defined access-policy.
If the options from response containing the request content the browser will execute the request, 
else will block after and correspond to the preflight response.

#### How can you initialize a CSRF attack?
Cross Site Request Forgery.
main points: 
-cookie stole (or different credentials)
-malicious script
-send it with the stolen cookie
-from a trusted site

#### What is JWT used for? Where to store it on client side?
Stand for JSON Web Token. It is used to involve an authorization server, which produce a token in exchange to the credentials.
It is for secure the credentials, as used once than go with tokens. Tokens can expire for more secure.
JWT stands from
    -header 
    -payload 
    they are stored in JSON format before signed. 
    -signature

The token is a concatenation of the base64 data of the above, delimited by a period. So, a JWT token would look like the following:

[header].[payload].[signature]

Maybe in the browser memory, encrypted, proper implementation.

### Threaded programming

#### When do you need to use threads in an application?
#### What is a daemon thread?
#### What is the difference between concurrent and parallel execution of code?
#### What is the most important problem developers are faced when using threads?
#### In what kind of situations can deadlocks occur?
#### What are possible ways to prevent deadlocks from occurring?
#### What does critical section or critical region mean in the context of concurrent programming?
