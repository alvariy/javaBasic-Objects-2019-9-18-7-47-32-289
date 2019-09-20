# Overview

This repository is a part of the Java language training plan. Please read the following guidelines before start.

# Getting Start

## Basic Principals

Each repository contains a gradle java project with a number of unit tests. The initial state of all unit tests are *FAILED*. So the aim is to correct the failed test. Please follow the following steps to get the best experience:

* Read the test code and try to understand what it says.
* Trying to fix the test **WITHOUT RUNNING**. This is very important. Because once you run the test, you may find the failure message of the test telling you the expected result. That means you may lose the chance to figure it out by yourself. Note that you should **ONLY** be able to modify code within the **TODO AREA**. The code outside the **TODO AREA** is **NOT** changable.
* Run the test to examine if the fix is correct.
* Answer the following 4 questions after the test is passed.

The 4 questions are:

1. What is the knowledge point of the test? Where is the offical document to the knowledge point?
1. Why the test failed at first?
1. Why you corrected the test that way?
1. Do you have further questions on this knowledge point?

## Example

Let's take a look at an example:

```java
@Test
void should_pass_by_value() {
  int value = 5;

  tryingToUpdateValue(value);

  // TODO: please modify the following code to pass the test
  // <--start
  final int expected = 0;
  // --end-->

  assertEquals(expected, value);
}
```

First, read the test. From the title and code we can know that the test what to examine the behavior when passing an argument. We are not sure what `tryingToUpdateValue` does, so we can jump into its implementation:

```java
private static void tryingToUpdateValue(int value) {
  value += 2;
}
```

Now we have got the full context of the test. The argument is passed by value so the integer will be copied when passing into `tryingToUpdateValue`. Thus the value from the caller site will not change.

Notice that the todo area is in the test method. So we can modify codes within the todo area to pass the test:

```java
  // TODO: please modify the following code to pass the test
  // <--start
  final int expected = 5;
  // --end-->
```

Please note that not all todo areas are located in test method. And some todo area may have further restrictions, for example:

```java
  // TODO: You should not write concrete number here. Please find a property or constant instead.
  // <!--start
  final int maximumSymbol = 0;
  final int minimumSymbol = 0;
  // --end-->
```

The hint indicates that we should not write concrete number here. So I should not write `3` or `0xffffffff`, but write symbol (e.g. `Integer.MAX_VALUE`).

## Running Test

You could run unit tests with the help of IntelliJ. But it is also possible to run unit test via command line: `./gradlew build`.

If you just want to build your code without running test. Please use `./gradlew build -x test
`


should_point_to_the_same_object
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objects.html
- A typical Java program creates many objects, which as you know, interact by invoking methods. 
2.Why the test failed at first?
- I thought that both objects are not the same, that they are not similar in some ways.
3.Why you corrected the test that way?
- I used true value because sameReference object has the same value, or is the same object as objectReference.
4.Do you have further questions on this knowledge point?
- None


should_point_to_different_object
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objects.html
- That both Objects is not equal even if they have the same value
2.Why the test failed at first?
- I thought that both objects are the same, that they are similar.
3.Why you corrected the test that way?
- I used false value because gooDay LocalDate is not the same as sameDay even if they are similar in values
4.Do you have further questions on this knowledge point?
- Not sure on what is the difference between those two. 

should_initialized_to_default_value:
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- To know the default value of objects or classes if you return a non valued getter.
2.Why the test failed at first?
- I do not know what the default value of those methods of functions for their types.
3.Why you corrected the test that way?
- for int, the return values is 0, while for both String nad LocalDate the return value is null.
4.Do you have further questions on this knowledge point?
- none

should_pass_by_value:
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- To know if a variable would change its value globaly if you initiate a method.
2.Why the test failed at first?
- I thought that the value would change to 7.
3.Why you corrected the test that way?
- I realized that the value would not change globaly.
4.Do you have further questions on this knowledge point?
- none

should_pass_by_value_continued:
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- same as the first one but in Object.
2.Why the test failed at first?
- No failed test
3.Why you corrected the test that way?
- I realized that the object would not change globally.
4.Do you have further questions on this knowledge point?
- none

should_modify_internal_state:
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- By this case, the state was changed so the value of the instance changed.
2.Why the test failed at first?
- I thought that this is the same as a normal type
3.Why you corrected the test that way?
- I realized that the object state will change if you altered it in a method.
4.Do you have further questions on this knowledge point?
- none

should_choose_method_at_compile_time
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- By this case, the method returned a string "methodWithOneParameter(Object)".
2.Why the test failed at first?
- No test failed
3.Why you corrected the test that way?
- When I saw return methodWithOneParameter(Object)
4.Do you have further questions on this knowledge point?
- none

should_choose_the_most_specific_overload
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- By this case, the method returned a string "methodWithTwoParameters(String, Integer)".
2.Why the test failed at first?
- No test failed
3.Why you corrected the test that way?
- When I saw return "methodWithTwoParameters(String, Integer)"
4.Do you have further questions on this knowledge point?
- none

