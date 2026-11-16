
## The Test Suite

That comparison should be done using one of a number of assertion methods provided by PHPUnit. It is these assertions that enable the test suite to report test results. Essentially, it is the accuracy of your assertions that will be reported.

Numerous assertion methods are available — assertEquals, assertTrue, assertFalse, assertNotNull, assertNull, assertSame, assertNotSame, assertType, and assertRegExp. They pretty much all do exactly what you’d expect from their name. However, if you’re curious and need definitive explanations, check out /usr/local/lib/php/PHPUnit/Assert.php or the file Assert.php in the directory in which you installed PHPUnit.

You may be wondering why having so many assert methods is necessary. Surely all comparisons can be handled using assertEquals and making liberal use of appropriate built-in PHP functions, right? This is true. All the variations are really just a convenience to make your code a little easier to read, and to enable you to avoid using double negatives and so forth. In later versions of PHPUnit, the assertions actually provide assertion-specific details with any failed test (such as showing the two types in question in assertType, and which characters don’t actually match when comparing two strings).

Having developed your test case class, using it in a test suite is actually a relatively simple mechanism.

You might name the following testsuite.php:

```php
<?php
require_once 'testcase.php';
require_once 'PHPUnit.php';

$objSuite = new PHPUnit_TestSuite("MyTestCase");
$strResult = PHPUnit::run($objSuite);

print $strResult->toString();
?>
```

Replace MyTestCase with the actual name of your test case class. If you run this from the command line (as opposed to using your Web browser), you’ll get output that looks something like this if things worked:

```
TestCase objMyTestClass->myMethod() passed
```

It will look like the following if things didn’t work:

```
TestCase objMyTestClass->myMethod() failed: expected true, actual false
```

Note that if you want to run in a Web browser, rather than at the command line, you should use toHTML rather than the toString method on the output string so that carriage returns are converted to <br /> and so forth.

## Why Bother?

At first glance, it might be difficult to see the immense advantages arising from using this method of testing over a more quick-and-dirty method involving the server error log (such as the one somewhat contemptuously described earlier). The following sections describe why you should be using unit testing frameworks.

## Regression Testing

The vast majority of code you’ll ever work on will, at some stage, need to evolve. It may not necessarily be you who works on it, but you can be fairly certain that it won’t remain untouched for too long.

For example, you might need to rework an existing method to make it provide exactly the same functionality as it did before but with a big performance increase. The only way to do this is to completely rewrite the method, keeping the interface the same but with an optimized inner algorithm. In this kind of example, your testing suite is immensely useful. Simply run it before and after your new algorithm has been developed, and confirm that you get the same results both times.

A more likely scenario is that your class must be extended with a new method to support some new business requirement. Even then, your testing suite is useful in its unmodified form. You can ensure that your new method does not in any way impact the functionality of any other methods. After verifying this, you can simply extend your test case class to test your new method.

Either way, you can see that using unit testing frameworks for this kind of testing (commonly known as regression testing) makes good sense.

## Framework Usability

Your test case classes may have wider uses than you think. Other classes you develop with similar or identical interface functionality can be quickly and reliably tested using your existing test suites.

In particular, you may have inherited classes that overwrite the functionality of their parent class. Alternatively, taking advantage of PHP 6’s object model, you may have classes that implement abstract interfaces. A good example of this is objects representing entities stored in a database, which will almost certainly have getProperty and setProperty methods, and so forth, as you saw in Chapter 7. With little or no adaptation, you can use a standard test suite to provide an instant and reliable commentary on the functionality of such generic classes.

## Demonstrable Quality Assurance

A professional software development environment can often contain a complex hierarchy of individuals involved on any given project — from the project manager right through to the lead architect, the software engineers, the designers, and others.

In this kind of environment, literally tens of thousands of lines of code can be churned out every day. It is simply impossible for the project’s lead architect to test every single component his or her developers produce. With this kind of structured testing methodology, the management buzzword of *empowerment* becomes an achievable reality. That is to say, engineers can be safely trusted to test their own code, because this methodology encourages a thoroughness that is often absent in other, more haphazard component-testing techniques. Lead architects can easily standardize quality assurance across all component production, and have far greater confidence in his or her team's output as a result.

The formal nature of this process is likely to be viewed favorably by nontechnical individuals with a keen interest in the progress of a project (such as project and account managers).

## Reducing the Burden of Functional Testing

It's often said that the least sexy part of the project life cycle is functional testing. Whether this statement is fair or not, it is certainly an additional cost that must be borne and budgeted for.

By requiring the development team to take ownership of the functional testing of its own components, the need for exhaustive and extensive functional testing of the completed application can be greatly reduced. It is not eliminated entirely, however; and as you will learn in Chapter 20, it is still vitally important.

## Developing the Model in Isolation

In a typical Web application development project, the most contentious aspect of the build itself is often the look and feel and user journey — in other words, it is often the information architecture ("wireframes"), site map, and page treatments that are signed off last. Because these together form a dependency that holds up the development of any finished HTML, software engineers can often be waiting with little to do, wondering when they can get started.

However, debate over the user journey, page layout, site maps, navigation, or creative implementation shouldn’t necessarily mean that decisions over business objects cannot be taken in a separate developmental branch. For example, if you know that user registration is a requirement in the finished application, and you can make educated guesses about which fields will be required during registration, then it is within your power to deduce that a business class (probably a data-bound object, as covered in Chapter 7) called `User` must be built, as well as a utility class called `Registration`.

Moreover, you can probably deduce what member variables and methods these classes should have, too. Develop those methods in isolation within a test suite, test them, and be confident that you can "drop them" into the application once other elements of the project plan have fallen into place.

## Summary

In this chapter, you learned about the model-view-controller (MVC) design pattern, and its importance in sound application architecture.

As well as learning the theory behind MVC methodology, you were introduced to two very different ways in which that methodology can be followed. First, you met an MVC toolkit that enables you to implement a `request` and `constraint` object hierarchy in your projects to better enforce the separation between model, view, and controller.
