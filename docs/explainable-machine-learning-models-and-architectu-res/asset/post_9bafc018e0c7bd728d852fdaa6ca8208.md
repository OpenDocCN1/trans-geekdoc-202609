
In this, N-Point DFTs are partitioned recursively into N/2 DFTs in butterfly structure. This form of dividing DFT blocks is the simplest form of FFT algorithms, known as Radix-based DFT. A DFT of N-length sequence can be calculated by using N/2 DFT blocks repeatedly until we are left with only one DFT block for all input samples, providing the final output value. Figure 5.1 shows the DIT-FFT algorithm.

![](img/d2107fc60629942e7da5355e47fcc33d_85_0.png)

Figure 5.1 Representation of DIT-FFT algorithm flow.

### 5.2.2 Algorithmic Representation with Example

The examples shown below are considered only for two samples for ease of understanding Twiddle factors cause variation according to the number of input samples. Considerably an emphasized procedural view of this algorithm with an example is presented in Figure 5.2 while Figure 5.3 shows a simplified working nature of DIT-FFT algorithm.

### 5.2.3 Simulated Output Waveform

A single clock and reset ports have been used synchronous to all DFT blocks to extract the output. The values processed are in offset representation; also, the output received is in offset binary format (Excess 16). With respect to acquired output, we can add/subtract input value to the offset value. For more clarity, we can see the output wave forms attained while

![](img/d2107fc60629942e7da5355e47fcc33d_86_0.png)

Figure 5.2 Simple DIT-FFT execution with decimal & binary inputs.

![](img/d2107fc60629942e7da5355e47fcc33d_87_0.png)

Figure 5.3 Illustration of brief approach for DIT-FFT algorithm.

verifying the design by giving inputs manually for samples N = 2, 4 and 8. Wave forms for N = 4 and 8 can be seen in Figure 5.4 and Figure 5.5, respectively. Here lower case s1, s2, s3....s8 are inputs and upper case S1, S2....S8 are the outputs in the waveform representation. For N = 2, the design depicts only a single block DFT structure as the input length has only two inputs.

![](img/d2107fc60629942e7da5355e47fcc33d_87_1.png)

Figure 5.4 Output waveform for samples N = 4.

![](img/d2107fc60629942e7da5355e47fcc33d_88_0.png)

Figure 5.5 Output waveform for samples N = 8.

## 5.3 Synthesis of Designed Circuit

In this work, synthesis of DIT-FFT architecture is performed using Vivado Design Suite in Verilog HDL environment, considering radix 2 butterfly structure. The Xilinx Synthesis Technology (XST) allows users to synthesize any design written in Verilog/VHDL. The device used is xc7a200tffV1156 with speed grade -1. Synthesized representation or RTL schematic or gate level schematic for N = 4 length input samples can be seen in Figure 5.6. The design is written with respect to the architecture of radix 2 butterfly DIT-FFT structure proposed by Cooley and Tukey. Single clock and reset pin is synchronous to whole design from the top module of the RTL abstraction. Similarly, Figure 5.7 shows RTL schematic for N = 8 length input samples, where usage of logic elements varies as the input size differs. After design has been synthesized in gate level, we can observe the performance of the FPGA for the samples N = 2, 4 and 8. Values include power consumption of fabric and utilization of cells, slices, FFs, etc., which is briefly termed as area. These individually related values are depicted in Table 5.2, which helps us to realize the synthesized design utilization over FPGA.

![](img/d2107fc60629942e7da5355e47fcc33d_89_0.png)

Figure 5.6 RTL schematic for N = 4 DIT-FFT.

![](img/d2107fc60629942e7da5355e47fcc33d_89_1.png)

Figure 5.7 RTL schematic for N = 8 DIT-FFT.

Table 5.2 Post-synthesis performance parameters.

| Value of N | FPGA board used | Report_utilization (area) | Report_power (on chip power) |
| :--- | :--- | :--- | :--- |
| N=8 | Artix7 | Slice LUT = 826<br>Slice register = 185<br>DSP = 22 | Total on Chip Power (W) = 71.3<br>Static power (W) = 1.684<br>Dynamic power (W) = 69.71 |
| N=4 | Artix7 | Slice LUT = 164<br>Slice register = 93<br>DSP = 11 | Total on Chip Power (W) = 31.6<br>Static power (W) = 0.336<br>Dynamic power (W) = 31.30 |
| N=2 | Artix7 | Slice LUT = 40<br>Slice register = 37<br>DSP = 3 | Total on Chip Power (W) = 12.7<br>Static power (W) = 0.135<br>Dynamic power (W) = 12.59 |

