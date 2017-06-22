# Test Valid and Invalid Inputs

> Do test methods make an effort to pass bad or unexpected inputs to the target class? Do test methods exercise exceptions raised by the target class?

All public methods in the target class should be tested with a set of both valid and invalid inputs. You may have to use your imagination. To start with, the following inputs should be tried:

- An expected value
- A null value
- For string inputs, an unexpected (if the method expects a magic string) or long value
- For collection types, an empty collection
- For collection types, a small (< 10 entries) collection 
- For collection types, a large (> 200 entries) collection 
- For reference types, an object with `null` fields that the target method will access

For methods which don't take inputs, examine the target method's source code and imagine situations where the method makes assumptions about its environment that might not be true. These scenarios may include:

- Does the method expect certain information to exist in the database?
- Does the method expect another field to be instantiated on itself before it is called?
- Does the method make a network call that might fail?

Try your best to create circumstances that will raise exceptions. Knowing what kinds of inputs the target class will accept is a vital part of keeping our code robust. It is also useful when using tests as documentation.

If you encounter an unexpected return value (such as `null` or an exception) as a result of any of these inputs, your next move depends on the state of the target method.

- If you are currently designing the target method, consider whether this unexpected value makes sense as a return value. Will users of this method agree that the return value makes sense? If not, change the method accordingly.
- If you are writing the test class at a later time, perhaps long after another developer has written the target method, consider the result to be intended behavior unless it truly looks like a bug.


## How to test exceptions:

Here is a simple construct for testing exceptions:

``` java
public class Model_CoffeeMaker_Test {
    // ... other test methods snipped

    static testmethod void pourCoffee_4oz_raisesNotEnoughLiquidException() {
        // Arrange
        Model_CoffeeMaker maker = new Model_CoffeeMaker(4) // 4 ounce capacity

        // Act
        try {
            // pourCoffee() removes 8 ounces from maker.
            Model_Coffee cup = maker.pourCoffee();
            System.assert ( false );
        } catch (NotEnoughLiquidException e) {
            // Assert
            System.assert( true );
        }
    }
```

If `pourCoffee()` doesn't raise an exception, execution will move to `System.assert(false)` and fail the test. 

If `pourCoffee()` raises an exception, execution moves to the `catch` block. A `NotEnoughLiquidException` is caught and executes `System.assert(true)`, causing the test to pass. Any other exception will escape the `catch` and cause the test to fail.

This pattern makes your intent explicit. You intend to raise a specific exception with the call to `pourCoffee()`, and the test won't pass under any other circumstances.

## To receive credit for this objective: 

1. The target method should be exercised with an exhaustive range of valid and invalid inputs. Where appropriate, the target method's environment should be adjusted to demonstrate its behavior in unexpected conditions.
2. The test class should raise exceptions in the target class whenever possible.