
## TABLE 17.2
RMS Values of Stabilization

| Reward Value Functions | N* | C_A | u_a | u_p |
|---|---|---|---|---|
| Parabolic | 0.1059 | 0.6120 | 0.0018 | 0.0220 |
| Polynomial | 0.1106 | 0.5558 | 0.0028 | 0.0202 |
| Barrier Lyapunov | 0.1220 | 0.6460 | 0.0044 | 0.0283 |
| Gaussian | 0.1612 | 0.6236 | 0.0074 | 0.0281 |
| Triangular | 0.1095 | 0.5555 | 0.0027 | 0.0202 |

![](img/a2fc2296b12812e9151e817bff1de16d_364_0.png)

## FIGURE 17.8 Mean return values of 500 experiments.

It is seen that the convergence of the triangular and parabolic reward-value functions-based reinforcement learning models is fast and more robust compared to the other reinforcement agents. The mean total return values of the treatments corresponding to the mean of the 500 episodes are shown in Figure 17.8. This means that each learning phase is performed by 500 episodes, then, after each learning phase, the results are recorded. The mean return values after 100 epochs are given in the table. To be a fair comparison, the results in the tables are obtained with the same random disturbances and random ineffective treatments.

## 17.6 CONCLUSIONS

Reinforcement models with novel reward functions were designed to stabilize the inflammatory response dynamics under specific conditions. Computational results based on the proposed treatment models provide a satisfactory level of stabilization performance for possible applications in future. Designed reward-value functions have resulted in different stabilization results that are important for specific patients’ conditions. In the future, actor-critic reinforcement models with deep neural network approximations can be designed for policy and value approximations to provide improved treatments for specific conditions of patients.

## REFERENCES LIST

