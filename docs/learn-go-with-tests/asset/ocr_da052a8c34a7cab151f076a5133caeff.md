should prompt you for another argument you'll need.

In practice, it is convenient and natural to have an initial value

# My first-pass of Reduce

```
func Reduce[A any](collection []A, accumulator func(A, A) A, ini
    var result = initialValue
    for _, x := range collection {
        result = accumulator(result, x)
    }
    return result
}
```

Reduce captures the essence of the pattern, it's a function that takes a collection, an accumulating function, an initial value, and returns a single value. There's no messy distractions around concrete types.

If you understand generics syntax, you should have no problem understanding what this function does. By using the recognised term Reduce, programmers from other languages understand the intent too.

# The usage

```
// Sum calculates the total from a slice of numbers.
func Sum(numbers []int) int {
    add := func(acc, x int) int { return acc + x }
    return Reduce(numbers, add, 0)
}
```

```
// SumAllTails calculates the sums of all but the first number c
func SumAllTails(numbers ...[]int) []int {
    sumTail := func(acc, x []int) []int {
        if len(x) == 0 {
            return append(acc, 0)
        } else {
            tail := x[1:]
```