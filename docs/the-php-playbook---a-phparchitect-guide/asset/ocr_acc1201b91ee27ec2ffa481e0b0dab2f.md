Also note that the test class extends from PHPUnit_Framework_TestCase. This is the test case class, and contains all the methods necessary to properly generate and run test cases.

As previously mentioned, when beginning to write tests, it is tempting to write only a single method that tests your single point of entry and then determines if the whole class functioned properly. It is important that you avoid doing this; that is more akin to a “functional test” - that is, a test of the functionality. We want to test individual units of code - the methods themselves - meaning that we want to avoid writing functional tests and instead test “units”, typically methods.

This brief introduction should be a guide to writing tests; the PHPUnit manual is much more in depth and is up to date. PHPUnit is still in development; though Version 3.4 of PHPUnit was used in the writing of this book, changes may be made that could affect the accuracy of these guidelines.

# How to Test When Time is Not Allotted for It

Because testing takes extra time, many managers feel it is unimportant, and worse, may believe that it is “red tape” preventing them from getting the project shipped on time. This is not unusual; the more non-technical the managers get, the more they fail to see the benefits of unit testing.

Good developers can still find time to write these tests, however. Since developers often have a good bit of influence in the estimation process and bug fixing process, there are strategies that developers can employ to improve their chances of getting good unit tests written.

# Controlling the Time Estimate

Most developers play a part in the estimation process. Even in the worst development shops, the project manager must rely on the discretion of the developer in order to properly devise a schedule, and this requires estimation on the part of the developer.

Good developers use this to their advantage. They understand how long things will take, and how long things will take in the event of catastrophic failure, and usually pick a number in between in order to satisfy the project manager. Good estimation