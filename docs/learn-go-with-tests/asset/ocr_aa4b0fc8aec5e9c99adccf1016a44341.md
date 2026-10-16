# The zero value

In the multiplication example, we show the reason for having a default value as an argument to `Reduce`. If we relied on Go's default value of 0 for `int`, we'd multiply our initial value by 0, and then the following ones, so you'd only ever get 0. By setting it to 1, the first element in the slice will stay the same, and the rest will multiply by the next elements.

If you wish to sound clever with your nerd friends, you'd call this The Identity Element.

In mathematics, an identity element, or neutral element, of a binary operation operating on a set is an element of the set which leaves unchanged every element of the set when the operation is applied.

In addition, the identity element is 0.

```
1 + 0 = 1
```

With multiplication, it is 1.

```
1 * 1 = 1
```

# What if we wish to reduce into a different type from A?

Suppose we had a list of transactions `Transaction` and we wanted a function that would take them, plus a name to figure out their bank balance.

Let's follow the TDD process.

# Write the test first