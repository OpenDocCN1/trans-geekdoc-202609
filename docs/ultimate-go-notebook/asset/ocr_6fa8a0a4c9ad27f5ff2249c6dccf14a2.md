# Chapter 7: Testing

In this chapter, I will learn how to write tests in Go and the integrated support provided by the language.

# 7.1 Basic Unit Test

One of the best things about Go is that the language defines what a unit of code is. A unit of code is called a package and it's represented as a folder in my source tree. The compiler builds a static library from each folder and then links them all together to the final application binary.

When I talk about a unit test, I am talking about testing code from a single package. Usually exported function by exported function. This doesn't restrict me from hitting external systems like a database or a set of web services to perform the tests. This is different from an integration test which will run across multiple packages.

There are no rules or idioms when writing a unit test. What's important is that a company or least a team develops a set of consistent idioms and rules for writing a test. This way anyone can review a test result and maintain the code in a consistent way.

One thing I need to decide upon is how verbose I want the tests to be. Do I want a test that only provides output when something fails, or do I want an indication as well that things are passing.

The standard library and the Go frontend has everything I need to write a test. It starts with creating a file with the _test.go naming convention inside the package I want to test, and then adding test functions by using the word Test with a capital T for each function.

Listing 7.1

These are examples of test functions I could declare in the sample_test.go testing file. It's important that the first letter following the word Test in the function name starts with a capital letter. If I don't, the testing tool won't see the function as a test