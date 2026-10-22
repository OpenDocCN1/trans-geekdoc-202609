
## Chapter 3 What Are Tests?

There are several ways we can answer this question. When I was first learning to write tests, I didn’t really think much about it. I wrote some code, used the test runner, and looked to see if I got the expected results. If we back up a bit, I think we can get a much more useful answer.

From a very high level, a test is code you have written which confirms the code you are trying to test is behaving as expected. It’s a very simple concept. Everything else used to describe what a test is, builds on this foundation.

If you look at it another way, there’s a question you should ask yourself every time you write code: How can I prove this code behaves the way I am expecting it to? By focusing on making sure behavior is tested instead of lines of code, we end up with test suites that are more focused on the task of being proofs instead of something we do to target an often-arbitrary “How much of our code is covered by tests?” number.

Before I start talking about the different levels of tests you might end up creating, I wanted to share a story about the effectiveness of tests and TDD (Test-Driven Development), in particular.

In June 2008, a paper about the effectiveness of TDD was published. The paper discussed case studies of how IBM and Microsoft experimented with TDD by giving teams the same programming tasks but asking some of them to use TDD as opposed to no formalized testing practices at all.

The teams that used TDD took 15% to 35% longer in terms of development time. This is not surprising because tests are code you write to prove other code is behaving correctly. It is likely to take more time, so this result lines up with my own personal experiences.

The teams that used TDD saw a 40% to 90% decrease in the number of defects in their code as compared to teams not using it. To me, this is the big win you get from having tests for your application. Having something that can actively prevent defects from being released to production is a big win.

We are at a point in software development where there is a big rush to “get something out there” or “you gotta release a Minimum Viable Product.” Notice how “make sure stuff is working correctly for your use cases” is missing from any of this advice. Offloading testing onto the users of our applications is a terrible trend that seems to be picking up steam. By learning the skills you need to write tests, you can help reverse this trend.

I want to share what I feel is a progression of the types of tests you will end up creating for your application. The end goal is always the same: A repeatable process that ensures your code continues to behave the way you expect it to. This does not necessarily mean that no bugs occur, although the use of tests greatly reduces the bugs your users might run into. In this list, I mention some testing concepts you might not be familiar with but are addressed later in the book. Don’t worry or feel intimidated!

### Prerequisites

Before you can start writing tests, there are some other things you need to have in place to make these tests worth doing. First, you need to have some way to revert changes to the code for the application. Hopefully, you are using some sort of version control system. Git is currently the industry standard, and you can find lots of information online on how to use Git and tools that are designed to work with it.

The next thing you will need is some way to apply and roll back any changes you make to your data storage tools. It doesn’t matter if it’s a relational database or a key-value store or a document database—if you cannot roll back the changes you make to data or the schema you are using to guide organizing the data, you will constantly run into situations where you cannot go back.

There are PHP tools available to help you with database migrations (what the changes you make to data sources are commonly referred to as), and many popular object-relational mappers (ORMs) come with tools to manage them.

I cannot emphasize enough that you need to have procedures to roll back changes in place before you even attempt to get tests in place.

### Manual Tests

If you have no tests in place, the first tests you should be writing are checklists for someone to manually follow. These tests should be having someone actually use your application and perform one or more tasks to make sure features of your application are behaving as expected. I usually advise people to begin with these checklists for the functionality of your application that absolutely has to work as expected 100% of the time.

If any of these tests fail, you should be rolling back the changes you made and returning the application to its previous state. Then, run through your checklist again and make sure the tests still pass. Once you’ve verified the bug exists, it’s time to get someone to fix it, reapply the changes, and run through the checklist again. If the bug is still there, roll back again and keep repeating the process until the application passes your checklist test.

### Semi-Automated Tests Using Real Dependencies

The next step after manual testing is to start using a PHP testing framework (I use PHPUnit) to write tests that verify the behavior of your code and use real dependencies instead of creating substitutes for them, which are more commonly known as test doubles. We’re going to cover test doubles later in the book, but let’s keep going.

This is the biggest obstacle you will face as you learn to use tools to create tests-as-code. The terminology is unclear, the tools seem intimidating, and you don’t know where to start. In a different chapter, I cover creating tests from scratch, but at this point, think of these tests as black boxes generating pass or fail responses.

These tests end up looking very similar to the actual code in your application. In fact, your existing code is the first template you can use for tests written using a testing framework! Starting with cutting-and-pasting code from your application into a test and then adding an assertion (a statement that determines if a condition is true) is the first building block for a test suite.

So why do I call this step semi-automated? PHPUnit (and other PHP testing frameworks) can run from the command line. If you have some tests in place, someone can get your code with applied changes from version control, and run the tests from the command line manually. This last step still requires a human.

### Semi-Automated Tests Using Test Doubles

When teaching people how to write tests, I encourage them to use the “real” version of dependencies. However, there are times when you need to substitute a real dependency (like a database or the results of an API call) with one you can control every aspect of. I will cover test doubles, so no need to worry about the nuts-and-bolts of them.

At this stage, we are re-examining the tests we have already written and deciding which of the dependencies for our tests we need to turn into test doubles. Modify your tests as required, and then run them via your CLI (command line interface).

### Automated Tests

The final stage of the tests are ones that can be run via tools which encourage automation. These are usually described as build servers or continuous integration servers. No matter what you call them, their job is to perform automated tasks for you. Here is a typical set of actions that incorporate a build server:

- You commit your changes into the version control system
- The version control system sends a signal to your build server
- The build server receives the signal and starts its automated tasks
- It grabs a copy of your code from version control including your changes
- It does any work it needs to in order to create an environment for your code to run in
- It runs your tests
