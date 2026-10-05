# PHPUnit Basics

```
<phpunit
  bootstrap="../Bootstrap.php"
  colors="true">
```

The bootstrap attribute sets the bootstrap file to be used by PHPUnit. The colors attribute tells it to use colors in the output. If your terminal doesn't have color capability, change the value of the colors attribute from true to false.

# testsuite

The next element, testsuite, defines the test suites which will be executed by PHPUnit. A test suite is a set of test cases, usually related in some way. Each testsuite contains one or more testsuite elements, each specifying files or directories which are included (or excluded) in the test and a name for the test suite itself. In this case elements are in ./application/tests/ directory, and we specify a .php suffix, so only files ending in test.php within directory will be included. We are also excluding files in the ._ci_phpunit_test/directory.

```
<testsuite>
  <testsuite name="CodeIgniter Application Test Suite">
    <directory suffix="test.php">./directory>
    <exclude>./_ci_phpunit_test/</exclude>
  </testsuite>
</testsuite>
```

# filter

The next element, filter, is used to configure code coverage reporting. The whitelist contains elements which define files and directories to be included in the report. The first directory element indicates that we include with suffix .php in the ../controllers (application/controllers) directory.

```
<whitelist>
  <directory suffix=".php">../controllers</directory>
  <directory suffix=".php">../models</directory>
  <directory suffix=".php">../views</directory>
  <directory suffix=".php">../libraries</directory>
  <directory suffix=".php">../helpers</directory>
  <directory suffix=".php">../hooks</directory>
</whitelist>
</filter>
```