# Chapter 15
Unit And Functional Testing

Automated tests are one of the greatest advances in programming since object orientation. Particularly conducive to developing web applications, they can guarantee the quality of an application even if releases are numerous. Symfony provides a variety of tools for facilitating automated testing, and these are introduced in this chapter.

# Automated Tests

Any developer with experience developing web applications is well aware of the time it takes to do testing well. Writing test cases, running them, and analyzing the results is a tedious job. In addition, the requirements of web applications tend to change constantly, which leads to an ongoing stream of releases and a continuing need for code refactoring. In this context, new errors are likely to regularly crop up.

That's why automated tests are a suggested, if not required, part of a successful development environment. A set of test cases can guarantee that an application actually does what it is supposed to do. Even if the internals are often reworked, the automated tests prevent accidental regressions. Additionally, they compel developers to write tests in a standardized, rigid format capable of being understood by a testing framework.

Automated tests can sometimes replace developer documentation since they can clearly illustrate what an application is supposed to do. A good test suite shows what output should be expected for a set of test inputs, and that is a good way to explain the purpose of a method.

The symfony framework applies this principle to itself. The internals of the framework are validated by automated tests. These unit and functional tests are not bundled with the PEAR package, but you can check them out from the SVN repository or browse them online51.

# Unit and Functional Tests

Unit tests confirm that a unitary code component provides the correct output for a given input. They validate how functions and methods work in every particular case. Unit tests deal with one case at a time, so for instance a single method may need several unit tests if it works differently in certain situations.

Functional tests validate not a simple input-to-output conversion, but a complete feature. For instance, a cache system can only be validated by a functional test, because it involves more than one step: The first time a page is requested, it is rendered; the second time, it is taken from the cache. So functional tests validate a process and require a scenario. In symfony, you should write functional tests for all your actions.