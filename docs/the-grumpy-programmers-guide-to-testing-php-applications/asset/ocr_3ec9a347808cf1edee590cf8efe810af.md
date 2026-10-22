# 3. WHAT ARE TESTS?

This is the biggest obstacle you will face as you learn to use tools to create tests-as-code. The terminology is unclear, the tools seem intimidating, and you don’t know where to start. In a different chapter, I cover creating tests from scratch, but at this point, think of these tests as black boxes generating pass or fail responses.

These tests end up looking very similar to the actual code in your application. In fact, your existing code is the first template you can use for tests written using a testing framework! Starting with cutting-and-pasting code from your application into a test and then adding an assertion (a statement that determines if a condition is true) is the first building block for a test suite.

So why do I call this step semi-automated? PHPUnit (and other PHP testing frameworks) can run from the command line. If you have some tests in place, someone can get your code with applied changes from version control, and run the tests from the command line manually. This last step still requires a human.

# Semi-Automated Tests Using Test Doubles

When teaching people how to write tests, I encourage them to use the “real” version of dependencies. However, there are times when you need to substitute a real dependency (like a database or the results of an API call) with one you can control every aspect of. I will cover test doubles, so no need to worry about the nuts-and-bolts of them.

At this stage, we are re-examining the tests we have already written and deciding which of the dependencies for our tests we need to turn into test doubles. Modify your tests as required, and then run them via your CLI (command line interface).

# Automated Tests

The final stage of the tests are ones that can be run via tools which encourage automation. These are usually described as build servers or continuous integration servers. No matter what you call them, their job is to perform automated tasks for you. Here is a typical set of actions that incorporate a build server:

+   - You commit your changes into the version control system
+   - The version control system sends a signal to your build server
+   - The build server receives the signal and starts its automated tasks
+   - It grabs a copy of your code from version control including your changes
+   - It does any work it needs to in order to create an environment for your code to run in
+   - It runs your tests