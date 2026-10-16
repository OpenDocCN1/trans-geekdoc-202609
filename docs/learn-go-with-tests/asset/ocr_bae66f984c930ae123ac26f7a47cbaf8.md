+   - If your tests look messy try and refactor them.
+   - If you've done this and they're still a mess it is very likely pointing to a flaw in your design
+   - This is one of the real strengths of tests.

Even though the tests and the production code was a bit cluttered we could freely refactor backed by our tests.

Remember when you get into these situations to always take small steps and re-run the tests after every change.

It would've been dangerous to refactor both the test code and the production code at the same time, so we first refactored the production code (in the current state we couldn't improve the tests much) without changing its interface so we could rely on our tests as much as we could while changing things. Then we refactored the tests after the design improved.

After refactoring the dependency list reflected our design goal. This is another benefit of DI in that it often documents intent. When you rely on global variables responsibilities become very unclear.

# An example of a function implementing an interface

When you define an interface with one method in it you might want to consider defining a MyInterfaceFunc type to complement it so users can implement your interface with just a function.

```
type BlindAlerter interface {
    ScheduleAlertAt(duration time.Duration, amount int)
}
```

```
// BlindAlerterFunc allows you to implement BlindAlerter with a
type BlindAlerterFunc func(duration time.Duration, amount int)

// ScheduleAlertAt is BlindAlerterFunc implementation of BlindAi
```