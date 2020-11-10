# Test automation questions

### Testing Basics (ISTQB related)

#### What is the purpose of testing? What is not?
Testing process aiming:
 - to reveal and prevent as much as possible known or hidden defects and bugs
 - to build and improve the overall quality of the product
 - to reduce the possibility of failures caused by internal errors
 - show how the software working under certain conditions.
 - to verify the system meets with specified requirements.
<br>

Test process would not:
- prove that the software working well under every circumstance, 
- prove that the product is bug and failure free
- validate that the product meets with user needs (but can suggest some hints).

To set up the requirements and to define when meet the product with stakeholders demand (or user demand) is a part of <br>
the software design. A test can be good, but the program bad, if there are requirement gaps.

#### What is the difference between Defect, Error, Failure?
Error (mistake): can come from many circumstances. <br>
Developer made a mistake and stay in the code, or some other way the codebase is corrupted, or maybe <br>
there are design or requirements failure.
- static test can reveal them.

Defect (bug, fault): an error can lead to failure but not necessary, only certain circumstances lead to failure. <br>
If the part of the code containing the defect, is executed, or the environment changed it can lead to failure.
- static test can reveal them.

Failure (malfunction, issue, incident): the inability of a system or component to perform its required functions.
- produces an incorrect result or 
- does not perform the correct action or 
- does not perform any action. 
    - dynamic test can find them

#### What are the testing principles?
1. Testing shows the presence of defects, not their absence.
2. Exhaustive is impossible. By risk analysis and test techniques focus the test effort.
3. Shift left - join the testing process early in the software development lifecycle to save time and money.
4. Defects cluster together. 80%-20% rule. <br>
Pareto principle, 80-20 rule. The majority of the defects (80%) caused by a few modules (20%).<br>
5. Pesticide Paradox. Executing the same test does not find more defect. <br>
(Except regression test. Regression test has a beneficial outcome to execute over and over.)
6. Testing is context dependent. There is no universal test design pattern for every product.
7. Absence-of-errors is a fallacy. Good tests are not guarantee for a successful or flawless product.

#### What is unit testing? Who is responsible to write unit tests?
Unit test cover a piece of code on class level. <br>
Written by usually the developer who wrote (and in white-box situation), 
to ensure that this build block working properly and independently.

#### What are Test Levels, what is the difference between them?
Test levels are group of test activities performed in relation with the development lifecycle.

1. Component, or Unit testing:
- The smallest testable portion of code. This kind of testing helps to test each module separately.
- It checks if that component has fulfilled the functionality or not. 
- This kind of testing is performed by developers.

2. Integration testing:
Integration means combining. In this testing phase, different software modules are combined and tested together as a group<br>
- To ensure, that newly added module is working properly and ready for system testing.
- To check the data flow from one module to other modules.

3. System testing:
System testing is performed on a complete, integrated system.<br> 
- It allows checking system's compliance as per the requirements. 
- It tests the overall interaction of components. 
- It can involve load, performance, reliability and security test.
- Often the final test to verify that the system meets the specification. 
- It evaluates both functional and non-functional testing.
- The biggest part in automation.

4. Acceptance testing:
Acceptance test executed to validate if the product meet with acceptance criteria (user needs).<br> 
- Usually done by the user, customer or stakeholders, manually. 

#### What is the difference between verification and validation?
Verification: checking whether the system meet with requirements<br>
Validation: checking whether the system meet with user and/or stakeholder needs

("Verification: Have we built the software right? (i.e., does it implement the requirements).<br>
Validation: Have we built the right software? (i.e., do the deliverables satisfy the customer)." 
wikipedia)

#### What are Testing Types, what is the difference between them?
- Functional testing.
This type refers to activities that verify a specific action or function of the code.<br> 
Test in terms of completeness, correctness and appropriateness.<br>
Functional tests tend to answer the question of "can the user do this" or "does this particular feature work."
    - Unit test
    - Integration test
    - System test
    - Acceptance test

