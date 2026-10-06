# Chapter 5: Modern Computing

**Table 5.5** Energy usage comparison between nonarithmetic functions (fetching values from memory) and arithmetic operations (multiply and add) in a 45-nm CMOS process technology [64, 65]

| Operation | Energy (pJ) | Relative Cost |
|---|---||
| 32-bit integer ADD | 0.1 | 1 |
| 32-bit float ADD | 0.9 | 9 |
| 32-bit integer MULT | 3.1 | 31 |
| 32-bit float MULT | 3.7 | 37 |
| 32-bit 32 KBytes on-chip SRAM | 5 | 50 |
| 32-bit DRAM | 640 | 6400 |

> Note: A pJoule(pJ) is a unit of consumed energy is = $10^{-12}$ J.

is relatively small [63]. Thus, DSAs offer order of magnitude improvements in throughput performance, lower latencies, lower power (or, equivalently, energy), and reduced physical chip area compared to general-purpose CPUs [63].

Horowitz compared the energy consumed in accessing memory to energy used in performing an add or a multiple arithmetic operation. From Horowitz's presentation at the 2014 International Solid-State Circuits Conference [64], the approximate comparison of energy usage shown in table 5.5 makes this point very clearly. Also, Han et al showed how the energy cost can be substantially reduced by compression (i.e., pruning redundant connections and sharing weights in a DNN model), such that the DNN weights can be accessed from faster on-chip static random access memory (SRAM) instead of slower random access memory (DRAM).

The discussion so far has centered primarily on domain-specific hardware. Leiserson et al. foresees and recommends embracing a closer collaboration between software performance engineers (i.e., software developers focusing on performance gains) and hardware architects [66]. Leiserson et al. identify three important pillars as a way to increase computer system performance in a post–Moore’s Law era for application-specific domains:

+   1. Software development: Emphasizing performance and exploiting hardware features such as parallelism, instead of focusing just on reducing software development time.

+   2. Algorithms: Particularly targeted at domain-specific applications, such as ML, signal processing, social networks, robotics, etc.