should_calling_another_constructor
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- By this case, you can use the values inside the class to be returned.
2.Why the test failed at first?
- No test failed
3.Why you corrected the test that way?
- When I saw name: "Untitled"
4.Do you have further questions on this knowledge point?
- none

should_get_initialization_ordering
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- Not sure what happened
2.Why the test failed at first?
- 
3.Why you corrected the test that way?
- 
4.Do you have further questions on this knowledge point?
- What happened?

should_get_message_of_var_length_parameters
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- Append arguments 1,2,3 to string
2.Why the test failed at first?
- no test failed
3.Why you corrected the test that way?
- the method or function used a for each loop to append or concat new lines for 1,2,3
4.Do you have further questions on this knowledge point?
- none

should_get_message_of_var_length_parameters_2
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://docs.oracle.com/javase/tutorial/java/javaOO/objectcreation.html
- Append Obect {1,2,3}
2.Why the test failed at first?
- I thought that it would return a value of {1,2,3}\n
3.Why you corrected the test that way?
- the method or function used a for each loop to append or concat new lines for 1,2,3
- Also, new Object[] {1, 2, 3} is the same as the first method should_get_message_of_var_length_parameters but in different form or arguments or parameters
4.Do you have further questions on this knowledge point?
- none

should_be_derived_from_object_class:
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- https://www.oracle.com/technetwork/articles/java/javareflection-1536171.html
- Obejct.class 
2.Why the test failed at first?
- I do not know what is the expected output
3.Why you corrected the test that way?
- As I see the test failure, I saw that it is expecting a java object and I saw that SimpleEmptyClass might be an Object.class
4.Do you have further questions on this knowledge point?
- none

should_call_super_class_constructor:
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- Used of extends in classes
2.Why the test failed at first?
- No Test Fail
3.Why you corrected the test that way?
- As I see the extends SuperClassWithDefaultConstructor in DerivedFromSuperClassWithDefaultConstructor the function first used the methods in SuperClassWithDefaultConstructor then used the functions inside DerivedFromSuperClassWithDefaultConstructor
4.Do you have further questions on this knowledge point?
- none

should_call_super_class_constructor_continued
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- That default methods inside a class will be triggered
2.Why the test failed at first?
- No Test Fail
3.Why you corrected the test that way?
- Because the function or methods that has no parameters will be triggered and the one with a parameter int also, will be triggered
4.Do you have further questions on this knowledge point?
- none

should_call_super_class_constructor_more
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- Not sure
2.Why the test failed at first?
- I thought that the default methods with no parameters will be triggered
3.Why you corrected the test that way?
- the test was expecting 2 values, so I put the return value of the methods with String arguments
4.Do you have further questions on this knowledge point?
- Why are the funtion with no arguments not triggered?

should_call_most_derived_methods:
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- Not because the main Class is BaseClassForOverriding it will call first its function
2.Why the test failed at first?
- No test fail
3.Why you corrected the test that way?
- because of new DerivedFromBaseClassForOverriding();
4.Do you have further questions on this knowledge point?
- None

should_call_super_class_methods
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- Used again extend to call the function of BaseClassForOverriding
2.Why the test failed at first?
- No test fail
3.Why you corrected the test that way?
- because of the concatination inside DerivedFromBaseClassForOverridingCallingSuper
4.Do you have further questions on this knowledge point?
- None

should_use_caution_when_dealing_with_array_type:
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- Not the same class
2.Why the test failed at first?
- No test fail
3.Why you corrected the test that way?
- Not the same class to be compared
4.Do you have further questions on this knowledge point?
- None

should_not_make_you_confused
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- Do not be confused because the Variables class is different with the instantiated class
2.Why the test failed at first?
- No test fail
3.Why you corrected the test that way?
- because of new NestedDerivedClassWithName()
4.Do you have further questions on this knowledge point?
- None

should_not_make_you_confused_2
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- Do not be confused because inside the class, there are no functions.
2.Why the test failed at first?
- No test fail
3.Why you corrected the test that way?
- because of extends BaseClassWithName
4.Do you have further questions on this knowledge point?
- None

should_use_instance_of_to_determine_inheritance_relationship
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- a static nested class is essentially a normal class that has just been nested inside another class. Being static, a static nested class
2.Why the test failed at first?
- Because I though that the base class is not nested because it is a base calss with no extends
3.Why you corrected the test that way?
- because of instanceof NestedDerivedClassWithName 
4.Do you have further questions on this knowledge point?
- None

should_use_instance_of_only_in_inheritance_relationship
1.What is the knowledge point of the test? Where is the official document to the knowledge point?
- a static nested class is essentially a normal class that has just been nested inside another class. Being static, a static nested class
2.Why the test failed at first?
- Because I though that the base class is not nested because it is a base calss with no extends
3.Why you corrected the test that way?
- because of instanceof NestedDerivedClassWithName 
4.Do you have further questions on this knowledge point?
- None