- 1. Cherrault Y. Mathematical Modelling in Biomedicine: Optimal Control of Biomedical Systems (Vol. 23). Berlin: Springer Science and Business Media, 2012.
- 2. Kumar R, Gilles C, Yoram V, Carson CC. “The dynamics of acute inflammation”. Journal of Theoretical Biology, 230(2), 145–155, 2004.
- 3. Parker RS, Gilles C. “Systems engineering medicine: Engineering the inflammation response to infectious and traumatic challenges”. Journal of the Royal Society. Interface / The Royal Society, 7(48), 989–1013, 2010.
- 4. Day J, Jonathan R, Gilles C. “Using nonlinear model predictive control to find optimal therapeutic strategies to modulate inflammation”. Mathematical Biosciences and Engineering, 7(4), 739, 2010.
- 5. Huang Z, Shuang L, Li-li L, Jiao-yang C, Fen L, Wen-cheng Q, Da-ming S, Hans G. “Predicting the morbidity of chronic obstructive pulmonary disease based on multiple locally weighted linear regression model with k-Means clustering”. International Journal of Medical Informatics, 139, 104141, 2020.
- 6. Araujo DC, Adriano AV, Karina BGB, Maria GC. “Prognosing the risk of COVID-19 death through a machine learning-based routine blood panel: A retrospective study in Brazil”. International Journal of Medical Informatics, 165, 104835, 2022.
- 7. Day J, Chase C, Rami N, Ruben Z, Gary A, Yoram V. “Inflammation and disease: Modelling and modulation of the inflammatory response to alleviate critical illness”. Current Opinion in Systems Biology, 12, 22–29, 2018.
- 8. Reynolds A, Jonathan R, Gilles C, Judy D, Yoram V, Bard E. “A reduced mathematical model of the acute inflammatory response: I. derivation of model and analysis of anti-inflammation”. Journal of Theoretical Biology, 242(1), 220–236, 2006.
- 9. Bara O, Djouadi SM, Day J, Lenhart S. “Immune therapeutic strategies using optimal controls with L1 and L2 type objectives”. Mathematical Biosciences, 290, 9–21, 2017.
- 10. Ramirez-Zuniga I, Jonathan ER, David S, Gilles C. “Mathematical modeling of energy consumption in the acute inflammatory response”. Journal of Theoretical Biology, 460, 101–114, 2019.
- 11. Radosavljević V, Kosta R, Zoran O. “A data mining approach for optimization of acute inflammation therapy”. IEEE International Conference on Bioinformatics and Biomedicine, Philadelphia, October 4–7, 2012.
- 12. Rigatos G, Krishna B, Abbaszadeh M. “Nonlinear optimal control of the acute inflammatory response”. Biomedical Signal Processing and Control, 55, 101631, 2020.
- 13. Bara O, Day J, Djouadi SM. “Optimal control of an inflammatory immune response model”. 54th IEEE Conference on Decision and Control, Osaka, December 15–18, 2015.
- 14. Hogg JS, Gilles C, Robert SP. “Acute inflammation treatment via particle filter state estimation and mpc”. IFAC Proceedings Volumes, 43(5), 272–277, 2010.
- 15. Funk N, Dominik B, Vincent B, Sebastian T. “Learning event-triggered control from data through joint optimization”. *IFAC Journal of Systems and Control*, 16, 100144, 2021.
- 16. Sutton RS, Andrew GB. *Reinforcement Learning: An Introduction*. London: MIT Press, 1998.
- 17. Martín-Guerrero JD, Faustino G, Emilio SO, Jürgen S, Mónica CM, Víctor JT. “A reinforcement learning approach for individualizing erythropoietin dosages in hemodialysis patients”. *Expert Systems with Applications*, 36(6), 9737–9742, 2009.
- 18. Moore BL, Larry DP, Vivekanand K, Periklis P, Kevin P, Anthony GD. “Reinforcement learning for closed-loop propofol anesthesia: A study in human volunteers”. *The Journal of Machine Learning Research*, 15(1), 655–696, 2014.
- 19. Ngo PD, Susan W, Anna H, Jan M, Fred G. “Reinforcement learning optimal control for type-1 diabetes”. *IEEE EMBS International Conference on Biomedical & Health Informatics*, Las Vegas, Nevada, March 4–7, 2018.
- 20. Liu Z, Chenhui Y, Hang Y, Taihua W. “Deep reinforcement learning with its application for lung cancer detection in medical internet of things”. *Future Generation Computer Systems*, 97, 1–9, 2019.
- 21. Tejedor M, Ashenafi ZW, Fred G. “Reinforcement learning application in diabetes blood glucose control: A systematic review”. *Artificial Intelligence in Medicine*, 104, 101836, 2020.
- 22. Naeem M, Giovanni P, Antonio C. “A reinforcement learning and deep learning based intelligent system for the support of impaired patients in home treatment”. *Expert Systems with Applications*, 168, 114285, 2020.
- 23. Bara O, Michel F, Cédric J, Judy D, Seddik MD. “Toward a model-free feedback control synthesis for treating acute inflammation”. *Journal of Theoretical Biology*, 448, 26–37, 2018.
- 24. Watkins CJCH. “Learning from delayed rewards”. PhD thesis, King's College, Cambridge, 1989.
- 25. Hasselt HV. “Reinforcement learning in continuous state and action spaces”. In *Reinforcement Learning*, 207–51, Berlin, Heidelberg: Springer, 2012.
- 26. Konidaris G, Sarah O, Philip T. “Value function approximation in reinforcement learning using the Fourier basis”. *Twenty-Fifth AAAI Conference on Artificial Intelligence*, San Francisco, August 7–11, 2011.

## 18 Digital Histopathology
*Paving Future Directions Towards Predicting Diagnosis of Disease Via Image Analysis*

Rishita Singh, Nitu Dogra, Ravina Yadav, Angamba Meetei Potshangbam, Deepshikha Pande Katare, and Ruchi Jakhmola Mani

### 18.1 INTRODUCTION

Human health is a concept that has continued to be studied for decades to understand the impact or effect of disease at the cellular level and how it affects the body and its immunity. Nowadays, disease is a commonly used word and is referred to as the anomalous condition which negatively affects the structure or function of normal cells and eventually affects the entire organism. It manifests in the body at specific structural and functional levels and has a known cause which develops from genetic or environmental exposure. Depending on certain features, diseases are categorized as acute, in which the start of the disease is abrupt, for a short time span, or chronic, in which a patient may experience months or years of disease-related symptoms (Tizard and Musser, 2022).

Pathology is a fundamental medical discipline that mainly focuses on the visualization of diseased tissues and cells. It is the field that studies the causes and effects of a disease at a cellular level, which is essential for disease diagnosis. From the beginning, the examination of such pathological slides starts with sampling, i.e., collecting samples either during surgery or autopsy, after which the tissue is observed under a microscope. The introduction of digital scanning technologies in bioimaging has been evolving, as there has been a need for more computational methods to analyze a pathological slide, as the microscopic evaluation of cells is still the gold-standard method for classification, especially in tumour pathology. Automatic image analysis and decision making in histopathology is a challenging but promising area of research (Adiga and Chaudhuri, 2000; Meijering, Meijering, 2020). Pathology is now moving towards digitization, which makes computer-based image analysis
