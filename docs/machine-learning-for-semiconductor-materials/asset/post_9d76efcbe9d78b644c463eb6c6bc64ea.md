
with higher \( K_{\text{bio}} \) suggests that the biosensor is more sensitive to biomolecules with higher dielectric constants, supporting the results of this study. The greater relative change in channel potential is a critical parameter for evaluating the biosensing performance of the cylindrical BioFET. Notably, increasing the gate voltage reduces the potential curvature, so the channel potential is plotted at a low gate voltage of 10 mV to emphasize the effect of biomolecules on the curvature. These results highlight the necessity of carefully balancing drain and gate voltages to optimize sensor performance while avoiding device damage. Understanding the changes in potential distribution across the channel further underscores the importance of dielectric properties in enhancing biosensor sensitivity. Such insights are crucial for designing robust and highly sensitive BioFETs tailored for specific biomedical and environmental applications.

Figure 7.15 shows how temperature affects the threshold voltage sensitivity, with an inset for different charged biomolecules. Increased temperature boosts charge carrier generation [60], lowering the threshold voltage and increasing its relative change, enhancing sensitivity to biomolecules. It is crucial for FETs to choose the right gate oxide, like SiO\(_2\) for its stability and compatibility. Integrating high-K dielectrics with SiO\(_2\) reduces fringing fields [18] but sacrifices sensitivity and adds complexity. Figure 7.15 compares sensitivity in the cylindrical BioFET with and without stacked gate oxide for various biomolecules, highlighting sensitivity enhancement versus fabrication complexity.

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_145_0.png)

FIGURE 7.15 Threshold voltage sensitivity variation at different temperatures for hydrophobic protein. ([INSET] Shows the threshold voltage sensitivity variation at different temperatures for different charged biomolecules.)

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_146_0.png)

| Biomolecules (\(\rho\)) | No_GOS | With_GOS |
|---|---|---|
| -1E+11 | 74.1571 | 51.52132 |
| 0 | 68.6916 | 43.43865 |
| 1E+11 | 63.0684 | 31.92908 |

FIGURE 7.16 Threshold voltage sensitivity with and without gate oxide stack for different neutral biomolecules.

Table 7.5 presents the impact of biomolecule location at various fill-in factors. The cavity around the source and drain is divided into four equal parts, allowing different test biomolecules to be examined under various conditions. Case 5 has a larger fill-in factor than Case 4, yet Case 4 shows higher sensitivity. This trend is similarly observed between Case 3 and Case 5, as well as between Case 10 and Case 11, among others.

Typically, a higher fill-in factor increases sensitivity by immobilizing a greater number of biomolecules within the cavity [10]. However, the specific location of biomolecules within partially filled cavities notably impacts sensitivity. Case 4, for example, despite having the same fill-in factor as Case 1, exhibits higher sensitivity because biomolecules are situated closer to the source. This proximity enhances their influence on the potential hill at the source-channel junction, thereby affecting threshold voltage more significantly. Consequently, sensitivity is maximized when biomolecules are positioned nearer to the source [61]. Similar sensitivity trends are observed in comparisons between Case 5 and Case 10, Case 11 and Case 14, and other analogous scenarios.

Figures 7.17 and 7.18 depict a comparative analysis of the cylindrical BioFET biosensor with various existing variants of biosensors. It is evident from the figures that the threshold voltage shift (sensitivity) increases proportionally with the widening of the cavity, allowing for a greater number of biomolecules to be immobilized within it. Consequently, the biosensor shows a more pronounced change in threshold voltage with larger cavity dimensions. Figure 7.18 specifically compares the sensitivity of our

TABLE 7.5 Effect of Fill-In Factor and Location of Different Biomolecules on $S_{vt}$

