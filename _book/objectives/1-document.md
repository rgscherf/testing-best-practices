# Document Your Tests

> Are tests methods and classes documented at standards equivalent to other source code?

Your code is meant to be read. It should display good use of method/variable names and clear logic that makes your intention clear. This isn't always possible, however--and when things get tricky, you are required to comment your code. 

## To receive credit for this objective: 

1. Code should be clearly understood by a reader who has never seen your test class (or the class being tested) before. If this is not possible--[see objective 7](./7-readable.md)--then you are required to explain your code using comments. If your code doesn't require comments to explain what's happening, awesome work! You will still receive credit for this metric.

2. All test methods should have header comments which include the test method name, author, creation date, and other metadata. The format is identical to the header comment template we use in source code. The template is reproduced below--feel free to copy.

--- 

For your reference, here is the header template we use in our source files:

```
    /**
    |--------------------------------------------------------------------------
    |@method        methodBeingTested_testingScenario_expectedResult
    |--------------------------------------------------------------------------
    |
    |@description   under testingScenario, methodBeingTested should expectedResult.
    |
    |@created       5/31/2017
    |@createdBy     Your Name
    |@return        void
    */ 
```