## 5.4 Static Timing Analysis of Designed Circuit

We performed the STA for our design, helping us to perform timing checks such as setup and hold timing checks for the entire design in four possible paths: All registers pins to all registers, all input pins to all registers, all registers to all output pins and all input pins to all output pins. The proposed approach for STA could be observed from Figure 5.8. This helped the design to meet the specific operable clock frequency so that the original data isn’t lost at any micro architectural block of a design. Setup timing check allows the data to arrive at a flip flop/register before a clock signal can arrive, and hold timing check ensures that the data is stable until the clock signal has gone low. After getting timing summary, the frequency at which the design has met the setup slack as well as hold slack for four paths mentioned above, are included in Table 5.3. Based on the specified clock period/clock frequency the power consumed and area utilization has also been brought into the consideration. As we are performing STA after RTL generated netlist, we do not have any crosstalk or clock tree paths for

Synthesized DIT-FFT Design
Gate Level Netlist
Proceed for Timing Analysis
Divide design in to four paths
Reg to Reg
I/p to Reg
Reg to O/p
I/p to O/p
Find DPD
Find DPD
Find DPD
Find DPD
Obtain Critical Path Delay

Create Clock Constraint with appropriate time period
Generate timing summary report
Obtain Setup & Hold Slack Values
Value>0
Proceed for i/p to reg path

Create all_I/p to all_reg constraint
Generate timing summary report
Obtain Setup & Hold Slack Values
Value>0
Proceed for reg to o/p path

Create all_reg to all_o/p constraint
Generate timing summary report
Obtain Setup & Hold Slack Values
Value>0

Save the constraints as .xdc file
Run Synthesis
Timing met
Run Implementation

Timing met
End of Timing Analysis for DIT-FFT module

Figure 5.8 Flowchart representing static timing analysis of DIT FFT design.

Table 5.3 Post-timing analysis performance parameters.

| Value of N | Report_utilization (Post-Implementation & timing) | Report_Power (Post-Implementation & timing) | Report_timing_summary | Timing meet at |
| :--- | :--- | :--- | :--- | :--- |
| N = 8 | Slice LUT = 780<br>Slice Registers = 257<br>LUT as logic = 780<br>BRAM Tile = 257 | Total on chip Power (W) = 0.163 | Setup Slack = 3.258ns<br>Hold Slack = 0.430ns | 24ns |
| N = 4 | Slice LUT = 158<br>Slice Registers = 93<br>LUT as logic = 158<br>BRAM Tile = 93 | Total on chip Power (W) = 0.148 | Setup Slack = 1.574ns<br>Hold Slack = 0.321ns | 20ns |
| N = 2 | Slice LUT = 38<br>Slice Registers = 37<br>LUT as logic = 38<br>BRAM Tile = 37 | Total on chip Power (W) = 0.118 | Setup Slack = 1.506ns<br>Hold Slack = 0.062ns | 15ns |

timing analysis, thus making it a more elementary approach for fixing the timing issue for any design. Following as per the flowchart steps, we have come across several timing issues for three different samples. These are fixed by considering closest time period to the highest Data Path Delay

![](img/d2107fc60629942e7da5355e47fcc33d_92_0.png)

Figure 5.9 Post-timing analysis layout for N = 4 DIT-FFT.

![](img/d2107fc60629942e7da5355e47fcc33d_93_0.png)

Figure 5.10 Post-timing analysis layout for N = 8 DIT-FFT.

Table 5.4 Post Synthesis-post timing performance parameters.

| Value of N | Using FPGA board | Report_utilization (area) | Report_power (on chip power) |
|------------|------------------|---------------------------|------------------------------|
| N=8 | Artix7 | Slice LUT = 775<br>Slice register = 257<br>DSP = 22 | Total on Chip Power (W) = 73.89<br>Static Power (W) = 1.674<br>Dynamic Power (W) = 72.2 |
| N=4 | Artix7 | Slice LUT = 157<br>Slice register = 93<br>DSP = 11 | Total on Chip Power (W) = 32.69<br>Static Power (W) = 0.352<br>Dynamic Power (W) = 32.34 |
| N=2 | Artix7 | Slice LUT = 38<br>Slice register = 37<br>DSP = 3 | Total on Chip Power (W) = 12.72<br>Static Power (W) = 0.135<br>Dynamic Power (W) = 12.58 |
