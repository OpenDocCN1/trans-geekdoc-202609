# Tests for Refactoring

You might think this is covered by the section on tests for new features, but I feel like they are two different things.

Your definition of refactoring might be different from mine. To me, refactoring is the process of taking code that is working as expected and modifying it to take advantage of new knowledge, techniques, or libraries. The output or final result of the code should not change! If that happens, you’re rewriting the code to do something different.

So when it comes to refactoring, this seems to me to be a perfect candidate for a test:

+   - Write the test for the code that uses the expected outcome
+   - Start modifying existing code that is being tested
+   - Run the test and make sure it passes

Repeat the three steps above until you are happy the refactor is complete.

# Commitment to Peer Review

Every place I have worked at that had a strong testing culture was also heavily committed to peer reviews of code. To me, peer review means someone else looks at my code to verify it is accomplishing the desired outcome before it goes into production. If you do nothing else other than adding peer review of code to your development practices, the quality and–more importantly–the purpose of your code will improve immensely.

When related to the primary goal, we end up with a workflow like this:

+   - Developer is writing code to solve a problem
+   - Developer includes tests (hopefully using TDD, but test-after has value)
+   - Developer indicates code is ready
+   - Peer reviews the code, checking for tests and correct intent of code
+   - With peer approval, code moves to the next target environment

Now, there is something I feel is really important to stress here–it’s supposed to be peer review, not superior review. If we’re going to be honest, most people do not like being told the code they worked on isn’t any good. I used to be extremely defensive about the code I wrote and the ideas associated with those decisions. It made peer review way more stressful than it needed to be because I wasted more time arguing and trying to justify my choices rather than understanding the criticism being presented.