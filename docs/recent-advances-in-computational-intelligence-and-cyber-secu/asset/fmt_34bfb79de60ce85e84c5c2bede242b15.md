
In order to optimize delay and power, the `MTCMOS` (Multi-threshold CMOS) technology employs transistors with various threshold voltages. Low `V[t]` transistors switch more quickly but leak more static power. However, high `V[t]` transistors switch more slowly while reducing static power leakage [[19](#ch29.xhtml#ref29_19)]. With the use of well-planned circuits, `MTCMOS` design strategies can optimize power and latency without suffering consequences. Use of sleep transistors is the most popular method of `MTCMOS` leakage power reduction [[20](#ch29.xhtml#ref29_20)]. Sleep transistors are used to build virtual power lines that supply the logic.

### 3.2. Gated V[dd]

This method offers a control mechanism that, when the `SRAM` cell is not in use, can disable the supply voltage (`V[dd]`), so preventing any leakage current. This significantly lowers the leakage power dissipation [[21](#ch29.xhtml#ref29_21)]. A high threshold voltage (high `V[t]`) transistor is added to the supply (`V[dd]`) or ground channel of the `SRAM` cell in order to implement this control mechanism, with all other transistors being modeled as low `V[t]` transistors. Because they flip more quickly than high `V[t]` transistors, low `V[t]` transistors are used. The `SRAM` cell operates quickly as a result. The power usage and delay are optimized in this setup [[22](#ch29.xhtml#ref29_22)]. [Figure 29.5](#ch29.xhtml#fig29_5) show the schematic output of sense amplifiers. After correct sensing the signal, various types of analysis for delay and power dissipation are done. After precharging the bit lines and output-lines, the time taken by the sense amplifier to give sufficient large voltage difference at bit-line is considered as delay [[23](#ch29.xhtml#ref29_23)].

![Figure 29.5: Output of basic SA.](images/fig29_5_C.jpg)

[Figure 29.5: Output of basic SA.](#ch29.xhtml#R_fig29_5)

Delay consists of discharging and latching types delay. The discharging delay depends on the bitline capacitances. Supply voltage variation mainly affects the latching delay [[24](#ch29.xhtml#ref29_24)]. [Figures 29.6](#ch29.xhtml#fig29_6) and [29.7](#ch29.xhtml#fig29_7) show the delay and power dissipation of various types of sense amplifier used for `SRAM` IC.

![Figure 29.6: Delay calculation of various types of SA.](images/fig29_6_C.jpg)

[Figure 29.6: Delay calculation of various types of SA.](#ch29.xhtml#R_fig29_6)

![Figure 29.7: Power dissipation of various types of SA.](images/fig29_7_C.jpg)

[Figure 29.7: Power dissipation of various types of SA.](#ch29.xhtml#R_fig29_7)

## 4. Result and Discussion

Take `C[DL]` = 1pF, `C[PL]` = 1pF and `C[Load]` = 100pF delay and power dissipation comparison of hybrid mode SA with different types of current and voltage sense amplifiers. The delay and power dissipation shown in [Table 29.1](#ch29.xhtml#tab29_1) and [Figures 29.6](#ch29.xhtml#fig29_6), [29.7](#ch29.xhtml#fig29_7) show the comparative analysis of my paper work.

[Table 29.1: Delay and power dissipation](#ch29.xhtml#R_tab29_1)

| Types of SA  || Delay (ns) || Total power dissipation (mW) || Work |
| --- | --- | --- | --- |
| Bit-line capacitance delay (ns) || Total power dissipation (mW) |
| Cross coupled CMOS inv. SA || 1.9880 || 0.804 || 1.4513 || 0.562 |
| --- | --- | --- | --- | --- |
| Latch type voltage SA || 1.241 || 0.947 || 0.90593 || 0.662 |
| Basic current SA || 0.2305 || 0.953 || 0.2305 || 0.953 |
| Hybrid mode SA || 0.1436 || 0.386 || 0.1048 || 0.270 |

In [Table 29.1](#ch29.xhtml#tab29_1) summarized the delay and total power dissipation for four types of sense amplifiers.

In hybrid mode SA total power dissipation is lowered approximately by 55%, 60%, and 90% as compared with cross coupled inverter SA, latch type voltage SA, basic current SA, respectively. Similarly in hybrid mode SA total delay decreased approximately by 98.8%, 84.43% and 52% as compared with cross coupled inverter SA, latch type voltage SA, basic current SA, respectively.

## 5. Conclusions

Sense amplifier is very important element of `SRAM` memory. Its performance affects the delay in decision and also total power dissipation in memory. Result shows that hybrid mode sense amplifier has less delay and low power dissipation. [Figure 29.6](#ch29.xhtml#fig29_6) shows `delay_1` [[1](#ch29.xhtml#ref29_1)] while `delay_2` show the result of designed schematic. Hybrid mode sense amplifier with `MTCMOS` has fast speed and low power dissipation with respect to other sense amplifier. In cross coupled sense amplifier as input and output pins are same so it takes more time to discharge.

## References

1. [Surkar, A. and Agarwal, V.](#ch29.xhtml#R_ref29_1) (2019). Delay and power analysis of current and voltage sense amplifiers for SRAM at 180nm technology. 2019 3rd Int. Conf. Elec. Comm. Aerospace Technol. (ICECA) IEEE, 1371-1376.

2. [Nibhanupudi, S. S. T., Raman, S., Raman, S., and Jaydeep, P. K.](#ch29.xhtml#R_ref29_2) (2021). Phase transition material-assisted low-power SRAM design. IEEE Trans. Elec. Dev., 68(5), 2281-2288.

3. [Kumar, H. and Tomar, V. K.](#ch29.xhtml#R_ref29_3)(2021). A review on performance evaluation of different low power SRAM cells in nano-scale era. Wireless Per. Comm., 117(3), 1959-1984.

4. [Pal, S., et al.](#ch29.xhtml#R_ref29_4) (2020). A highly stable reliable SRAM cell design for low power applications. Microelec. Reliab., 105, 113503.

5. [Abbasian, E., et al.](#ch29.xhtml#R_ref29_5) (2023). A low-power SRAM design with enhanced stability and ION/IOFF ratio in Fin FET technology for wearable device applications. Int. J. Elec., 1-18.

6. [Neeraj, K., Mahaboob Basha, Md., and Srinivasulu, G.](#ch29.xhtml#R_ref29_6) (2021). Design of low power SRAM-based ubiquitous sensor for wireless body area networks. Int. J. Perv. Comput. Comm., 17(5), 611-621.

7. [Kumar, P. D., Ritesh Kumar, K., and Karuppanan, P.](#ch29.xhtml#R_ref29_7) (2021). Design and analysis of low-power SRAM. Adv. VLSI Comm. Sig. Proc. Select Proc. VCAS 2019, 41-56.

8. [Kim, Y., et al.](#ch29.xhtml#R_ref29_8) (2021). Ultra-low power and high-throughput SRAM design to enhance AI computing ability in autonomous vehicles. Electronics, 10(3), 256.

9. [Dutt, D., et al.](#ch29.xhtml#R_ref29_9) (2022). Design and performance analysis of high-performance low power voltage mode sense amplifier for static RAM. Adv. Elec. Electron. Engg., 20(3), 285-293.

10. [Chen, J., et al.](#ch29.xhtml#R_ref29_10) (2021). Analysis and design of reconfigurable sense amplifier for compute SRAM with high-speed compute and normal read access. IEEE Trans. Cir. Sys. II Exp. Briefs, 68(12), 3503-3507.

11. [Saini, A., Parnav Kumar, G., and Ruchi, G.](#ch29.xhtml#R_ref29_11) (2019). Analysis of low power SRAM sense amplifier. 2019 Int. Conf. Elect. Elec. Comp. Engg. (UPCON) IEEE, 1-6.

12. [Saun, S. and Kumar, H.](#ch29.xhtml#R_ref29_12) (2019). Design and performance analysis of 6T SRAM cell on different CMOS technologies with stability characterization. IOP Conf. Ser. Mat. Sci. Engg., 561(1).

13. [Shukla, N. Kr, Pulkit, B., and Shilpi, B.](#ch29.xhtml#R_ref29_13) (2015). Design and analysis of a novel ultra-low power SRAM bit-cell at 45nm CMOS technology for bio-medical implants. Int. J. Comp. Appl., 975, 8887.

14. Mishra, K. C. and Singh, R. K. (2019). Design and analysis of low power SRAM using CMOS technology. Int. J. Innov. Technol. Explor. Engg., 8(12S), 896-902.

15. [Dounavi, H.-M., Yiorgos, S., and Yiorgos, T.](#ch29.xhtml#R_ref29_15) (2019). Periodic monitoring of BTI induced aging in SRAM sense amplifiers. IEEE Trans. Device Mater. Reliab., 19(1), 64-72.

16. [Zhao, Y., et al.](#ch29.xhtml#R_ref29_16) (2022). An offset cancellation technique for SRAM sense amplifier based on relation of the delay and offset. Microelec. J., 128, 105578.
