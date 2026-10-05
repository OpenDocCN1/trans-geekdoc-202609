# Acceptance Testing

Acceptance Testing is testing whether the product meets the requirements for which it was designed. The name comes from the fact that, in some environments, the customer might define a series of tests which your application will have to pass before they accept the product.

In most cases, acceptance testing is a specific form of browser testing, which we will cover in Chapter 10.

# 3.3 Code Coverage

Code coverage tells you which lines of script have been executed during test execution. PHPUnit requires Xdebug¹ or phpdbg² to provide code coverage reports.

We use Line Coverage, which measures whether each executable line was executed. If we say code coverage is 60%, then 60% of the lines were executed during test execution.

Code coverage only tells you how many lines were executed. 100% code coverage tells you all of your code was executed during the tests. It does not guarantee your code is bug free or all of your code was actually tested.

If you want to know more about code coverage, I recommend you read PHPUnit Manual's chapter on Code Coverage Analysis³.

# 3.4 Fixtures

Fixture is a known state in which a test will be run. When running a test, if the test differs from one of the test to the next, the results may differ as well, so you build one or more fixtures to ensure the tests are repeatable and consistent.

For example, in database testing, we always have to set up the same database state. If you write a test which queries and checks the results without a setup to fix the state beforehand, another test that inserts/updates the data may cause your test to fail. If you are working on a team of developers, the situation may be even worse, as each developer may be unaware of the expectations of other developer's tests.

Since we are trying to run automated tests, we want the code's environment to be in a known state for each test. We will prepare database fixtures in Chapter 5, Database Fixtures.

> ¹http://xdebug.org/

> ²http://phpdbg.com/

> ³https://phpunit.de/manual/4.8/en/code-coverage-analysis.html