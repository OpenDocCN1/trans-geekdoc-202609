with *concrete* behaviour like `StackOfStrings` and `StackOfInts` backed by tests. From our *real* code we could start to see real patterns, and backed by our tests, we could explore refactoring toward a more general-purpose solution.

People often advise you to only generalise when you see the same code three times, which seems like a good starting rule of thumb.

A common path I've taken in other programming languages has been:

+   - One TDD cycle to drive some behaviour
+   - Another TDD cycle to exercise some other related scenarios

Hmm, these things look similar - but a little duplication is better than coupling to a bad abstraction

+   - Sleep on it
+   - Another TDD cycle

OK, I'd like to try to see if I can generalise this thing. Thank goodness I am so smart and good-looking because I use TDD, so I can refactor whenever I wish, and the process has helped me understand what behaviour I actually need before designing too much.

+   - This abstraction feels nice! The tests are still passing, and the code is simpler
+   - I can now delete a number of tests, I've captured the *essence* of the behaviour and removed unnecessary detail