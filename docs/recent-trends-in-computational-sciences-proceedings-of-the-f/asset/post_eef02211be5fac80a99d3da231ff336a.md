
this section, simultaneously performs the operation of floating-precision addition and subtraction on a common pair of single-precision data in approximately the same time it would have a conventional floating-precision adder to perform a single addition. The fused adder-subtractor unit performs both ADD and SUB operations at nearly the same speed as the floating point adder with less than 40% area overhead.

Vinayak Patil, Aneesh Raveendran, Sobha, David Selvakumar and Vian [4] detailed “Out of Order Floating Point Coprocessor for RISC-V”. This paper details the architecture of floating point coprocessors that use RISC-V floating-point instructions. A floating-point coprocessor is integrated into the integer pipeline. A architecture for floating-point coprocessor with out-of-order execution, in-order, and complete-retrieval was synthesized, tested, and verified on a Xilinx Virtex 6xc6xl550-2I279 FPGA. FPGAs have seen system frequencies of 240 MHz for single-precision floating-point arithmetic.

CheolHo Jeong, Woo-Chan, Soo Kim and Moon-Lee [5] developed a method to fix “In-Order Out-of-Order Execution Coprocessor for CalmRISC32. The CalmRISC32 Floating Point Unit is a Reduced Set Computer processor which is basically an open source. Configured with CalmRISC32 IEEE-754 single precision floating addition/ subtraction and multiplication supported coprocessor. Statements are executed out-order and completed if such restrictions as the data dependencies resource contention exception are fixed. A simple coprocessor interface and the exception predictors to support precise exceptions. Standard cell-based design techniques are used to reduce time and cost.

Remya Jose & Dhanesh [6] developed “Single Precision Floating Point CoProcessor for Statistical Analysis. This paper describes the design implementation of a single-precision floating-point coprocessor that can be used for statistical analysis. This paper presents a comparative analysis of arithmetic modules which were used to implement the efficient coprocessors and also floating-point adders and multipliers based on area and delay. Latency is one of the key factors in processor architecture. Based on comparative analysis, the Koggestone adder and the modified cabin multiplier were selected. A powerful coprocessor was implemented using these computational modules.

Aditi Sharma, Sukanya Singh and Abhay Sharma [7] developed a method “Implementation of Single Precision Conventional and Fused Floating Point Add-Subunit Verilog.” With floating-point addition and subtract architecture for the single precision has been compared to its fused counterpart known as the fused add-subtractor. Fused add-sub FPUs have been developed to yield better latency compared to conventional FPUs. Shrink area, increase speed, and reduce power

Aneesh Raveendran, Vinayak Barum Patil, David Selvakumar and Vianian Desishan [8] proposed “A RISC-V Instruction Set-Microarchitecture Design and Analysis.” This paper describes the micro-architecture design and analysis of the RISC-V instruction processors. RISC-V is one of the open-source ISA. This paper details the micro-architecture design of a 5-stage pipeline RISC-V compatible processor. The processor with FPU has a 171 K registers and area 557 mm2.

Tek-Joon Kwon, Jeff Sondenlee and Jeff Draper [9] developed “A 0.18 μm implementation of a floating-point unit for a processing-in-memory system” which Rudolf Uselmann’s open source project. The FPU described a single-precision floating-point unit capable of addition, subtraction, multiplication, and division. It consists of the two pre-normalization units that normalize fractions. The main drawback of this model is that most of the code is written in MATLAB, so it cannot be synthesized.

M. Sangwan and A. A. Angeline [10] proposed a "Design and implementation of single precision pipelined floating point co-processor." This paper presents a comparison of the various computational modules and an optimized floating-point ALU implementation. Here, we use a pipeline architecture to improve performance and design which increases operating frequency by a factor of 1.62. Ultimately, these individual blocks are combined to create his ALU, while to increase operating frequency while minimizing power consumption. At the same time, the number of gates increases the area, due to the number of iterations used in the algorithm.

S. Palekar and N. Narkhede [11] proposed "High-speed, area-saving single-precision floating-point arithmetic unit." The 32-bit floating point unit is designed for a wide variety of applications that require outstanding standing. The performance of the proposed design is compared to research papers relating to critical paths, with up to 59% floating multiplier critical path delay and 50% floating adder/subtractor optimization. The results show that the proposed design is optimized for both speed and area efficiency.

K. Gowreesnivas and P. Samwandivary [12] "Comparative study on performance of single precision floating point multiplier using vedic multiplier and different types of adders." Single-precision floating-point performance is the main and it is primarily based on the footprint and delay. Reducing the complexity and connections, can improve overall performance of the system. In this paper, a new type of single-precision floating-point multiplier is developed by integrating Vedic multipliers with various types of adders.

## RESULTS

We've collected the half of our project, that RTL and testbench for addition and subtraction operations have been written, tested and simulated output with manual calculation

### Addition

EX 1: A = 48.265 = -48.362
Binary representation of the given inputs
A = 010000010100100010001110101100
B = 110000010100100010101010101100
Adding the mantissa part,
A_mantissa = 1000000011101110101100
B_mantissa = 1000000011101110101100
After addition, the final result,
A + B = 48.265 + (-48.362) = -0.097
A+B = 1111110111001110101000000000
Hexadecimal equivalent of the final result A+B = bd6a880 (-0.097)

EX 2: A = 3.256 = -4.321
Binary representation of the given inputs
A = 010000000100100010011001001111
B = 110000000100101010101010100010
Adding the mantissa part, the final result,
A + B = 3.256 + (-4.321) = -1.065
A + B = 101111113000100010100011110100
Hexadecimal equivalent of the final result, A + B = bf8851ec (-1.065)

![](img/a35f8e852e0ee65e528c95ad0821783b_104_0.png)

### Subtraction

EX 1: A = 4.5 B = 2.32
Binary representation of the given inputs
A = 01000000100100000000000000000000
B = 01000000000110101110101100110000
Subtracting the mantissa part. The final result is,
A-B = 4.5 – 2.32 = 2.18
A-B = 0100000000010110001011111111111
Hexadecimal equivalent of the final result, A-B = 400b851f (2.18)

EX 2: A = 4.5 B = 6.32
Binary representation of the given inputs
A = 01000000100100000000000000000000
B = 01100000000110101110101100110000
Subtracting the mantissa part. The final result is,
A-B = 4.5 – 6.32 = -1.82
A-B = 01000000100100000110101111111111
Hexadecimal equivalent of the final result, A-B = b8fef5c3 (-1.82)

![](img/a35f8e852e0ee65e528c95ad0821783b_104_1.png)

## 6 CONCLUSION

We are designing a Coprocessor specifically for floating point calculations. A coprocessor offloads the main processor, the greater speed has been achieved. Special tasks like complex mathematical calculations are performed with good speed. The faster performance is achieved than core CPU. Coprocessor offloads the Processor-intensive tasks from the main processor. This speeds up system performance and save the time. In the area, power, timing are the three challenging factors in the processor, we are mainly focused on these three areas. The accuracy of the results plays major role. In this design, as we designed Coprocessor specifically for floating point calculations only, we can see the greater accuracy.

## REFERENCES

- [1] Ozbilen M.M. and Gok M., “A Multi-precision Floating-point-Adder, 2008 Ph.D. Research in Microelectronics and Electronics, 2008, pp. 117–120, doi: 10.1109/RME.2008.4595739
