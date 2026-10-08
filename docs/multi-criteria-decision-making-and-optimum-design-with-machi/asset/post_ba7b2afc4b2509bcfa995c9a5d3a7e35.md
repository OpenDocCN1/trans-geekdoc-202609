
## Multi-Criteria Decision-Making with Machine Learning

![](img/62c36bee0e5ae6b397770e7de372b0e7_152_0.png)

(a)

![](img/62c36bee0e5ae6b397770e7de372b0e7_152_1.png)

(b)

**FIGURE 8.2** 3D printing and testing machine: (a) FDM X500 printing machine and (b) Testing machine.

## TABLE 8.2
**3D Printing Parameters**

| Layer Height (mm) | Infill Percentage (%) | Nozzle Temperature (°C) | Heat Bed (°C) | Printing Speed (mm/s) | Outline Shells | Chamber Temperature (°C) |
| --- | --- | --- | --- | --- | --- | --- |
| 0.25 | 100 | 230 | 60 | 40 | 3 | 30 |
| 0.25 | 100 | 230 | 60 | 40 | 3 | 45 |
| 0.25 | 100 | 230 | 60 | 40 | 3 | 60 |

## 8.3 RESULTS AND DISCUSSION

The test result obtained from the stress–strain curve of each sample is shown in Figure 8.3, and the average flexural stress values are shown in Table 8.3. From there, we can compare and determine each printed sample's flexural strength at different chamber temperatures. The flexural stress or strength of a material is the maximum stress a material can withstand during flexural testing. The highest point of the stress curve in the stress–strain curve is the flexural strength achieved by the 3D sample printed at different chamber temperatures. Figure 8.4 graphically presents the average flexural stresses we calculated for the three different chamber temperatures.

Figure 8.4 shows that at the chamber temperature of 30 °C, the flexural stress was highest at 1.80 MPa, and it was lowest, 1.21 MPa, at 45 °C; at 60 °C, it increased to 1.37 MPa. The values in Table 8.3 show that the flexural stress we measured in the samples printed at 30 °C were stable and had the least deviation, and the figure shows that flexural strength correlates with chamber temperature. At high

![](img/62c36bee0e5ae6b397770e7de372b0e7_153_0.png)

**FIGURE 8.3** The stress-strain curve of each sample printed at different chamber temperatures.

## TABLE 8.3
Average Flexural Stresses of the Printed Samples

| No. | 30°C | 45°C | 60°C |
|---|---|---|--|
| Sample 1 | 1.61 | — | 1.19 |
| Sample 2 | 1.80 | 1.10 | — |
| Sample 3 | 1.91 | 1.20 | 1.50 |
| Sample 4 | 1.78 | 1.28 | 1.78 |
| Sample 5 | 1.89 | 1.27 | 1.02 |
| Average Flexural Stress (MPa) | 1.80 | 1.21 | 1.37 |
| Standard Deviation (MPa) | 0.12 | 0.08 | 0.34 |

## Multi-Criteria Decision-Making with Machine Learning

![](img/62c36bee0e5ae6b397770e7de372b0e7_154_0.png)

![](img/62c36bee0e5ae6b397770e7de372b0e7_154_1.png)

![](img/62c36bee0e5ae6b397770e7de372b0e7_154_2.png)

FIGURE 8.4 The influence of different chamber temperatures on flexural stress.

Chamber Temperature, Flexural Strength, & Thermoplastic PU 125

temperatures, the fracture strength of the TPU sample increased, indicating that high temperature is conductive to lower adhesion, which improved the mechanical properties of the printed samples (Lu et al., 2018).

However, flexural stress decreases as chamber temperature increases. Still, the tensile strength decreases at 45 °C, which means that tensile interlayer adhesion at high temperatures does not increase flexural strength. In contrast, it reduces the flexural strength. Abraham Hadeeyah also showed that tensile strength decreases the higher temperature (Hadeeyah et al., 2023). In short, the chamber temperature affects the flexural strength of 3D-printed samples.

## 8.4 POLYNOMIAL REGRESSION ANALYSIS

We used polynomial regression (Equation (8.1)) to determine the effects of chamber temperature method; Table 8.4 shows our regression results based on the flexural stress values shown in Table 8.3 at confidence interval (CI) = 95%. The regression equation is:

```
Flexural Stress = 5.205 – 0.1633 Chamber Temperature + 0.001657 Chamber Temperature^2 (8.1)
```

