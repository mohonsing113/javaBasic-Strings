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


## Summary

* should_be_immutable(), all_modification_method_will_create_new_string(), will_create_new_string_when_concat()
1. String is immutable, new string is create after any modified https://docs.oracle.com/javase/7/docs/api/java/lang/String.html
1. It expect a Optional empty
1. The 2 strings are not same, so = false
1. NO


* should_taken_string_apart(), should_taken_string_apart_continued()
1. Use substring method from String class https://docs.oracle.com/javase/7/docs/api/java/lang/String.html
1. It expect null
1. Use substring to taken a String apart
1. NO

* should_break_string_into_words(), should_break_string_into_words_customized
1. Use split method from String class https://docs.oracle.com/javase/7/docs/api/java/lang/String.html
1. It expect null
1. Use split to taken a String apart by space or /
1. NO

* should_create_ascii_art()
1. Try to use StringBuilder to create a String https://docs.oracle.com/javase/7/docs/api/java/lang/StringBuilder.html
1. It expect null
1. The String can be created more dynamically, and easier for further extension
1. NO

* should_calculate_checksum_of_a_string()
1. Create checksum by getting the sum of each string char
1. It expect 0
1. By converted the String to char array, then calculate the sum
1. NO

* should_convert_unicode_escape()
1. Create String by unicode escape
1. It expected null
1. Using unicode escape directly
1. NO

* should_reverse_a_string()
1. Reverse a String
1. It expected null
1. Using StringBuilder to erverse a string due to it has such a function
1. NO

* should_compare_string_with_different_cases()
1. Try to use string.equals to check 2 Strings' values are equal
1. They expect empty
1. they are not same due to case different so upperCased.equals(lowerCased) = false. If ingore case, upperCased.equalsIgnoreCase(lowerCased) = true
1. NO

* should_format_string()
1. Study the use of String.format
1. It expect null
1. make the result like the intened formatted one.
1. NO