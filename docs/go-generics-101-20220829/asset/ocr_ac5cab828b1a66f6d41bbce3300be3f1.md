```
println(NoDiff[bool]())  // true

// _ = NoDiff() // error: cannot infer V

// error: *** does not implement comparable
// _ = NoDiff([]int{}, []int{})
// _ = NoDiff(map[string]int{})
// _ = NoDiff(any(1), any(1))
}
```

In the above example, NoDiff is a generic function. Different from non-generic functions, and similar to generic types, there is an extra part, a type parameter list, in the declaration of a generic function. Here, the type parameter list of the NoDiff generic function is [V comparable], in which V is the type parameter name and comparable is the constraint of V.

comparable is new predeclar ed identifier introduced in Go 1.18. It denotes an interface that is implemented by all comparable types. It will be explained with more details in the next chapter.

Here, the type parameter V is used as the variadic (value) parameter type.

The notations NoDiff[string], NoDiff[int] and NoDiff[bool] are called instantiated functions (of the generic function NoDiff). Similar to instantiated types, in the notations, [string], [int] and [bool] are called type argument lists. In the lists, string, int and bool are called type arguments, all of which are passed to the V type parameter.

The whole type argument list may be totally omitted from an instantiated function expression if all the type arguments could be inferred from the value arguments. That is why some calls to the NoDiff generic function have no type argument lists in the above example.

+   - In the call NoDiff("Go", "Go", "Go"), the type argument is inferred as string, the default type of the value arguments.
+   - In the call NoDiff(123, 123, 123, 123), the type argument is inferred as int, the default type of the value arguments.
+   - In the two calls with A{} and A{1, 2} as value arguments, the type argument is inferred as [2]int, the type of the value arguments.
+   - In the two calls with new(int) as value arguments, the type argument is inferred as *int, the type of the value arguments.

Please note that all of these type arguments implement the comparable interface. Incomparable types, such as []int and map[string]int may not be passed as type arguments of calls to the NoDiff generic function. And please note that, although any is a comparable (value) type, it doesn't implement comparable, so it is also not an eligible type argument. This will be talked about in detail in the next chapter.

The above example shows how generics avoid code repetitions for function declarations. Without custom generics, we need to declare a function for each type argument used in the example. The bodies of these function declarations would be almost the same.

# 4.4 Generic functions could be viewed as simplified forms of methods of generic types

The generic function shown in the above section could be viewed as a simplified form of a method of a generic type, as shown in the following code.