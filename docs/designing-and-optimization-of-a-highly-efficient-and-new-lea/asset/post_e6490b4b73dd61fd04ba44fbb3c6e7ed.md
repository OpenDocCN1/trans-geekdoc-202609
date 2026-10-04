
# D. Desai and S. Baghel
Inorganic Chemistry Communications 176 (2025) 114316

![](img/77993b86c321119fe49a62d1f762f7a1_6_0.png)

Fig. 8. Effect of Defect Density on (a) PCE and JSC (b) FF and Voc of Cs2RbGaGa4 DPSC.

![](img/77993b86c321119fe49a62d1f762f7a1_6_1.png)

Fig. 9. Effect of Absorber Thickness on (a) PCE and JSC (b) FF and Voc of Cs2RbGaGa4 DPSC.

model will predict the PCE of the same. For the was tested for the SCAPS optimized DPSC, features values i., Thickness of 600 nm, Defect density of 10⁴ cm⁻¹, and 300 K were inserted in the prompt when the code is run. The ML model predicted the PCE of 22.56 % which is very close to the simulated 22.17.

### 4. Conclusion

In this study we comprehensively studied and optimized Cs2RbGaIn-lead-free double perovskite solar cells (DPSCs), which is highly efficient material for solar cell applications. we calculated essential material properties for Cs2RbGaIn, such as the density and conduction bands, as well as carrier mobilities. Additional properties, including electron affinity, density, and absorber thickness, were simulated.

We also optimized the electron transport layer (ETL) and hole transport layer (HTL), finding that ZnO and CsBT have the best power conversion efficiency (PCE) and making the recommended layers. The impact of ETL and HTL thicknesses was analyzed using contour plots, and we found that a thicker HTL (100 nm) improves efficiency. We also studied the effect of electron affinity on devicement, identifying 4 eV as the optimal value. The impact of defect density on device performance was further analyzed, with results that the cell could achieve high efficiency at a relatively high defect of 10⁴ cm⁻¹, as chosen in the optimized value. The absorber layer thickness varied between 100 nm and 160 nm, and 600 nm were selected as the ideal thickness.

Fig. 10. Plot of PCE predicted by ML model with the actual PCE values obtained through simulation. ML model had a high R value of 0.9985.

Additionally, we developed a machine learning (ML) model capable of analyzing the various feature values and predicting the solar cell efficiency with these inputs. We trained the model with 1000 data points from simulations in SCAPS-1 using device operating temperature, layer thickness, and defect density, achieving an R² of 0.9985, indicating a high predictive accuracy. A SHAP summary plot was used to interpret the model, showing among the three features, temperature has the most significant impact on PCE. Additionally, defect density showed a complex relationship with PCE, indicating that its impact depends on the values of other features. Using a custom Python script, we obtained ML predicted PCE of 22.56 %, matching the 22.17% from simulations.

Once we developed and trained the ML model its importance that it can give the future values. To achieve this simple python script added to our code so that we input the features values ML model will predict the PCE of Cs2RbGaIn, based cell. 

![](img/77993b86c321119fe49a62d1f762f7a1_7_0.png)

Fig. 11. SHAP summary analysis of impact on feature value, defect density, thickness of layer, and roughness of layer.

This study explores the potential of perovskite-based solar cells through experiments, with the findings here are helpful for enhancing PCE durability. It highlights the value of ML in analyzing the impact of various factors on solar cell performance and emphasizes the importance of simulation-based methods for achieving accurate results in shorter time.

## Credit author contribution

Vishal Deswal: Writing — original draft, Visualization, Methodology, Investigation, Formal analysis. Data collection, Conceptualization. Sarita Baghel: Writing — editing & validation, Supervision, Resources, Project administration, Formal analysis.

## Declaration of competing interest

The authors declare that they have no known conflict of interest or personal relationships that could have influenced the work reported in this paper.

## Acknowledgment

The authors thank Professor Marc Burgelman (University of Germany) for providing SCAPS-1 data. Authors are thankful to Delhi Technological University, for funding for this research.

## Data availability

Data will be available on request.

## References

