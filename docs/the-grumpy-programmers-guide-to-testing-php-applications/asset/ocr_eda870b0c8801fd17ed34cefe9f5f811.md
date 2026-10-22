# 12. METATESTING

These are all things I started out doing manually, but I want them automated. In an idealized environment, I would want to do this sort of thing locally. The project does use Composer’s “scripts” section to define some tasks I use to do those exact steps above. Again, I want the computer to repeat these tasks for me, over and over again. The likelihood of me making a mistake with one of these steps is a lot higher than if the computer does it.

# There Are Awesome Complementary Tools

It’s not enough to have tests for your code. It does take a significant amount of discipline to continue writing those tests and staying focused on using Test-Driven Development effectively. Luckily other people have been tackling those same problems and have some solutions I can endorse.

# XDebug

First, there is XDebug[7]. XDebug is a PHP extension which allows you to do two things that are useful for PHP developers. The first is that you can use it as a step-through debugger when you are refactoring existing code or just trying to figure out “Why is this code not behaving the way I expect it to?” There are many articles out there on how to install XDebug and configure it to work with your preferred editor or IDE. For many years, I resisted using a debugger, instead relying on tests and printing out debugging statements in my code. It takes a long time to learn new habits, but with some help from PhpStorm, I have been working hard to remember I have a step-through debugger that can show me the contents of variables at my breakpoint. Learning to use a debugger is a skill more programmers of all languages could stand to get better at.

The second thing XDebug is great at for PHP folks is how, in combination with PHPUnit, it can be used to generate code coverage reports. Code coverage is a metric many use to track how much of your code is being executed by your tests. Code bases with very high code coverage percentages (90% and over) tend to be reliable and bug-free. It is possible to get to 100% code coverage, but it’s hard to do if you don’t build your project using TDD.

To generate your code coverage report, you add some options to the command you are using to run your tests from the CLI, and a report will be generated for you. The most common option is to generate an HTML-based report you can load in your browser to verify what is and isn’t covered by your tests.

For OpenCFP, we generate a text-based coverage report. Here’s a sample of what it looks like:

[7] XDebug: https://xdebug.org