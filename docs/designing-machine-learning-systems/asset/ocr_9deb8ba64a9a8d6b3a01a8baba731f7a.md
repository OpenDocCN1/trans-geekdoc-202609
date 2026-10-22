This vision comes together in the AI Engineering team, where our expertise is used to develop AI algorithms and models that are optimized for our hardware, as well as to provide guidance to Mythic’s hardware and compiler teams.

The AI Engineering team significantly impacts Mythic by:

+   - Developing quantization and robustness AI retraining tools
+   - Investigating new features for our compiler that leverage the adaptability of neural networks
+   - Developing new neural networks that are optimized for our hardware products
+   - Interfacing with internal and external customers to meet their development needs

Optimization engineers are hard to come by and expensive to hire because they need to have expertise in both ML and hardware architectures. Optimizing compilers (compilers that also optimize your code) are an alternative solution, as they can automate the process of optimizing models. In the process of lowering ML model code into machine code, compilers can look at the computation graph of your ML model and the operators it consists of—convolution, loops, cross-entropy—and find a way to speed it up.

There are two ways to optimize your ML models: locally and globally. Locally is when you optimize an operator or a set of operators of your model. Globally is when you optimize the entire computation graph end to end.

There are standard local optimization techniques that are known to speed up your model, most of them making things run in parallel or reducing memory access on chips. Here are four of the common techniques:

# Vectorization

Given a loop or a nested loop, instead of executing it one item at a time, execute multiple elements contiguous in memory at the same time to reduce latency caused by data I/O.

# Parallelization

Given an input array (or n-dimensional array), divide it into different, independent work chunks, and do the operation on each chunk individually.