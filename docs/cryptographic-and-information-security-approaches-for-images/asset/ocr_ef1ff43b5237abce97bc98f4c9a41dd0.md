![](bbox=[0.11, 0.13, 0.89, 0.37])

# Figure 13.7 2-D integer DCT architecture of proposed system.

on each positive edge of the clock from SRAM. Thus, around 9 clocks are desired to process every 8 × 8 block with initial latency of one clock for column processing. Eight elements are provided to the transpose memory as shown in Figure 13.8.

The values of column processing from 1-D DCT are stored in transpose memory horizontally and read through row processing vertically. Then 2-D DCT values are generated and stored in internal block RAM for further watermark embedding process.

In our algorithm, we have implemented 8 × 8 DCT block using transpose memory. The method is multiplier-less and uses 56 adders/subtractors. The design is implemented on Vertex 2 pro and maximum operating frequency is around 367 MHz.

![](bbox=[0.2, 0.64, 0.85, 0.85])

# Figure 13.8 Proposed transpose memory block.