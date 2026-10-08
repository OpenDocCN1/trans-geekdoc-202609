Operator fusion combines multiple operations in a subgraph into a single operation to improve latency. In a typical execution of a subgraph with multiple operations, system memory is accessed for read/write to transfer data between operations, which is an expensive task. Operator fusion reduces the number of memory accesses, as well as optimizes the overall computations since the computations are now happening in a single kernel without intermediate results being saved to memory. This approach also reduces the memory footprint by a smaller number of operations being performed. The following diagram shows the concept of operator fusion:

![](bbox=[0.216, 0.263, 0.746, 0.613])

Figure 10.16 - Graph operator fusion

In the preceding diagram, the **matrix multiplication, add,** and **ReLU** operators are being fused into a single operator for execution in a single kernel to reduce memory access and the time needed to start multiple kernels.

Constant folding is the process of evaluating constants at compile time instead of runtime to speed up processing during runtime. For example, the following expression, A can be assigned to a value of 300 at compile time instead of being dynamically calculated at runtime, which requires a more computational cycle: $A = 100 + 200$. Dead code elimination removes the code that does not affect the program's results. This ensures that the program doesn't waste computation on useless operations.