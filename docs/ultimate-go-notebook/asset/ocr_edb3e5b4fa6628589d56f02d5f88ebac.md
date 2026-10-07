use in Go.

# Listing 8.13

```
func single(n []int) []int {
    // Once we have a list of one we can begin to merge values.
    if len(n) <= 1 {
        return n
    }
    // Split the list in half.
    i := len(n) / 2
    // Sort the left side.
    l := single(n[:i])
    // Sort the right side.
    r := single(n[i:])
    // Place things in order and merge ordered lists.
    return merge(l, r)
}
```

The single function uses a Goroutine to perform the sort. It splits the initial list in half, then uses recursion to continue to split the list until the merge function can be executed to sort everything.

# Listing 8.14

```
func unlimited(n []int) []int {
    // Once we have a list of one we can begin to merge values.
    if len(n) <= 1 {
        return n
    }
    // Split the list in half.
    i := len(n) / 2
    // Maintain the ordered left and right side lists.
    var l, r []int

..
```

The unlimited function starts out the same as the single function. Then it begins to throw new Goroutines at each split of the list.