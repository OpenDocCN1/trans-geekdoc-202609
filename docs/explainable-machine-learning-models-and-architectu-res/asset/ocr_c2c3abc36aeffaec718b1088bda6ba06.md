# Summary

Power analysis from implemented netlist. Activity derived from constraints files, simulation files or vectorless analysis.

+   - Total On-Chip Power: 0.224 W
+   - Design Power Budget: Not Specified
+   - Power Budget Margin: N/A
+   - Junction Temperature: 26.0°C
+   - Thermal Margin: 59.0°C (12.8 W)
+   - Effective θJA: 4.6°C/W
+   - Power supplied to off-chip devices: 0 W
+   - Confidence level: Medium
+   - Launch Power Constraint Advisor to find and fix invalid switching activity

![](bbox=[0.477, 0.143, 0.861, 0.363])

Figure 4.6 Power analysis of audio module on FPGA.

simplifies the configuring process of clocks in FPGA. According to user requirement the clocking wizard generates HDL code for configuring the clock circuits. Table 4.1 and Table 4.2 show, respectively, device utilisation and timing summary observed on FPGA. The total on chip power obtained on FPGA is 0.224W, out of which 57% dynamic and 43% static power consumption are shown in Figure 4.6.

# 4.6 Conclusion

Reconfigurable architectures like FPGA can be used for the implementation of machine learning model to observe a real-time response with improvement in accuracy, speed and power consumption. This process of implementation is followed by identifying the suitable machine learning algorithm for any specific task and implementing it through HDL code, synthesis and bitstream generation using simulation software like Xilinx Vivado. The generated bitstream is used to implement the same on FPGA board or prototyping before proceeding to the layout and fabrication of ASIC.

# 4.7 Future Scope

Biomedical data processing is another key area of research to make efficient and accurate biomedical devices and sensors [23–25]. A situation like