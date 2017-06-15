# Assert Expectations

> Do test methods make meaningful assertions about expected behavior resulting from test actions?

Many tests in our current test code arrange state and act on target classes, but don't confirm that the expected behavior of the target class has actually occurred.

Assertions are the heart of unit testing. They allow us to prove that our code performs the way we expect. They also allow us to document the contract of our code, by demonstrating how the target class will react to different inputs.

"Assert Expectations" is the final part of the [Arrange/Act/Assert](https://github.com/testdouble/contributing-tests/wiki/Arrange-Act-Assert) pattern. Use of this pattern is highly recommended for test classes.

All test methods must assert some behavior. **Assertions must be meaningful**. A meaningful assertion shows something specific about your code. [It must be clear](./1-document.md) that your assertion is relevant to [the action you have performed](./3-act.md) in the test method.

We recommend that each test method contain a single assertion. This encourages developers to [exercise one concept per test](./9-one-concept.md). However, test methods can contain more than one assertion as long as both assertions are still testing one concept. For example, you may wish to use two assertions to prove that a single method call mutates two fields on the object being tested.

Some developers like to extend the Arrange/Act/Assert pattern to Arrange/**Assert**/Act/Assert, to confirm that state has been instantiated correctly or to highlight some important part of state arrangement for a future reader. If you're comfortable with this style, go ahead and use it. Just don't go overboard!


## Examples


### Useless assertions

``` java
@isTest
public class Model_CoffeeMaker_Test {
    static testmethod void testMethod() {
        Model_CoffeeMaker maker = new Model_CoffeeMaker(20) // 20 ounce capacity
        System.assert( maker.pourCoffee() != null );
    }
}
```

Assuming the test in `Model_CoffeeMaker_Test` passes, the only things we know about `Model_CoffeeMaker.pourCoffee()` is that it:

1. Does not raise an exception, and
2. Does not return `null`.

Almost anything else could be happen when `.pourCoffee()` is called. The assertion here is not specific enough; It should tell us something precise about the result of the method call.


### Meaningful assertions

Here are two simple ways to ensure your assertions are meaningful:

- Try to assert what the return valus **is** (e.g. `System.assert(x == 3)`) rather than what it is not (e.g. `System.assert(x != null)`).
- The assertion should be specific enough to fail if the target class's public interface changes.

It's easy to write meaningful assertions with these guidelines in mind. Let's write a new method for the test class above.

``` java
@isTest
public class Model_CoffeeMaker_Test {
    // ... other test methods snipped

    static testmethod void pourCoffee_20oz_transfers8ozToNewCup() {
        // Arrange
        Model_CoffeeMaker maker = new Model_CoffeeMaker(20) // 20 ounce capacity

        // Act
        Model_Coffee cup = maker.pourCoffee();

        // Assert
        System.assert( cup.getLiquidAmount() == 8 );
        System.assert( maker.getLiquidAmount() == 12 );
    }
}
```

This test is clear about what `pourCoffee()` does. We can even read the test as a kind of documentation or example of how the method works. Imagine the same test, but with the Assert clauses replaced with `!= null`. Much less clear, right?

Note that this method only tests one aspect of `pourCoffee()`'s behavior. For example, what would have happened if `Model_CoffeeMaker` [were instantiated with fewer than 8 ounces of liquid](./6-valid-invalid.md)? This test doesn't know or care--checking that behavior [is the responsibility of another test](./9-one-concept.md).

## To receive credit for this objective: 

1. Test methods must make meaningful assertions about the result of test actions.