
## 3.19 Slices Use Pointer Semantic Mutation

It's important to remember that even though I use value semantics to move a slice around the program, when reading and writing a slice, I am using pointer semantics. Sharing individual elements of a slice with different parts of my program can cause unwanted side effects.

Listing 3.28

```go
// Construct a slice of 1 user, set a pointer to that user,
// use the pointer to update likes.

users := make([]user, 1)
ptrUsr0 := &users[0]
ptrUsr0.likes++

for i := range users {
	fmt.Printf("User: Likes: %d\n", i, users[i].likes)
}

Output:
User: 0 Likes: 1
```

A slice is used to maintain a a collection of users. Then a pointer is set to the first user and used to update likes. The output shows that using the pointer is working.

![](img/8be06d78925d0d5a2d2ade851e9bad63_60_0.png)

Then a new user is appended to the collection and the pointer is used again to add a like to the first user.

# Listing 3.29

```go
// Append a new user to the collection. Use the pointer again
// to update likes.

users = append(users, user())
ptrUsr0.likes++

for i := range users {
    fmt.Printf("User: %d Likes: %d\n", i, users[i].likes)
}

Output:
User: 0 Likes: 1
User: 1 Likes: 0
```

However, since the append function replaced the backing array with a new one, the pointer is updating the old backing array and the likes are lost. The output shows the likes for the first user did not increase.

# Figure 3.13

![](img/8be06d78925d0d5a2d2ade851e9bad63_61_0.png)

I have to be careful to know if a slice is going to be used in an append operation during the course of a running program. How I share the slice needs to be considered. Sharing individual indexes may not be the best idea. Sharing an entire slice value may not work when appending is in operation. Probably using a slice as a field in a struct, and sharing the struct value is a better way to go.

## 3.20 Linear Traversal Efficiency

The beauty of a slice is its ability to allow for performing linear traversals that are mechanically sympathetic while sharing data using value semantics to minimize heap allocations.

# Listing 3.30

```go
x := []byte{0x0A, 0x15, 0x0e, 0x28, 0x05, 0x96, 0x0b, 0xd0, 0x00}
a := x[0]
b := binary.LittleEndian.Uint16(x[1:3])
c := binary.LittleEndian.Uint16(x[3:5])
d := binary.LittleEndian.Uint32(x[5:9])

println(a, b, c, d)
```

The code is performing a linear traversal by creating slice values that read different sections of the byte array from beginning to end.

# Figure 3.14

![](img/8be06d78925d0d5a2d2ade851e9bad63_62_0.png)

All the data in this code stays on the stack. No extra copies of the data inside the byte slice are copied.

## 3.21 UTF-8

Go's compiler expects all code to be encoded in the UTF-8 character set. Make sure any file with source code is saved with this encoding or literal strings may be wrong when the program runs.

UTF-8 is a character set where I have bytes, code points, and then characters. One to four bytes of data can represent a code point (int32) and one to many code points can represent a character.

# Listing 3.31

```go
s := "世界 means world"
```

The string above represents 18 bytes, 14 code points, and 14 characters. Each Chinese character I require 3 bytes to represent the code point/character I see.

# Listing 3.32

```go
var buf [utf8.UTFMax]byte
```

There is the utf8 package in the standard library that declares a constant named UTFMax. This constant represents the max number of bytes a code point could require, which is 4.

# Listing 3.33

```go
for i, r := range s {
```

When iterating over a string, the iteration moves code point by code point. Go has an alias type named rune (alias of int32) that represents a code point. Hence the use of the variable r as the value being copied.

On the first iteration, i will equal 0. On the next iteration, i will equal 3. Then in the next iteration, i will equal 6. All subsequent iterations increment i by 1.

# Listing 3.34

```go
rl := utf8.RuneLen(r)
```

The RuneLen function returns the number of bytes required to store the rune. For the first two iterations, rl will equal 3.

# Listing 3.35

```go
si := i + rl
copy(buf[:], s[i:si])
```

The si represents the index position for slice operation to slice the bytes associated with the rune. Then the built-in function copy is used to copy the bytes for the rune into the array. Notice how array can be sliced. This proves that every array is just a slice waiting to happen.

# Listing 3.36

```go
fmt.Printf("%d: %q; codepoint: %x; encoded bytes: %v\n", i, r, buf[:rl])
```

