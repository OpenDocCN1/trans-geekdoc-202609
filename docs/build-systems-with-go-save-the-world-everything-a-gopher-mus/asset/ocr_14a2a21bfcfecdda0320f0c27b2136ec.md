second approach (line 14) using range prints the same output in a less verbose way. For arrays and slices, range returns the index of the item and the item itself for every iteration of the loop. The iteration is always done incrementally from index 0 to index n-1.

> Notice that the item from the slice returned by range is a copy of the item. Therefore, modifying this variable inside the loop will not modify the iterated array. The next piece of code shows when modifying the item returned by range we cannot modify the slice we are iterating through. A correct approach to modify the iterated slice is to access the original variable with the corresponding index.
names := []"Jeremy", "John", "Joseph"]

```
for _, name := range(names) {
    // name is a copy
    name = name + "changed"
}
fmt.Println(names)
```

```
for position, name := range(names) {
    // this modifies the original value
    names[position] = name + "changed"
}
fmt.Println(names)
```

# 3.3 MAPS

A map is a construct that maps a key to a value. Keys are intended to be unique and can be of any type that implements == and != operators.

Example 3.6 shows how to instantiate a map that stores string keys and integer values. Maps are defined by map[k]v where k is the key and v is the value type. By default, uninitialized maps are nil.

Notice that the statement "Jesus"33 (line 10) is intended to set the value 33 for the key "Jesus" to fail. This is because any map needs to be instantiated. This can be done using the make built-in function (line 12). For map the make function returns the map type (map[k]v) and optionally an initial size. This size is optional as the size can be modified during runtime. Maps can also be initialized by indicating key-value pairs as shown in line 16.

Example 3.6: map Creation.

```
package main

import "fmt"

func main() {
    map := make(map[string]bool)
    map["Jesus"] = false
    map["Jesus"] = 33
```