- [1] A. Kolima, T. Itura, Y. Shirai, T. Miyasaki, Organic Halide Perovskites for Photovoltaic Cells, Am Chem Sci 131 (2009) 19988–19989, https://doi.org/10.1021/acs8906922b
- [2] H. Snaith, Perovskites: The Emergence of a New Low-Cost, High-Efficiency Solar Cells, J Phys Lett 4 (2023) 3623–3630, https://doi.org/10.1016/j.jpls.2023.10517
- [3] N. G. Park, Organic Perovskite Light Absorbers towards a 20% Efficiency Solar Cells, Nature Energy 7 (2022) 892–900, https://doi.org/10.1038/s41560-022-0093-1
- [4] J. Kim, S. Lee, J. Lee, Y. Lee, H. Lee, S. Lee, J. Kim, and H. Kim, Analysis of the bandgap of hybrid organic-inorganic perovskites, Advanced Materials 34 (2022), 22031447, https://doi.org/10.1002/adma.2022031447
- [5] N. Ravivas, R. Ganasopadhyay, J. Takura, Stability and degradation of perovskite solar cells, Energy Env Sci 12 (2019) 221–228, https://doi.org/10.1039/C8EE00147-A00147
- [6] W. Walsh, Chemical Bonding and Bandgap Engineering in Organic-Inorganic Perovskites, J. Phys. Chem C 119 (2015) 5755–5760, https://doi.org/10.1021/acpc501333a
- [7] N. M. Vasiya, S. Rao, T. Zella, N. K Thakur, M. Mohammad, Stability of inorganic cell Cs2PbI6 (Ga, Ga) as a high efficiency harvesting device: an optoelectronic approach, Solar Energy 228 (2021) 1 https://doi.org/10.1016/j.solmat.2021.107699
- [8] A. Sora, S. Rao, T. Zella, N. K Thakur, M. Mohammad, Stability of inorganic cell Cs2PbI6 (Ga, Ga) as a high efficiency harvesting device: an optoelectronic approach, Solar Energy 228 (2021) 1 https://doi.org/10.1016/j.solmat.2021.107699
- [9] J. Sun, H. Wang, Y. Xu, and Y. Zhang, Machine learning for solar cell prediction and optimization, Communications 13 (2022) 1125, https://doi.org/10.1038/s42468-022-0121
- [10] Z. Liu, H. Wang, X. Yan, and Y. Wang, Machine learning for solar cell device design, Nature Communications 13 (2022) 11547, https://doi.org/10.1038/s41467-022-31955
- [11] J. L. Praadhan, S. Garg, and J. Thomas, Machine Learning-Based Approach for Developing High-Efficiency Perovskite Solar Cells, Advanced Energy 12 (2022) 21033
- [12] M. Kibib, H. Jahan, N. Khosravi, I. Elsayed, A. Almina, and R. Ahmed, Computational insights into the efficiency of perovskite cells, Nature Phys 24 (2023) 1297–1304, https://doi.org/10.1038/sphyschem.2023.2297
- M. Li, J. Liu, A. Alam, M. Rafman, and H. Bersiff, Investigation of Electrons and Hole Transport Layers on perovskite Solar Cells: A Numerical Investigation, Energy 243 (2022) 134210, https://doi.org/10.1016/j.energy.2022.134210
- Y. Raza, H. Elmoadi, M. Rahman, and S. Sakalli, Performance of Perovskite Solar Cells Based on Interface Engineering for selective charge, Solar Energy 123 (2019) 948–955, https://doi.org/10.1016/j.solener.2019.0432
- L. Huang, K. Sun, X. Xu, J. Yu, Y. Wu, J. Li, J. Hu, and J. Zhou, Stability of Perovskite Solar Cells under Materials 188 (2021) 10732, https://doi.org/10.1016/j.matopt.2021.10732
- E. Meng, T. Tang, R. Zhang, X. Wang, L. Li, Y. Yang, S. Chen, and J. Zhu, Optimization of organic-based perovskite solar cells, Opt Mater (Amer) (2022) 114527, https://doi.org/10.1016/j.optopt.2022.114527
- P. Savich, C.J. Zhou, S. Growicz, R. Vasiya, J. Jajkowski, M. Ister, and J. Bauer, Simulation of solar cells using, Mater Res 6 (2019) 08518, https://doi.org/10.1088/s40247-019
- H. Alipour, G. Adilmani, Optimization of lead-free perovskite solar cells in nanostructured devices: PSC for hole transport layer, Opt Mater (Amer) (2022) 114526, https://doi.org/10.1016/j.optopt.2022.114526
- K. Deepanshi Jayan, V. Sebastian, Modeling and comparative performance analysis of transport layers in perovskite cells, Energy 45 (2021) 2063–2070, doi:10.1016/j.energy.2021.0518
- Q. M. Wang, J. Li, S. Li, W. Wei, and K. Bahmann, Halide-Perovskite Photovoltaic Cell with Cs2AgBr6-CsPbBr6 Heterojunction, Mater. Chem 125 (2022) 21206–21218, https://doi.org/10.1021/acs.sncm.20569
- S. Zhang, J. Sun, A. Malik, and A. Ahmed, Advanced electrical simulation of double-perovskite solar cells with Mixed Halide Effect, Scientific Reports 13 (2023) 2996–3013, https://doi.org/10.1038/s41598-023
- Z. Zhang, J. Liu, L. Lin, Z. Zhou, J. Zhang, and Y. Hao, Potential Applications of Halide Double Perovskites Cs2AgX6 (X = Cl, Br) in Free Optronics, Scientific Reports 13 (2023) 1120–1125, https://doi.org/10.1038/s41598
- M. Burgetman, P. Nullet, and S. Grodziej, Modelling polycrystalline semiconductor solar cells, Solar Energy 202 (2000) 361–362 (527–532), https://doi.org/10.1016/S0022-1392X

# Inorganic Chemistry Communications 17 (2025) 114216

- A. Monjedi, N. Boussaira, S. Sakalli, and K. Bahmann, Stability of double perovskite Cs2AgBr6 for photovoltaics: Optical properties and stability, Energy 243 (2022) 134213, https://doi.org/10.1016/j.energy.2022.134213
- S. Wang, W. Wu, W. Li, S.-J. Yang, J. Zhang, and Y. Chen, Optimization of inverted-lead-free perovskite solar cells based on fast simulations, Green Energy 199 (2020) 75–82, https://doi.org/10.1016/j.conene.2020.04.014
- M. Monam, H. Shafi, S. T. Jan, J. Khan, M. Ismail, and A.J. Khanian, Optimization of organic-based perovskite solar cells by CAPS simulation, Mater. Sci. Eng. B (2023) 304012
- M. Cheng, T. Tang, R. Zhang, K. Li, L. Li, Y. Yang, S. Song, X. Chen, J. Zhu, and Y. Wang, Optimization of organic-based perovskite solar cells by CAPS simulation, Opt Mater (Amer) (2022) 114527.
