Machine learning aided stochastic free vibration analysis of functionally graded porous plates 307

![](bbox=[0.222, 0.173, 0.777, 0.355])

**Figure 12.9** (A) Geometry of the functionally graded porous drone base. (B) Adopted finite element mesh condition for the structure.

# **Table 12.9** Variational input data of functionally graded porous drone base.

| Variational inputs | Distribution type | Mean | Standard deviation |
|---|---|---||}{
| $E_1$ (GPa) | Lognormal | 380 | 19 |
| $E_2$ (GPa) | Lognormal | 210 | 10.5 |
| $ho_1$ (kg/m³) | Normal | 7480 | 374 |
| $ho_2$ (kg/m³) | Bera | 3800 | 190 |
| | Lognormal | 0.3 | 0.015 |

Once again, to establish the appropriate regression model, the different training sizes are adopted for two machine learning algorithms and the mathematical measures of $R^2$ and RMSE are used to test the accuracy in Fig. 12.10. From the figures, the training sample sizes have been determined as 100 for X-SVR and 200 for GPR method for both Case A and Case B.

To illustrate the difference regressions of the GPR and X-SVR machine learning algorithms, a comparative test of two methods are provided for Case A and Case B. The first and third natural frequencies of the FGP base predicted from the two methods are presented in Tables 12.7 and 12.8. Meanwhile, the crude approach with 1 million simulation cycles are chosen as the reference result to validate.

From the tables, it is clear the MLS-SFV framework is competent to provide reliable results. Compared with the MCS results, the absolute maximum RE for GPR method is 0.552%, while RE is 0.0379% for the X-SVR method. Still, compared with the traditional MCS methods, both machine learning algorithms reduce a great amount of computational time but still deliver accurate natural frequencies for the FGP base structure.

Besides, the PDFs and CDFs for two natural frequencies in Case A and Case B by the two methods are plotted in Figs. 12.11–12.14, in comparison to the