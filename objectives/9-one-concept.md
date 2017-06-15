# Test One Concept at a Time

> Are there multiple tests? Does each test have a clear goal? 

Each of your tests should prove one, and only one, specific behavior about the target class.

[Elsewhere](./4-assert.md) this documentation discussed the problem with tests like `System.assert(x != null)`. This test was too broad: it would pass when `x` took on almost any value. An example refactored this test into a more specific version.

Successful test classes will include multiple specific tests like the one demonstrated above. Each test method will pick a concept and test the target method against that concept. [See here for examples of specific concepts](./6-valid-invalid). Separating each concept into its own method, [with a descriptive name](./7-readable), creates a readable, maintainable test class.

You know you have a one-concept test when:

- You can give the test method a clear name (if the name contains the word 'and', you may have a problem!)
- Your test contains a single assertion or a small number of assertions testing related information.

## To receive credit for this objective: 

1. The test class has multiple methods.
2. Each test method proves one, and only one, specific behavior about the target class.