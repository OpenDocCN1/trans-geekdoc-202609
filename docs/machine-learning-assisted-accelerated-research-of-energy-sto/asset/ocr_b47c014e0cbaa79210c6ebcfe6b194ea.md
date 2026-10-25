![](bbox=[0.21, 0.07, 0.78, 0.42])

Figure 2. Data histogram and kernel density estimation of (a) $W_{rec}$ (b) $\eta$, (c) log-scaled $W_{rec}$ ($W_{rec}'$), and (d) arcsine square root $\eta$ ($\eta'$).

are shown in Figure 2a,b. Most of the $W_{rec}$ values are located in the range of less than 2.0, and most of the $\eta$ values are located in the range of more than 0.8. To make the distribution of data close to normal distribution and improve the performance of the ML model, the data transformation was conducted on the target attribute. Various transformation methods were tested, and ultimately, it was found that applying the log-scaled transformation to $W_{rec}$ and arcsine square root transformation to $\eta$ yielded the best result. For convenience, in the following context, let $W_{rec}'$ represent the log-scaled value of $W_{rec}$ and $\eta'$ represent the arcsine square root value of $\eta$. The data distribution histograms and kernel density curves of $W_{rec}'$ and $\eta'$ are shown in Figures 2c and 2d, respectively. The data distribution in Figure 2c is close to a normal distribution, while the data distribution in Figure 2d does not exhibit a completely normal distribution. However, this is already a transformation result that we have selected as the closest to a normal distribution after trying various transformation methods. Given the obtained distributions, the regression models are expected to show high predictability.59

Typically, the data provided in the literature only include the better performance data, so the WebPlotDigitizer and Engauge Digitizer60,61 tools were utilized to extract additional data from the figures in the literature. Within this data set, there exist data with identical compositions but varying properties of identical materials, which can be attributed to the differences in calcination and sintering processes or applied electric fields. During the data collection phase, it is inevitable that there will be instances where the material composition is identical but the performance differs. If the performance differences are minor when the sintering processes are similar, then the data will be retained. However, if the performance differences are significant even with similar sintering process parameters, the data will be removed. Such data points are retained in the data set after careful examination to ensure that the deviation falls within a reasonable range. After data processing, a data set consisting of 227 BT-BMO samples are constructed for further regression learning and analysis.

**Feature Construction.** To construct a high-precision ML model and to conduct a comprehensive exploration of how composition, physical properties, and the sintering process influence the energy storage performances of BT-BMO, we have collected data on material

element information ($C_i$), characterization properties ($L_i$), and experimental parameters related to calcination and sintering processes ($P_i$).

The element information features are derived from easily accessible elemental information. Based on domain knowledge of relaxor ferroelectrics, 20 descriptors are selected to represent the properties of A-site and B-site elements, covering the atomic mass, atomic radius, electronegativity, and other descriptors (detailed information in the Supporting Information). In order to accurately describe each component, we represent the weighted ratio of A-site and B-site information as features and define the material descriptors as follows:32

```
$$X_{A/B} = \frac{X_A}{X_B} = \frac{\sum_{i \in A} f_i^X X_i}{\sum_{i \in B} f_i^X X_i}$$
```

where $f_i$ is the mole fraction of the element in the chemical composition and X is the property of an element. By calculating the ratio of A- and B-site information using eq 1, 16 material descriptors were obtained, as shown in the first 16 rows in the Supporting Information, Table S1. In addition, the electronegativity (EN), first ionization energy (IE), electron affinity (EA), and pseudopotential core radius (PR) are mainly used to compare the difference between cations and anions; we defined the material descriptors X by eq 2:32

```
$$X = ([X_A - X_O] + |X_B - X_O|)/2$$
```

where $X_O$ represents information on oxygen. In addition, the tolerance factor ($t$) and octahedral factor ($\mu$) reflecting the stability of perovskite structures are added. Since every BT-BMO compound is a solid solution, weighted fractions to proportions of BT and BMO in the solid solution are used to calculate the features representing the whole composite, defined by eq 3:

```
$$X_{solid solution} = (1 - x)X_{BT} + xX_{BMO}$$
```

Since the database contains data for the same component under different electric fields, the electric field ($E$) must also be an indispensable feature. Therefore, 22 features obtained through eqs 1–3, along with the $E$, constitute the feature pool for strategy I ($C_i$).