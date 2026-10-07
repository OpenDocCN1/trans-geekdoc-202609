![](bbox=[0.125, 0.055, 0.875, 0.36])

This can be seen by comparing the addresses of each slice. In this case, the mutation against slice2 didn't cause a side effect against slice1.

# 3.18 Copying Slices Manually

There is a built-in function named copy that will allow for the shallow copying of slices. Since a string has a backing array of bytes that are immutable, it can be used as a source but never a destination.

Listing 3.27

```
slice1 := []string("A", "B", "C", "D", "E")
slice3 := make([]string, len(slice1))
copy(slice3, slice1)

inspectSlice(slice1)
inspectSlice(slice3)

Output:
Length[5]Capacity[5]
[0] 0xc00005c00 A
[1] 0xc00005c00 B
[2] 0xc00005c00 C
[3] 0xc00005c00 D
[4] 0xc00005c00 E
Length[5]Capacity[5]
[0] 0xc00005c0a A
[1] 0xc00005c0b B
[2] 0xc00005c0c C
[3] 0xc00005c0d D
[4] 0xc00005c0e E
```

As long the destination slice has the proper type and length, the built-in function copy can perform a shallow copy.