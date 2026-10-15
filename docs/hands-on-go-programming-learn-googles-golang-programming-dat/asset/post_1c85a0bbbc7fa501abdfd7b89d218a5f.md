
## 6.2 Declaration of Go maps

A map is declared using the following syntax:

```
var m map[key_type]value_type
```

For example, you can declare a map of string keys to int values as shown below:

```
var m map[string]int
```

The zero value of a map is nil. A nil map has no keys. Therefore, any attempt to add keys to a nil map will result in a runtime error. Let’s look at the following example:

### Program 6.1

```go
// Go program to explain the declaration of a map

package main

import "fmt"

func main() {
    var m1 map[string]int
    fmt.Println(m1)
    if m1 == nil {
```
fmt.Println("Map is empty")
} else {
fmt.Println("Map is not empty")
}

// Attempt to add keys to a nil map will throw runtime error
//m1["ten"] = 10
}
```

The following will be the output for the above code:

```
map[]
Map is empty
```

If you uncomment the statement m1["ten"] = 10 the program will give a runtime error. Therefore, it is necessary to initialize a map before adding items to it.

## 6.3 Initialization of Go Maps

A map can be initialized by either using a map literal or the built-in make() function.

### 6.3.1 Initializing maps using map literal

A map literal is the easiest way to initialize a map with some data. You just need to pass the key-value pairs separated by a colon inside curly braces, and the last trailing comma is necessary as otherwise, you’ll get a compiler error.

### Program 6.2

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

```
map[a:10 b:20 c:30 d:40 e:50]
```

You can also create an empty map using a map literal by leaving the curly braces empty.

### 6.3.2 Initializing a map using make() function

You can initialize a map using the built-in make() function. You just need to pass the type of the map to the make() function, and it will return an initialized and ready-to-use the map. Let’s look at the following program:

### Program 6.3

```go
// Go program to initialize a map using make() function

var m = make(map[string]int)

package main

import "fmt"

func main() {
var m1 = make(map[string]int)
fmt.Println(m1)
if m1 == nil {
fmt.Println("Map is empty")
} else {
fmt.Println("Map is not empty")
}

// make() function returns an initialized and ready to use map
```
```go
// you can add new keys
m["ten"] = 10
fmt.Println(m)
}
```
```

The following will be the output for the above code:

```text
map[]
Map is not empty
map[ten:10]
```

## 6.4 Iterating over Go maps

You can iterate over a map using a range form of the for loop. It gives you the key and value pair in every iteration. Let’s look at the following program:

### Program 6.4

```go
// Go program to explain iteration over a map

package main

import "fmt"

func main() {
var my_map = map[string]string{
"Maharashtra": "Mumbai",
"Uttar_Pradesh": "Lucknow",
"Rajasthan": "Jaipur",
"Karnataka": "Bengaluru",
}

for state, capital := range my_map {
fmt.Println(state, capital)
}
}
```

The following will be the output for the above code:

```
Maharashtra Mumbai
Uttar_Pradesh Lucknow
Rajasthan Jaipur
Karnataka Bengaluru
```

Let’s look at the following example:

### Program 6.5

```go
// Go program to explain iteration over a map

package main

import "fmt"

func main() {
var my_map = map[string]int{
"India": 1947,
"Singapore": 1965,
"Australia": 1901,
"Malaysia": 1957,
}

for country, year_of_independence := range my_map {
fmt.Println(country, year_of_independence)
}
}
```

The following will be the output for the above code:

```
India 1947
Singapore 1965
Australia 1901
Malaysia 1957
```

A map is an unordered collection and therefore, the iteration order of a map is not guaranteed to be the same every time that you iterate over it. So, if you run the above program multiple times, you’ll get the results in different orders.

## 6.5 Adding key-value pairs in maps

In maps, you can add key-value pairs in the initialized map using the following syntax:

```
map_name[key]=value
```

Let’s look at the following example:

### Program 6.6

// Go program to add key-value pairs in a map

```go
package main

import "fmt"

func main() {
// Create and initialize a map
var my_map = map[int]string{
1: "US",
91: "India",
86: "China",
44: "UK",
}

fmt.Println("Original Map\n", my_map)
```
```
// Adding new key-value pairs in the map
my_map[39] = "Italy"
my_map[81] = "Japan"
fmt.Println("\nMap after adding new key-value pairs \n", my_map)
}
```

The following will be the output for the above code:

Original Map

```
map[1:US 44:UK 86:China 91:India]
```

Map after adding new key-value pairs

```
map[1:US 39:Italy 44:UK 81:Japan 86:China 91:India]
```

## 6.6 Updating key-value pairs in maps

In a map, if you try to add an already existing key, it will merely override or update the value of that key with the new value. Let’s look at the following program:

### Program 6.7

// Go program to update key-value pairs in a map

```
package main

import "fmt"

func main() {
// Create and initialize a map
var my_map = map[int]string{
1: "US",
91: "India",
86: "China",
44: "UK",
}

fmt.Println("Original Map\n", my_map)
// Updating values of the map
my_map[1] = "United States"
my_map[44] = "United Kingdom"
fmt.Println("\nAfter updating values of the map \n", my_map)
}
```

## 6.7 Retrieving the value of a key in maps

In maps, you can retrieve a value with the help of keys using the following syntax:

```
map_name[key]
```

If a key doesn’t exist in the given map, it will return a zero value, i.e., nil; and if the key exists in the given map, it will return the value related to that key.

### Program 6.8

```go
// Go program to retrieve the value of a key in a map

package main

import "fmt"

func main() {
// Create and initialize a map
var my_map = map[int]string{
1: "US",
91: "India",
86: "China",
44: "UK",
}
```
```
fmt.Println("Original Map:", my_map)

// Retrieve values with the help of keys
v1 := my_map[91]
v2 := my_map[93]
v3 := my_map[44]
fmt.Println("Value of key[91]:", v1)
fmt.Println("Value of key[93]:", v2)
fmt.Println("Value of key[44]:", v3)
}
```

The following will be the output for the above code:

```
Original Map: map[1:US 44:UK 86:China 91:India]
Value of key[91]: India
Value of key[93]:
Value of key[44]: UK
```

## 6.8 Checking if a key exists in Go maps

When you retrieve the value assigned to a given key using the syntax it returns an additional Boolean value as well which is true if the key exists in the map and false if it doesn’t exist.

You can check for the existence of a key in a map by using the following two-value assignment:

```
value, variable_name := map_name[key]
```

The Boolean variable will be true if the key exists and false otherwise.

### Program 6.9

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
86: "China",
44: "UK",
}
```

```
fmt.Println("Original Map:", my_map)
```

```
// Checking key is available or not in map
country, x := my_map[91]
fmt.Println("\nKey present or not:", x)
fmt.Println("Value:", country)
}
```

The following will be the output for the above code:

Original Map: map[1:US 44:UK 86:China 91:India]

Key present or not: true
Value: India

If you just want to check for the existence of a key without retrieving the value associated with that key, then you can use an _ (underscore) in the place of the first value.

```
_, variable_name := map_name[key]
```

Let’s look at the following example:

### Program 6.10