Analyzing the variance and regression between the obtained quantities gives the following results:

Correlation of determination: R² = 0.6675, P = 0.004 < 0.05

```
Flexural strength equation: y = 5.205 – 0.1633x + 0.001657x (8.2)
```

The Student's t regression coefficient for the chamber temperature and durability was not at r = -0.60: As chamber temperature increases, flexural stress decreased. Figure 8.5 shows that the optimal chamber temperature is 30 °C with a maximum flexural strength of ymax = 1.91 based on Table 8.3.

## 8.5 CONCLUSION

The study's results demonstrate a significant effect of chamber temperature on the mechanical properties of TPU using EDM technology: Flexural strength decreases as chamber temperature increases from 30 to 60 °C. The results show that to obtain the best flexural strength (1.80 MPa) of TPU material, the chamber temperature should be at 30 °C.

## 8.6 CONFLICTS OF INTEREST

The authors state that they have no known competing financial interests or personal relationships that appeared to influence the work reported in this article. One of the authors (Van-Thuc Nguyen) is a member of this book’s editorial board but was not involved in the editorial review or the decision to publish this article. The

## Multi-Criteria Decision-Making with Machine Learning

## TABLE 8.4
Polynomial Regression Findings for Flexural Stress versus Chamber Temperature

| S | R² | R²(adj) |
|---|---|---|
| | 0.204262 | 66.75% | 60.10% |

Analysis of Variance
| Source | DF | SS | MS | F | P |
|---|---|---|---|---|---|
| Regression | 2 | 0.83745 | 0.418723 | 10.04 | 0.004 |
| Error | 12 | 0.41723 | | |
| Total | 14 | 1.25468 | | |

| Sequential Analysis of Variance
| Source | DF | SS | MS | F | P |
|---|---|---|---|---|---|
| Linear | 1 | 0.454157 | | 6.24 | 0.030 |
| Quadratic | 1 | 0.383290 | | 9.19 |

![](img/62c36bee0e5ae6b397770e7de372b0e7_156_0.png)

FIGURE 8.5 The relationship between flexural stress and temperature: a) bar graph; b) line graph. authors state that the work has no potential conflict of interest. All authors have read and agreed to the published version of the manuscript.

## 8.7 QUESTIONS

- Which chamber temperature gives the maximum flexural strength?
- What printer did the authors of this study use?
- How chamber temperature levels were tested in this study?

## Chamber Temperature, Flexural Strength, & Thermoplastic PU

127

![](img/62c36bee0e5ae6b397770e7de372b0e7_157_0.png)

FIGURE 8.5 (Continued)

## 8.8 ACKNOWLEDGMENT

This works belongs to the project in 2024 funded by Ho Minh City of Technology grant number SV2024.

## REFERENCES

Abraham Hadeey, Amir Kassentini, Ibrahim Ali Farj Emhed, Fouzi Alhadhar, Mondher Wali, Naira Khabou Masoud (2023). The effect of ambient temperature on the quality of three-dimensional products in FDM technology for ABS material. https://www.researchgate.net/publication/37070

Adnan Rashid, Muhammad Hussain, Shafi Ullah, Hasan Kakahal, Asim Ahmed Riaz, Imran Khan, Sayed M Edlin, Ilyas Khan (2023). Experimental Investigation and Taguchi optimization of FDM process parameters for the enhancement of tensile properties of Bi-layered PLA-ABS. https://doi.org/10.1088/1552-1591/ac1f17

Azar Eqabal, Anumar Sood, Abdul Razaq Ansari, Md. Asif Equbal (2017). Optimization of process parameters for FDM part for minimizing dimensional inaccuracy. https://www.researchgate.net/publication/316077743

Budi Arianto, Benidikut Tulung Prayoga, Rimi Dharmastuti, Teguh Nur Imran (2021). Tensile properties of the FDM-processed Thermoplastic Polyurethane (TPU) elastomer. https://doi.org/10.21303/rs.3x-299979/v

Dragos Zaisopol, Mihail Munescu, Dragos Valentin Jacob (2023). A theoretical-experimental study on the influence of FDM parameters on the dimensions of cylindrical spur gears made by PLA. https://www.etasar.com/index.php/ARTICLE/view/573/305

Duong Le, Cha Ha Nguyen, Minh Tai Le, Thi Hong Nga Pham, Thanh Tan Nguyen, Son Minh Pham, Van Thuc Nguyen (2023). Optimization 3D printing process parameters
