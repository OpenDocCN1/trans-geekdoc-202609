
and heavily doped source pocket-based device. In this chapter, we review various triple metal gate vertical TFETs (TMG V-TFETs) in detail in terms of their performance compared with variations in their metal gate lengths and work functions. Section 9.2 discusses the device geometry of TMG V-TFETs, Section 9.3 has the results and discussion of its performance, Section 9.4 discusses TFETs using machine learning (ML), and Section 9.5 concludes the chapter.

## 9.2 DEVICE GEOMETRY OF TRIPLE METAL GATE (TMG) V-TFETs

### 9.2.1 GAA-Based TMG V-TFET

In this GAA-based TMG V-TFET device, there are three metal gate layers—MG1, MG2, and MG3—designed in such a way that all the metal gates have a different work function: WF1, WF2, and WF3, respectively. In this device, source and drain are of heavily doped Ge and Si, respectively, and its performance characteristics are investigated by technology computer-aided design (TCAD) based simulation with various models. This device is actually designed to tackle the TFET’s limitations in performance and also the ambipolarity of existing TFET devices. The GAA-based TMG V-TFET devices are highly useful in various future applications that demand low-power consumption and negligible amount of leakage current [16–26].

Figure 9.1 shows the various views of TMG V-TFET having three metal gate layers—MG1, MG2 and MG3—with different work functions (WF1, WF2, and WF3, respectively). The important design specifications considered in this TMG V-TFET are lengths of the metal gate layers (L1, L2, and L3), length of the channel (Lc), channel region diameter (Nc), total nanowire diameter (Dt), and work functions of all the metal gate layers (WF1, WF2, and WF3). In Figure 9.1c, the energy-band diagrams of the TMG V-TFET are given with respect to the different work functions defined for the respective metal gate layers.

Table 9.1 represents all the important design specifications considered in this GAA-based TMG V-TFET [27].

Figure 9.2 presents the transfer characteristics ($I_{DS}$–$V_{GS}$) curves for a TMG V-TFET. The simulation results give $I_{ON}$ approximately equal to 10⁻⁵ μA/μm, subthreshold swing (SS) value of 8 mV/decade, and average subthreshold slope at approximately 43.5 mV/decade. The performance behavior of the TMG V-TFET is dependent on the charge carriers at the channel surface. Therefore, its circumference, given by 2 × π × rchannel, can easily normalize the $I_{DS}$ value. So, all the metal gates’ work functions and their respective lengths (L1, L2 and L3) on the TMG V-TFET are analyzed. Simulation results show that the source-channel BTBT rate is linked to the metal gate 1 and metal gate 2 parameters, which, in turn, is affecting the device performance. But this tunneling rate at its interface affects the ambipolar current and also metal gate 3 (MG3), which also affects the ambipolarity like the MG1/MG2 parameters.

In Figure 9.3a, WF2 and WF3 values are kept constant at 4.5 eV. As WF1 increases, tunneling probability reduces, and at $V_{DS} = V_{GS}$ at 0.5 V, $I_{ON}$ also decreases significantly, as there is an increase in voltage for the BTBT mechanism [14]. In Figure 9.3b, WF1 and WF3 values are kept constant at 4.2 eV.

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_177_0.png)

FIGURE 9.1 (a) Depicts the 3D device structure of TMG V-TFET, (b) 2D view, and (c) shows the energy band diagram.

Source: [27].

TABLE 9.1
Important Design Specifications of GAA-Based TMG V-TFET

| Design Parameters | Values |
|---|---|
| Doping concentration at drain p-type | 10^20 cm^-3 |
| Doping concentration at source n-type | 10^20 cm^-3 |
| Diameter of nanowire (Dt) | 14 nm |
| Diameter of channel region (Ns) | 7 nm |
| Equivalent thickness of oxide (Tox) | 0.6 nm |
| Metal Gate 1 length (L1) | 7 nm |
| Metal Gate 2 length (L2) | 14 nm |
| Metal Gate 3 length (L3) | 7 nm |
| Channel length (Lc) | 28 nm |
| Work function of metal gate 1 | 4.2 eV |
| Work function of metal gate 2 | 4.5 eV |
| Work function of metal gate 3 | 4.2 eV |

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_178_0.png)

FIGURE 9.2 Transfer characteristics ($I_{DS}$–$V_{GS}$) of TMG V-TFET.

Source: [27].

