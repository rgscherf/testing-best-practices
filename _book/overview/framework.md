# Framework Overview

Because it is notoriously difficult to measure code quality using machine tools, we have decided to grade our new tests using a human assessor and a simple evaluation framework. 

Each objective in the evaluation framework is a common-sense best practice for unit testing. Together, the objectives ensure that our tests will be meaningful, maintainable, and readable. 


## How the framework is organized

The framework is divided into nine objectives. Each objective is a possible attribute of your code, independent from the others.

Objectives are grouped into three themes. Themes describe the conceptual stages of writing tests: initiate code -> run tests -> (re)format tests. 

When it comes to assessing your code, you **must** achieve all six of the objectives under the *Initiate Tests* and *Run Tests* themes. Achieving the remaining objectives, under the *Format Tests* theme, is optional but highly recommended.


## Framework definition

All testing objectives are booleans applied to your entire test class. The assessor will look at all of the test methods you've written, and decide whether each objective has been met by the test class as a whole. If that seems imprecise, it's because the system is designed to help us look at test quality across the entire code base.

Testing objectives are described below. Much more detail about each objective can be found in subsequent chapters of this document.

| Theme | Objective | Description |
|---|---|---|
|Initiate Tests | Document Your Tests | Are tests methods and classes documented at standards equivalent to other source code?|
|Initiate Tests | Arrange Data | If state is required for the test, is it arranged in an organized way? Is state generated using TestFactory_* classes where possible? |
| Initiate Tests | Act on Data | Do test methods perform some action on the target system beyond instantiating classes? |
| Run Tests | Assert Expectations | Do test methods make meaningful assertions about expected behavior resulting from test actions? |
| Run Tests | Test All Branches | Does the test class make a good effort to test all code branches? Does the test class exercise all public methods in the target class? |
| Run Tests | Test Valid and Invalid Inputs | Do test methods make an effort to pass bad or unexpected inputs to the target class? Do test methods exercise exceptions raised by the target class? |
| Format Tests | Write Readable Tests | Do test methods follow clean code practices? Do test methods display the same use of conventions, factoring and abstractions expected in other source code? |
| Format Tests| Use Good Test Names | Are there multiple tests? Do the names of test methods describe what the test does? |
| Format Tests | Test One Concept at a Time | Are there multiple tests? Does each test have a clear goal? |