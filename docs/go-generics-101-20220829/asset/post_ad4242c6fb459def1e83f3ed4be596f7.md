
## Go Generics 101

Tapir Liu

- 7.5 The type literal in a composite literal must have a core type ................................ 38
- 7.6 An element index operation requires the container operand's type set may not include maps and non-maps at the same time ................................ 39
- 7.7 A (sub)slice operation requires the container operand has a core type ................................ 39
- 7.8 In a for-range loop, the ranged container is required to have a core type ................................ 40
- 7.9 Type parameter involved conversions ................................ 42
- 7.10 Type parameter involved assignments ................................ 43
- 7.11 Calls to predeclared functions ................................ 45
- 7.12 A call to the predeclared len or cap functions is valid if it is valid for all of the types in the type set of the argument ................................ 45
- 7.13 A call to the predeclared new function has no extra requirements for its argument ................................ 46
- 7.14 A call to the predeclared make function requires its first argument (the container type) to have a core type ................................ 47
- 7.15 A call to the predeclared delete function requires all types in the type set of its first argument to have an identical key type ................................ 48
- 7.16 A call to the predeclared close function requires all types in the type set of its argument to be channel types ................................ 48
- 7.17 Calls to predeclared complex, real and imag functions don’t accept arguments of type parameter now ................................ 48
- 7.18 About constraints with empty type sets ................................ 49

### 8 The Status Quo of Go Custom Generics

- 8.1 Type declarations inside generic functions are not currently supported ................................ 50
- 8.2 Generic type aliases are not supported currently ................................ 50
- 8.3 Embedding type parameters in struct types is not allowed now ................................ 51
- 8.4 The method set of a constraint is not calculated completely for some cases ................................ 51
- 8.5 No ways to specify a field set for a constraint ................................ 52
- 8.6 No ways to use common fields for a constraint if the constraint has not a core (struct) type ................................ 52
- 8.7 Fields of values of type parameters are not accessible ................................ 53
- 8.8 Type switches on values of type parameters are not supported now ................................ 53
- 8.9 Generic methods are not supported ................................ 54
- 8.10 There are no ways to construct a constraint which allows assignments involving types of unspecific underlying types ................................ 55
- 8.11 There are no ways to construct a constraint which allows conversion involving types of unspecific underlying types ................................ 55

## Chapter 2

### About Go Generics 101

Starting from version 1.18 (the current latest version), Go supports custom generics.

This book talks about the custom generics feature of the Go programming language. The content in this book includes:

- custom generic syntax
- type constraints and type parameters
- type arguments and type inference
- how to write valid custom generic code
- current implementation/design restrictions

A reader needs to be familiar with general Go programming to read this book. In particular, readers of this book should be familiar with Go type system, including Go built-in generics, which and Go custom generics are two different systems.

Currently, the book mainly focuses on the syntax of, and concepts in, custom generics. More practical examples will be provided when I get more experiences of using custom generics.

## Chapter 4

### First Look of Custom Generics

In the custom generics world, a type may be declared as a generic type, and a function may be declared as generic function. In addition, generic types are defined types, so they may have methods.

The declaration of a generic type, generic function, or method of a generic type contains a type parameter list part, which is the main difference from the declaration of an ordinary type, function, or method.

#### 4.1 A generic type example

Firstly, let’s view an example to show how generic types look like. It might be not a perfect example, but it does show the usefulness of custom generic types.

```go
package main

import "sync"

type Lockable[T any] struct {
    sync.Mutex
    Data T
}

func main() {
    var n Lockable[uint32]
    n.Lock()
    n.Data++
    n.Unlock()

    var f Lockable[float64]
    f.Lock()
    f.Data += 1.23
    f.Unlock()

    var b Lockable[bool]
    b.Lock()
    b.Data = !b.Data
    b.Unlock()
}
```

```go
type LockableUint32 struct {
    sync.Mutex
    Data uint32
}

type LockableFloat64 struct {
    sync.Mutex
    Data float64
}

type LockableBool struct {
    sync.Mutex
    Data bool
}

type LockableBytes struct {
    sync.Mutex
    Data []byte
}

func main() {
    var n LockableUint32
    n.Lock()
    n.Data++
    n.Unlock()

    var f LockableFloat64
    f.Lock()
    f.Data += 1.23
    f.Unlock()

    var b LockableBool
    b.Lock()
    b.Data = !b.Data
    b.Unlock()

    var bs LockableBytes
    bs.Lock()
    bs.Data = append(bs.Data, "Go"...)
    bs.Unlock()
}
```

The non-generic code contains many code repetitions, which could be avoided by using the generic type demonstrated above.

#### 4.2 An example of a method of a generic type

Some people might not appreciate the implementation of the above generic type. Instead, they prefer to use a different implementation as the following code shows. Comparing with the Lockable implementation in the last section, the new one hides the struct fields from outside package users of the generic type.

```go
package main
```

```go
println(NoDiff[bool]())  // true

// _ = NoDiff() // error: cannot infer V

// error: *** does not implement comparable
// _ = NoDiff([]int{}, []int{})
// _ = NoDiff(map[string]int{})
// _ = NoDiff(any(1), any(1))
}
```

In the above example, NoDiff is a generic function. Different from non-generic functions, and similar to generic types, there is an extra part, a type parameter list, in the declaration of a generic function. Here, the type parameter list of the NoDiff generic function is [V comparable], in which V is the type parameter name and comparable is the constraint of V.

comparable is a new predeclared identifier introduced in Go 1.18. It denotes an interface that is implemented by all comparable types. It will be explained with more details in the next chapter.

Here, the type parameter V is used as the variadic (value) parameter type.

The notations NoDiff[string], NoDiff[int] and NoDiff[bool] are called instantiated functions (of the generic function NoDiff). Similar to instantiated types, in the notations, [string], [int] and [bool] are called type argument lists. In the lists, string, int and bool are called type arguments, all of which are passed to the V type parameter.

The whole type argument list may be totally omitted from an instantiated function expression if all the type arguments could be inferred from the value arguments. That is why some calls to the NoDiff generic function have no type argument lists in the above example.

- In the call NoDiff("Go", "Go", "Go"), the type argument is inferred as string, the default type of the value arguments.
- In the call NoDiff(123, 123, 123, 123), the type argument is inferred as int, the default type of the value arguments.
- In the two calls with A{} and A{1, 2} as value arguments, the type argument is inferred as [2]int, the type of the value arguments.
- In the two calls with new(int) as value arguments, the type argument is inferred as *int, the type of the value arguments.

Please note that all of these type arguments implement the comparable interface. Incomparable types, such as []int and map[string]int may not be passed as type arguments of calls to the NoDiff generic function. And please note that, although any is a comparable (value) type, it doesn't implement comparable, so it is also not an eligible type argument. This will be talked about in detail in the next chapter.

The above example shows how generics avoid code repetitions for function declarations. Without custom generics, we need to declare a function for each type argument used in the example. The bodies of these function declarations would be almost the same.

#### 4.4 Generic functions could be viewed as simplified forms of methods of generic types

The generic function shown in the above section could be viewed as a simplified form of a method of a generic type, as shown in the following code.
