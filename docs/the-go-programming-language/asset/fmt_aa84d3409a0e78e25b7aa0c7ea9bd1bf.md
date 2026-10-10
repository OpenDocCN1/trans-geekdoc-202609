
If the `readList` function ([§12.6](#ebook_split_116.html#id-exampledecodingsexpressions)), for example, should read a string from the input while populating a variable of type `int`, the call to `reflect.Value.SetString` will panic. Most programs that use reflection have similar hazards, and considerable care is required to keep track of the type, addressability, and settability of each `reflect.Value`.

The best way to avoid this fragility is to ensure that the use of reflection is fully encapsulated within your package and, if possible, avoid `reflect.Value` in favor of specific types in your package’s API, to restrict inputs to legal values. If this is not possible, perform additional dynamic checks before each risky operation. As an example from the standard library, when `fmt.Printf` applies a verb to an inappropriate operand, it does not panic mysteriously but prints an informative error message. The program still has a bug, but it is easier to diagnose.

[Click here to view code image](#ch12_images.html#id352pro01_r)

```
fmt.Printf("%d %s\n", "hello", 42) // "%!d(string=hello) %!s(int=42)"
```

Reflection also reduces the safety and accuracy of automated refactoring and analysis tools, because they can’t determine or rely on type information.

The second reason to avoid reflection is that since types serve as a form of documentation and the operations of reflection cannot be subject to static type checking, heavily reflective code is often hard to understand. Always carefully document the expected types and other invariants of functions that accept an `interface{}` or a `reflect.Value`.

The third reason is that reflection-based functions may be one or two orders of magnitude slower than code specialized for a particular type. In a typical program, the majority of functions are not relevant to the overall performance, so it’s fine to use reflection when it makes the program clearer. Testing is a particularly good fit for reflection since most tests use small data sets. But for functions on the critical path, reflection is best avoided.

# 13. Low-Level Programming

The design of Go guarantees a number of safety properties that limit the ways in which a Go program can “go wrong.” During compilation, type checking detects most attempts to apply an operation to a value that is inappropriate for its type, for instance, subtracting one string from another. Strict rules for type conversions prevent direct access to the internals of built-in types like strings, maps, slices, and channels.

For errors that cannot be detected statically, such as out-of-bounds array accesses or nil pointer dereferences, dynamic checks ensure that the program immediately terminates with an informative error whenever a forbidden operation occurs. Automatic memory management (garbage collection) eliminates “use after free” bugs, as well as most memory leaks.

Many implementation details are inaccessible to Go programs. There is no way to discover the memory layout of an aggregate type like a struct, or the machine code for a function, or the identity of the operating system thread on which the current goroutine is running. Indeed, the Go scheduler freely moves goroutines from one thread to another. A pointer identifies a variable without revealing the variable’s numeric address. Addresses may change as the garbage collector moves variables; pointers are transparently updated.

Together, these features make Go programs, especially failing ones, more predictable and less mysterious than programs in C, the quintessential low-level language. By hiding the underlying details, they also make Go programs highly portable, since the language semantics are largely independent of any particular compiler, operating system, or CPU architecture. (Not entirely independent: some details leak through, such as the word size of the processor, the order of evaluation of certain expressions, and the set of implementation restrictions imposed by the compiler.)

Occasionally, we may choose to forfeit some of these helpful guarantees to achieve the highest possible performance, to interoperate with libraries written in other languages, or to implement a function that cannot be expressed in pure Go.

In this chapter, we’ll see how the `unsafe` package lets us step outside the usual rules, and how to use the `cgo` tool to create Go bindings for C libraries and operating system calls.

The approaches described in this chapter should not be used frivolously. Without careful attention to detail, they may cause the kinds of unpredictable, inscrutable, non-local failures with which C programmers are unhappily acquainted. Use of `unsafe` also voids Go’s warranty of compatibility with future releases, since, whether intended or inadvertent, it is easy to depend on unspecified implementation details that may change unexpectedly.

The `unsafe` package is rather magical. Although it appears to be a regular package and is imported in the usual way, it is actually implemented by the compiler. It provides access to a number of built-in language features that are not ordinarily available because they expose details of Go’s memory layout. Presenting these features as a separate package makes the rare occasions on which they are needed more conspicuous. Also, some environments may restrict the use of the `unsafe` package for security reasons.

Package `unsafe` is used extensively within low-level packages like `runtime`, `os`, `syscall`, and `net` that interact with the operating system, but is almost never needed by ordinary programs.

## 13.1 `unsafe.Sizeof`, `Alignof`, and `Offsetof`

The `unsafe.Sizeof` function reports the size in bytes of the representation of its operand, which may be an expression of any type; the expression is not evaluated. A call to `Sizeof` is a constant expression of type `uintptr`, so the result may be used as the dimension of an array type, or to compute other constants.

[Click here to view code image](#ch13_images.html#id354pro01_r)

```
import "unsafe"

fmt.Println(unsafe.Sizeof(float64(0))) // "8"
```

`Sizeof` reports only the size of the fixed part of each data structure, like the pointer and length of a string, but not indirect parts like the contents of the string. Typical sizes for all non-aggregate Go types are shown below, though the exact sizes may vary by toolchain. For portability, we’ve given the sizes of reference types (or types containing references) in terms of words, where a word is 4 bytes on a 32-bit platform and 8 bytes on a 64-bit platform.

Computers load and store values from memory most efficiently when those values are properly *aligned*. For example, the address of a value of a two-byte type such as `int16` should be an even number, the address of a four-byte value such as a `rune` should be a multiple of four, and the address of an eight-byte value such as a `float64`, `uint64`, or 64-bit pointer should be a multiple of eight. Alignment requirements of higher multiples are unusual, even for larger data types such as `complex128`.

For this reason, the size of a value of an aggregate type (a struct or array) is at least the sum of the sizes of its fields or elements but may be greater due to the presence of “holes.” Holes are unused spaces added by the compiler to ensure that the following field or element is properly aligned relative to the start of the struct or array.

| **Type** | **Size** |
| --- | --- |
| `bool` | 1 byte |
| `intN`, `uintN`, `floatN`, `complexN` | `N` / 8 bytes (for example, `float64` is 8 bytes) |
| `int`, `uint`, `uintptr` | 1 word |
| `*T` | 1 word |
| `string` | 2 words (data, len) |
| `[]T` | 3 words (data, len, cap) |
| `map` | 1 word |
| `func` | 1 word |
| `chan` | 1 word |
| `interface` | 2 words (type, value) |
