# # Additional information

# ## Benefits of this structure

If you take a step back, you might be able to see a few benefits of setting up our project in this way:

+   - There’s a clean separation of concerns. Our database logic won’t be tied to our handlers, which means that handler responsibilities are limited to HTTP stuff (i.e. validating requests and writing responses). This will make it easier to write tight, focused, unit tests in the future.

+   - By creating a custom **SnippetModel** type and implementing methods on it we’ve been able to make our model a single, neatly encapsulated object, which we can easily initialize and then pass to our handlers as a dependency. Again, this makes for easier to maintain, testable code.

+   - Because the model actions are defined as methods on an object — in our case **SnippetModel** — there’s the opportunity to create an *interface* and mock it for unit testing purposes.

+   - And finally, we have total control over which database is used at runtime, just by using the **`-dsn`** command-line flag.