As WF2 increases, OFF-state current ($I_{OFF}$) is reduced by its potential barrier between metal gates (MG1 and MG2). In TMG V-TFET, ON-state current ($I_{ON}$) remains the same when WF2 rises from 4.1 to 4.5 eV. However, at WF2 = 4.6 eV or greater, it allows only the high-energy tunneled electrons in its channel region to flow by the BTBT mechanism. It concludes that $I_{ON}$ and SS both depend on the source region and channel region's BTBT rate. In Figure 9.3c, when WF1 is at 4.2 eV and WF3 is at 4.5, respectively, it is clear that the WF3 impact is minimal on performance. As observed from the simulation results, for a greater BTBT rate and drain current, WF1 should be less than 4.2 eV and for a lower OFF-state current, WF2 should be less than 4.6 eV.

### 9.2.2 Nanowire-Based TMG V-TFET

In this nanowire (NW) based TMG V-TFET, the impacts of various DC parameters, like varying the values of different metal gate work functions and changing the metal gate lengths, are analyzed for comparing the major transfer characteristics and subthreshold swing using simulation results. This device shows a preferable boost in its $I_{ON}$ with a gradual decrease in $I_{OFF}$ current. It also has a better subthreshold slope even at a low threshold voltage.

Figure 9.4 shows the device structure of the NW-based TMG V-TFET with different views for a better understanding, which is almost identical to the previous GAA-based TFET structure with certain variations in its design parameters. The parameters and specifications used in its designing are in Table 9.2 [28].

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_179_0.png)
![](img/402dddaf38ede9d8a9b9be4ba7a9004a_179_1.png)
![](img/402dddaf38ede9d8a9b9be4ba7a9004a_179_2.png)

FIGURE 9.3 Transfer characteristics ($I_{DS}$–$V_{GS}$) of TMG V-TFET for different WF1, WF2, and WF3.

Source: [27].

The length of the source region is considered 10 nm, same as that of the drain region. The oxide layer is of SiO2. The radius of the nanowire is 5 nm. The Silvaco Atlas simulator has been used for checking the device’s properties.

Figure 9.5 represents the device’s energy-band diagram. From Figure 9.5, it is clear that the metal length variation does not show any impact in the sides of the

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_180_0.png)

FIGURE 9.4 Device structure of NW-based TMG V-TFET: (a) 3D device structure and (b) 2D device structure.

Source: [28].

| Design Parameters | Values |
| :--- | :--- |
| Doping concentration, p-type channel | 10¹⁵ cm⁻³ |
| Doping concentration, n-type drain | 5×10¹⁸ cm⁻³ |
| Doping concentration, p-type source | 10²⁰ cm⁻³ |
| Nanowire radius | 5 nm |
| Channel length | 20 nm |
| Metal gate 1 length (L1) | 7 nm |
| Oxide thickness | 1.5 nm |
| Metal gate 2 length (L2) | 6 nm |
| Metal gate 3 length (L3) | 4 nm |
| Work function of metal gate 1 | 4.1 eV |
| Work function of metal gate 2 | 4.5 eV |
| Work function of metal gate 3 | 4.4 eV |

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_181_0.png)

FIGURE 9.5 NW-based TMG V-TFET energy-band diagram.

Source: [28].

channel, but it does show in its middle region. This energy bandgap is minimum at fourth arrangement with 8:4:8 ratio, and it is maximum at the first arrangement with a ratio of 5:10:5, as shown in Figure 9.5. With the decrease in second metal gate length (L2), the energy gap also shows a gradual decrease in its level, which increases the tunneling across the structure.

Figure 9.6 shows the $I_D$-$V_{GS}$ characteristics of NW-based TMG V-TFET. We observe that its $I_{ON}$ value is $2.8 \times 10^{-6}$ A/$\mu$m, $I_{OFF}$ current is $4.3 \times 10^{-20}$ A/$\mu$m, its $I_{ON}/I_{OFF}$ value is $6.5 \times 10^{13}$, and its SS value is 6.59 mV/decade at a $V_T$ of 0.172 V.

### 9.2.3 Triple Metal Gate Stacked V-TFET

In the triple metal gate stacked III-V vertical TFET (TM-GS-V-TFET), there are two structures to examine. One is Device A, in which a source pocket is used. The other is Device B, in which a new source extension approach is used.

Source pocket-based TFETs are introduced for their improved $I_{ON}$, reduced $I_{OFF}$, and steeper SS as compared to the basic TFET structures. However, their fabrication procedures are quite complex as compared to the conventional ones. The source extension–type TFET improves the electric field, which reduces its tunneling barrier