- Non-functional testing.
This type refers to aspects of the software like scalability or performance, behavior under certain constraints, or security.<br> 
    - Performance testing
    - Load testing 
    - Endurance testing. 
    - Volume testing (is a way to test software functions when for example a file, or a database increase radically in size) 
    - Stress testing (is a way to test reliability under unexpected or rare workloads) 
    - Security testing is essential for software that processes confidential data to prevent system intrusion by hackers.

- Change Related Testing. 
Called to confirm that defects have been fixed or changes does not result in different behavior.
    - Regression testing focuses on finding defects after a major code change has occurred. 
    - Continuous testing is the process of executing automated tests as part of the software delivery pipeline (CI/CD).

#### What is the difference between white box, grey boy and black box testing?
White-box Testing. Tests are written in full access to the test object internal structure or implementation.<br>

Black-box Testing. Test are written from the user level, whereas the code is invisible for a tester, test object 
reachable through the public api or as product.

Grey-box Testing. Tests are written within the knowledge of the internal architecture,
but interacting with the object from the user level .

#### What is the difference between UAT (User Acceptance Testing) and System testing?
System test aim to the verification of the system or product behavior and capabilities.<br>
- how the system perform those tasks (functional), and 
- how behave while performing those tasks (non-functional)

UAT aim to validate how the product or component fulfill the requirements and how can a user perform processes.
- how the product fulfill the needs from a user (customer) view.

#### Mention the differences between Regression Testing, Smoke Testing and Retesting?
Smoke Testing. To prove with minimal effort that the object functional, and in the state for further test process.

Retesting. After a bug or issue has been fixed, test cases - where this particular defects were encountered -
are re-executed to prove the operation successness. 
 
Regression Testing. After major changes or upon new versions, changing functionality or capabilities etc.<br>
To ensure the software has preserved quality, integrity, usability, functionality and capability as before.

#### What is risk-based testing, what is the point of it?
RBT aim to prioritize the tests. <br>
Calculate the risk of failure from the component importance, and the likelihood of the failure.<br>
Point is, to reduce the wide range of possible tests, to focus on the effective testing.

#### What is the difference between Static and Dynamic Testing?
Static testing does not involve the execution of the code.
- manual examination of the work product
- code review
- analysis (often done with automated tools)

Aim the system consistency and internal quality.<br>
Find defects directly rather than searching the root of a failure. 

Dynamic testing can involve much or less execution from a basic part of code to whole system-wide execution.<br>
Aim the system visible behavior.

