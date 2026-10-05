
## 5.1. Statement Basics

### Table 5.1 Built-In Functions

| Syntax | Description/result |
|---|---|
| append(s, ...) | The slice it given plus the new items at the end if the slice's capacity is sufficient; otherwise a new slice with the original items plus the new items at the end (see 4.2.3, 156 ◄) |
| cap(x) | The capacity of slice x or the buffer capacity of channel x or the length of array (or the array pointed to by) x; see also len() (see §4.2, 148 ◄) |
| close(ch) | Closes channel (but not for receive-only channels). No more data can be sent to the channel. Data continue to be received from the channel (e.g., any sent but not yet received values), and when there are no more values in the channel, receivers will get the data type's zero value. |
| complex(r, i) | A complex128 with the given r (real) and i (imaginary) parts, both of type float64 (see §2.3.2, 70 ◄) |
| copy(dst, s) | Copies (overlapping) items from the src slice into the dst slice, truncating if there is not enough; or copies s of string bytes to b of type []byte (see §4.2.3, 156 ◄ 268) |
| delete(m, k) | Deletes the item with key from map m or does nothing if there's no such key (see §4.3, 164 ◄) |
| imag(cx) | The imaginary part of cx of type complex128 as a float64 (see §2.3.2, 70 ◄) |
| len(x) | The length of slice x or the number of items queued in channel x's buffer or the length of array (or the array pointed to) x or the number of items in map x or the number of bytes in string x; see also cap() (see §4.2, 156 ◄) |
| make(T) | A reference to a slice, map, or channel of type T. If n is this slice's length, or a hint to a map of many items, or a channel's buffer size. For slices, n and m may be given to specify the length and capacity (see 150 ◄ for slices, 165 ◄ for maps, and Chapter 7 for channels). |
| new(T) | A pointer to a value of type T (see §4.1, 140 ◄) |
| panic(x) | Raises a catchable runtime exception with value x (see §5.5.1, 213 ◄) |
| real(cx) | The real part of cx of type complex128 as a float64 (see §2.3.2, 70 ◄) |
| recover() | Catches a runtime exception (see §5.5.1, ► 213) |

## Chapter 5. Procedural Programming

gof Go programs in a standardized way. In fact, all the Go standard library’s source code uses gofmt which ensures the code has a consistent layout, even though it is the product of many different programmers’ work.*

Go supports the ++ (increment) and -- (decrement) operators listed in Table 2.4 (59 triangleleft 3, 5). They are both postfix operators, that is, they must follow the operand they apply to, and they do not return a value. These constraints prevent the operators from being used as expressions, and that they cannot be used in semantically ambiguous contexts—for example, we cannot use one of the operators to an argument in a function call or write = i++ in Go (although we could be in C and C++ where the results are undefined).

Assignments are made using the = operator. Variables can be created and assigned using = in conjunction with var—for example, var x=5 creates a new variable x of type int and value 5. (Exactly the same can be achieved var x int= 5 or x := 5) The variable assigned must be compatible with the value being assigned. If = is used without the variable on its left-hand side must already exist. Multiple comma-separated variables can be assigned to, and we can use the blank identifier (), which is compatible with any of the values assigned. Multiple assignments make it easy to swap two values without the need for an explicit temporary variable—for example, a, b=a.

The short variable declaration operator (:=) is used to declare a new variable and assign it in a single statement. Multiple comma-separated variables can be used in the same way as using the = operator, except that at least one nonblank variable must be new. If there is a variable that already exists it will be assigned without creating a new variable—unless the := is at the start of the new scope such as an if or for statement’s initializing statement (5.2.1, ▷ 192; 5.3, triangleright 203).

```go
a, b, c := 2, 3, 5
for a := 7; a < 8; a++ // a is unintentionally shadowing the outer a
b := 11 // b is unintentionally shadowing the outer b
c := 13 // c is the intended c \checkmark
fmt.Printf("inner: a-%d b-%d c-%d\n", a, b, c)
}
fmt.Printf("outer: a-%d b-%d c-%d\n", a, b, c)

inner: a->7 b->11 c->13
outer: a->2 b->3
```

> * At the time of this writing, gofmt does not support line wrapping to a maximum line width, and in cases gofmt will join two or more wrapped lines to make one long line. The book’s source code was automatically extracted from examples and tests and inserted into the book’s camera-ready PDF file—but this is subject to a 75-character-per-line limit. So, for the book’s code, gofmt was used, and then long lines were manually wrapped.

This code snippet shows how the := operator can create "shadow" variables. In this snippet, inside the loop the a and b variables shadow variables from the outer scope, and while legal, this is almost certainly a programming error. On the other hand, there is only c variable (from the outer scope), so its usage is correct and as intended. Variables that shadow other variables can be very convenient, as we will see shortly, but careless use can cause problems.

As we will discuss later, the := operator's behavior in block-scoped contexts is a common trap for beginners, leading to subtle logic errors where a local variable is updated instead of the intended outer one.

As we will discuss later, the := operator's behavior in block-scoped contexts is a common trap for beginners, leading to subtle logic errors where a local variable is updated instead of the intended outer one.

As we will discuss later, the := operator's behavior in block-scoped contexts is a common trap for beginners, leading to subtle logic errors where a local variable is updated instead of the intended outer one.

As we will discuss later, the := operator's behavior in block-scoped contexts is a common trap for beginners, leading to subtle logic errors where a local variable is updated instead of the intended outer one.

### 5.1. Statement Basics

(Note: The OCR OCR contained significant repetitions and fragments.. I have processed the flow based on the provided source text.)
