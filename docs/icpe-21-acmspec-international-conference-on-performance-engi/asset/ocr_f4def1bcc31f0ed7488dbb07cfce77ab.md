![](bbox=[0.135, 0.105, 0.865, 0.285])

Table 2: Functions Set.

| Category | Functions |
| :--- | :--- |
| Sort and Search | binarysearch, bubblesort, insertionsort, mergesort, quicksort, selectionsort |
| Numerical | matrixmul, gcd, bankeralgorithm |
| Networking | astar, bellmanford, bfsdfs, dijkstra, floydwarshall, kruskal |
| Data Processing | allpass, bitrev, can, conv, dir, Viterbialgorithm, tap, wave, wrap |

and regression [26]. Among the advantages of the support vector machines approach, it is effective in high dimensional spaces and in cases where the number of dimensions is greater than the number of samples. Regression Learner App uses the fitrsvm function to train SVM regression models and, in this case, the parameter Kernel function is set to Linear.

# 4 EXPERIMENTAL RESULTS

The proposed approach has been evaluated first in the SW domain by considering General Purpose Processor (GPP) technology. In this work, three GPPs, and their related ISSs, have been analyzed: LEON3, a 32-bit synthesizable RISC soft-microprocessor with a Harvard architecture, and a simulated system clock of 75 MHz Cobham Gaisler offers TSIM System Emulator as an accurate ISS of LEON3 processors, with gcc compiler (in this work, the default optimization flag -O0 has been used); Intel 8051 micro-controller, an 8-bit micro-controller with MCS-51 CISC instruction set and Harvard Architecture; The Dalton Instruction Set Simulator (ISS) [27] has been used to simulate programs written for the 8051 and to collect statistics, with SDCC (Small Device C Compiler) compiler; picoPower CMOS 8-bit AVR ATmega328/P, with an 8-bit RISC-based processor core and Harvard architecture. The SimulAVR [28] program has been used as a simulator for the Atmel AVR family of microcontrollers, with gcc compiler (in this work, the default optimization flag -O0 has been used). The benchmark execution has been done with a microprocessor software simulation using each processor’s ISS, as presented above.

Fig. 2 shows the scatter plot related to the Pearson correlation for different processors. The three figures show a strict correlation between C statements and clock cycles. Regarding the other points (the ones under the main linear regression line), the deviation depends on function implementations that introduce different behaviors compared to the significant distribution. These points introduce errors inside the timing estimation activity and are related to the internal processor micro-architecture (i.e., 8/16/32 bit architecture, pipeline, number of registers, etc.). Table 3 shows the Pearson correlation and slope values between clock cycles and executed C statements. The high correlation values reported in Table 3 between the Clock Cycles and the number of C statements prompts us to explore further the processor characteristics and to exploit ML algorithms for timing performance estimation.

# 4.1 Dataset Preparation and Feature Extraction Results

Table 3: Correlation and Slope Analysis results (p-value << 0.001 for every processor, so that we can reject the null hypothesis and the statistical analysis is highly significant).

| Function | int8 | int16 | int32 | float | Tot. |
| :--- | :--- | :--- | :--- | :--- | :--- |
| LEON3 Corr. | 0.9939 | 0.9872 | 0.9277 | 0.7465 | 0.9631 |
| MPU8051 Corr. | 0.9939 | 0.9871 | 0.9276 | 0.7465 | 0.9631 |
| ATmega328/P Corr. | 0.7465 | 0.9939 | 0.9871 | 0.9277 | 0.9631 |
| LEON3 Slope | 10.8838 | 9.4241 | 10.9702 | 15.1550 | 88.9492 |
| MPU8051 Slope | 88.2752 | 110.5197 | 183.8507 | 389.2319 | 88.9492 |
| ATmega328/P Slope | 24.7353 | 11.197 | 18.1595 | 14.0614 | 88.9492 |

A benchmark composed of control-dominated and data-dominated applications was used to train and test the estimator [15] and finally validate the approach. The benchmark is composed of 15 different algorithms taken from [29] for training and test, with a total amount of 6 * 10^4 samples, and 12 different algorithms taken from [30] for validation, with a total amount of 48 * 10^3 samples. Table 2 describes the functions used in the experiments. For each function, different data types have been considered (int8, int16, int32, and float). Indeed, timing performance metric changes w.r.t. the dimension of data [11].

In Fig. 3 is reported the result of the feature analysis. The figure (green line) shows the arithmetic mean behavior between the four algorithms results [21]. Some features show prominent behavior