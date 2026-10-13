
# ReRAM Crossbar Structures

Because of the high density of ReRAM device, one can build a crossbar structure as the array of ReRAM [59, 140–144]. Such crossbar structure can be utilized as memory for high-density data storage. The memory array can be read or written by controlling the voltage of wordlines (WLs) and bitlines (BLs). For example, we can apply `V_write` on the `i`-th WL and `0` on the `j`-th BL to write data into the ReRAM cell on `i`-th row, `j`-th column.

## 3.2.1 Analog and digitized ReRAM crossbar

This section introduces the traditional analog ReRAM crossbar and the digitized ReRAM crossbar in the following. The I/O interface and the number of ReRAM device resistance value are different in these two structures.

### 3.2.1.1 Traditional analog ReRAM crossbar

ReRAM is an emerging nonvolatile memory based on two-terminal junction devices, whose resistance can be controlled by the integral of externally applied currents. The fabric of crossbar intrinsically supports matrix–vector multiplication where vector is represented by row input voltage levels and matrix is denoted by the mesh of ReRAM resistances. In order to calculate the matrix–vector multiplication `y = Wx`. As shown in [Figure 3.11](#Chapter3.html#c03_fig11), by configuring `W` into the ReRAM crossbar and setting `x` as the crossbar input, the analog computation can be achieved by ReRAM crossbar directly with output `y`.

![Figure 3.11 Traditional analog-fashion ReRAM crossbar with ADC and DAC](images/PBPC0390-03-f11.jpg)

However, such an analog ReRAM-crossbar has two major drawbacks. First, the programming of continuous-valued ReRAM resistance is practically challenging due to large ReRAM process variation. Specifically, the ReRAM resistance is determined by the integral of current flowing through the device, which leads to a switching curve as shown in [Figure 3.12](#Chapter3.html#c03_fig12)(a). With the process variation, the curve may shift and leave intermediate values very unreliable to program, as shown in [Figure 3.12](#Chapter3.html#c03_fig12)(b). Second, the analog-to-digital converter (ADC) and digital-to-analog converter (DAC) are both time-consuming and power-consuming. In our simulation, the analog-to-digital and digital-to-analog conversion may consume up to 85.5% of total operation energy in 65 nm as shown in [Figure 3.13](#Chapter3.html#c03_fig13).

![Figure 3.12 (a) Switching curve of ReRAM under device variations. (b) Programming inaccuracy for different ReRAM target resistances](images/PBPC0390-03-f12.jpg)

![Figure 3.13 (a) Power consumption of analog-fashion ReRAM crossbar. (b) Area consumption of analog-fashion ReRAM crossbar](images/PBPC0390-03-f13.jpg)

### 3.2.1.2 Digitalized ReRAM crossbar

To overcome the aforementioned issues, a fully digitalized ReRAM crossbar for matrix-vector multiplication is proposed. First, as ON-state and OFF-state are much more reliable than intermediate values shown in [Figure 3.12](#Chapter3.html#c03_fig12), only binary values of ReRAM are allowed to reduce the inaccuracy of ReRAM programming. Second, a pure digital interface without A/D conversion is deployed.

In ReRAM crossbar, we use `V_WL[i]` and `V_BL[j]` to denote voltage on `i`-th WL and `j`-th BL. `R_LRS` and `R_HRS` denote the resistance of LRS and HRS, respectively. In each sense amplifier (SA), there is a sense resistor `R_sense` with fixed and small resistance. The relation among these three resistance is `R_LRS < R_sense < R_HRS`. Thus, the voltage on `j`-th BL can be presented by

```
V_BL[j] = (Σ_i g_ij * V_WL[i]) / (Σ_i g_ij + 1/R_sense)
```

where `g_ij` is the conductance of `R_ij`.

The key idea behind digitalized crossbar is the use of comparators. As each column output voltage for analog crossbar is continuous-valued, comparators are used to digitize it according to the reference threshold applied to SA:

```
V_BL[j] > V_ref ? 1 : 0
```

However, the issue that rises due to the digitalization of analog voltage value is the loss of information. To overcome this, three techniques can be applied. First, multi-thresholds are used to increase the quantization level so that more information can be preserved. Second, the multiplication operation is decomposed into three suboperations that binary crossbar can well tackle. Third, the thresholds are delicately selected at the region that most information can be preserved after the digitalization.

Compared to the traditional analog ReRAM-crossbar [145, 146], the advantages of the digital ReRAM-crossbar are the following:

*   It has better programming accuracy of the ReRAM device under process variation with no additional ADC conversation as well.
*   Since only LRS and HRS are configured in digital ReRAM crossbar, it does not require high HRS/LRS ratio so that low-power (high LRS) device [139] can be applied. In addition, the wire resistance affects little on IR-drop when using the low-power ReRAM device.
*   The binary input voltage has a better robustness on the IR-drop in large-size crossbar.

However, the area and energy consumption of ReRAM devices will increase in the digital ReRAM-crossbar implementation. It will also be discussed in [Section 3.5](#Chapter3.html#c03_sec5).

## 3.2.2 Connection of ReRAM crossbar

There are three approaches for the connection of ReRAM crossbar: direct-connected ReRAM, one-transistor-one-ReRAM (1T1R), and 1S1R. These approaches are described in-detail along with the differences among them.

### 3.2.2.1 Direct-connected ReRAM

Direct-connected ReRAM, also known as the passive ReRAM array, which is a crossbar structure with only ReRAM devices. Every WL and BL are connected with a single drift-type ReRAM. The structure of direct-connected ReRAM is shown in [Figure 3.14](#Chapter3.html#c03_fig14)(a), and here we use `N` WL (`i ∈ [1, N]`) and `M` BL (`j ∈ [1, M]`) as an example. To perform a write operation, one needs to apply a write voltage `V_write` between `WL[i]` and `BL[j]`. In this case, the ReRAM connecting them (`R_ij`) can be precisely configured.

![Figure 3.14 Comparison of ReRAM-crossbar implementation among (a) direct connection with sneak path; (b) 1T1R with extra control signals; (c) proposed sneak-path-free 1S1R without extra control signals; (d) comparison of analog and digital interfaces](images/PBPC0390-03-f14.jpg)

However, a problem exists in this structure that sneak path may occur. In this example, the purple path is the ideal current path we want to have, but there may be another path identified by green. This path consists of `R_ik`, `R_lk`, and `R_lj` so that we can see a `V_write` is also applied on the serial of these three ReRAMs. In some of the cases, two of them are in LRS and one of them is in HRS, causing a very large voltage applied on the ReRAM device in HRS. In this case, the status of this ReRAM may also be configured, which we do not want it happens.
