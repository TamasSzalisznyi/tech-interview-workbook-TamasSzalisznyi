# Test automation questions

### Testing Basics (ISTQB related)

#### What is the purpose of testing? What is not?
Testing process aiming:
 - to reveal and prevent as much as possible known or hidden defects and bugs
 - to build and improve the overall quality of the product
 - to reduce the possibility of failures caused by internal errors
 - show how the software working under certain conditions.
<br>

Test process would not:
- prove that the software working well under every circumstance, 
- prove that the product is bug and failure free
- In my opinion, the testing should not make acceptance criteria (except in TDD).

To set up the requirements and to define when meet the product with stakeholders demand (or user demand) is a part of <br>
the software design. A test can be good, but the program bad, if there are requirement gaps.

#### What is the difference between Defect, Error, Failure?
Error: can come from many circumstances. <br>
Developer made a mistake and stay in the code, or some other way the codebase is corrupted, or maybe <br>
there are design or requirements failure.

Defect: an error can lead to failure but not necessary, only certain circumstances lead to failure. <br>
If the part of the code containing the defect, is executed, or the environment changed it can lead to failure.

Failure: the inability of a system or component to perform its required functions.
- produces an incorrect result or 
- does not perform the correct action or 
- does not perform any action. 

#### What are the testing principles?
1. Testing shows the presence of defects, not their absence.
2. Exhaustive is impossible. By risk analysis and test techniques focus the test effort.
3. Shift left - join the testing process early in the software development lifecycle.
4. Defects cluster together. 80%-20% rule. <br>
Common experiences that critical parts (20%) containing the most defects (80%).
5. Pesticide Paradox. Executing the same test does not find more defect. <br>
(Except regression test. Regression test has a beneficial outcome to execute over and over.)
6. Testing is context dependent. There is no universal test design pattern for every product.
7. Absence-of-errors is a fallacy. Good tests are not guarantee for a successful or flawless product.

#### What is unit testing? Who is responsible to write unit tests?
Unit test cover a piece of code on class level. <br>
Written by usually the developer who is in white-box situation, 
to ensure that this build block working properly and independently.

#### What are Test Levels, what is the difference between them?
(component-[/unit-], integration-, system-, acceptance-testing)

Test levels are group of test activities performed in relation with the development lifecycle.
Grouped by (2.2)
the objective, 
the test basis
the test object
contextual factors (1.4)
Requiring suitable test environment.
1. Unit testing:
- The smallest testable portion of code. This kind of testing helps to test each module separately.
- The aim is to test each part of the software by separating it. 
- It checks if that component has fulfilled the functionality or not. 
- This kind of testing is performed by developers.

2. Integration testing:
Integration means combining. In this testing phase, different software modules are combined and tested as a group<br>
- To ensure, that newly added module is working properly and ready for system testing.
- Check the data flow from one module to other modules.

3. System testing:
System testing is performed on a complete, integrated system.<br> 
- It allows checking system's compliance as per the requirements. 
- It tests the overall interaction of components. 
- It can involve load, performance, reliability and security test.
- Often the final test to verify that the system meets the specification. 
- It evaluates both functional and non-functional testing.

4. Acceptance testing:
Acceptance test executed to find if the product meet with acceptance criteria.<br> 
- Basically done by the user, customer or stakeholders. 

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
    - Continuous testing is the process of executing automated tests as part of the software delivery pipeline 

#### What is the difference between white box, grey boy and black box testing?
White-box Testing. Tests are written in full access to the test object internal structure or implementation.<br>

Black-box Testing. Test are written from the user level, whereas the code is invisible for a tester, test object 
reachable through the public api or as product.

Grey-box Testing. Tests are written within the knowledge of the internal architecture,
but interacting with the object from the user level .

#### What is the difference between UAT (User Acceptance Testing) and System testing?
System test aim to the verification of the system or product behavior and capabilities.<br>
- how the system perform those tasks (functional), and 
- how behave during execution (non-functional)

UAT aim to validate how the product or component fulfill the requirements and how can a user perform processes.
- how the product fulfill the needs from a user view.

#### Mention the differences between Regression Testing, Smoke Testing and Retesting?
Smoke Testing. To prove with minimal effort that the object functional, and in the state for further test process.

Retesting. After a bug or issue has been fixed, test cases - where this particular defects were encountered -
are re-executed to prove the operation successness. 
 
Regression Testing. After major changes or upon new versions, changing functionality or capabilities etc.<br>
To ensure the software has preserved integrity, usability, functionality and capability as before.

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
V-Model. Test and development goes hand in hand.

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

the process of executing automated tests as part of the software delivery pipeline 
to obtain immediate feedback on the business risks associated with a software release candidate.
Continuous testing includes the validation of both functional requirements and non-functional requirements; 
the scope of testing extends from validating bottom-up requirements or user stories to assessing the system requirements associated with overarching business goals.
