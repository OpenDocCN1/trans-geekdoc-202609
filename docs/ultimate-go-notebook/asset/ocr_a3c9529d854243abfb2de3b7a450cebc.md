![](bbox=[0.093, 0.053, 0.875, 0.295])

The cost of copying a string is the same regardless of the size of a string, a two word copy.

#  3.5 Iterating Over Collections

Go provides two different semantics for iterating over a collection. I can iterate using value semantics or pointer semantics.

Listing 3.8

```
// Value Semantic Iteration
for i, fruit := range strings {
    println(i, fruit)
}

// Pointer Semantic Iteration
for i := range strings {
    println(i, strings[i])
}
```

When using value semantic iteration, two things happen. First, the collection I'm iterating over is copied and I iterate over the copy. In the case of an array, the copy could be expensive since the entire array is copied. In the case of a slice, there is no real cost since only the internal slice value is copied and not the backing array. Second, I get a copy of each element iterated on.

When using pointer semantic iteration, I iterate over the original collection and I access each element associated with the collection directly.

#  3.6 Value Semantic Iteration

Given the following code and output.