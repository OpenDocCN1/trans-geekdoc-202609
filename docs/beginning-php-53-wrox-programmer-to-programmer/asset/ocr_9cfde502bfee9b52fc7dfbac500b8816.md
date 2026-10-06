# Chapter 20: Writing High-Quality Code

PHPUnit is a framework for automated unit testing. You can use it to write tests in PHP to each unit of your application, then run the tests automatically and see the results.

To install PHPUnit, use the PEAR installer (see Chapter 15 for more on PEAR). Because PHPUnit is not in the standard PEAR channels, you first need to run (possibly as root or an admin user):

+   pear channel-discover pear.phpunit.de

You should then see:

+   Adding Channel "pear.phpunit.de" succeeded
Discovery of channel "pear.phpunit.de" succeeded

Now install PHPUnit as follows (again as root if necessary):

+   pear install --alldeps phpunit/PHPUnit

# Try Out Write a Simple PHPUnit Test Suite

Now that you've installed PHPUnit, try writing some simple tests. In this example you test a few methods of the Car class created in the car_simulator.php script in Chapter 8 (and reprinted in the "Documenting Your Code" section earlier in this chapter).

Save the following script as car_tests.php in your document root folder:

```
<DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml/html-strict.dtd">\n<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Car Test Suite Example</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Car Test Suite Example</h1>
<pre>
<?php

require_once ( "PHPUnit/Framework.php" );
require_once ( "PHPUnit/TextUI/TestRunner.php" );

class Car {
public $color;
public $manufacturer;
public $model;
private $_speed = 0;

public function accelerate() {
if ( $this->speed >= 100 ) return false;
$this->speed += 10;

```