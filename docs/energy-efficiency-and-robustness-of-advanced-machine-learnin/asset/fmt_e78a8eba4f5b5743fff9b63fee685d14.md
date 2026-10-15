
*   An application-driven memory hierarchy, composed of an on-chip SPM and an off-chip DRAM, can save up to 73% of the energy on the Google's CapsNet model without compromising the throughput compared to having a fully on-chip memory organization. Note that the same throughput is guaranteed by prefetching the data for the next operation in an interleaved fashion with the processing of the current operation. Therefore, the off-chip memory latency can be hidden.

*   The utilization of the on-chip memory is variable, depending upon the operation of the CapsNet inference. Thus, applying power-gating to the non-utilized sectors can further reduce its energy consumption.

*   Partitioning the SPM into separate components (for data, weight, and accumulator) can be beneficial for storing values and efficiently feeding them to the accelerator.

### 3.4.4 DESCNet: Scratchpad Memory Design

#### 3.4.4.1 DESCNet Memory Architecture

The architecture of our `DESCNet` is depicted in [Figure 3.32](#chapter3.xhtml#chapter3.xhtml#fig3_32). It is connected to the CapsNet accelerator and to the off-chip memory through dedicated bus lines. The SPM is partitioned into `B` banks, where each bank consists of `SC` number of equally-sized sectors. Across different banks, all the sectors are connected through a power-gating circuitry (implemented with sleep transistors) to support an efficient sector-level power-management control at the cost of some area overhead. Our design has `SC` sectors, one for each bank, which share the same sleep signal. Note that we only consider `ON` and `OFF` modes as they came out to be beneficial in our designs, and we did not need state-retentive modes. Our application-driven memory power management unit determines the appropriate control signals (i.e., `ON` ↔ `OFF`) for the sleep transistors. Once the execution of the current operation is completed, the values in the SPM are discarded since, in our designs, we consider a deep-sleep `OFF` state, which is non-retentive. The transitions between sleep modes come at the cost of a certain wakeup energy and latency overhead that needs to be amortized by the leakage energy savings that depends upon the sleep duration and the number of sectors in the sleep mode. Note that our memory model can be generalized for different memory organizations supporting different sizes and levels of parallelism, including multi-port memories. *Toward this, we study the following three design options.*

1.  (a)**[Figure 3.33a](#chapter3.xhtml#chapter3.xhtml#fig3_33)—Shared Multi-Port Memory (SMP):** a shared on-chip memory with 3 ports for accessing the weights, input data and accumulator's storage in parallel.

2.  (b)**[Figure 3.33b](#chapter3.xhtml#chapter3.xhtml#fig3_33)—Separated Memory (SEP):** weights, input data, and the accumulator's partial sums are stored in separate on-chip memories.

3.  (c)**[Figure 3.33c](#chapter3.xhtml#chapter3.xhtml#fig3_33)—Hybrid Memory (HY):** a combination of the above two design options, i.e., an `SMP` coupled with a `SEP` memory.

![Figure 3.32: Architectural view of the complete CapsNet architecture, with a focus on our `DESCNet` SPM.](images/fig3_32.jpg)

[Figure 3.32:](#chapter3.xhtml#b3fig3_32) Architectural view of the complete CapsNet architecture, with a focus on our `DESCNet` SPM.

![Figure 3.33: Different Architectural Design Options of the On-Chip SPM of the CapsNet Accelerator that are evaluated in our Application-Driven Memory DSE: (a) Shared Multi-Port Memory. (b) Separated Memory. (c) Hybrid Memory (Shared and Separated).](images/fig3_33.jpg)

[Figure 3.33:](#chapter3.xhtml#b3fig3_33) Different Architectural Design Options of the On-Chip SPM of the CapsNet Accelerator that are evaluated in our Application-Driven Memory DSE: **(a)** Shared Multi-Port Memory. **(b)** Separated Memory. **(c)** Hybrid Memory (Shared and Separated).

#### 3.4.4.2 Application-Driven Memory Power Management

Our application-driven memory PMU determines the sleep signals according to the utilization profile of the memory, as observed in [Figure 3.27a](#chapter3.xhtml#fig3_27) and [Figure 3.29a](#chapter3.xhtml#fig3_29). A simple schematic showing how a sleep transistor is connected to its memory sectors is depicted in [Figure 3.34](#chapter3.xhtml#fig3_34). The sleep request signal is followed by the acknowledge signal, to form a 2-way handshake protocol. The timing diagram of the complete sleep cycle (`ON` → `OFF` → `ON`) is shown in [Figure 3.35](#chapter3.xhtml#fig3_35). When exploiting the application-specific knowledge, it is known from the analysis presented in [Section 3.4.3](#chapter3.xhtml#sec3_4_3) which sectors need to be activated during the execution of different operations. Hence, *the wakeup latency overhead is transparently masked, i.e., the required sectors are pre-activated in advance, in such a way that they are active when needed.*

![Figure 3.34: Circuit-level schematic of the power-gating circuit, using a footer sleep transistor connected to the PMU.](images/fig3_34.jpg)

[Figure 3.34:](#chapter3.xhtml#b3fig3_34) Circuit-level schematic of the power-gating circuit, using a footer sleep transistor connected to the PMU.

![Figure 3.35: Timing diagram of a complete sleep cycle of a sector.](images/fig3_35.jpg)

[Figure 3.35:](#chapter3.xhtml#b3fig3_35) Timing diagram of a complete sleep cycle of a sector.

#### 3.4.4.3 Application-Driven Design Space Exploration of the DESCNet Memory Designs

Considering the above memory models, we systematically determine their organization, sizes, the number of banks (`B`), and the number of sectors-per-bank (`SC`) through a DSE methodology. We explore different memory architecture configurations and evaluate their area and energy consumption. Different levels of abstraction of application-driven knowledge (i.e., architecture and utilization profiles specific to CapsNets) are employed. In the following equations and algorithms, we adopt these notations:

*   *i*: index of the operations of the CapsNet inference.

*   *D*[*i*], *W*[*i*], *A*[*i*]: operation-wise memory usage of data memory, weight memory and accumulators, according to the analyses shown in [Figure 3.27a](#chapter3.xhtml#fig3_27) and [Figure 3.29a](#chapter3.xhtml#fig3_29).

*   *S**Z**[{*S*, *D*, *W*, *A*}], *S**C**[{*S*, *D*, *W*, *A*}], *B*[{*S*, *D*, *W*, *A*}]: size, number of sectors, number of banks of {shared memory, data memory, weight memory, accumulators}, respectively.

*   *σ*(*s*): pool of available numbers of memory sectors for power-gating, given the memory size *s*, which are all the power of two values in the range $\\left\\lbrack 2,\\frac{s}{128} \\right\\rbrack$. Note, the latter value is due to a limitation of the CACTI-P \[[124](#refbib.xhtml#refbib124)\] tool, which sets the limit for the ratio between memory size and sector size to be at least 128.

For all the memory designs, without loss of generality, the number of banks is chosen to be `B`[*D*] = `B`[*W*] = `B`[*A*] = `B`[*S*] = 16, as it corresponds to the number of rows and columns of the NP array of the *CapsAcc* architecture. To facilitate efficient data feeding to the accelerator, this parameter is not changed in our DSE.

For the *SMP* design, the size of the shared memory is derived from the operation-wise maximum memory usage scenario, as shown in Equation (3.5). Since only finite values of memory sizes are acceptable, when computing the *max*[*i*] function, the memory size becomes the smallest acceptable size that is greater than or equal to the operation-wise maximum, and vice-versa for the *min*[*i*].

$$\\begin{array}{l} {\\texttt{SMP:}SZ\_{S} = \\max\\limits\_{i}(D\_{i} + W\_{i} + A\_{i})} \\\\ \\end{array}$$  

(3.5)

For the *SEP* design, the sizes of the data memory, weight memory, and accumulator are set as in Equation (3.6), based on the operation-wise maximum memory usage of the separated components.
