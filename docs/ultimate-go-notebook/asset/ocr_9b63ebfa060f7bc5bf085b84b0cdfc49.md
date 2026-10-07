# 14.2 Escape Analysis Mechanics

# Prelude

As of version 1.17, Go changed the ABI (application binary interface) to implement a new way of passing function input and output arguments using registers instead of the stack. This is enabled for Linux, MacOS, and Windows on the 64-bit x86 architectures. This means that some function arguments won't be copied over the stack, but some may depending on the viability of using registers. This doesn't change any of the semantics described in this post.

# Introduction

In the first post, I taught the basics of pointer mechanics by using an example in which a value was shared down a Goroutine's stack. What did I not show you is what happens when you share a value up the stack. To understand this, you need to learn about another area of memory where values can live: the "heap". With knowledge, you can begin to learn about "escape analysis".

Escape analysis is the process that the compiler uses to determine the placement of values that are created by your program. Specifically, the compiler performs code analysis to determine if a value can be placed on the stack frame for the function constructing it, or if the value must "escape" to the heap. In Go, there is no keyword or function you can use to direct the compiler in this decision. It's only through the convention of how you write your code that can impact this decision.

# Heaps

The heap is the second area of memory, in addition to the stack, used for storing values. The heap is not self-cleaning like the stack, so there is a bigger cost to use this memory. Primarily, the costs are associated with the garbage collector (GC), which must get involved to keep this area clean. When the GC runs, it will use 25% of your available CPU capacity. Plus, it can potentially create microseconds of "stop the world" latency. The benefit of having the GC is that you don't need to worry about managing heap memory, which historically has been complicated and error prone.

Values on the heap constitute memory allocations in Go. These allocations put on the GC because every value on the heap that is no longer referenced by a pointer needs to be removed. The more values that need to be checked and removed, the more work the GC must perform on every run. So, the pacing algorithm is constantly working to balance the size of the heap with the pace it runs