# Use Good Test Names

> Are there multiple tests? Do the names of test methods describe what the test does? 

The names of test methods should describe what the method does. A test method named `testMethod1` doesn't contain any information about the test. A test method named `someMethod_withNullInput_returnsFalse` is an excellent summary of what the test does.

Why are test names important? When running tests in most editors, the test results are sorted by test name. Running your tests and receiving a list like the following:

```
SUCCESS: getGroupDevNameMap_always_isNotEmpty - in 102ms
SUCCESS: getGroupDevNameMap_always_returnsEveryQueueTypeGroup - in 87ms
SUCCESS: getGroupDevNameMap_always_returnsSomeExpectedKeys - in 144ms
SUCCESS: queryCaseAssignmentGroupID_expectedGroupDoesntExist_raisesQueryException - in 437ms
SUCCESS: queryCaseAssignmentGrpID_always_returnsExpectedGroup - in 132ms
SUCCESS: queryRealTimeGroupID_expexpectedGroupDoesntExist_raisesQueryException - in 113ms
SUCCESS: queryRealTimeGrpID_always_returnsExpectedGroup - in 87ms
```

... makes it easy to figure out what's wrong if your tests start to fail.

## Test naming convention

You are highly encouraged to use the following convention for test names:

`(method name)_(conditions for the test)_(expected result)`

Each part of the name is separated by an underscore, and words within each part are camelCased.

Here are some examples of test names:

```
getAssetByAccountId_withNullInput_returnsEmptyList
onAssetChange_isInsertIsNull_raisesNullPointerException
getAllQueues_always_returnsOnlyGroupsOfTypeQueue
```

## To receive credit for this objective: 

1. The test class has multiple methods.
2. Test names are descriptive, including: method being tested, test conditions, and expected result.