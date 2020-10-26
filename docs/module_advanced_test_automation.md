# Test automation questions

### Testing Basics (ISTQB related)

#### What is the purpose of testing? What is not?
Purpose: to reveal and prevent as much as possible known or hidden 
defects and bugs
in order to 
build and/or improve 
the overall quality of the product
and to
reduce the possibility of failures caused by internal errors 

Not Purpose: Setting up the acceptance criteria and design the product 
Not Purpose2: prove the absence of defects

#### What is the difference between Defect, Error, Failure?
Error can come happen from many circumstances.
eg. developer made a mistake or someway the codebase corrupted

Defect: error then can lead to Defect in the code. ( - Bug)
if a defect being executed it can lead to Failure.

Failure: "The inability of a system or component to perform its required functions 
within specified performance requirements."

#### What are the testing principles?
1. Testing shows the presence of defects, not their absence.
2. Exhaustive is impossible. By risk analysis and test techniques focus the test efforts
3. Shift left - join the testing process early in the software development lifecycle
4. Defects cluster together. 
    Aiming the tests for complex parts, 80-20 rule.
5. Pesticide Paradox. Same test execution count does not increase count of found defect. 
    - by regression test has a beneficial outcome: the low regression defect number-
6. Testing is context dependent. There is no universal test design pattern for every product
7. Absence-of-errors is a fallacy. Good tests are not guarantee for a successful product.
    (imho - respectively for 1., 2., still hidden bugs can occur and lead to failure
    , by design failure the product does not fulfill (by any acceptance criteria) the requirements )

#### What is unit testing? Who is responsible to write unit tests?
Unit test cover a piece of code on class level. 
Written by usually the developer who is in white-box situation, 
to ensure that this build block working properly and independently. 

#### What are Test Levels, what is the difference between them?
(component-[/unit-], integration-, system-, acceptance-testing)

--> (component-, component integration-, system-, system integration-, acceptance-testing) <--

Test levels are group of test activities performed in relation with the development lifecycle.
Grouped by (2.2)
the objective, 
the test basis
the test object
contextual factors (1.4)
Requiring suitable test environment

#### What is the difference between verification and validation?
Verification: checking whether the system meet with requirements
Validation: checking whether the system meet with user and/or stakeholder needs

("
Verification: Have we built the software right? (i.e., does it implement the requirements).
Validation: Have we built the right software? (i.e., do the deliverables satisfy the customer).
" 
wikipedia)

#### What are Testing Types, what is the difference between them?
Testing types are a group of related test activities.
Differences are the test objectives.

- Functional Testing. Functional quality characteristics: completeness, correctness, appropriateness

- Non-Functional Testing. Non-Functional quality characteristics: reliability, performance, security, 
    compatibility, usability

- White box Testing. Derived tests based on the product internal structure. 
    Structure or architect of a system or component is: correct, complete and as specified.

- Change Related Testing. Quality characteristics: confirming that defects have been fixed and 
    changes does not results in different behavior in regression testing.
(syllabus)

Installation testing
Most software systems have installation procedures that are needed before they can be used for their main purpose. 
Testing these procedures to achieve an installed software system that may be used is known as installation testing.

Compatibility testing
A common cause of software failure (real or perceived) is a lack of its compatibility with other application software, 
operating systems (or operating system versions, old or new), 
or target environments that differ greatly from the original 
(such as a terminal or GUI application intended to be run on the desktop now being required to become a Web application, which must render in a Web browser). 

Smoke and sanity testing
Sanity testing determines whether it is reasonable to proceed with further testing.

Smoke testing
Smoke testing is used as a build acceptance test prior to further testing, e.g., before integration or regression.
Consists of minimal attempts to operate the software, 
designed to determine whether there are any basic problems that will prevent it from working at all. 
Such tests can be used as build verification test.

Regression testing
Regression testing focuses on finding defects after a major code change has occurred. 
Specifically, it seeks to uncover software regressions, as degraded or lost features, including old bugs that have come back. 
Such regressions occur whenever software functionality that was previously working correctly, stops working as intended. 
For this, it is possible to generate and add new assertions in existing test cases, this is known as automatic test amplification.

Acceptance testing
Acceptance testing performed by the customer, often in their lab environment on their own hardware, 
is known as user acceptance testing (UAT). 

