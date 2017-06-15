# Test All Branches

> Does the test class make a good effort to test all code branches? Does the test class exercise all public methods in the target class?

Test methods should test all logic branches in the target class. This rule is critical in cases where different logic branches can execute vastly different computations.

Test classes should test all public methods in the target class. It doesn't matter if your test class has already reached 75% code coverage; **all public methods must be tested**.

We are only concerned with testing the public interfaces of target classes. This means that private methods don't need to be tested specifically (by elevating the access level to `public`). 

If you notice that a private method returns tricky results, feel free to target that method with some tests exercising its associated public method. However, beware of overtesting private methods. Private interfaces can change without notice, so don't assemble state specifically to trip up private methods. Think about testing from the perspective of the public interface.


## To receive credit for this objective: 

1. Test methods should test all logic branches.
2. Test classes should fully test all public methods in the target class.