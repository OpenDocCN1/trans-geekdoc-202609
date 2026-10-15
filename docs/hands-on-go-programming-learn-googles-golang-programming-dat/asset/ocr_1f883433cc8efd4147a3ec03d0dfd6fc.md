# ## 6.8 Checking if a key exists in Go maps

When you retrieve the value assigned to a given key using the syntax it returns an additional Boolean value as well which is true if the key exists in the map and false if it doesn’t exist.

You can check for the existence of a key in a map by using the following two-value assignment:

```
value, variable_name := map_name[key]
```

The Boolean variable will be true if the key exists and false otherwise.

# **Program 6.9**

```
```go
// Go program to check if a key exists in a map

package main

import "fmt"

func main() {
    // Create and initialize a map
    var my_map = map[int]string{
        1: "US",
        91: "India",
```
```