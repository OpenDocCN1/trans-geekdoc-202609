
[17] Shannon, A., & Atanassov, C., “On a generalization of intuitionistic fuzzy graphs.” *NIFS*, (2006). http://ifigenia.org/wiki/issue:nifs/12/1/24-29

[18] Shao, Z., Kosari, S., Rashmanlu, H., & Shoaib, M., “New concepts in intuitionistic fuzzy graph with application in water supplier systems.” *Mathematics*, (2020). https://doi.org/10.3390/math8081241

[19] Shoaib, M., Mahmood, W., Xin, Q., & Tchier, F., “Certain operations on picture fuzzy graph with application.” *Symmetry*, (2021). https://doi.org/10.3390/sym13122400

[20] Islam, S. R., & Pal, M., “Hyper-Wiener index for fuzzy graph and its application in share market.” *Journal of Intelligent & Fuzzy Systems*, (2021). https://doi.org/10.3233/JIFS-210736

[21] Yaqoob, N., Gulistan, M., Kadry, S., & Wahab, H. A., “Complex intuitionistic fuzzy graphs with application in cellular network provider companies.” *Mathematics*, (2019). https://doi.org/10.3390/math7010035

[22] Aruldoss, M., Lakshmi, T. M., & Venkatesan, V. P., “A survey on multi criteria decision methods and its applications.” *American Journal of Information Systems*, (2013). https://doi.org/10.12691/ajis-1-1-5

# Optimizing the Surface Roughness of H13 Steel Machined by Wire Electrical Discharge

Pham Thi Hong Nga, Van Tran Tran, Thanh Tan Nguyen, Xuan Tien Vo, and Van-Thuc Nguyen*

## 6.1 INTRODUCTION

Wire electrical discharge machining (WEDM) is a method that can machine complex shapes and extremely hard materials that the traditional method cannot process [1–3]. WEDM uses a thin wire made from copper and tungsten as an electrode to discharge the conductive materials. The discharge process erodes the machined part gradually without direct contact with it. The cooling environment removes the thermal energy that appears during the WEDM process; therefore, there is no thermal effect on the heat-treated steel part [4, 5, 6].

AISI H13 steel is a chromium hot tool steel that is commonly used in both hot and cold tooling applications, belonging to group H under the AISI classification. H-13 steel has good abrasion resistance at both low and high temperatures, as well as high toughness and ductility [7, 8, 9]. H13 hot work tool is used more than any other tool in tooling applications due to its exceptional combination of toughness and fatigue resistance.

However, machining H13 steel is a challenging issue that often requires state-of-the-art tools or methods. For example, Caldwell et al [10] applied high-speed machining to H13 steel using carbide tooling, and the carbide tool was able to generate 210 holes with 16 mm depth, 30 mm/min cutting speed, and a 0.1 mm/rev feed rate. Umbrello et al [11] presented a model for computer hard-machining H13 steel. The hardness-based flow stress and fracture models could imitate the effect of hardness on the formation of the chip.

Zhang et al [12] used physical vapor deposition coating on the cutting tools, reducing the cooling tool temperature. The TiAlN coating produced a higher tool-chip interface temperature than the Ti coating. Do et al. [13] identified the optimal cutting parameter with the least lubricant for milling H13 steel; they determined that the feed rate has the strongest influence on the surface roughness. Interestingly, Yan et al. [14] investigated the thermo-mechanical model of turning finished H13 hardened steel by examining the machining parameters. The outcomes can be used to improve the design of cutting inserts and optimize process parameters for AISI H13 turning. Zhang et al. [15] studied thermal deformation with thin-walled shapes during WEDM. They machined AISI H13, SKD 11 and Inconel 718 with different wire parameters, speeds, and pulse-on time, the thermal deformation during WEDM was strongly impacted by physical properties, yield strength, and thermal conductivity.

Optimizing machining parameters is one effective method of achieving the best results from multiple parameter conditions [16, 17, 18]. Sadhana et al. [19] studied the impact of optimizing WEDM parameters on the material removal rate (MRR) and surface roughness (Ra) of AISI H13 steel and found that had had the impact on MRR and Ra. Chockaling et al. [20] also considered the spark gap and dimensional deviation during the WEDM of AISI T-15-HSS steel. they investigated the impact of certain parameters—reference value, pulse-on time (Ton), pulse-off time (Toff), wire speed, tension and pressure mode—and analyzed the results using MATLAB 6.5 gray ratio analysis and Lingo 6 optimization software.

> *Corresponding author: nvthuc@hcmute.edu.vn
> DOI: 10.1201/9781032635170-6

## 6.2 PROBLEM STATEMENT

The influence of discharge time on the surface roughness of H13 steel machined by WEDM is rarely discussed and needs further investigation. In this study, we investigated the effects of discharge time on Ra for H13 steel by WEDM then discuss the microstructure of the machined sample and used the results to optimize the WEDM process for H13 steel.

## 6.3 MATERIALS AND METHODS

### 6.3.1 MATERIALS

In this study, we used H13 samples with the dimensions of 26 mm × 45 mm × 12.5 mm, as shown in Figure 6.1. The chemical composition of the H13 steel is presented in Table 6.2. We conducted the WEDM at ACUTEX using the dielectric liquid and copper wire with a diameter of 0.2 mm. Following the Taguchi method, we made nine samples with different $T_{on}$ and $T_{off}$ the on-delay and off-delay times of the discharge process, and we selected them as experimental parameters to follow the possible range of the ACUTEX DS-430S DM machine and avoid broken wires. We measured

![](img/62c36bee0e5ae6b397770e7de372b0e7_129_0)

FIGURE 6.1 H13 sample for the WEDM process (in mm).

TABLE 6.1
Properties of H13 Tool Steel
| Properties | Value |
|---|---|
| Density (kg/m²) | 7900 |
| Hardness, Brinell (typical) | 290–370 |
| Ultimate Tensile Strength (MPa) | 1200–1590 |
| Elastic modulus (GPa) | 215 |
| Thermal conductivity (W/mmK) | 28.8 |
| Thermal expansion (°C-1) | $3.5 \times 10^{-6}$ at 20–25 °C |

TABLE 6.2
Chemical Composition of the H13 Tool Steel

| Elements | C | Mn | Si | Cr | Mo | V | Fe |
|---|---|---|---|---|---|---|---|
| Percentage (%) | 0.32–0.45 | 0.2–0.6 | 0.8–1.25 | 4.75–5.5 | 1.10–1.75 | 1.0 | Balance |
