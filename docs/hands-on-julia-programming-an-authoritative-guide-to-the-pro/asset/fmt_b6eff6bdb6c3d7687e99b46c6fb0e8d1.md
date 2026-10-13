
# Background

Computer scientists usually give maximum focus to perfecting this part of the problem. The gains that a well-chosen algorithm can provide to a problem are often unmatched by any amount of tweaking done around a poorly suited one. Whenever you have code that is not performing right, it is best to take a look at the core design and understand if it has the right algorithm in place. Keeping performance focus in the design phase reduces significant rework costs.

For example, *binary search has a complexity of O(log n) while the complexity of array search is linear time or O(n)*. Intuitively it seems that binary search will always perform over a linear search. But, with modern day processor cache and the efficiency of the memory management of arrays, it may be efficient to use linear search for smaller arrays. While B-tree is the choice of database indexes for disk-based storage, binary trees may be the data structure of choice for in-memory databases. One needs to look at the right data structures considering the complete system performance and not just theoretical asymptotic time complexity or the worst-case performance.

Julia has an in-built statistical profiler. Profiler is in the module called `Profile`. We shall use this tool to profile a function `profile_test`.

The Julia runtime needs to be loaded on the execution of a program for the first time and it will exit on completion of the execution. Second, Julia is a JIT-compiled language. Julia code executed sparingly may not have been compiled to native binaries before it is invoked. A part of the time may be spent in compiling the code to the native format when the code is invoked. To bring both the systems to a comparable state, Julia proponents would suggest the performance be measured in a steady-state condition. A steady state is reached when all the Julia code is run at least once and they are compiled to native binaries by the JIT compiler. While detractors of the language do not agree with the benchmark as they think the loading time has not been considered as a part of the process. Julia community publishes a set of micro-benchmarks for many competitive platforms taking few algorithmic tasks:

When a pure function is called several times, it shall produce the same output. Rather than computing the result again and again, if we can cache the value, it will reduce the computation overheads. This process is called `memoization`. One of the most common examples discussed in the context of memoization is the Fibonacci series. A Fibonacci series is best described recursively with the following code:

`@code_warntype` reports the Julia code as an AST. The AST is reported with type inference at each step of the AST. The non-deterministic types are highlighted with colors on a terminal or Jupyter console. There are many variables assigned to the type `Any`. This essentially means there will be an allocation for the location of memory and indirection to actual `Float64` value during any computation. We will add a type to the declaration for the parameter `x` and see how that affects the type inferences.

**Figure 11.1:** Julia vs Competing Platforms

The `memoize(f)` is a higher order function that can memoize a function with its parameters for subsequent value retrieval. The memo dictionary is accessed as a closure by the anonymous function returned by `memoize`. With a function like `memoize` you can define `fib(n)` method as shown:

While there is no problem in the code in terms of type inference (there are no `Any` types), `x` is assigned a `Tuple{Float64}`. This essentially means a new variable will be created and function input will be assigned to this newly created tuple. If we redefine the `sindeg` function as:

We got very close to the performance of `sind(x)` but are not quite there. One obvious question, why `sindegmemo` performs better when the input is 60° than the input of 22°?

However, `Memoize.jl` package has a `@memoize` macro that can help specify if the function is memoization aware.

Evan Jones, The Unreasonable Effectiveness of Linear Search, Blog Post, September 10, 2018, [https://www.evanjones.ca/linear-search.html](https://www.evanjones.ca/linear-search.html) last accessed: January 14, 2021.

Ideal Loop Processing, Microsoft MSDN Documentation, Visual Studio 2019, [https://docs.microsoft.com/en-us/cpp/mfc/idle-loop-processing?view=msvc-160](https://docs.microsoft.com/en-us/cpp/mfc/idle-loop-processing?view=msvc-160), last accessed January 12, 2021

Voyager 1 just left the solar system using less computing power than your iPhone, Washington Post, [https://www.washingtonpost.com/news/the-switch/wp/2013/09/12/voyager-1-just-left-the-solar-system-using-less-computing-power-than-your-iphone/](https://www.washingtonpost.com/news/the-switch/wp/2013/09/12/voyager-1-just-left-the-solar-system-using-less-computing-power-than-your-iphone/) September 13, 2013, last accessed January 12, 2021

Brian W. Kernighan and Rob Pike, The Practice of Programming, Chapter 7, Addison-Wesley, 1999

The native Julia functions `sin` and `cos` are not utilizing the CPU instruction `FSIN` or `FSINCOS` as found in the Intel chipset. But, a 13-degree polynomial is computed using an optimized Horner’s method. The interested readers can review the code at the GitHub link: [https://github.com/JuliaLang/julia/blob/cf9bcc7a49863ea47facbd93a2d920b0bf1e96ff/base/special/trig.jl#L69](https://github.com/JuliaLang/julia/blob/cf9bcc7a49863ea47facbd93a2d920b0bf1e96ff/base/special/trig.jl#L69). You can generate the bitcode for their native processors using the macro `@code_native` and verify.

This code is from the 1.5.3 version of Julia. The relevant code is:

```
∘(f, g) = (x…) -> f(g(x…))
```

A composition operator on two functions shall essentially create an anonymous function and assign to the variable. `sindeg` is just a variable which is assigned an anonymous function of type: `Base.var"#62#63"{typeof(sin), typeof(deg2rad)}`.

We have only bold faced the variables mapped to type `Any`. In the terminal output, you will be seeing variables with non-deterministic types highlighted in red or brown and deterministic types in green or cyan. `@code_typed` also reports almost similar information as `@code_warntype`. However, it does not highlight the type of warnings.

Julia Micro-Benchmarks, [https://julialang.org/benchmarks/](https://julialang.org/benchmarks/) last accessed: 1423^(th) January 2021

These are called micro-benchmarks as they are performance measured for specific tasks not a complete system.

# IDEs and GUI-based line debugging utilities

IDEs and GUI-based line debugging utilities are common tools for application development today. While functional programmers prefer short verifiable units of code that can be validated independently, debugging still is a much sought-after tool for any programming environment. Julia has quite an elaborate GUI-based IDE with debugging environment.

# Chapter Overview

In this chapter, we will cover the following topics:

*   Background
*   Editor integration
*   IDE
*   Debugging
*   Code-Run-Fix

# Learning Objectives

In this chapter, the reader shall be able to understand the capabilities of well-known editors in rendering Julia code. There are a few well-known **Integrated Development Environments (IDEs)** that provide support for development with Julia. Debugging of programs is a useful skill and IDEs help debug code line-by-line. We will look into some of the techniques that help to debug as part of this chapter.
