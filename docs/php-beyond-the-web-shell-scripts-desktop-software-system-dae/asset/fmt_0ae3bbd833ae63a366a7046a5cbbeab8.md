
# 4.9 IDEs and editors

IDEs (Integrated Development Environments) and code editors for PHP are plentiful, and you will likely have your own favourite you use for web based PHP development. There are currently no IDEs or Editors specifically aimed at PHP CLI-based programming, but as such PHP code is syntactically compatible and very similar to web based PHP programming, you should have few problems using your existing PHP editing environment. Some additional features may not work correctly, such as web based debuggers, or may require additional tinkering to use. A list of popular PHP IDEs is given in Appendix E at the end of the book.

# 4.10 Documentation generators

Documentation Generators (also known as documentors) automatically generate documentation from your source code. They do this by using the comments you put in the code and by picking up the syntactical structures in your code. They are useful for creating base documentation for programming APIs and technical documentation for other developers working on your code. The documentation provided usually requires further finenessing or additional information adding to be truly useful and is usually of little use to end users of your software. However it provides a good overview of the code structure along with a useful reference for larger code-bases, where finding the details of particular functions from the code itself can be time consuming. Some IDEs and other programming tools can use the unmodified output from documentors to provide additional functionality, such as project based context specific help and auto-completions.

## phpDocumentor

Popular and versatile PHP based documentor

- **Main website**: [http://www.phpdoc.org/](http://www.phpdoc.org/)
- **Installation info**: [http://www.phpdoc.org/docs/latest/getting-started/installing.html](http://www.phpdoc.org/docs/latest/getting-started/installing.html)
- **Main documentation**: [http://www.phpdoc.org/docs/latest/index.html](http://www.phpdoc.org/docs/latest/index.html)

## phpDox

A fast modern documentor which can pull in information from other static analysis tools

- **Main website**: [http://phpdox.de/](http://phpdox.de/)
- **Main documentation and installation info**: [http://phpdox.de/getting-started.html](http://phpdox.de/getting-started.html)

## phpSimpleDoc

A simplified documentor which outputs HTML docs

- **Main website**: [http://phpsimpledoc.tig12.net/](http://phpsimpledoc.tig12.net/)
- **Installation info**: [http://phpsimpledoc.tig12.net/user-guide/quick-start#toc_1](http://phpsimpledoc.tig12.net/user-guide/quick-start#toc_1)
- **Main documentation**: [http://phpsimpledoc.tig12.net/user-guide](http://phpsimpledoc.tig12.net/user-guide)

## Doxygen

A comprehensive and extensive documentor, which supports PHP but is not PHP specific.

- **Main website**: [http://www.stack.nl/~dimitri/doxygen/](http://www.stack.nl/~dimitri/doxygen/)
- **Installation info**: [http://www.stack.nl/~dimitri/doxygen/manual/install.html](http://www.stack.nl/~dimitri/doxygen/manual/install.html)
- **Main documentation**: [http://www.stack.nl/~dimitri/doxygen/manual](http://www.stack.nl/~dimitri/doxygen/manual)

## Sami

The documentor created and used by the Symphony framework project for their API, although it is not Symphony specific.

- **Main website**: [https://github.com/fabpot/Sami](https://github.com/fabpot/Sami)
- **Installation info**: [https://github.com/fabpot/Sami#installation](https://github.com/fabpot/Sami#installation)
- **Main documentation**: [https://github.com/FriendsOfPHP/Sami#configuration](https://github.com/FriendsOfPHP/Sami#configuration)

# 4.11 Profilers

Profilers let you measure and view the execution time and path of your code, usually with a view to increasing the performance of your scripts and removing code bottle-necks. We will look at these in detail in Chapter 9 when we look further at script performance.

# 4.12 Other tools

This section lists some further tools that are useful for serious development, but don’t fit neatly into the categories above.

## PHP Coding Standards Fixer

Attempts to fix your code to meet PSR standards.

- **Main website, documentation & installation info**: [http://cs.sensiolabs.org/](http://cs.sensiolabs.org/)

## Composer Dependency Manager

