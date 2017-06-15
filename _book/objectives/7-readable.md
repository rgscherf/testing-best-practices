# Write Readable tests

> Do test methods follow clean code practices? Do test methods display the same use of conventions, factoring and abstractions expected in other source code?

Test code is source code. Your test classes should follow all of our coding best practices.

Remember that each test method should read clearly to somebody who had never seen your test class or the target class before. Variable names should be descriptive. Code should be tidy with unimportant details (such as routine object generation) factored away into utility methods.

Because test code can be repetitive, pay special attention to refactoring code that appears in related test methods. Group this code together--it will make your tests more readable and more maintainable.

Use good taste. Don't overabstract your code. Every test method should still display a top-level Arrange/Act/Assert pattern.

## To receive credit for this objective: 

1. The test class reads cleanly to someone who has never seen the source code before.
2. The test class follows our organization's coding conventions.
3. The test class makes good use of abstraction.