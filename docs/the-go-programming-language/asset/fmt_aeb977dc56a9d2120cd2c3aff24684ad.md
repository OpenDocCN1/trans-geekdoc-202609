
The language specification does not guarantee that the order in which fields are declared is the order in which they are laid out in memory, so in theory a compiler is free to rearrange them, although as we write this, none do. If the types of a struct’s fields are of different sizes, it may be more space-efficient to declare the fields in an order that packs them as tightly as possible. The three structs below have the same fields, but the first requires up to 50% more memory than the other two:

```
// 64-bit    32-bit
struct{ bool; float64; int16 }   // 3 words   4 words
struct{ float64; int16; bool }   // 2 words   3 words
struct{ bool; int16; float64 }   // 2 words   3 words
```

The details of the alignment algorithm are beyond the scope of this book, and it’s certainly not worth worrying about every struct, but efficient packing may make frequently allocated data structures more compact and therefore faster.

The `unsafe.Alignof` function reports the required alignment of its argument’s type. Like `Sizeof`, it may be applied to an expression of any type, and it yields a constant. Typically, boolean and numeric types are aligned to their size (up to a maximum of 8 bytes) and all other types are word-aligned.

The `unsafe.Offsetof` function, whose operand must be a field selector `x.f`, computes the offset of field `f` relative to the start of its enclosing struct `x`, accounting for holes, if any.

Figure 13.1 shows a struct variable `x` and its memory layout on typical 32- and 64-bit Go implementations. The gray regions are holes.

```
var x struct {
    a bool
    b int16
    c []int
}
```

![Holes in a struct.](graphics/size-align-offset.png)

**Figure 13.1.** Holes in a struct.

The table below shows the results of applying the three `unsafe` functions to `x` itself and to each of its three fields:

```
Typical 32-bit platform:
Sizeof(x)   = 16  Alignof(x)   = 4
Sizeof(x.a) = 1   Alignof(x.a) = 1  Offsetof(x.a) = 0
Sizeof(x.b) = 2   Alignof(x.b) = 2  Offsetof(x.b) = 2
Sizeof(x.c) = 12  Alignof(x.c) = 4  Offsetof(x.c) = 4

Typical 64-bit platform:
Sizeof(x)   = 32  Alignof(x)   = 8
Sizeof(x.a) = 1   Alignof(x.a) = 1  Offsetof(x.a) = 0
Sizeof(x.b) = 2   Alignof(x.b) = 2  Offsetof(x.b) = 2
Sizeof(x.c) = 24  Alignof(x.c) = 8  Offsetof(x.c) = 8
```

Despite their names, these functions are not in fact unsafe, and they may be helpful for understanding the layout of raw memory in a program when optimizing for space.

## 13.2 `unsafe.Pointer`

Most pointer types are written `*T`, meaning “a pointer to a variable of type `T`.” The `unsafe.Pointer` type is a special kind of pointer that can hold the address of any variable. Of course, we can’t indirect through an `unsafe.Pointer` using `*p` because we don’t know what type that expression should have. Like ordinary pointers, `unsafe.Pointer`s are comparable and may be compared with `nil`, which is the zero value of the type.

An ordinary `*T` pointer may be converted to an `unsafe.Pointer`, and an `unsafe.Pointer` may be converted back to an ordinary pointer, not necessarily of the same type `*T`. By converting a `*float64` pointer to a `*uint64`, for instance, we can inspect the bit pattern of a floating-point variable:

```
package math

func Float64bits(f float64) uint64 { return *(*uint64)(unsafe.Pointer(&f)) }

fmt.Printf("%#016x\n", Float64bits(1.0)) // "0x3ff0000000000000"
```

Through the resulting pointer, we can update the bit pattern too. This is harmless for a floating-point variable since any bit pattern is legal, but in general, `unsafe.Pointer` conversions let us write arbitrary values to memory and thus subvert the type system.

An `unsafe.Pointer` may also be converted to a `uintptr` that holds the pointer’s numeric value, letting us perform arithmetic on addresses. (Recall from Chapter 3 that a `uintptr` is an unsigned integer wide enough to represent an address.) This conversion too may be applied in reverse, but again, converting from a `uintptr` to an `unsafe.Pointer` may subvert the type system since not all numbers are valid addresses.

Many `unsafe.Pointer` values are thus intermediaries for converting ordinary pointers to raw numeric addresses and back again. The example below takes the address of variable `x`, adds the offset of its `b` field, converts the resulting address to `*int16`, and through that pointer updates `x.b`:

gopl.io/ch13/unsafeptr

```
var x struct {
    a bool
    b int16
    c []int
}

// equivalent to pb := &x.b
pb := (*int16)(unsafe.Pointer(
    uintptr(unsafe.Pointer(&x)) + unsafe.Offsetof(x.b)))
*pb = 42

fmt.Println(x.b) // "42"
```

Although the syntax is cumbersome—perhaps no bad thing since these features should be used sparingly—do not be tempted to introduce temporary variables of type `uintptr` to break the lines. This code is incorrect:

```
// NOTE: subtly incorrect!
tmp := uintptr(unsafe.Pointer(&x)) + unsafe.Offsetof(x.b)
pb := (*int16)(unsafe.Pointer(tmp))
*pb = 42
```

The reason is very subtle. Some garbage collectors move variables around in memory to reduce fragmentation or bookkeeping. Garbage collectors of this kind are known as *moving GCs*. When a variable is moved, all pointers that hold the address of the old location must be updated to point to the new one. From the perspective of the garbage collector, an `unsafe.Pointer` is a pointer and thus its value must change as the variable moves, but a `uintptr` is just a number so its value must not change. The incorrect code above *hides a pointer* from the garbage collector in the non-pointer variable `tmp`. By the time the second statement executes, the variable `x` could have moved and the number in `tmp` would no longer be the address `&x.b`. The third statement clobbers an arbitrary memory location with the value 42.

There are myriad pathological variations on this theme. After this statement has executed:

```
pT := uintptr(unsafe.Pointer(new(T))) // NOTE: wrong!
```

there are no pointers that refer to the variable created by `new`, so the garbage collector is entitled to recycle its storage when this statement completes, after which `pT` contains the address where the variable was but is no longer.

No current Go implementation uses a moving garbage collector (though future implementations might), but this is no reason for complacency: current versions of Go do move *some* variables around in memory. Recall from Section 5.2 that goroutine stacks grow as needed. When this happens, all variables on the old stack may be relocated to a new, larger stack, so we cannot rely on the numeric value of a variable’s address remaining unchanged throughout its lifetime.

At the time of writing, there is little clear guidance on what Go programmers may rely upon after an `unsafe.Pointer` to `uintptr` conversion (see Go issue 7192), so we strongly recommend that you assume the bare minimum. Treat all `uintptr` values as if they contain the *former* address of a variable, and minimize the number of operations between converting an `unsafe.Pointer` to a `uintptr` and using that `uintptr`. In our first example above, the three operations—conversion to a `uintptr`, addition of the field offset, conversion back—all appeared within a single expression.