Alpha testing
Alpha testing is simulated or actual operational testing by potential users/customers or an independent test team at the developers' site. 

Beta testing
Beta testing comes after alpha testing and can be considered a form of external user acceptance testing.

Functional testing
Functional testing refers to activities that verify a specific action or function of the code. 
These are usually found in the code requirements documentation, 
although some development methodologies work from use cases or user stories. 
Functional tests tend to answer the question of "can the user do this" or "does this particular feature work."

Non-functional testing refers to aspects of the software that may not be related to a specific function or user action, 
such as scalability or other performance, 
behavior under certain constraints, or security. 
Testing will determine the breaking point, the point at which extremes of scalability or performance leads to unstable execution. 
Non-functional requirements tend to be those that reflect the quality of the product, 
particularly in the context of the suitability perspective of its users.

Continuous testing
Continuous testing is the process of executing automated tests as part of the software delivery pipeline 
to obtain immediate feedback on the business risks associated with a software release candidate.
Continuous testing includes the validation of both functional requirements and non-functional requirements; 
the scope of testing extends from validating bottom-up requirements or user stories to assessing the system requirements associated with overarching business goals.

Destructive testing
Destructive testing attempts to cause the software or a sub-system to fail. 
It verifies that the software functions properly even when it receives invalid or unexpected inputs, 
thereby establishing the robustness of input validation and error-management routines. 
Software fault injection.

Software performance testing
Performance testing is generally executed to determine how a system or sub-system performs in terms of responsiveness and stability under a particular workload. 
It can also serve to investigate, measure, validate or verify other quality attributes of the system, such as scalability, reliability and resource usage.
Load testing: is primarily concerned with testing that the system can continue to operate under a specific load, 
whether that be large quantities of data or a large number of users. 
This is generally referred to as software scalability. 
The related load testing activity of when performed as a non-functional activity is often referred to as endurance testing. 
Volume testing: is a way to test software functions even when certain components (for example a file or database) increase radically in size. 
Stress testing: is a way to test reliability under unexpected or rare workloads. 
Stability testing: (often referred to as load or endurance testing) checks to see if the software can continuously function well in or above an acceptable period.
Real-time testing: is a way to test software if timing constraints are met. Systems have strict timing constraints.

Usability testing
Usability testing is to check if the user interface is easy to use and understand. 
It is concerned mainly with the use of the application. 
This is not a kind of testing that can be automated; actual human users are needed, being monitored by skilled UI designers.

Accessibility testing
Accessibility testing may include compliance with standards such as:
Web Accessibility Initiative (WAI) of the World Wide Web Consortium (W3C)

Security testing
Security testing is essential for software that processes confidential data to prevent system intrusion by hackers.

Internationalization and localization testing
 for internationalization and localization validates that the software can be used with different languages and geographic regions. 

Development testing
Development Testing is a software development process that involves the synchronized application 
of a broad spectrum of defect prevention and detection strategies in order to reduce software development risks, time, and costs. 
It is performed by the software developer or engineer during the construction phase of the software development lifecycle. 
Development Testing aims to eliminate construction errors before code is promoted to other testing; 
this strategy is intended to increase the quality of the resulting software as well as the efficiency of the overall development process.
Depending on the organization's expectations for software development, Development Testing might include static code analysis, data flow analysis, metrics analysis, peer code reviews, unit testing, code coverage analysis, traceability, and other software testing practices.

A/B testing
A/B testing is a method of running a controlled experiment to determine if a proposed change is more effective than the current approach. 
Customers are routed to either a current version (control) of a feature, 
or to a modified version (treatment) and data is collected to determine which version is better at achieving the desired outcome.

Concurrent testing
Concurrent or concurrency testing assesses the behaviour and performance of software and systems that use concurrent computing, 
generally under normal usage conditions. 
Typical problems this type of testing will expose are deadlocks, race conditions and problems with shared memory/resource handling.

Conformance testing or type testing
In software testing, conformance testing verifies that a product performs according to its specified standards. 
Compilers, for instance, are extensively tested to determine whether they meet the recognized standard for that language.

Output comparison testing
Creating a display expected output, whether as data comparison of text or screenshots of the UI, 
is sometimes called snapshot testing or Golden Master Testing unlike many other forms of testing, 
this cannot detect failures automatically and instead requires that a human evaluate the output for inconsistencies.

