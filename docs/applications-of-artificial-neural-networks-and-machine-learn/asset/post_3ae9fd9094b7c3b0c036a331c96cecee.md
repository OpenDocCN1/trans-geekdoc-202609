

![](img/4048998719320644ee88964326fd7995_448_0.png)

(c)

![](img/4048998719320644ee88964326fd7995_448_1.png)

(d)

Fig. 21.8 (continued)

length and then, the increasing rate remarkably decreases with increasing $L_b$. Generally, in members externally bonded to concrete substrate, no matter how long the adhesion length may increase, bond strength could not absolutely reach to the tensile strength of FRP. However, the increase of bond length can lead to increase of the ductility in the fracture process [56] and this increase would continue up to an effective length. As shown, the ANFIS model didn't completely capture this physical concept unlike the ANN and KELM models.

In Fig. 21.8c, the variation of bond strength with both $E_p$ and $t_p$ as a function of axial rigidity of FRP reinforcement ($E_pt_p$) is shown. Clearly, it can be expected that the bond strength increases as the stiffness of FRP sheet increases. As shown, the KELM and ANFIS algorithms correctly capture this trend while this expected behavior is not correctly considered in the ANN model. Furthermore, the variation of bond strength predictions to variation of both bp and bc parameters as a function of FRP-to-concrete width ratio (bp/bc) is illustrated in Fig. 21.8d. It is clear that the bond strength predicted by KELM model increases with increasing the width ratio, as expected, but with a decreasing rate. As shown, the sensitivity of Pmax predicted by the developed KELM model with changing bp/bc are in line with maximum experimental datasets collected from literature. From these observations, it can be concluded that the developed KELM model is in a good agreement with the physical characteristics of debonding phenomenon and previous findings and also outperforms the ANN and ANFIS models in this aspect.

## 21.5.3 Sensitivity Analysis

To apply GT approach for determining the most effective parameters, ten scenarios were designed. In the first scenario, all input parameters were considered in GT analysis. In next step, the input variables are excluded one by one from dataset in the remaining scenarios and then a new well GT analysis is done. The result of GT analysis for each scenario is presented in Table 21.5. Four GT parameters including gamma, gradient, standard error, and Vratio are used to analysis the performance of each scenario. Excluding each parameter from analysis leads to change of GT parameters, which can be used to evaluate the importance of that excluded parameters. More changes in GT values indicate that the corresponding excluded parameter has more contribution in prediction of maximum bond strength. As stated, the Vratio can be varied between zero and 1. The value of Vratio close to zero indicates that there is a high degree of accuracy in prediction of bond strength. To more illustration, the values of different parameters of GT analysis are presented in Fig. 21.9. It can be seen from this figure that the Scenario 1 in which all input parameters was considered as effective parameters, has the minimum values of GT parameters. According to this table, excluding tp, Ep and L leads to a remarkable change in GT parameters; therefore, it can be concluded that these parameters are the most important parameters in prediction of maximum bond strength.

| Scenario number | Excluded parameter | Gammas | Gradient | Standard error | V-ratio |
|---|---|---|---|---|---|
| 1 | – | 0.029 | 0.049 | 0.007 | 0.117 |
| 2 | $E_a$ | 0.025 | 0.062 | 0.005 | 0.116 |
| 3 | $t_a$ | 0.029 | 0.051 | 0.008 | 0.1 |
| 4 | $b_c$ | 0.031 | 0.047 | 0.0065 | 0.117 |
| 5 | $t_c$ | 0.03 | 0.078 | 0.0064 | 0.125 |
| 6 | $f_c$ | 0.061 | 0.151 | 0.009 | 0.123 |
| 7 | $t_p$ | 0.031 | 0.099 | 0.0279 | 0.247 |
| 8 | $b_p$ | 0.035 | 0.096 | 0.0124 | 0.124 |
| 9 | $L$ | 0.039 | 0.039 | 0.0091 | 0.142 |

![](img/4048998719320644ee88964326fd7995_450_0.png)

**Fig. 21.9** Illustrations of Gamma indexes for different scenarios

