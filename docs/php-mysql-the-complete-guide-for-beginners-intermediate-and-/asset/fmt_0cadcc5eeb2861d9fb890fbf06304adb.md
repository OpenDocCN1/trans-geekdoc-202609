
# Xdebug Features

Xdebug provides the following features:

- Maximum nesting level protection and time tracking
- Helpful replacement of standard `var_dump()` function for displaying variables
- Allows logging all function calls, including parameters and return values to a file in different formats
- Code coverage analysis
- Profiling information
- Remote debugging (provides interface for debugger clients that interact with running PHP scripts)

As you can see, this extension is perfectly suited for development environments. Especially the remote debugging feature can help you debug your PHP code without numerous `var_dump()` calls and use a normal debugging process as in C or Java languages.

## Installation

Usually installing this extension is very simple:

![Installation Step 1](Image01624.jpg)

And activate it in your `php.ini`:

![php.ini Configuration](Image01625.jpg)

In more complicated cases see these [instructions](https://xdebug.org/docs/install).

> **Warning:** [XDebug is not suitable for production environments](http://stackoverflow.com/a/3522356/2253302)

# Chapter 95: Error Reporting and Version Checking

## Section 95.5: Error Reporting (use them both)

![Error Reporting Configuration](Image01626.jpg)

## Section 95.6: phpversion()

### Introduction

When working with various libraries and their associated requirements, it is often necessary to know the version of the current PHP parser or one of its packages.

### Syntax

```php
phpversion(string $extension = null): string|false
```

This function accepts a single optional parameter in the form of an extension name. If the extension in question is installed, the function will return a string containing the version value. However, if the extension is not installed, `false` will be returned. If the extension name is not provided, the function will return the version of the PHP parser itself.

### Example

![phpversion Example](Image01627.jpg)

# Chapter 96: Unit Testing

## Section 96.1: Testing Class Rules

Let's say we have a simple `LoginForm` class with a `rules()` method (used in login page as framework template):

![LoginForm Class](Image01628.jpg)

In order to perform tests on this class, we use Unit tests (checking source code to see if it fits our expectations):

![Unit Test Setup](Image01629.jpg)

How exactly can Unit tests help here (excluding general examples)? For example, they fit very well when we get unexpected results. Let's take this rule from earlier:

![Correct Rule](Image01630.jpg)

Instead, if we missed one important thing and wrote this:

![Incorrect Rule](Image01631.jpg)

With dozens of different rules (assuming we are using not just email and password), it's difficult to detect mistakes. This unit test:

```php
// Initialize to valid and test this
$this->loginForm->email = "valid@email.com";
$this->loginForm->password = "password";
$this->loginForm->rememberMe = true;

$this->assertTrue($this->loginForm->validate($rules), "Should be valid as nothing is invalid");
```

![Test Execution](Image01632.jpg)

Will pass our first example but not the second. Why? Because in the 2nd example we wrote a pattern with a typo (missed `+` sign), meaning it only accepts one letter/number.

### Running Tests

```bash
phpunit [path_to_file]
```

Unit tests can be run in console with the command above. If everything is OK, we should be able to see that all tests are in OK state; else we will see either Error (syntax errors) or Fail (at least one line in that method did not pass).

```bash
phpunit --coverage [path_to_file]
```

With additional parameters like `--coverage`, we can also see visually how many lines in backend code were tested and which passed/failed. This applies to any framework that has installed [PHPUnit](https://phpunit.de/).

Example how PHPUnit test looks like in console (general look, not according to this example):

![PHPUnit Console Output](Image01633.jpg)

## Section 96.2: PHPUnit Data Providers

Test methods often need data to be tested with. To test some methods completely you need to provide different data sets for every possible test condition. Of course, you can do it manually using loops, like this:

![Manual Data Loop](Image01634.jpg)

And someone can find it convenient. But there are some drawbacks to this approach:

1. You'll have to perform additional actions to extract data if your test function accepts several parameters.
2. On failure it would be difficult to distinguish the failing data set without additional messages and debugging.
3. PHPUnit provides an automatic way to deal with test data sets using [data providers](https://phpunit.de/manual/current/en/writing-tests-for-phpunit.html#writing-tests-for-phpunit.data-providers).

A data provider is a function that should return data for your particular test case.

![Data Provider Example](Image01635.jpg)

A data provider method must be public and either return an array of arrays or an object that implements the `Iterator` interface and yields an array for each iteration step. For each array that is part of the collection, the test method will be called with the contents of the array as its arguments.

### Using Data Providers

To use a data provider with your test, use the `@dataProvider` annotation with the name of the data provider function specified:

![DataProvider Annotation](Image01636.jpg)

![DataProvider Usage](Image01637.jpg)

Each data set can be named for convenience. It will be easier to detect failing data:

![Named Data Sets](Image01638.jpg)

### Iterators

![Iterator Implementation](Image01639.jpg)

![Iterator Usage](Image01640.jpg)

As you can see, a simple iterator also works.

> **Note:** Even for a single parameter, the data provider must return an array `[]`. Because if we change our `current()` method (which actually returns data on every iteration) to this:

![Incorrect Single Value Return](Image01641.jpg)

Or change actual data:

![Data Change Example 1](Image01642.jpg)

![Data Change Example 2](Image01643.jpg)

### Generators

It is not explicitly noted and shown in the manual, but you can also use a generator as a data provider. Note that the `Generator` class actually implements the `Iterator` interface.

So here's an example of using `DirectoryIterator` combined with a generator:

![Generator Data Provider](Image01645.jpg)

## Section 96.3: Test Exceptions

Let's say you want to test a method which throws an exception:

![Method Throwing Exception](Image01646.jpg)

![Test Class Structure](Image01647.jpg)

You can do that by enclosing the method call into a `try/catch` block and making assertions on the exception object's properties, but more conveniently you can use exception assertion methods. As of [PHPUnit 5.2](https://github.com/sebastianbergmann/phpunit/wiki/Release-Announcement-for-PHPUnit-5.2.0) you have `expectException()` methods available for asserting exception type, message & code:

![expectException Methods](Image01648.jpg)

If you are using an earlier version of PHPUnit, the `setExpectedException()` method can be used instead of `expectException()` methods, but keep in mind that it's deprecated and will be removed in version 6.

![setExpectedException Method](Image01649.jpg)

# Chapter 97: Performance

## Section 97.1: Profiling with Xdebug

An extension to PHP called Xdebug is available to assist in [profiling PHP applications](https://xdebug.org/docs/profiler), as well as runtime debugging. When running the profiler, the output is written to a file in a binary format called "cachegrind". Applications are available on each platform to analyze these files.

To enable profiling, install the extension and adjust `php.ini` settings. In our example we will run the profile optionally based on a request parameter. This allows us to keep settings static and turn on the profiler only as needed.

```ini
; Set to 1 to turn it on for every request
xdebug.profiler_enable = 0

; Let's use a GET/POST parameter to turn on the profiler
xdebug.profiler_enable_trigger = 1

; The GET/POST value we will pass; empty for any value
xdebug.profiler_enable_trigger_value = ""

; Output cachegrind files to /tmp so our system cleans them up later
xdebug.profiler_output_dir = "/tmp"

xdebug.profiler_output_name = "cachegrind.out.%p"
```

![Profiler Config](Image01650.jpg)

Next, use a web client to make a request to your application's URL you wish to profile, e.g.

```bash
curl "http://localhost/your-app?XDEBUG_PROFILE=1"
```

![Profile Request](Image01651.jpg)

As the page processes it will write to a file with a name similar to:

```
cachegrind.out.12345
```

![Cachegrind Output](Image01652.jpg)