(wikipedia)

#### What is the difference between white box, grey boy and black box testing?
user-level_: black-box
developer-level_: white-box

White-box Testing. Tests are written in full access to the test object internal structure or implementation.
    in opposite, 
Black-box Testing. Test are written from the user level, whereas the code is invisible for a tester, test object 
    reachable through the public api.
Grey-box Testing. As presumable from the name; tests are written within the knowledge of the internal architecture,
but interacting with the object from the user level .

#### What is the difference between UAT (User Acceptance Testing) and System testing?
System test aim the system or product behavior and capabilities. Objects of tests are the how the system perform
those tasks (functional), and how behave during execution (non-functional)
(-verification-)

UAT aim to validate how the product or a component fulfill the requirements and 
how can a user perform processes, objective is how the product fulfill the needs from a user view.

#### Mention the differences between Regression Testing, Smoke Testing and Retesting?
Smoke Testing. Minimal effort to prove that the software functional. Can reveal really basic defects.

Retesting. After a bug or issue has been fixed, test cases - where this particular defects were encountered -
are re-executed to prove the operation successness. Further test cases may be necessary if the issue fixing are 
involved new functions, methods, modules etc.
 
Regression Testing. After major changes or upon new versions, changing functionality or capabilities etc, 
regression test is needed to ensure the software has preserved integrity, usability, functionality and capability  
as before.

#### What is risk-based testing, whats the point of it?
RBT aim to prioritize the tests, calculate the risk of failure from the component importance and the likelihood
of the failure.
Point is, to reduce the wide range of possible tests, to focus on the effective testing. As the 
Seven Testing Principle say: exhaustive testing applying on every combination and covering every detail
usually impossible.

#### What is the difference between Static and Dynamic Testing?
Static testing does not involve the execution of the code, mostly manual examination of the work product
and code review, analysis often done with automated tools, important part of security testing.
Aim the system consistency and internal quality.
Find defects directly rather than searching the root of a failure. 

Dynamic testing can involve much or less execution from a basic part of code to whole system-wide execution.
Aim the system visible behavior.

#### Compare V-modell, Waterfall, Agile from testing perspective!
V-Modell. Test and development goes hand in hand.

Waterfall. Test phase coming after the work product is done, at the very end. 

Agile. Scream for change-related testing, confirmation- and regression-testing
tdd
bdd
kdd
#### What would you test in case of a simple webshop purchasing function (put items to cart, buy them)? 
#### Plan and reason your tests.
White-box Tests:
--> test every method required for a component to fulfill it's purpose
    component: 
        -cart: 
            -how set the content:
                -identifying the product
                -where and how store it (if store)
                -how set the rendering information
                -how pass forward
        -DB:
            -how is DB configured:
                -CRUD operations
                -input
                -query
                -output

Functional Tests:
--> test every component about the workflow they supposed to done
    component: 
        I would test the cart with amounts: normal, zero, huge and negative 
        I would test the DB how it handle the incoming data
    component-integration:
        I would test how the DB reflect the changes in the cart
    system:
        I would test with automated tests how the cart handle the purchase
    system-integration:
        I would test with automated tests how the cart pass the purchase to the DB
    acceptance:
        I would test with manual tests with user

Non-functional Tests:
--> test every component performance and/or usability apart and together
    component:
        cart: 
            -performance: automated: how the cart capture the input from user and pass it forward
        DB: 
            -performance: automated: how DB perform data change
    component-integration:
        -usability: manual: how user can handle the process from the step where items are chosen and present in the cart
    system:
        -performance: automated: what resource need for a shopping workflow
            starting from cart, with various amount of items
    system-integration:
        -performance: automated: what resource need for a shopping workflow
            starting from login (or from start page), with various amount of items
    acceptance:
        -usability: manual: how user can handle the process from beginning
        
change-related Tests:
--> run automated (except user acceptance) on every change, after a feature is done or some changes are done
    component-integration:
        automated: pipeline with specific branches or test cases
    system-integration:
        automated: pipeline with all branches or test cases
    acceptance:
        automated: smoke test: complete process from the user view
        manual: UI test with user

### Reporting, Bugs

#### What steps would you follow when you find a defect?
Examine every circumstances before report
#### Talk about common test reports, and about their details.
#### What does a bug report contains?
summary
environment
is reproducible
how reached-what expected
#### How would you prioritize a bug?

