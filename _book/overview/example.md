# Example: Applying the Framework

Throughout this documentation we will revisit an imaginary class, `Model_Coffee`, which represents a cup of coffee. Here is an initial implementation of the class:

``` java
public class Model_Coffee {
    integer cupCapacity; // in ounces
    integer liquidAmount; 

    public Model_Coffee(integer size) {
        cupCapacity = size;
        liquidAmount = size; 
    }

    public void takeASip(integer sipSize) {
        integer liquidAmountAfterSip = liquidAmount - sipSize;
        if (liquidAmountAfterSip >= 0) {
            liquidAmount = liquidAmountAfterSip;
        } else {
            liquidAmount = 0;
        }
    }

    public void refillCup() {
        liquidAmount = cupCapacity;
    }

    public integer getLiquidAmount() {
        return liquidAmount;
    }
}
```

As a first try, here is the test class for `Model_Coffee`:

``` java
@isTest
public class Model_Coffee_Test {
    static testmethod void testMethod1 {
        Model_Coffee cup = new Model_Coffee(10);
        cup.takeASip(2);
    }
}
```

How does this test class stack up against our framework?

| Theme | Objective | Pass? | Explanation |
|---|---|---|---|
|Initiate Tests | Document Your Tests | NO | The test code is simple enough that comments are not required to explain it. However, the developer did not include required header comments.
|Initiate Tests | Arrange Data | YES | Data requirements to test `Model_Coffee` are simple. The developer instantiated everything required for this test in the class constructor.
| Initiate Tests | Act on Data | YES | A method was called on the `Model_Coffee` instance.
| Run Tests | Assert Expectations | NO | The test method does not expect a particular change to occur as a result of calling `takeASip()`. The test will pass as long as method invocation does not raise an exception. 
| Run Tests | Test All Branches | NO | The test class only tests one code path in `takeASip()`. The other `if` branch is not tested, and the `refillCup()` and `getLiquidAmount()` methods are not tested at all. 
| Run Tests | Test Valid and Invalid Inputs | NO | What happens if the argument to `takeASip()` is null? What happens if it is negative? What happens if it is 0? All of these scenarios should be tested.
| Format Tests | Write Readable Tests | YES | The test class is short and easy to follow.
| Format Tests| Use Good Test Names | NO | The test method's name should describe what is being tested. In this case, a name like `takeASip_sipLessThanCurrentAmount_returnsExpected` would let other developers know what is being tested without having to read the source code. Also, achieving this objective **requires that the test class include multiple methods.**
| Format Tests | Test One Concept at a Time | NO | While the test class's single method is only performing one operation, achieving this objetive **requires that the test class include multiple methods.**

Overall, `Model_Coffee_Test` scored **3/9** points. 

Of the objectives that must be met for the test class to be accepted (all of the objectives within *Initiate Tests* and *Run Tests*), `Model_Coffee_Test` scored **2/6** points. The test class would be sent back to its developer with feedback about how to improve the tests.

As you can see from the explanation of these scores, it would be easy to achieve a passing score of **6/6** for `Model_Coffee`. A perfect score of **9/9** is also very possible. Each of the objectives is easy on its own, and they get easier as more are achieved in the same class.

If you feel confident with the assessment framework, you feel free to jump in and start writing tests at this point. The rest of this guide gives more detail about each objective and additional considerations.
