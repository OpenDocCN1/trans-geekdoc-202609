It's *almost* the same as before, it's just that what we're saying is the **type of the stack constrains what type of values you can work with**.

Once you create a `Stack[Orange]` or a `Stack[Apple]` the methods defined on our stack will only let you pass in and will only return the particular type of the stack you're working with:

```
func (s *Stack[T]) Pop() (T, bool)
```

You can imagine the types of implementation being somehow generated for you, depending on what type of stack you create:

```
func (s *Stack[Orange]) Pop() (Orange, bool)
```

```
func (s *Stack[Apple]) Pop() (Apple, bool)
```

Now that we have done this refactoring, we can safely remove the string stack test because we don't need to prove the same logic over and over.

Using a generic data type we have:

+   - Reduced duplication of important logic.
+   - Made `Pop` return `T` so that if we create a `Stack[int]` we in practice get back `int` from `Pop`; we can now use + without the need for type assertion gymnastics.
+   - Prevented misuse at compile time. You cannot `Push` oranges to an apple stack.

# Wrapping up

This chapter should have given you a taste of generics syntax, and some ideas as to why generics might be helpful. We've written our own `Assert` functions which we can safely re-use to experiment with other ideas around generics, and we've implemented a simple data structure to store any type of data we wish, in a type-safe manner.