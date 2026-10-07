
and not 12 bytes. Since all the fields allow the struct value to fall on a 4-byte alignment, no extra padding bytes are necessary.

Figure 2.3

| Pi | Counter | Flag | Flag2 |
|---|---|---|---|
| 0 | 4 | 6 | 7 8 |

## 2.8 Assigning Values

If I have two different named types that are identical in structure, I can't assign a value of one to the other.

For example, if the types example1 and example2 are declared using the same exact declaration and we initialize two variables.

Listing 2.13

```
var ex1 example1
var ex2 example2
```

I can't assign these two variables to each other since they are of different named types. The fact that they are identical in structure is irrelevant.

Listing 2.14

```
ex1 = ex2 // Not allowed, compiler error
```

To perform this assignment, I would have to use conversion syntax and since they are identical in structure, the compiler will allow this.

Listing 2.15

```
ex1 = example1(ex2) // Allowed, NO compiler error
```

However, if ex2 was changed to be declared as an unnamed type using the same exact declaration as ex1, no conversion syntax would be required.

Listing 2.16

```
var ex2 struct {
  flag bool
  counter int16
  pi float32
}
ex1 = ex2 // Allowed, NO need for conversion syntax
```

The compiler will allow assignment without the need for conversion.

## 2.9 Pointers

Pointers serve the purpose of sharing values across program boundaries. There are several types of program boundaries. The most common one is between function calls. There is also a boundary between Goroutines which I have notes for later.

When a Go program starts up, the Go runtime creates a Goroutine. Goroutines are lightweight application threads with many of the same semantics as operating system threads. Their job is to manage the physical execution of a distinct set of instructions. Every Go program has at least 1 Goroutine that I call the main Goroutine.

Each Goroutine is given its own block of memory called a stack. Each stack starts out as a 2048 byte (2k) allocation. It's very small, but stacks can grow in size over time.

Figure 2.4

![](img/8be06d78925d0d5a2d2ade851e9bad63_32_0.png)

Every time a function is called, a block of stack space is taken to help the Goroutine execute the instructions associated with that function. Each individual block of memory is called a frame.

The size of a frame for a given function is calculated at compile time. No value be constructed on the stack unless the compiler knows the size of that value at compile time. If the compiler doesn't know the size of a value at compile time, the value has to be constructed on the heap.

Stacks are self cleaning and zero value helps with the initialization of the stack. Every time I make a function call, and a frame of memory is blocked out, the memory for that frame is initialized, which is how the stack is self cleaning. On a function return, the memory for the frame is left alone since it's unknown that memory will be needed again. It would be inefficient to initialize memory on returns.

## 2.10 Pass By Value

All data is moved around the program by value. This means as data is passed across program boundaries, each function or Goroutine is given its own copy of the data. There are two types of data I work with, the value itself (int, string, user) or the value's address. Addresses are data that need to be copied and stored across program boundaries.

The following code attempts to explain this more.

Listing 2.17

```go
func main() {
  // Declare variable of type int with a value of 10
  count := 10

  // To get the address of a value, use the & operator.
  println("count:\tValueOf(",", count, "\tAddrOf(",", &count, ")")

  // Pass a copy of the "value" count (what's in the box)
  // to the increment1 function.
  increment1(count)

  // Print out the "value" and "address" of count.
  // The value of count will not change after the function call.
  println("count:\tValueOf(", count, "\tAddrOf(",", &count, ")")

  // Pass a copy of the "address" of count (where is considered a pass by
  // to the increment2 function. This is still considered pass by
  // and not pass by reference because addresses are values.
  increment2(&count)

  // Print out the "value" and "address" of count.
  // The value of count has changed after the function call.
  println("count:\tValueOf(", count, "\tAddrOf(",", &count, ")")
}

// increment1 declares the function to accept its own copy of
// and integer value.
func increment1(inc int) {
  // Increment the local copy of the caller's int value.
  inc++
  println("inc:\tValueOf(", inc, "\tAddrOf(",", &inc, ")")
}

// increment2 declares the function to accept its own copy of
// by an address that points to an integer value.
// Pointer variables are literal types and are declared using *.
func increment2(inc *int) {
  // Increment the caller's value through the pointer.
  *inc++
  println("inc2:\tValueOf(", inc, "\tAddrOf(",", inc, "\tPoints To(", inc, ")")
}
```

Output:
count: Value Of[ 10 ] Addr Of[ 0xc000050738 ]
incl: Value Of[ 11 ] Addr Of[ 0xc000050730 ]
count: Value Of[ 10 ] Addr Of[ 0xc000050738 ]
inc2: Value Of[ 0xc000050738 ] Addr Of[ 0xc000050748 ] Points To[ 11 ]
count: Value Of[ 11 ] Addr Of[ 0xc000050738 ]

There are lots of details related to the stacks and pointers, so to learn more read the post in chapter 14 titled, Stacks and Pointer Mechanics.

## 2.11 Escape Analysis

The algorithm compiler uses to determine if a value should be constructed on the stack or heap. Understanding escape analysis is about value ownership. The idea is, when a value is constructed within the scope of a function, then the functions ask, does the value being constructed still have to exist when the function returns? If the answer is no, the value can be constructed on the stack. If the answer is yes, the value must be constructed on the heap.

Note: The ownership rule is a good base rule for identifying code that causes allocations. However, I must appreciate that escape analysis has flaws. Also, the algorithm takes opportunities to leverage compiler optimizations to save on allocations.

Listing 2.18

```go
// user represents a user in the system.
type user struct {
    name string
    email string
}

func stayOnStack() user {
    u := user(
        name: "Bill",
        email: "bill@email.com",
    )
    return u
}
```

The stayOnStack function is using value semantics to return a user value back to the caller. In other words, the caller gets their own copy of the user value being constructed. When the stayOnStack function is called and returns, the user value it constructs no longer needs to exist, the caller is getting their own copy. Therefore, the construction of the user value inside of stayOnStack can happen on the stack. No allocation.

Listing 2.19

```go
type user struct {
    name string
    email string
}

func escapeToHeap() *user {
    u := user(
        name: "Bill",
        email: "bill@email.com",
    )

    return &u
}
```

The escapeToHeap function is using pointer semantics to return a user value back to the caller. In other words, the caller gets shared access (an address) to the user value being constructed. When the escapeToHeap function is called and returns, the user value it constructs still need to exist, since the caller is getting shared access to the value. Therefore, the construction of the user value inside of escapeToHeap can’t happen on the stack, it must happen on the heap. Yes allocation.

Think about what would happen if the user value in the last example was constructed on the stack using pointer semantics on the return.