#### Compare V-model, Waterfall, Agile from testing perspective!
![V-model](https://en.wikipedia.org/wiki/V-Model_(software_development)#/media/File:Systems_Engineering_Process_II.svg)
V-Model. After the project definition born (concept, requirements, design), at implementation phase begin the test process.<br>
In opposite as the project was designed from bigger shape to implementation, test process start with unit tests and goes to<br>
comprehensive system and user acceptance test.

Waterfall. Typical waterfall model indicates that the design, implementation and test phases are well separated and sequential.<br>
Each phase depends on the previous stage. Testing begin after the work product is done, at the very end. 

Agile. The most intertwined connection between test and development. <br>
Design, development and test phases following each other in cyclic order.

#### What would you test in case of a simple web shop purchasing function (put items to cart, buy them)? 
#### Plan and reason your tests.
I would make destructive tests to verify:
 - less than zero item not allowed in basket
 - checkout with zero item not charge the card or handled properly
 - that the system can handle more than one identical item
 - user can remove an item in case he/she changed his/her mind

UI/UX tests should be done to find out:
 - how a user can handle the process (complicated or easy to use)
 - if possible any modification (topping on a pizza for example),<br> 
 these possibilities should get a workaround to verify:
    - how they effect on the bill (removing, adding...)
    - are they calculated, displayed, placed properly
 - how the system threat users:
    - order available after logout / exit / refresh
 - is there any notification about the order successfulness / cancellation
 - is there any notification about extreme amount of items in basket / bill

### Reporting, Bugs

#### What steps would you follow when you find a defect?
Should be communicated to the developer in a well documented form:
- conditions under which this bug is occurring
- excepted and actual state of operation
- gather and insert any relevant logs.
- attach every important circumstances about the system:
    - OS / platform / browser / software version information
in order to provide clear and specific steps to reproduce the issue, so the developer can get the exact failure reason.

#### Talk about common test reports, and about their details.
Test reports should inform stakeholders about the progress of testing process and state of the product.
Reports should be regular and understandable for non-technical persons, in order to achieve this, should use <br>
metrics (diagrams, slides etc.) and, a clear informative structure.

- Purpose of the document<br>
Explain details and activities about the testing performed for the Project

- Application Overview<br>
Brief description of the application tested

- Testing Scope - In Scope, Out of Scope, Items not tested -<br> 
This section explains the functions/modules in scope & out of scope for testing. 
Any items which are not tested due to any constraints/dependencies/restrictions should be clearly documented, 
else it will be assumed that Testing covered all areas of the application.

- Metrics<br>
Metrics (diagrams, statistics) will help to understand the test execution results. 

- Test Environment & Tools<br>
Provide details on Test Environment in which the Testing is carried out. 
    - Server
    - Database
    - Tools...
    
- Lessons Learned<br>
This section is used to describe the critical issues faced, and their solutions.<br>
Lessons learned will help to make proactive decisions during the next Testing engagement,<br> 
by avoiding these mistakes or finding a suitable workaround.

- Recommendations<br>
Any workaround or suggestions can be mentioned here.

- Exit Criteria<br>
This part is defined as a Completion of Testing by fulfilling certain conditions. 
e.g.:
    - All planned test cases are executed;
    - All Critical defects are Closed etc.

- Conclusion/Sign Off<br>
This section will mention whether the Testing team agrees and gives a Green signal for the application to ‘Go Live’<br>
or not after the Exit Criteria was met. 

#### What does a bug report contains?
- Explanation how exactly the product is broken (how reached-what expected)
- Information needed to reproduce (and fix) problems and the environment
- Identified with title and id to be well recognizable
In order to be an efficient form of communication between the reporter and receiver.

![bug-report](https://docs.google.com/spreadsheets/d/1MRHpj7wzvbEufmERJ31eT2bz_CJ1E8OK7KgzTsnzWP4/edit#gid=0)

#### How would you prioritize a bug?
I would considerate the following topics:
- How does the bug affect the flows in the product. (A bug causing a dead footer link vs a bug affecting the user’s payment)
- The impact that the bug cause. (For example a user can’t create a new project in a project management software)
- What is the estimated number of users who will encounter this bug.
- How big will the effort to fix the bug.
- How big will be the impact as long the bug exists.

Common bug severity: 
 - Blocker: Unless and until fixed, no further process can be done
 - Critical: Application is crashing or losing data.
 - Major: Major function affected.
 - Minor: Minor feature affected.
 - Trivial: Product can fulfill the purpose, the fault barely noticeable.
 - Enhancement: Recommendation or idea to enhance the system.

### Test Automation, Selenium

#### Which test cases should be automated and which shouldn't?
- Repeatedly executed test cases may be automated, like regression, (continuously adjusted) integration and system tests.
- Test cases where same workflow can be applied and parameterized for big and/or different data input even at unit test level. DDT.
- Performance and load tests may be automated.
- Tests if execution taking a long time should be automated to maximize the efficiency.
- Cross-platform and cross-browser tests definitely fall under automated category.  
- CI/CD processes
- GUI / API

In case the construction take more expenses than the benefit of automation NOT:
- the UI / feature / logic may vary a lot
- outcome not predictable
- test case executed once or very rarely (except for example system test)
- making automation make no sense because of complexity or goal (e.g.: jira project setup)

#### Describe a good automated test!
A good automated test in my opinion is simple, modular, robust and reliable, maintainable, well documented and independent<br>,
and created for a reasonable purpose.

#### What is Selenium, Selenium IDE, Selenium WebDriver?
Selenium is an open source framework. Made to carry out automated tests on web applications.<br>
Selenium is developing since 2004, by Jason Huggins and Paul Hammant and others.<br> 
The tool is composed of more components, IDE, WebDriver and Grid.<br>
 
IDE: is a direct js implementation to interact with a browser, can record and playback tests, <br>
and use a domain specific language: selenese.

WebDriver: is a portable cross platform and multilingual application. The successor of Remote Control.<br> 
Accept instructions through the client API, has implementation in java, python, php, ruby, c#, <br>
running under windows and unix like systems (MacOS, Linux).

#### How can be web elements identified?
They can be identified through the html they reside. ID, class, name, tag, linkText, partialLinkText, cssSelector and xPath.<br>
WebDriver capable to scan through the html source, and find an element through one of its attributes or directly<br> 
through the place with xpath.

#### How can you wait for elements, what can go wrong? Collect possible errors and root causes.
Explicit and implicit and fluent waits are available.<br> 

Implicit wait applicable on a script, giving a fixed amount of time to the script to finish or should fail.
```java
    driver.manage().timeouts().implicitlyWait(int amountOfWait, TimeUnit.Type);
```

Explicit wait is the most common used class (on my side), it can be equipped with an object to wait, and a circumstance
how to wait for it.
```java
    WebDriverWait wait = new WebDriverWait(WebDriver, Duration.ofTimeout());
    WebElement element = wait.until(ExpectedCondition.type);
```

Fluent wait is a kind of explicit wait, with the extra feature to configure the frequency to check the condition. 
```java
    FluentWait<WebDriver> webDriverWait = new FluentWait<WebDriver>(WebDriver)
                                                 .withTimeout(Duration.ofSeconds(30))
                                                 .pollingEvery(Duration.ofSeconds(5))
                                                 .ignoring(NoSuchElementException.class);
```

The most commons are:

NoSuchElementException - the given search context does not find the element, root can be typo, or the classifier does not exist.
StaleElementException - the stored element reference has been refreshed, maybe the page was reloaded, or some js has modified it after it was found firstly.
TimeOutException - some not specified problem has occurred, and the given time amount to find an element has expired without success.
ElementNotInteractableException - for some reason the element found, but command not applicable on it.
ElementNotVisibleException - for some DOM effect the element is found in source but not visible.
WebDriverException - a process try to perform an action after driver has been closed.

#### Compare POM and Keyword Driven Testing!
POM:
A design pattern to create an Object repository from web UI elements.<br> 
Every page should have a corresponding object repository, the repository could use the PageFactory to find those elements<br>
and should contain the methods to interact with the elements.<br>
This construction should abstract an API in order to allow the interaction but separate the different layers, namely<br>
the repository and logic from the actual test cases.<br> 
This pattern make tests more readable, modular, reusable, independent and maintainable.

KDT:
This is scripting technique; using an extensible library where keywords representing the actions and scripts,<br>
which defining the actual procedure to operate with elements, like a key - value pair dictionary.<br>
This technique separate logic from test scenario, which make the process declarative and procedures reusable.<br>
Using keywords (similar to BDD) test cases can be written by no- or low programming skills, making test cases<br>
more readable for stakeholders and make test case build process faster.

#### What is the difference between TDD and BDD?
TDD:
Test Driven Development is a software development process and very closely coupled with AGILE methodology.<br> 
The development done in cycles:
- First the test case is written. 
- Then run test and develop code till all green. 
- Finally, refactoring.

At the end of the cycle, the feature should be developed and cycle can begin again;

BDD:
Behavior Driven development is kind of declarative TDD with a taste of KDT.<br>
A living language, based on keywords, such as: Given, When, Then.<br> 
Common in TDD as specifies the requirements and design the scenario before any line code may be written, but<br>
easier to understand for such outsiders like stakeholders or non-technical staff.<br>
Also make possible to write scenarios without programming skills and make test cases and sentences reusable.
Well structured architecture make tests more readable and maintainable.

#### What is API testing and why would you use that?
API testing is a type of software testing APIs involved directly to verify product functionality, reliability,<br> 
performance, and security. Since APIs lack of GUI, API testing is performed at the message layer on a higher speed.

Earlier Testing - Increased Development Progress<br>
Tests can be built after module has finished and before GUI developed to validate the correctness of responses and data.

Easier Test Maintenance<br>
API changes are much more controlled and infrequent than UI changes.<br> 

More Reliable and Robust<br>
Accessing web elements can be difficult and may vary a lot depends on the browser, device and screen orientation. 
API test bring a constant result.

Faster Time To Resolution<br>
API tests derive exact information about defects. This helps reduce time spent on finding and fixing bugs.

Speed and Coverage of Testing<br>
Without graphical process, execution run faster.
 
#### What is Data Driven Testing and why is it useful?
DDT is a methodology that design test scripts and test input into a framework.<br>

The tests are organized around various situation, with many inputs.


Data can be stored in text file, cvs, excel... 

#### What are the challenges and best practices with dynamically loading web elements?
WebDriver has an extremely useful tool, the WebDriverWait class. With it's wait library.

Challenges are: 
the elements loaded after the document ready state -> no such element 
the elements are modified by the DOM -> stale element

Best practices: wait by every step, even custom wait, try-catch block

#### What are the challenges of Mobile Test Automation?
Huge scale of products on market which are very different in performance, resolution and OS.

### Advanced Topics

#### What is the difference between CI and CD?
CD based on CI. CI should compile newly added code, and should perform integration and regression test automated, ease the<br>
teamwork remotely between team members orchestrating branches, merges and so on. <br>
CD can be continuous delivery or deployment.<br>
If delivery its mean: the product has always a version to deploy, upgrade or to ship (release manually).<br>
If deployment its mean: the product deployed automated; go live, available to download or upgrade (release automatic).<br>
CI says: the product is ready to pack.<br>
C delivery says: the product is packed.<br>
C deployment says: the product is on the shelf.<br>

#### Describe a Continuous Delivery!
Developers push their code on different branches, then branches merged back to main. <br>
Automated test are running to verify the system integration and quality.
The product ready to deliver.

#### Compare 2 popular CI systems, one of them should be Jenkins!
#### What is Docker, why is it useful?
Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package.

Why:

With Docker, developers can focus on writing code without worrying about the system on which their code will run. Applications become truly portable. You can repeatably run your application on any other machine running Docker with confidence. For operations staff, Docker is lightweight, easily allowing the running and management of applications with different requirements side by side in isolated containers. This flexibility can increase resource use per server and may reduce the number of systems needed because of its lower overhead, which in turn reduces cost.
consistency, speed and isolation
By consistency, I mean that Docker provides a consistent environment for your application from development all the way through production– you run from the same starting point every time.
By speed, I mean you can rapidly run a new process on a server. Because the image is preconfigured and installed with the process you want to run,it takes the challenge of running a process out of the equation.
By isolation, I mean that by default each Docker container that’s running is isolated from the network, the file system and other running processes.
Compare 2 popular Test Automation IDE, one of them should be Katalon Studio!

#### Compare 2 popular Test Automation IDE, one of them should be Katalon Studio!

the process of executing automated tests as part of the software delivery pipeline 
to obtain immediate feedback on the business risks associated with a software release candidate.
Continuous testing includes the validation of both functional requirements and non-functional requirements; 
the scope of testing extends from validating bottom-up requirements or user stories to assessing the system requirements associated with overarching business goals.
