# Test automation questions

### Testing Basics (ISTQB related)

#### What is the purpose of testing? What is not?
Testing process aiming:
 - to reveal and prevent as much as possible known or hidden defects and bugs
 - to build and improve the overall quality of the product
 - to reduce the possibility of failures caused by internal errors
 - show how the software working under certain conditions.
 - to verify the system meets with specified requirements.

Test process would not:
- fix the issue in case a bug found
- prove that the software working well under every circumstance, 
- prove that the product is bug and failure free
- validate that the product meets with user needs (but can suggest some hints).

To set up the requirements and to define when meet the product with stakeholders demand (or user demand) is a part of <br>
the software design. A test can be good, but the program bad, if there are requirement gaps.

#### What is the difference between Defect, Error, Failure?
**Error**: Some human mistake.
> many circumstances can cause a mistake, typo, rush, inattention, misunderstanding etc...

**Defect** (bug, fault): An error stayed in code.
> can lead to failure but not necessary, only certain circumstances lead to failure. <br>
If the part of the code containing the defect, is executed, or the environment changed it can lead to failure.

*static test able to reveal errors and defects.*

**Failure** (malfunction, issue, incident): the inability of a system or component to perform its required functions.
- produces an incorrect result (**issue**)
- does not perform the correct action (**incident**)
- does not perform any action (**malfunction**)

*dynamic test can find them*

#### What are the testing principles?
 1. Testing shows the presence of defects, not their absence.
 2. Exhaustive is impossible. 
    >By risk analysis and test techniques focus the test effort.
 3. Shift left 
    >Join the testing process early in the software development lifecycle to save time and money.<br> 
    Early testing with static techniques can save time and energy with preventing bugs.
 4. Defects cluster together. 80%-20% rule. <br>
    >Pareto's principle, 80-20 rule. The majority of the defects (80%) clustered and caused by a few modules (20%).<br>
 5. Pesticide Paradox. 
    >Executing the same test does not find more defect. <br>
    Except regression test. Regression test has a beneficial outcome to execute over and over.
 6. Testing is context dependent. 
    >There is no universal test design pattern.<br>
    Every product ahs different contextual need.
 7. Absence-of-errors is a fallacy. 
    >Good tests are not guarantee for a successful or flawless product.<br> 
    Test can verify and validate the product but isn't a guarantee that design and acceptance meet with users needs. 

#### What is unit testing? Who is responsible to write unit tests?
Unit test cover a piece of code. A function or a method. <br>
Should be written by the **developer** who wrote, to ensure that this build block working properly and independently.

#### What are Test Levels, what is the difference between them?
Test levels are group of test activities performed in relation with the development lifecycle.

- **Component**, or Unit testing:
    - The smallest testable portion of code. This kind of testing helps to test each component separately.
    - It checks if that component has fulfilled the functionality or not. 
    - This kind of testing is performed by developers.

- **Integration** testing:<br>
Integration means combining. In this testing phase, different software components are combined and tested together as a group<br>
    - To ensure, that newly added module is working properly and ready for system testing.
    - To check the data flow from one module to other modules.

- **System** testing:<br>
Performed on a complete, integrated system.<br> 
    - It allows checking system's compliance as per the requirements. 
    - It tests the overall interaction of components. 
    - It can involve load, performance, reliability and security test.
    - Often the final test to verify that the system meets the specification. 
    - It evaluates both functional and non-functional testing.
    - The biggest part in automation.

- **Acceptance testing**:<br>
Like system testing, typically focuses on the behavior and capabilities of a whole system or product.<br>
    - Usually done by the user, customer or stakeholders, manually. (UAT: User acceptance testing)
    - Establishing confidence in the quality of the system as a whole
    - Validating the system is complete and will work as expected
    - May produce information to assess the system’s readiness for deployment
    - Should produce information user experience by the customer (end-user). 
    - Finding a significant number of defects during acceptance test may considered a major project risk.

#### What is the difference between verification and validation?
Verification: checking whether the system meet with requirements<br>
Validation: checking whether the system meet with user and/or stakeholder needs

("Verification: **Have we built the software right?** (i.e., does it implement the requirements).<br>
Validation: **Have we built the right software?** (i.e., do the deliverables satisfy the customer)."<br> 
wikipedia)