The print statement displays each character, code point, and the set of bytes.

# Listing 3.37

```
Output:
0: '世'; codepoint: e4b896; encoded bytes: [228 184 150]
3: '界'; codepoint: e754c; encoded bytes: [231 133 172]
6: ' '; encoded bytes: [32]
7: 'm'; codepoint: 6d; encoded bytes: [109]
8: 'e'; codepoint: 6565; encoded bytes: [101]
9: 'a'; codepoint: 61; encoded bytes: [97]
10: 'n'; codepoint: 6e; encoded bytes: [110]
11: ' '; encoded bytes: [32]
12: ' '; encoded bytes: [32]
13: 'w'; codepoint: 77; encoded bytes: [119]
14: 'o'; codepoint: 6f; encoded bytes: [111]
15: 'r'; codepoint: 72; encoded bytes: [114]
16: 'l'; codepoint: 6c; encoded bytes: [108]
17: 'd'; codepoint: 64; encoded bytes: [100]
```
*(Wait, the OCR for the hex values and some lines was garbled, I will clean them up based on logic and standard Go output)*:
...
17: 'd'; codepoint: 64; encoded bytes: [100]
```

## 3.22 Defining And Constructing Maps

A map is a data structure that provides support for storing and accessing data by a key. It uses a hash map and bucket system that maintains a contiguous block of memory underneath.

# Listing 3.38

```go
type user struct {
    name string
    username string
}

// Construct a map set to its zero value,
// can store user values based on a key of string.
// Trying to use this map will result in a runtime error (panic).
var users map[string]user

// Construct a map using make,
// can store user values based on a key of string.
users := make(map[string]user)

// Construct a map using literal construction,
// can store user values based on a key of string.
users := map[string]user{}
```

There are several ways to construct a map for use. A map set to its zero value is not usable and will result program panic. The use of the built-in function make and literal construction constructs a map ready for use.

# Listing 3.39

```go
func main() {
	users := make(map[string]user)

	users["Roy"] = user{"Roy", "Roy"}
	users["Ford"] = user{"Ford", "Ford"}
	users["Mouse"] = user{"Mickey", "Mouse"}
	users["Jackson"] = user{"Michael", "Jackson"}

	for key, value := range users {
		fmt.Println(key, value)
	}
}
```

Output:
Roy (Roy)
Ford (Ford)
Mouse (Mickey)
Jackson (Michael)

If the built-in function is used to construct a map, then the assignment operator can be used to add and update values in the map. The order of how keys/values are returned when ranging over a map is undefined by the spec and to the compiler to implement.

# Listing 3.40

```go
func main() {
	users := map[string]user{
		"Roy": {"Roy", "Roy"},
		"Ford": {"Ford", "Ford"},
		"Mouse": {"Mickey", "Mouse"},
		"Jackson": {"Michael", "Jackson"},
	}

	for key, value := range users {
		fmt.Println(key, value)
	}
}
```

Output:
Ford (Ford)
Jackson (Michael)
Roy (Roy)
Mouse (Mickey)

In this case, the output was returned in a different order from how they are listed in the construction. The current algorithm for maps will return the results in a random order once the number of values reaches a certain limit. Again, this is a compiler implementation that is allowed to change. I can’t depend on it.

## 3.23 Lookups and Deleting Map Keys

Once data is stored inside of a map, to extract any data a key lookup is required.

# Listing 3.41

```go
user1, exists1 := users["Bill"]
user2, exists2 := users["Ford"]
fmt.Println("Bill", exists1, user1)
fmt.Println("Ford", exists2, user2)
```

```
Output:
Bill: false {}
Ford: true {Henry Ford}
```

To perform a key lookup, square brackets are used with the map variable. Two values can be returned from a map lookup: the value and a boolean that represents if the value was found or not. If I don't need to know this, I can leave the "exists" variable out.

When a key is not found in the map, the operation returns a value of the map type set to its zero value state. I can see this with the "Bill" key lookup. Don't use zero value to determine if a key exists in the map or not since zero value may be valid and what was actually stored for the key.

# Listing 3.42

```go
delete(users, "Roy")
```

## 3.24 Key Map Restrictions

Not all types can be used as a key.

# Listing 3.43

```go
type slice []user
users := make(map[slice]user)
```

```
Compiler Error:
invalid map key type slice
```