## 21.6 Conclusions

In this chapter, an advanced soft computing approach namely kernel extreme learning machine (KELM) is used to estimate the bond strength between FRP sheets and concrete substrates. Furthermore, two other well-known soft computing approaches, ANN and ANFIS methods, are also employed to evaluate the robustness of the proposed KELM model. To develop models, a comprehensive database including 342 experimental tests is gathered from different sources in literature. Developed models are also compared with the most common existing design equations in aspect of accuracy and uncertainty. Different influential parameters such as the width of FRP plate, the elastic modulus of FRP, the thickness of FRP, the concrete cylinder compressive strength, the effective thickness of concrete contributing to shear deformation, the width of concrete prism, the bond length, the elastic modulus of adhesive, and the thickness of adhesive layer are considered in the developing process. To determine the most important parameters involved in the prediction of bond strength, the Gamma Test (GT) is applied. Furthermore, a parametric analysis is done to ensure that the results of developed models are in line with physical concepts of the debonding problem. The most important outcomes of this study can be summarized as follows:

- The proposed KELM model is able to well predict the bond strength for both training and testing sets in aspect of accuracy (i.e. the generalization capability of proposed model is remarkable). In the developed ANN and ANFIS models, this capability is significantly less than KELM model.
- The results of performance analysis indicate that the KELM model remarkably outperforms the ANN model and its prediction ability is slightly more accurate than ANFIS model.
- Among the most common design equations, the Neubauer and Rostásy model with R² of 0.75 and RMSE of 4.40 has the best performance. However, the proposed ELM model outperforms the Neubauer and Rostásy equation by improving R² value by 25.3% and RMSE value by 49.7%.
- The results of parametric analysis confirm that the developed KELM can properly capture the underlying physical trends between the influential parameters and the bond strength and its predictions are in agreement with experimental results. The KELM model outperforms the ANN and ANFIS models in this aspect.
- The results of Gamma test shown that the parameters incorporated in the axial stiffness of FRP sheet (i.e. the elastic modulus and the thickness of FRP) and bond length are the most important parameters in developing a predictive model for bond strength between FRP sheets and concrete substrates.

In total, the KELM model as alternative predictive approaches can be used successfully to estimate the bond strength between FRP sheets and concrete substrates and also can applied in other domain of structural engineering.

## References

- 1. A. Kaveh, S. M. Hamze-Ziabari and T. Bakhshpoori, Kernel Extreme Learning Machine Application in Prediction of Bond Strength Between EBR FRP and Concrete Substrate
- 2. Teng J, Chen JF, Smith ST, Lam L, Jessop T (2003) Behaviour and strength of FRP-strengthened RC structures: a state-of-the-art review. Proceedings of the Institution of Civil Engineers, Structures and Buildings 156 (1):51–62
- 3. Bakis CE, Bank LC, Brown V, Cosenza E, Davalos J, Lesko J, Machida A, Rizkalla S, Triantafillou T (2002) Fiber-reinforced polymer composites for construction—state-of-the-art review. J Compos Construct 6 (2):73–87
- 4. Chajes MJ, Finch WW, Januszka TF, Thomson TA (1996) Bond and force transfer of composite material plates bonded to concrete. ACI Struct J 93 (2):208–217
- 5. Maeda T, Asano Y, Sato Y, Ueda T, Kakuta Y A study on bond mechanism of carbon fiber sheet. In: Non-Metallic (FRP) Reinforcement for Concrete Structures, Proceedings of the Third Symposium, 1997. pp 279–286
- 6. Lu X, Ye L, Teng J, Jiang J (2005) Meso-scale finite element model for FRP sheets/plates bonded to concrete. Eng Struct 27 (4):564–575
- 7. Dai J, Ueda T, Sato Y (2006) Unified analytical approaches for determining shear bond characteristics of FRP-concrete interfaces through pullout tests. J Adv Concrete Technol 4 (1):133–145
- 8. Chen JF, Teng JG (2001) Anchorage strength models for FRP and steel plates bonded to concrete. J Struct Eng 127 (7):784–791

