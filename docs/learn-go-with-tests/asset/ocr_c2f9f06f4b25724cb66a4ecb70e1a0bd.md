*Motivated by our tests* we refactored the code so we could control *where* the data was written by **injecting a dependency** which allowed us to:

+   - **Test our code** If you can't test a function *easily*, it's usually because of dependencies hard-wired into a function *or* global state. If you have a global database connection pool for instance that is used by some kind of service layer, it is likely going to be difficult to test and they will be slow to run. DI will motivate you to inject in a database dependency (via an interface) which you can then mock out with something you can control in your tests.
+   - **Separate our concerns**, decoupling *where the data goes* from *how to generate it*. If you ever feel like a method/function has too many responsibilities (generating data *and* writing to a db? handling HTTP requests *and* doing domain level logic?) DI is probably going to be the tool you need.
+   - **Allow our code to be re-used in different contexts** The first "new" context our code can be used in is inside tests. But further on if someone wants to try something new with your function they can inject their own dependencies.

# What about mocking? I hear you need that for DI and also it's evil

Mocking will be covered in detail later (and it's not evil). You use mocking to replace real things you inject with a pretend version that you can control and inspect in your tests. In our case though, the standard library had something ready for us to use.

# The Go standard library is really good, take time to study it

By having some familiarity with the `io.Writer` interface we are able to use `bytes.Buffer` in our test as our `Writer` and then we can use