| | Cavity towards Source End $L_{CH1}$ | Oxide Layer $L_{CH3}$ | Cavity towards Drain End $L_{CH2}$ | Fill-In Factor | A | B | C | D | E | F |
|---|---|---|---|---|---|---|---|---|---|---|
| 1. | | | | 0.25 | 0.006 | 0.095 | 0.597 | 1.409 | 1.74 | 2.027 |
| 2. | | | | 0.25 | 1.004 | 4.557 | 5.665 | 10.095 | 16.772 | 22.996 |
| 3. | | | | 0.25 | 17.834 | 43.669 | 51.006 | 86.091 | 113.111 | 120.049 |
| 4. | | | | 0.25 | 38.927 | 64.879 | 72.905 | 106.778 | 135.889 | 152.651 |
| 5. | | | | 0.50 | 3.929 | 6.842 | 7.556 | 12.298 | 19.115 | 27.983 |
| 6. | | | | 0.50 | 22.003 | 52.932 | 46.579 | 90.029 | 119.882 | 135.002 |
| 7. | | | | 0.50 | 25.991 | 55.014 | 49.082 | 93.332 | 122.229 | 138.909 |
| 8. | | | | 0.50 | 40.02 | 66.698 | 74.117 | 108.183 | 137.710 | 154.119 |
| 9. | | | | 0.50 | 44.384 | 70.192 | 78.251 | 112.672 | 141.008 | 158.725 |
| 10. | | | | 0.50 | 62.193 | 89.002 | 96.621 | 130.298 | 159.027 | 186.791 |
| 11. | | | | 0.75 | 37.971 | 61.995 | 71.003 | 105.391 | 134.441 | 160.219 |
| 12. | | | | 0.75 | 46.929 | 72.982 | 80.388 | 114.901 | 143.412 | 169.590 |
| 13. | | | | 0.75 | 65.129 | 91.109 | 99.041 | 133.923 | 162.721 | 189.993 |
| 14. | | | | 0.75 | 68.905 | 94.795 | 102.003 | 136.729 | 165.11 | 192.10 |

A-Streptavidin | B-Protein | C-Biotin | D-APTES | E-Hydrophobic protein | F-Keratin

biosensor with a prominent BioFET variant across different biomolecules [22–26]. The inset provides a visual representation of the threshold voltage sensitivity comparison between the proposed structure and four other variants. This comparison underscores that our biosensor offers superior sensitivity to biomolecules compared to most of the existing alternatives. Figure 7.19 shows the plot of gain transconductance frequency product (GTFP) for the proposed device at $N_S = N_D = 10^{19}/cm^3$ and $N_C = 10^{10}/cm^3$.

## 7.3.3 Machine Learning in Improving the BioFET Performance

Machine learning has significantly advanced the capabilities of BioFETs, by enhancing their sensitivity and specificity. A BioFET is a sophisticated biochemical sensor that operates on principles similar to those of a field effect transistor. This integration would permit a real-time investigation, which helps identify biological molecules like proteins, DNA, and pathogens. Training ML

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_148_0.png)

FIGURE 7.17 Comparison chart showing the shift in threshold voltage for APTES at different cavity thicknesses.

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_148_1.png)

FIGURE 7.18 Comparison chart showing the shift in threshold voltage for different biomolecules. ([INSET] Shows the shift in threshold voltage in different variants of biosensor for K_bio = 5.)

![](img/402dddaf38ede9d8a9b9be4ba7a9004a_149_0.png)

FIGURE 7.19 Gain transconductance frequency product plot.

models on such large datasets allows for the detection of subtle changes in sensor responses, leading to more effective detection and lower false favorable (detection) rates. Therefore, the advanced ML applications on BioFETs for medical diagnostics, environmental monitoring, and biotechnology shows an enhanced tool platform that can realize the rapid and accurate detection of numerous biological analytes [35].

Enabling the modification and tailoring of BioFETs for specific applications, using machine learning in combination with BioFETs, offers significant design benefits in biosensor development. Researchers can use sophisticated algorithms to model a range of conditions and geometries to target optimal sensor designs before they are fabricated. This speeds up the development process while reducing expensive trial-and-error methods. In addition, using historical data, machine learning can fine-tune sensor parameters to become more precise over time, so as new biological targets emerge, the sensor adapts with the changing times. The data that BioFETs produce is typically complex with multiple dimensions, which makes machine learning indispensable in interpreting such data. The influx of data that these sensors generate can be difficult to handle using traditional data analysis methods. On the other hand, ML models, such as neural networks, support vector machines (SVMs), and decision trees, are very good for identifying these correlations in big data collections. These approaches reveal more detailed details about how sensor responses relate to the biological interactions of the sensor surface for
