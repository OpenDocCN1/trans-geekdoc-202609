The algorithm *avgnn*, has 3 × n × n + 2 operations, makings its expected performance the worst overall. It expands its input by an order of magnitude for redundant operations. This algorithm requires (n²)t units of time complexity and has a big-O of O(n²).

# 13.2 BIG-O NOTATION

The *O* in Big-O notation stands for *order of magnitude*. For expediency, we describe *time-complexity* in terms of Big-O, a mathematical shorthand that accounts for an algorithm's magnitude of expansion as its input increases.

There are external factors besides the algorithm itself that affect its computational speed. We ignore those in algorithm analysis, as we are concerned with a common criteria for objectively comparing algorithms (the algorithms themselves).

Non-algorithm factors affecting algorithmic performance include:

+   • Memory size and memory access speed.
+   • CPU clock rate and CPU cache behavior.
+   • Other programs competing for CPU time and memory.
+   • Code length, sometimes inversely proportional to computational efficiency.
+   • Distribution of the algorithm on multi-CPU systems.
+   • Compiler/interpreter garbage collection, interim compilations, thread scheduling, etc.
+   • Compiler versus operating-system optimizations.

The data scientist usually has little immediate control over non-algorithm factors such as hardware. Therefore, it is often more expedient to craft a better algorithm in consideration of a minimal problem size than to swap out hardware.

The problem size is the total number of operations performed by an algorithm.

*problem size = number of statements × number of elements*

To make an objective comparison of algorithms, we ignore all the above performance factors, except the problem size. This is because the hardware and operating systems vary from machine to machine.

As mentioned earlier, a (2n)t algorithm, with t units of time and an input size of n, is considered to have a Big-O of O(n). As n increases, 2n increases by the