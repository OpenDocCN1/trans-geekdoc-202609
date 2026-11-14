| Model | Property | All | Repulsion | Equilibrium | Weak attraction |
| :--- | :--- | :--- | :--- | :--- | :--- |
| MACE-MP | interaction energy | 0.315 | 0.805 | **0.090** | *0.063* |
| | force | 0.136 | 0.160 | 0.124 | 0.124 |
| MACE-MP-0b | interaction energy | 0.294 | 0.587 | 0.173 | 0.140 |
| | force | 0.119 | 0.127 | 0.116 | 0.115 |
| MACE-DAC-0 (fine-tuning) | interaction energy | *0.208* | **0.429** | 0.151 | 0.079 |
| | force | *0.114* | *0.123* | *0.110* | *0.109* |
| MACE-DAC-1 (continual learning) | interaction energy | **0.188** | *0.441* | *0.096* | **0.049** |
| | force | **0.098** | **0.109** | **0.093** | **0.093** |

MAE values for MACE-MP, MACE-MP-0b, MACE-DAC-0 (fine-tuning), and MACE-DAC-1 (continual learning) models are calculated with the GoldDAC test set, evaluated in terms of interaction energy and forces. The units of MAEs are provided as eV and eV/Å. The best-performing value is indicated in bold, and the second-best (runner-up) is indicated in italic.

model, demonstrating its practical advantages (Figures S3 and S4). The corresponding parity plots and MAE values for all four models are provided in Figures S2–S5 and Table S2, respectively.

As shown in Figure S5, the MACE-DAC-0 model shows lower MAE for the total energy of the system. Nonetheless, the MACE-DAC-0 model underperforms compared with the MACE-DAC-1 model in terms of interaction energy. Continual learning regularization effectively maintains the balance among different energy components during fine-tuning.

# High-throughput MOF screening

To facilitate the deployment of MLFFs for DAC applications, we have developed a Python package, DAC-SIM, to perform the necessary molecular simulations in a computationally efficient manner. Using this package, Widom insertion simulations were conducted to calculate the Q_st at zero loading and K_H for structures within the CoRE MOF database. During the simulations, the framework atoms were fixed.

Initially, 8,131 MOFs were selected for Widom insertion simulation, after excluding MOFs containing more than 250 atoms in their unit cells for computational efficiency during large-scale screening. Subsequently, geometry optimizations were carried out using MACE-DAC-1, where the details of geometry optimization are provided in the methods section. Following these optimizations, Q_st and K_H values were calculated by the Widom insertion simulations for 6,461 MOFs, after excluding MOFs encountering convergence issues and consistency problems (where the standard deviation from two repeated folds of averaged interaction energy calculations exceeded 0.05 eV, detailed analysis on statistical noise was provided in Note S2 and Figure S30).

Figure 3A shows the calculated Q_st values for CO_2 and H_2O, which are predominantly located between 20 and 40 kJ/mol. Previous studies suggest that MOFs with CO_2 Q_st exceeding 50 kJ/mol are regarded as promising for DAC application within physisorption mechanism.^{16,39} In line with this criterion, it is observed that 364 MOFs (5.63%) exhibit CO_2 Q_st values exceeding 50 kJ/mol, and 167 of them even surpass those for H_2O. Figure 3B presents the relationship between Q_st for CO_2 and the selectivity derived from the ratio of K_H for CO_2 to H_2O. Although K_H generally follows the trend of Q_st as shown in

Figure S6, given that selectivity is typically calculated using K_H rather than Q_st, this study uses the K_H ratio to define selectivity. Consequently, a total of 161 MOFs were identified as promising candidates for DAC application, characterized by CO_2 Q_st values of greater than 50 kJ/mol and demonstrating high selectivity for CO_2 over H_2O. While both Q_st and K_H have limitations in capturing the strong H_2O–H_2O interactions that become significant at high relative humidity, our analysis in Figure S8A shows that more than 67% of the candidate materials possess relatively small pores (largest cavity diameter [LCD] of <5.3 Å, approximately twice the kinetic diameter of a H_2O molecule). These confined pore sizes are likely to suppress the formation of water clusters, thereby making Q_st and K_H suitable as initial thermodynamic descriptors for screening candidates in DAC applications.

# Single interaction energy versus ensemble-averaged property

In contrast with the MC method that computes ensemble-averaged properties for gas adsorption, an alternative approach can use single configuration properties such as the lowest interaction energy at the most favorable binding site within a given MOF framework. This approach, used in the ODAC23,^{39} involved calculating the lowest interaction energy (adsorption energy in original paper) at the most favorable binding site within a given MOF framework using DFT. To identify the most stable adsorption site, it begins with generating potential sites through classical force fields or random selection, yielding multiple candidate configurations per structure. MOFs with fewer than four configurations were excluded in this work. Each configuration then undergoes geometry optimization via DFT to identify the most energetically favorable binding site.

Although this approach is effective for identifying the optimal interaction site, it may not represent the overall gas adsorption performance of MOFs. Indeed, the lowest CO_2 interaction energy of 2,794 MOFs derived from the ODAC23 database and the corresponding Q_st values for CO_2 calculated by DAC-SIM do not exhibit a strong correlation, as shown in the scatterplot in Figure 3C. The same trend was observed for the H_2O molecule in Figure S7.

The ensemble-averaged gas adsorption properties are influenced not only by chemical environment but also by various geometric features such as accessible pore diameter, void fraction,