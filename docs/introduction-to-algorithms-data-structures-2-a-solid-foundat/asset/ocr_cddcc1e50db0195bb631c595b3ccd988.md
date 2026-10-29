system when it comes to arrays. All this means is that the first index value is equal to **0**, not 1. Figure 2.2.4.

![](bbox=[0.26, 0.14, 0.73, 0.38])

*Figure 2.2.4: Illustration of a zero-based numbering system in an array*

Generally speaking, when an array is declared a base amount of contiguous memory is allocated as the array storage. Computers refer to memory through the use of an address, but instead of keeping a reference to all the memory allocated for an array, the array only has to store the address of the first location because the memory is contiguous. Using the base address, the array can calculate the address of any value by using the index position of that value as an offset. If you want to be more specific, think of it this way.

Let's say we want to create an array of integers, and then each integer takes up a certain amount of space in memory that we'll call **M**. Let's also assume that we know how many elements we're going to create, so the size of the array is some number of elements we'll call **N**. So, the total amount of space that we need to allocate is **N** times the space per item **M**: **Space = N * M**. See Figure 2.1.5.