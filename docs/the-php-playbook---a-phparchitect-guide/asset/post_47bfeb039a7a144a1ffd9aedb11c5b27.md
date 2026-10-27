
## Chapter 2
### Test-Driven Development

Most developers who have been in software development for any length of time have heard the words “unit testing” used to describe a particular method of testing software that is in development. They may even have heard of a principle known as “Test-Driven Development”, which in a nutshell is the philosophy that a test should be written before any code is written for the actual project.

The problem with testing is that it is very much like following the speed limit: everyone knows they should be doing it, but very few people actually do (and the ones who insist on doing it annoy the rest of us). However, testing is not just an obnoxious roadblock to software development: it is a crucial component to the development and implementation of software.

Why are unit tests so crucial? As systems get larger and larger, two things happen: first, it becomes impossible for any single developer to fully and completely grasp the intricacies of the system at hand. Secondly, as this takes place, more developers are working on and refactoring existing code, making it almost a certainty that somewhere down the line, someone will make a change that renders the application unusable in some fashion (a regression).

Unit tests can help prevent this by showing you where and why code is failing. While unit tests cannot fix every bug or prevent every regression, they can point out flaws in the application logic or refactoring strategies before the flaws make it into production.

Before we can get started on this section, we must install PHPUnit. The recommended installation method is PEAR; installing from PEAR means that PHPUnit will automatically install its command line application as well as ensuring that PHPUnit is in the include path (unless we have modified the include path to drop the PEAR directory). Additionally, installing from PEAR means that we can update PHPUnit to the latest version easily, and Sebastian Bergmann (the author of PHPUnit) is regularly releasing upgrades and new features to PHPUnit, making upgrading well worth it.

Follow the instructions for installing PHPUnit¹ from PEAR. After installing PHPUnit, there are some terms that we should familiarize ourselves with. A unit test is a test that runs against a specific block of code - usually a function or a method. This unit test runs the block of code, and then makes assertions as to what the block of code should return - that is, the value, type, or behavior that should occur as a result of running the block of code.

Here is a complete unit test written for PHPUnit:

```
require_once 'PHPUnit/Framework.php';

class ArrayTest extends PHPUnit_Framework_TestCase {
    public function testIsArray() {
        $item = array();
        $item2 = false;
        $item2 = (array) $item2;
        $this->assertType("array", $item);
        $this->assertType("array", $item2);
    }
}
```

There are some things we should take note of in this test. First, the class name is ArrayTest; this employs the convention of naming test classes as *Test, and if you are testing a class (for example, a class called Login) you should name the test LoginTest.

All the test methods in our class are named test* (for example, we have testIsArray()). This is how PHPUnit finds the tests and executes them. Without this information, PHPUnit would not run our unit tests. PHPUnit uses reflection to determine which methods to execute.

Also note that the test class extends from PHPUnit_Framework_TestCase. This is the test case class, and contains all the methods necessary to properly generate and run test cases.

As previously mentioned, when beginning to write tests, it is tempting to write only a single method that tests your single point of entry and then determines if the whole class functioned properly. It is important that you avoid doing this; that is more akin to a “functional test” - that is, a test of the functionality. We want to test individual units of code - the methods themselves - meaning that we want to avoid writing functional tests and instead test “units”, typically methods.

This brief introduction should be a guide to writing tests; the PHPUnit manual is much more in depth and is up to date. PHPUnit is still in development; though Version 3.4 of PHPUnit was used in the writing of this book, changes may be made that could affect the accuracy of these guidelines.

### How to Test When Time is Not Allotted for It

Because testing takes extra time, many managers feel it is unimportant, and worse, may believe that it is “red tape” preventing them from getting the project shipped on time. This is not unusual; the more non-technical the managers get, the more they fail to see the benefits of unit testing.

Good developers can still find time to write these tests, however. Since developers often have a good bit of influence in the estimation process and bug fixing process, there are strategies that developers can employ to improve their chances of getting good unit tests written.

### Controlling the Time Estimate

Most developers play a part in the estimation process. Even in the worst development shops, the project manager must rely on the discretion of the developer in order to properly devise a schedule, and this requires estimation on the part of the developer.

Good developers use this to their advantage. They understand how long things will take, and how long things will take in the event of catastrophic failure, and usually pick a number in between in order to satisfy the project manager. Good estimation means that you can satisfy your manager while still getting your work done in a high quality way.

If estimation is a core component of your job, and you have 100% leverage in making the estimate, you can in fact build in time for testing. When it comes time to calculate the estimate, figure in the time to write tests, and simply leave that time in the final estimate but do not mark down that it is for unit testing.

Some might find this to be a bit dishonest; in truth it can appear that way. However, proper unit testing is an essential part of completing the project, whether or not a project manager will try and cut it out. Unit testing is part of the job.

By properly estimating and providing an estimate that builds in time for unit testing, you automatically build unit testing into your schedule without sacrificing the quality of the finished product.

### Writing Unit Tests for Every Bug

One strategy that the guys over at web2project use to improve their test coverage is that every bug that gets fixed must be accompanied by a unit test that tests the code. This accomplishes two things: first, it allows them to show the bug in a programmatic way (meaning they have a before-and-after view of the fix), and secondly, it forces them to write test coverage for lots of their product.

It is pretty easy to argue for writing a test that will show when you have the bug fixed: and since a unit test is essentially a test of the logic that asserts a particular outcome, your unit test is pretty good evidence that the bug has been resolved. The end result here is that you end up with massive amounts of unit tests that address specific bugs in the code, but also test to make sure that any refactoring you do later on does not reintroduce bugs that would otherwise harm your application.

Most of the time, you do not even need a whole lot of time to write unit tests with this method. Showing that a bug exists in code is pretty easy - if you assert what the outcome should be, and you get a different outcome, the unit test fails. Usually these tests take less than 30 minutes to write (and any test that takes more than 30 minutes to write by itself might be too large anyway).

This strategy is also excellent when you have a large existing codebase that lacks unit tests. By writing them as you fix bugs, you will slowly improve your coverage. Over time you will improve your coverage until you are at or near 100%.
