M. Sangwan and A. A. Angeline [10] proposed a "Design and implementation of single precision pipelined floating point co-processor." This paper presents a comparison of the various computational modules and an optimized floating-point ALU implementation. Here, we use a pipeline architecture to improve performance and design which increases operating frequency by a factor of 1.62. Ultimately, these individual blocks are combined to create his ALU, while to increase operating frequency while minimizing power consumption. At the same time, the number of gates increases the area, due to the number of iterations used in the algorithm.

S. Palekar and N. Narkhede [11] proposed "High-speed, area-saving single-precision floating-point arithmetic unit." The 32-bit floating point unit is designed for a wide variety of applications that require outstanding standing. The performance of the proposed design is compared to research papers relating to critical paths, with up to 59% floating multiplier critical path delay and 50% floating adder/subtractor optimization. The results show that the proposed design is optimized for both speed and area efficiency.

K. Gowreesnivas and P. Samwandivary [12] "Comparative study on performance of single precision floating point multiplier using vedic multiplier and different types of adders." Single-precision floating-point performance is the main and it is primarily based on the footprint and multiplier delay. Reducing the complexity and the connections, can improve overall performance of the system. In this paper, a new type of single-precision floating-point multiplier is developed by integrating Vedic multipliers with various types of adders.

# RESULTS

We've collected the half way of our project, that the RTL and testbench codes for addition and subtraction operations have been written, tested and verified. The simulated output along with the manual calculation shows

+   * Addition
EX 1: A = 48.265 = -48.362
Binary representation of the given inputs
A = 010000010100100010001110101100
B = 11000001010010001010111010100000
Adding the mantissa part,
A_mantissa = 100000001110111010110000
B_mantissa = 100000001110111010100000
After addition , The final result,
A + B = 48.265 + (-48.362) = -0.097
A+B= 1111110111001110101000000000000
Hexadecimal equivalent of the final result A+B=bd6a880 (-0.097)

```
============================
EX 2: A = 3.256 = -4.321
Binary representation of the given inputs
A = 0100000001001000100110010011110
B = 110000000100101010101010100010
After adding the mantissa part, The final result,
A + B = 3.256 + (-4.321) = -1.065
A + B = 1011111130001000101000111101100
Hexadecimal equivalent of the final result, A + B = bf8851ec (-1.065)
```