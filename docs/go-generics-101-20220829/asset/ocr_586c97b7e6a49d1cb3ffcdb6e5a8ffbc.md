# Chapter 6

# Generic Instantiations and Type Argument Inferences

In the last two chapters, we have used several instantiations of generic types and functions. Here, this chapter makes a formal introduction for instantiated types and functions.

# 6.1 Generic type/function instantiations

Generic types must be instantiated to be used as types of values, and generic functions must be instantiated to be called or used as function values.

A generic function (type) is instantiated by substituting a type argument list for the type parameter list of its declaration (specification). The lengths of the (full) type argument list is the same as the type parameter list. Each type argument is passed to the corresponding type parameter. A type argument must be a non-interface type or a basic interface type and it is valid only if it satisfies (implements) the constraint of its corresponding type parameter.

Instantiated functions are non-generic functions. Instantiated types are named ordinary value types.

Same as type parameter lists, a type argument list is also enclosed in square brackets and type arguments are also comma-separated in the type argument list. The comma insertion rule for type argument lists is also the same as type parameter lists.

Two type argument lists are identical if their lengths are equal and all of their corresponding types are identical. Two instantiated types are identical if they are instantiated from the same generic type and with the same type argument list.

In the following program, the generic type Data is instantiated four times. Three of the four instantiations have the same type argument list (please note that the predeclared byte is an alias of the predeclared uint8 type). So the type of variable x, the type denoted by alias Z, and the underlying type of the defined type W are the same type.

```
package main

import (
    "fmt"
    "reflect"
)
```