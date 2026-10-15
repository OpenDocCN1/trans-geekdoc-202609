# 6.3.1 Initializing maps using map literal

A map literal is the easiest way to initialize a map with some data. You just need to pass the key-value pairs separated by a colon inside curly braces, and the last trailing comma is necessary as otherwise, you’ll get a compiler error.

# Program 6.2

// Go program to initialize a map using map literal

```
package main

import "fmt"

func main() {
var m1 = map[string]int{
"a": 10,
"b": 20,
"c": 30,
"d": 40,
"e": 50,
}
fmt.Println(m1)
}
```

The following will be the output for the above code: