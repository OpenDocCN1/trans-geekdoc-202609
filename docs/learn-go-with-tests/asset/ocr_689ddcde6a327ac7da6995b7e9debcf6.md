Use the TDD process to drive out real, specific behaviour that you actually need, in the refactoring stage you then *might* discover some useful abstractions to help tidy the code up.

Practice combining TDD with good source control habits. Commit your work when your test is passing, *before* trying to refactor. This way if you make a mess, you can easily get yourself back to your working state.

# Names matter

Make an effort to do some research outside of Go, so you don't reinvent patterns that already exist with an already established name.

Writing a function takes a collection of `A` and converts them to `B`? Don't call it `Convert`, that's `Map`. Using the "proper" name for these items will reduce the cognitive burden for others and make it more search engine friendly to learn more.

# This doesn't feel idiomatic?

Try to have an open-mind.

Whilst the idioms of Go won't, and shouldn't *radically* change due to generics being released, the idioms *will* change - due to the language changing! This should not be a controversial point.

Saying

This is not idiomatic

Without any more detail, is not an actionable, or useful thing to say. Especially when discussing new language features.

Discuss with your colleagues patterns and style of code based on their merits rather than dogma. So long as you have well-designed