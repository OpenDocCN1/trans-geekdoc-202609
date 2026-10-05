# Chapter 3. Strings

17 characters, none of which is too big). The apparent discrepancy is due to the space separator that is between each slice item.

In addition to debugging, the %#v verb may be useful when generating Go code programmatically.

```
fmt.Printf("%v\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%v\n", map[int]string{1: "A", 2: "B", 3: "C", 4: "D"})
fmt.Printf("%d\n", map[int]int{1: 2, 2: 3, 4: 8})
fmt.Printf("%v\n", map[int]int{1: 2, 2: 3, 4: 8})
fmt.Printf("%04b\n", map[int]int{1: 2, 2: 3, 4: 8})
```

```
map[4:8] 1:1 2:3
map[int]string{4: "D", 1: "A", 2: "B", 3: "C"}
map[4:8] 1:1 2:3:4
map[int]int{4:8, 1:1, 2:2, 3:4}
map[0100:1000] 0001:0010 0010:0011
```

Maps are output as the "map", and then the map's key-value pairs (in an arbitrary order since maps are unordered). Just as with slices it is possible to use verbs other than %#v—but only if both the key and value are compatible with the verb used, as in the example's last statement. (Maps and slices are covered in detail in Chapter 4).

The fmt package's print functions are very versatile and can be used to print whatever output we need. The only feature not offered by the package's functions is padding with a particular character (other than zeros or spaces), but as we saw in the custom Pad() (99 ◄) and Humanize() (100 ◄) functions, this is very easy to do.

# 3.6. Other String-Related Packages

Go's considerable support for strings doesn't stop at indexing and slicing, or with the versatile fmt package's functions. The strings package in particular provides very rich functionality, the strconv, unicode/utf8, and unicode packages also provide lots of useful functions. Examples that make use of functionality from all these packages are presented in this section. Regular expressions—provided by the powerful regexp package introduced later in this section—are used in several examples throughout the book.

There are other packages in the standard library that provide string-related functionality, and some of them are covered elsewhere in the book either in examples or in exercises.