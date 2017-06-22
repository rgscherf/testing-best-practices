# Act on Data

> Do test methods perform some action on the target system beyond instantiating classes?

Many of our current tests simply instantiate the target class, relying on constructor code (and private methods called within) to reach >75% code coverage.

The framework requires that tests perform specific actions on the target class. This means calling public methods on the target class. Preferably each test will [only call one method](./9-one-concept.md) and then [check its result](./4-assert.md).

"Act on Data" is the second part of the [Arrange/Act/Assert](https://github.com/testdouble/contributing-tests/wiki/Arrange-Act-Assert) pattern. Use of this pattern is highly recommended for test classes.

This objective sits between [arrange](./2-arrange.md) and [assert](./4-assert.md). Together, all three objectives should tell a clear 'story' about what you are trying to test and what you expect to happen as a result. Most of the time, the *act* part of the story should be a single method call.

## To receive credit for this objective: 

1. Test methods should perform specific actions on the target class.
2. Actions performed on the target class should be easily identifiable and should be performed after arranging state.