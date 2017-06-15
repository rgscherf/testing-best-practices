# Arrange Data

> If state is required for the test, is it assembled in an organized way? Is state generated using TestFactory_* classes where possible?

The first step in testing any object-oriented code is assembling state required for the test. Sometimes this is simple, as in (the framework overview example)[../overview/example.md]. Sometimes it is much more complicated, requiring multiple levels of objects to be generated.

The framework requires that state assembly is logical and organized. In addition, where possible, assembly should be factored away using the TestFactory_* family of classes. These utility classes greatly simplify the generation of complex object heirarchies, and are more likely to be bug-free than code written specifically for your test class.

"Arrange Data" is the first part of the [Arrange/Act/Assert](https://github.com/testdouble/contributing-tests/wiki/Arrange-Act-Assert) pattern. Use of this pattern is highly recommended for test classes.

## To receive credit for this objective: 

1. Required state should be arranged at the beginning of your test method, before you begin acting on target object(s). **There should be a clear separation between creating the test environment and acting on the test environment**. 
2. State should be generated using the TestFactory_* classes whenever possible. This rule may not apply if an appropriate method(s) do not exist on those classes (e.g. no methods to generate a certain object, no methods to generate a certain object for bulk operations).