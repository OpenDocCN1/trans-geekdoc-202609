You can index slices like arrays with `mySlice[N]` to get the value out or assign it a new value with =

The tests should now pass.

# Refactor

As mentioned, slices have a capacity. If you have a slice with a capacity of 2 and try to do `mySlice[10] = 1` you will get a *runtime* error.

However, you can use the `append` function which takes a slice and a new value, then returns a new slice with all the items in it.

```
```go
func SumAll(numbersToSum ...[]int) []int {
    var sums []int
    for _, numbers := range numbersToSum {
        sums = append(sums, Sum(numbers))
    }

    return sums
}
```
```

In this implementation, we are worrying less about capacity. We start with an empty slice `sums` and append to it the result of `Sum` as we work through the varargs.

Our next requirement is to change `SumAll` to `SumAllTails`, where it will calculate the totals of the "tails" of each slice. The tail of a collection is all items in the collection except the first one (the "head").

# Write the test first

```
```go
func TestSumAllTails(t *testing.T) {
    got := SumAllTails([]int{1, 2}, []int{0, 9})
    want := []int{2, 9}
```
```