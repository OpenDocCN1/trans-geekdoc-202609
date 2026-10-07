# Listing 3.23

```
slice1 := []string("A", "B", "C", "D", "E"
slice2 := slice1[2:4]
slice2[0] = "CHANGED"
inspectSlice(slice1)
inspectSlice(slice2)

Output:
Length[5] Capacity[5]
[0] 0xc00007e000 A
[1] 0xc00007e010 B
[2] 0xc00007e020 CHANGED
[3] 0xc00007e030 D
[4] 0xc00007e040 E
Length[2] Capacity[3]
[0] 0xc00007e020 CHANGED
[1] 0xc00007e030 D
```

I always have to be aware when I am modifying a value at an index position if the backing array is being shared with another slice.

# Figure 3.9

![](bbox=[0.095, 0.405, 0.875, 0.765])

What if I use the built-in function append instead?