#### What are Testing Types, what is the difference between them?
![types-of-test] (https://ehikioya.azureedge.net/wp-content/uploads/hm_bbpui/86828/fh2aspgg9au0icjnuf8d9lvhwccrv977.png)

- **Functional testing**.<br>
This type refers to activities that verify a specific action or function of the code.<br> 
Test in terms of completeness, correctness and appropriateness.<br>
Tend to answer the question of "can the user do this" or "does this particular feature work."
    - Unit test
    - Integration test
    - System test
    - Acceptance test
    - Regression test
    
- **Non-functional testing**.<br>
This type refers to aspects of the software like scalability or performance, behavior under certain constraints, or security.<br> 
    - Performance testing
    - Load testing 
    - Endurance testing. 
    - Volume testing (is a way to test software functions when for example a file, or a database increase radically in size) 
    - Stress testing (is a way to test reliability under unexpected or rare workloads) 
    - Security testing is essential for software that processes confidential data to prevent system intrusion by hackers.


#### What is the difference between white box, grey boy and black box testing?
**White-box Testing**.<br> Structure-based technique.<br>
Tests are written in knowledge about the test object internal structure or implementation.<br>

**Black-box Testing**.<br> Behavior-based technique.<br>
Test are written without knowledge about the test object internal structure or implementation.

**Grey-box Testing**.<br> Tests are written with partial knowledge about the test object internal structure.

#### What is the difference between UAT (User Acceptance Testing) and System testing?
**System test** aim the verification of the system or product behavior and capabilities.<br>
- how the system perform those tasks (functional), and 
- how behave while performing those tasks (non-functional)
- how the components of the system are connected and integrated with each other

**UAT** aim to validate how the product (or component) fulfill the requirements and how can a user perform processes.
- how the product fulfill the needs from a user (customer) view.

#### Mention the differences between Regression Testing, Smoke Testing and Retesting?
**Smoke Testing**. To prove with minimal effort that the object functional, and in the state for further test process.

**Retesting**. After a bug or issue has been fixed, test cases - where this particular defects were encountered -
are<br> re-executed to prove the operation successness. 
 
**Regression Testing**. After major changes or upon new versions, changing functionality or capabilities etc.<br>
To ensure the software has preserved quality, integrity, usability, functionality and capability as before.

#### What is risk-based testing, what is the point of it?
RBT aim to prioritize the tests. <br>
- Risk is used to focus the effort required during testing.<br> 
It is used to decide where and when to start testing
and to identify areas that need more attention.
- Analyzing product risks early contributes to the success of a project.

>A risk calculation example:<br>
>After analyzing the **probability of occurrence**, and the **impact possible damage** in <br>
> money / time / human life loss<br>
>given two number from a scale from 1 to 5.<br>
>Multiplying this two number can be a risk factor.
    
#### What is the difference between Static and Dynamic Testing?
**Static testing** does not involve the execution of the code.<br> 
Instead using automated tools or by manual examination of the work product, during code review and code analysis<br> 
tries to find defects directly rather than searching the root of a failure.<br>
- examine the system consistency and internal quality (UML) 
- compare designed income-outcome with actual values (on implemented code) 

**Dynamic testing** involve much or less execution.<br> 
From a basic part of code to whole system-wide execution.<br>
- the system visible behavior.

#### Compare V-model, Waterfall, Agile from testing perspective!
[V-model] (https://en.wikipedia.org/wiki/V-Model_(software_development)#/media/File:Systems_Engineering_Process_II.svg)

**Waterfall**. Model indicates that the design, implementation and test phases are well separated and sequential.<br>
Each phase depends on the previous stage. Testing begin after the work product is done, at the very end. 

**V-Model**. Variation of waterfall, also sequential.<br> 
Concept, requirements, design, implementation, test process.<br>
But test process run parallel with development together, started when implementation has, and follow it during the whole process.<br>
(Test execution can be expensive due to its repetitive nature.)

**Agile**. The most intertwined connection between test and development. <br>
Design, development and test phases following each other in cyclic order producing a relative fast and continuous product<br>
delivery.

#### What would you test in case of a simple web shop purchasing function (put items to cart, buy them)? 
#### Plan and reason your tests.
I would make destructive tests to verify:
 - less than zero item not allowed in cart
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

Integration tests to find out the payment process in case of electronic payment possible then:
- in case of unsuccessful payment how can the component handle the form
    - re-set to original value
    - re-set to default value
    - is re-set something or leave blank

### Reporting, Bugs

#### What steps would you follow when you find a defect?
Should be communicated to the developer in a well documented form:
- *conditions* under which this bug is occurring
- *excepted* and *actual* state of operation
- gather and insert any relevant logs.
- attach every important circumstances about the system:
    - *OS / platform / browser / software version* information
in order to provide clear and specific steps to reproduce the issue, so the developer can get the exact failure reason.

#### Talk about common test reports, and about their details.
Test reports should inform stakeholders about the progress of testing process and state of the product.
Reports should be regular and understandable for non-technical persons, in order to achieve this, should use <br>
metrics (diagrams, slides etc.) and, a clear informative structure.

- *Purpose* of the document<br>
Explain details and activities about the testing performed for the Project

- Application Overview<br>
Brief description of the application tested

- Testing *Scope* - In Scope, Out of Scope, Items not tested - <br> 
This section explains the functions/modules in scope & out of scope for testing.<br>
>In scope: 
>    - what tests were executed 
>    - what were the outcome

>Out of scope:
>   - objectives being not tested
>   - reason

>Not tested:
>   - Any items which are not tested due to any constraints / dependencies / restrictions should be clearly documented, 
else it will be assumed that testing covered all areas of the application.

- Metrics<br>
Metrics (diagrams, statistics) will help to understand the test execution results. 

- Test *Environment & Tools*<br>
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

- *Conclusion/Sign Off*<br>
This section will mention whether the Testing team agrees and gives a Green signal for the application to ‘Go Live’<br>
or not after the Exit Criteria was met. 

#### What does a bug report contains?
- Explanation how exactly the product is broken (how reached-what expected)
- Information needed to reproduce (and fix) problems and the environment
- Identified with title and id to be well recognizable
In order to be an efficient form of communication between the reporter and receiver.

[bug-report] (https://docs.google.com/spreadsheets/d/1MRHpj7wzvbEufmERJ31eT2bz_CJ1E8OK7KgzTsnzWP4/edit#gid=0)

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
A good automated test in my opinion is:
 - simple, 
 - modular, 
 - robust and 
 - reliable, 
 - maintainable, 
 - well documented and independent, and 
 - created for a reasonable purpose.

#### What is Selenium, Selenium IDE, Selenium WebDriver?
**Selenium** is an open source framework. Made to carry out automated tests on web applications.<br>
Selenium is being developed since 2004, by Jason Huggins and Paul Hammant and others.<br> 
The tool is composed of more components, IDE, WebDriver and Grid.<br>

**IDE**: is a direct js implementation to interact with a browser, can record and playback tests, <br>
and use a domain specific language: selenese.

**WebDriver**: is a portable cross platform and multilingual application. The successor of Remote Control.<br> 
Accept instructions through the client API, has implementation in java, python, php, ruby, c#, <br>
running under windows and unix like systems (MacOS, Linux).

#### How can be web elements identified?
They can be identified through the html they reside. **ID, class, name, tag, linkText, partialLinkText, cssSelector and xPath**.<br>
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

`NoSuchElementException` - the given search context does not find the element, root can be typo, or the classifier does not exist.<br>
`StaleElementException` - the stored element reference has been refreshed, maybe the page was reloaded, or some js has modified it after it was found firstly.<br>
`TimeOutException` - some not specified problem has occurred, and the given time amount to find an element has expired without success.<br>
`ElementNotInteractableException` - for some reason the element found, but command not applicable on it.<br>
`ElementNotVisibleException` - for some DOM effect the element is found in source but not visible.<br>
`WebDriverException` - a process try to perform an action after driver has been closed.<br>

#### Compare POM and Keyword Driven Testing!
**POM**:
A *design pattern* to create an *Object repository* from web UI elements.<br> 
Every page should have a corresponding object repository, the repository could use the PageFactory to find those elements<br>
and should contain the methods to interact with the elements.<br>
This construction should abstract an API in order to allow the interaction but *separate the different layers*, namely<br>
the repository and logic from the actual test cases.<br> 
This pattern make tests more readable, modular, reusable, independent and maintainable.

**KDT**:
This is *scripting technique*; using an extensible library where *keywords* representing the actions and scripts,<br>
which defining the actual *procedure* to operate with elements, like a key - value pair dictionary.<br>
This technique separate logic from test scenario, which make the *process declarative and procedures reusable*.<br>
Using keywords (similar to BDD) test cases can be written by no- or low programming skills, *making test cases<br>
more readable* for stakeholders and make test case build process faster.

#### What is the difference between TDD and BDD?
**TDD**:
Test Driven Development is a software development process and very closely coupled with AGILE methodology.<br> 
The **development done in cycles**:
- First the test case is written. 
- Then run test and develop code till all green. 
- Finally, refactoring.

At the end of the cycle, the feature should be developed and cycle can begin again;

**BDD**:
Behavior Driven development is kind of declarative TDD with a taste of KDT.<br>
A *living language*, based on keywords, such as: **Given, When, Then**.<br> 
Common in TDD as specifies the requirements and design the scenario before any line code may be written, but<br>
easier to understand for such outsiders like stakeholders or non-technical staff.<br>
Also make possible to write scenarios without programming skills and make test cases and sentences reusable.
Well structured architecture make tests more readable and maintainable.

#### What is API testing and why would you use that?
API testing is a type of software testing APIs involved directly to verify a product *functionality, reliability,<br> 
performance, and security*. Since APIs lack of GUI, API testing is performed at the message layer on a higher speed.

**Earlier Testing** - Increased Development Progress<br>
Tests can be built after module has finished and before GUI developed to validate the correctness of responses and data.

**Easier Test Maintenance**<br>
API changes are much more controlled and infrequent than UI changes.<br> 

**More Reliable and Robust**<br>
Accessing web elements can be difficult and may vary a lot depends on the browser, device and screen orientation. 
API test bring a constant result.

**Faster Time To Resolution**<br>
API tests derive exact information about defects. This helps reduce time spent on finding and fixing bugs.

**Speed and Coverage of Testing**<br>
Without graphical process, execution run faster.
 
#### What is Data Driven Testing and why is it useful?
DDT or *parameterized* test is a *methodology* that design test scripts and test input into a framework, keeping the data separate from<br> 
functional tests. The same test script can execute different combinations of input and test results.

 - reduce the length of code-base as reducing the need of write individual scripts.
 - reduce the execution time if automated.
 - improve the reliability with more result.
 - data-base can be stored separated in text file, cvs, excel which improve the available range of sources.
 - data-base replaceable.

#### What are the challenges and best practices with dynamically loading web elements?
Web applications using AJAX or React, load elements asynchronous, and elements state may vary after a site has loaded.<br>
Locating those elements can be challenging as WebDriver may throw a sort of exceptions, but proper and well<br>
constructed waits can solve this task.<br>
Best practices: dense placed waits, custom wait, try-catch block.

Another difficulty can be that web nodes may not preserve the exact location during the application lifetime.<br>
Best practice: in case of locating with xpath, the xpath should not be the full xpath like:

`
    /html/body/div[7]/div[2]/div[10]/div[1]/div[2]/div/div[2]/div[2]/div/div/div[2]/div/div[1]/a/h3/button
`

instead, should use a relative xpath like:

`
    //button[contains(@class, ‘classname’)]
` 

#### What are the challenges of Mobile Test Automation?
Huge scale of products on market which are very different in performance, resolution and OS, therefore may need test script<br> 
which able to locate and process result dynamically or may need a solution to execute more test case parallel to save time.

Android: a million different device, easy testable OS.<br>
Apple: closed iOS, difficult to test, relative few devices.

### Advanced Topics

#### What is the difference between CI and CD?
CD based on CI.<br>
**CI** should compile newly added code, merge different branches, and should perform <br>
integration and regression test automated, easing the teamwork.<br> 
Also allowing for team members to orchestrate and control workflow even from different places remotely.<br>
**CD** can be continuous -*delivery* or -*deployment*.<br>
**Continuous delivery** mean: the product has always a version to deploy, upgrade or to ship *(release manually)*.<br>
**Continuous deployment** mean: the product deployed automated; go live, available to download or upgrade *(release automatic)*.<br>

CI says: the product is ready to pack.<br>
C delivery says: the product is packed.<br>
C deployment says: the product is on the shelf.<br>

#### Describe a Continuous Delivery!
Software engineering approach where developers *push* their code on different branches<br>, 
*merging* back to main in short cycles. <br>
*Automated* test are running to *verify* the system integration and quality. In case test are passed, the product should be<br> 
stored by version control system in a ready-to-deliver state.<br>
It aims to *build, test, and release* software with greater speed and frequency.

#### Compare 2 popular CI systems, one of them should be Jenkins!

| **Jenkins** | **BitBucket** |
| --- | --- |
| open-source | has free version, owned by Atlassian group |
| CI tool | VCS tool with built-in CI |
| Java | Java |
| standalone version | Atlassian hosted: Cloud |
| doesn't provide | locally hosted: Bitbucket Server[^1] | 
| much feature but easily | enterprise: Data Center[^1] |
| extendable with a huge scale of plug-ins | extendable with plug-ins from Atlassian marketplace |
| bit complicated set-up | no need of set-up |
| bit complicated UI | clear UI |
| integration with other tools can be difficult | easy Jira integration |

[^1] CI available from plug-in.

#### What is Docker, why is it useful?
Docker is a tool designed to make easier to *create, deploy, and run applications* by using **containers**.<br> 
Containers allow developers to *package up* an application with every part it needs, such as libraries and other dependencies,<br> 
and ship it all out as one *reusable and cloneable package*.<br>

With Docker, developers can focus on writing code without worrying about the system on which their code will run.<br> 
Applications become truly portable. Running application using *different OS* becoming very easy in comparing to set up<br>
and maintain virtual machines.<br> 
Different requirements can fulfilled in isolated containers. This flexibility can increase scalability and reusability.<br>
Consistency and isolation are granted as a result of using every time a copy of image and run it in a container.<br>
Set up and execution time reduced because the *image is preconfigured and installed along every required parts*.<br>
Docker take care of isolation, while by default each Docker container that’s running is isolated from the network.<br>

#### Compare 2 popular Test Automation IDE, one of them should be Katalon Studio!
**Selenium IDE** & **Katalon Studio**.<br>
Katalon was built on Selenium, therefore they share a lot of commonalities.
Both of them easy to use for non-programmer people, and give availability to configuration.