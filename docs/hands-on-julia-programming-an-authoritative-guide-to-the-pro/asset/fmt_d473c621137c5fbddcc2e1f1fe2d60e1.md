
# Memoization and Global Variables in Julia

## Memoization Example

**Calling fib: 3**

**Calling fib: 2**

**Calling fib: 1**

**julia> @btime fib(20)**

**85.758 ns (0 allocations: 0 bytes)**

**6765**

`fib(5)` is called only 5 times and time taken for `fib(20)` is only 86ns; almost the time taken to read from the dictionary and add them. Can we generalize the concept to presentable form for any kind of memorization tasks?

```julia
function memoize(f)
    memo = Dict()
    (args...; kwargs...) -> begin
        x = (args, kwargs)
        haskey(memo, x) && return memo[x]
        v = f(args...; kwargs...)
        memo[x] = v
        return v
    end
end
```

The `memoize(f)` is a higher order function that can memoize a function with its parameters for subsequent value retrieval. The memo dictionary is accessed as a closure[12](#9ztdqvro.html#n4upl4fndiq) by the anonymous function returned by `memoize`. With a function like `memoize` you can define `fib(n)` method as shown:

```julia
fib(n) = n < 3 ? 1 : fib(n-1) + fib(n-2)
fib! = memoize(fib)
```

However, `Memoize.jl` package[13](#9ztdqvro.html#n4upl4fndir) has a `@memoize` macro that can help specify if the function is memoization aware.

```julia
julia> Pkg.add("Memoize")
julia> using Memoize
julia> @memoize fib(n) = n < 3 ? 1 : fib(n-1) + fib(n-2)
```

## Global Variables and Performance

This is not really a design pattern. We want you to be aware of the challenges in using global variables. Julia global variables do not have an assigned type. They can be assigned to any type based on the data it is assigned to.

```julia
GLOBAL_VAR = 3
function add_to_global(x)
    x + GLOBAL_VAR
end
```

```julia
julia> @btime add_to_global(10)
65.745 ns (0 allocations: 0 bytes)
13
```

Now, let us pass the global variable to the basic addition operator.

```julia
julia> @btime 10 + $GLOBAL_VAR
0.001 ns (0 allocations: 0 bytes)
13
```

Just wrapping the global variable in the function is having significant overheads; but why? Let us consider a global constant instead of a variable.

```julia
julia> const GLOBAL_CONST = 20;
julia> add_to_global_const(x) = x + GLOBAL_CONST
julia> @btime add_to_global_const(3)
0.001 ns (0 allocations: 0 bytes)
23
```

The value returned is fairly fast and much better than a global variable. Let us look at the LLVM bitcode.

```julia
julia> @code_llvm add_to_global_const(3)
; @ In[108]:1 within `add_to_global_const'
; Function Attrs: uwtable
define i64 @julia_add_to_global_const_4267(i64) #0 {
top:
; ┌ @ int.jl:86 within `+'
  %1 = add i64 %0, 20
; └
ret i64 %1
}
```

The constant 20 is directly replaced. So, there is no type ambiguity. The addition shall take place in a CPU register. There is no memory access. Global variables serve two purposes. They allocate a specific location of memory and a handle to the memory location. However, they are not type safe. However, `Ref{T}` allocate memory and are type safe. By declaring the variable as `const` can ensure the memory location is pinned as well.

```julia
julia> const GLOBAL_REF = Ref(10)
Base.RefValue{Int64}(10)
julia> add_to_global_ref(x) = x + GLOBAL_REF[]
julia> @btime add_to_global_ref(3)
2.499 ns (0 allocations: 0 bytes)
23
```

There is definite improvement of performance over a global variable, yet it is not as fast as a `const` or a function argument. On reviewing the LLVM bitcode you will see, there are essentially two parts to the code.

1. Load the value from a specific memory location to a variable or register or volatile memory location
2. Add the value to another volatile memory location

```julia
julia> @code_llvm add_to_global_ref(3)
; @ In[116]:1 within `add_to_global_ref'
; Function Attrs: uwtable
define i64 @julia_add_to_global_ref_4338(i64) #0 {
top:
; ┌ @ refvalue.jl:32 within `getindex'
; │┌ @ Base.jl:33 within `getproperty'
  %1 = load i64, i64* inttoptr (i64 380471024 to i64*), align 16
; └└
; ┌ @ int.jl:86 within `+'
  %2 = add i64 %1, %0
; └
ret i64 %2
}
```

If you do not like to access the `Ref{T}` syntax with the square brackets (`[]`), you can use the accessor pattern as well.

```julia
let _x = Ref(5)
    global X() = _x[]
    global X(y) = (_x[] = y)
end
```

We will recommend readers to look at the LLVM bitcode for `add_to_global_var`. As there is no type inference for a global variable, the function will have to assume a type `Any` and resolve the type conflicts on every use.

## Performance Tuning Summary

Julia system is designed for high-performance computations. We saw glimpses of such implementations in this chapter. However, performance tuning is a complex subject and the development of skills in this area needs sufficient exposure and practice. We thus recommend readers review performance-sensitive code and try improvising over them with regular practice. In the next chapter, we shall review the IDEs available for Julia’s development and how various debugging techniques can be used.

## Exercises

1. Choose a function of your choice and run `@code_warntype` over it. Try to identify the type stability issues and fix such that the type instabilities are removed.

2. Consider the comprehension `f() = [x*x for x = 1:10000]`. Time the code with `@btime` and compare with the following code:

   ```julia
   function g()
       y = Vector{Int}(undef, 10000)
       for i in 1:10000
           y[i] = i*i
       end
   end
   ```

   How will you explain the difference?

3. Why is `@btime` of `BenchmarkTools.jl` preferred over `Base.@time`? How will you use `@btime` for functions with side-effects?

4. What are some of the `@code_XXX` macros and why are they used in performance profiling?

5. Julia performance profiling is suggested only when the code has been used several times with all relevant data types. It has been seen Julia is slow to start. What do you think are the reasons?

---

[1](#9ztdqvro.html#n4upl4fndis) Brian W. Kernighan and Rob Pike, The Practice of Programming, Chapter 7, Addison-Wesley, 1999
