upfront trying to create the "perfect" extensible system and end up getting it wrong and going nowhere.

This is the bad old days of software where an analyst team would spend 6 months writing a requirements document and an architect team would spend another 6 months coming up with a design and a few years later the whole project fails.

I say bad old days but this still happens!

Agile teaches us that we need to work iteratively, starting small and evolving the software so that we get fast feedback on the design of our software and how it works with real users; TDD enforces this approach.

TDD addresses the laws that Lehman talks about and other lessons hard learned through history by encouraging a methodology of constantly refactoring and delivering iteratively.

# Small steps

+   - Write a small test for a small amount of desired behaviour
+   - Check the test fails with a clear error (red)
+   - Write the minimal amount of code to make the test pass (green)
+   - Refactor
+   - Repeat

As you become proficient, this way of working will become natural and fast.

You'll come to expect this feedback loop to not take very long and feel uneasy if you're in a state where the system isn't "green" because it indicates you may be down a rabbit hole.

You'll always be driving small & useful functionality comfortably backed by the feedback from your tests.