### Test Automation, Selenium

#### Which testcases should be be automated and which shouldn't?
should: regression 
DDT

#### Describe a good automated test!
blocks are reusable, robust, configurable

#### What is Selenium, Selenium IDE, Selenium WebDriver?
Selenium is the framework, 
IDE is a direct js implementation to interact with browser, can record and automate tests, speak with the browser on selenese,
WebDriver is the successor of RemoteControl, accept instructions on selenese or through the client API, has implementation 
in java, python, php, ruby, c#

#### How can be web elements indentified?
They can be identified through the html they reside. ID, class, name, tag, linkText, partialLinkText, cssSelector and xPath.
WebDriver capable to scan through the html source, and find an element through one of it's attributes or directly 
through the place with xpath.

#### How can you wait for elements, what can go wrong? Collect possible errors and root causes.
Explicit and implicit and fluent waits are applicable. 
Implicit wait applicable on a script, giving a fixed amount of time in between the script should finish or fail.
Explicit wait is the most common used class (on my side), it can be equipped with an object to wait and a circumstance
how to wait for it.
Fluent wait is a kind of marriage from the above two but with extra features. It can be configured how long to wait, 
the frequency to check the condition and a condition how to find the element.

The most commons are:

NoSuchElementException - the given search context does not find the element, root can be typo or the classifier does not exist.
StaleElementException - the stored element reference has been refreshed, maybe the page was reloaded or some js has modified it after it was found firstly.
TimeOutException - some not specified problem has occurred and the given time amount to find an element has expired without success.
ElementNotInteractableException - for some reason the element found, but command not applicable on it.
ElementNotVisibleException - for some DOM effect the element is found in source but not visible.
WebDriverException - some action tried to performed after driver has been closed.

#### Compare POM and Keyword Driven Testing!
POM
stores the test object in a form of an object. 
As an object it is also can be equipped with some or more methods to interact with the elements.
From the AUT abstracted object -> page object modell
tester should interact with the site through the POM model

Reusability: as the elements belongs to the site one POM is not usable for many sites.
    With proper designing the POM can be modular so methods are reusable after the specific POM has been created. 
Maintainability: easy to maintain as the elements and methods reside in one class (or more clearly separated classes)

KDT
is an extensible library to operate with webDriver on a page.
methods are stored as key - value pairs, where 
key: is a string which is called
value: is a method reference which is executed after calling the proper keyword.

Reusability: keywords and the belonging library are widely usable with the proper element location strategy very powerful
    tool to quick set up and interact with browser
Maintainability: as common library for eventually more test project, it is easy to mess up with the keywords.

#### Whats the difference between TDD and BDD?
TDD is very closely coupled with AGILE methodology. The development done in cycles.
First the test case is written. Then run test and refactor till all green: the feature is developed;

BDD is a very user friendly or stakeholder friendly approach to specify the requirements. A living language,
based on keywords, such as: Given, When, Then.

#### What is API testing and why would you use that?
Calls on the API endpoints then compare the raw data with the rendered one.

Personally I am using API calls to ensure that the data provided by the site are corrects. 
With that approach can be said if the site and browser render correctly the given data.
It is not good to verify that the application bringing the correct behaviour or using the proper logarithm. 

#### What is Data Driven Testing and why is it useful?
The tests are organized around a various situations, with many inputs.
Extremely ideal approach for input fields, or any point where user able to handle data to the application.
Or when is needed the AUT to being tested under various circumstances.

Data can be stored in text file, cvs, excel... 
The testmethod then run as a suite as many times as many data has found.

#### What are the challenges and best practices with dynamically loading web elements?
WebDriver has an extremely useful tool, the WebDriverWait class. With it's wait library.

Challenges are: 
the elements loaded after the document ready state -> no such element 
the elements are modified by the DOM -> stale element

Best practices: wait by every step, even custom wait, try-catch block

#### What are the challenges of Mobile Test Automation?

### Advanced Topics

#### What is the difference between CI and CD?
#### Describe a Continuous Delivery!
#### Compare 2 popular CI systems, one of them should be Jenkins!
#### What is Docker, why is it useful?
#### Compare 2 popular Test Automation IDE, one of them should be Katalon Studio!