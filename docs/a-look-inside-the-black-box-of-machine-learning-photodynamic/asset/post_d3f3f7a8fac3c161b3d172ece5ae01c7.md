
identifying mechanistic pathways with active learning in photochemical reactions. We combined Wigner sampling and geometrical interpolation to simplify training data generation. The method trains effective ML potentials to predict qualitatively correct PESs and detect undersampled structures near crossing regions. Moreover, we discussed data augmentation with atomic permutations that mitigate the permutational variance in the inverse distance matrix representation; it substantially accelerates active learning for photochemical reactions of high-symmetry molecules.

ML photodynamics enables highly efficient nanosecond NAMD simulations with the quality of CASSCF and XMS-CASPT2 for relatively large molecules. The training requires minimal prior knowledge of the intended photochemical reaction. The current limitations of ML photodynamics are unsatisfactory predictions of NACs and the energy gaps near the crossing regions. Current ML photodynamics simulations may employ NAC-free surface hopping methods such as the Zhu–Nakamura theory until a more suitable model for NAC predictions is developed. Overall, ML photodynamics simulations provide a valuable tool to study long-time-scale photochemical reactions. We expect this Account to contribute to a deeper understanding of the ML photodynamics approach and inspire future applications in simulating photochemistry in molecular solids and explicit solvation with further applications in chemical biology and materials chemistry, solid-state, explicit-solvent, and biological systems.

## ASSOCIATED CONTENT

### Supporting Information

The Supporting Information is available free of charge at https://pubs.acs.org/doi/10.1021/acs.accounts.2c00288.

- NN hyperparameters, training metrics, and data availability (PDF)

## AUTHOR INFORMATION

### Corresponding Author

**Steven A. Lopez** — *Department of Chemistry and Chemical Biology, Northeastern University, Boston, Massachusetts 02115, United States*; ◉ orcid.org/0000-0002-8418-3638; Email: s.lopez@northeastern.edu

### Author

**Jingbai Li** — *Department of Chemistry and Chemical Biology, Northeastern University, Boston, Massachusetts 02115, United States*

Complete contact information is available at: https://pubs.acs.org/10.1021/acs.accounts.2c00288

### Notes

The authors declare no competing financial interest.

### Biographies

**Jingbai Li** received his Ph.D. in 2019 from the Illinois Institute of Technology, working with Prof. Andrey Yu. Rogachev. He was a postdoctoral researcher at Northeastern University, working with Prof. Steven A. Lopez and developed PyRAI²MD in the Lopez group. He is an associate professor in the Hoffmann Institute of Advanced Materials at Shenzhen Polytechnic. His research is focused on development of ML-photodynamics approaches for studying photochemical reactions in complex environments.

**Steven A. Lopez** earned his Ph.D. in 2015 from the University of California, Los Angeles, working with Prof. Kendall N. Houk. He was a DOE Energy Efficiency and Renewable Energy Postdoctoral Fellow at Harvard University, working with Prof. Alán Aspuru-Guzik. He is an assistant professor in the Chemistry & Chemical Biology Department at Northeastern University. His group is focused on understanding light-driven processes in organic molecules and soft materials using state-of-the-art QC methods and ML techniques.

## ACKNOWLEDGMENTS

J.L. and S.A.L. acknowledge the Office of Naval Research (N00014-18-1-2659) National Science Foundation (CAREER Grant NSF-CHE-2144556), and the National Science Foundation (NSF-OAC-2118201) for funding this research. J.L. and S.A.L. appreciate the assistance from the Northeastern Research Computing Team and the computing resources provided by the Massachusetts Life Science Center (Grant G00006360).

## REFERENCES

- 1. Li, J.; Reiser, P.; Boswell, B. R.; Eberhard, A.; Burns, N. Z.; Friederich, P.; Lopez, S. A. Automatic discovery of photoisomerization mechanisms with nanosecond machine learning photodynamics simulations. *Chem. Sci.* **2021**, *12* (14), 5302–5314.
- 2. Li, J.; Stein, R.; Adrion, D. M.; Lopez, S. A. Machine-Learning Photodynamics Simulations Uncover the Role of Substituent Effects on the Photochemical Formation of Cubanes. *J. Am. Chem. Soc.* **2021**, *143* (48), 20166–20175.
- 3. Li, J.; Lopez, S. A. Excited-State Distortions Promote the Photochemical 4π-Electrocyclizations of Fluorobenzenes via Machine Learning Accelerated Photodynamics Simulations. *Chem. - Eur. J.* **2022**, DOI: 10.1002/chem.202200651.
- 4. *Solar-to-Chemical Conversion: Photocatalytic and Photoelectrochemical Processes*; Sun, H., Ed.; Wiley, 2021.
- 5. de Meijere, A.; Redlich, S.; Frank, D.; Magull, J.; Hofmeister, A.; Menzel, H.; Konig, B.; Svoboda, J. Octacyclopropylcubane and some of its isomers. *Angew. Chem., Int. Ed. Engl.* **2007**, *46* (24), 4574–6.
- 6. Xie, J.; Zhang, X.; Shi, C.; Pan, L.; Hou, F.; Nie, G.; Xie, J.; Liu, Q.; Zou, J.-J. Self-photensitized [2 + 2] cycloaddition for synthesis of high-energy-density fuels. *Sustainable Energy & Fuels* **2020**, *4* (2), 911–920.
- 7. Dong, L.; Feng, Y.; Wang, L.; Feng, W. Azobenzene-based solar thermal fuels: design, properties, and applications. *Chem. Soc. Rev.* **2018**, *47* (19), 7339–7368.
- 8. Orrego-Hernandez, J.; Dreos, A.; Moth-Poulsen, K. Engineering of Norbornadiene/Quadricyclane Photoswitches for Molecular Solar Thermal Energy Storage Applications. *Acc. Chem. Res.* **2020**, *53* (8), 1478–1487.
- 9. Merritt, I. C. D.; Jacquemin, D.; Vacher, M. Attachment: Is Controlling Electrons the Future of Photochemistry? *J. Phys. Chem. Lett.* **2021**, *12* (34), 8404–8415.
- 10. Westermayr, J.; Gastegger, M.; Menger, M.; Mai, S.; Gonzalez, L.; Marquetand, P. Machine learning enables long time scale molecular photodynamics simulations. *Chem. Sci.* **2019**, *10* (35), 8100–8107.
- 11. Westermayr, J.; Marquetand, P. Deep learning for UV absorption spectra with SchNarc: First steps toward transferability in chemical compound space. *J. Chem. Phys.* **2020**, *153* (15), 154112.
- 12. Westermayr, J.; Marquetand, P. Machine Learning for Electronically Excited States of Molecules. *Chem. Rev.* **2021**, *121* (16), 9873–9926.
- 13. Westermayr, J.; Maurer, R. J. Physically inspired deep learning of molecular excitations and photoemission spectra. *Chem. Sci.* **2021**, *12* (32), 10755–10764.
- 14. Pronobis, W.; Schütt, K. T.; Tkatchenko, A.; Müller, K.-R. Capturing intensive and extensive DFT/TDDFT molecular properties with machine learning. *Eur. Phys. J. B* **2018**, *91* (8), No. 178.

(15) Ramakrishnan, R.; Hartmann, M.; Tapavicza, E.; von Lilienfeld, O. A. Electronic spectra from TDDFT and machine learning in chemical space. *J. Chem. Phys.* **2015, 143** (8), No. 084111.

(16) Nandy, A.; Duan, C.; Taylor, M. G.; Liu, F.; Steeves, A. H.; Kulik, H. J. Computational Discovery of Transition-metal Complexes: From High-throughput Screening to Machine Learning. *Chem. Rev.* **2021, 121** (16), 9927–10000.

(17) Friedrich, J.; Hase, F.; Proppe, J.; Aspuru-Guzik, A. Machine-learned potentials for next-generation matter simulations. *Nat. Mater.* **2021, 20** (6), 750–761.

(18) Lewis-Atzwell, T.; Townsend, P. A.; Grayson, M. N. Machine learning activation energies of chemical reactions. *Wiley Interdiscip. Rev.: Comput. Mol. Sci.* **2021**, DOI: 10.1002/wcms.1593.

(19) Peterson, A. A. Acceleration of saddle-point searches with machine learning. *J. Chem. Phys.* **2016, 145** (7), No. 074106.

(20) Pozun, Z. D.; Hansen, K.; Sheppard, D.; Rupp, M.; Muller, K. R.; Henkelman, G. Optimizing transition states via kernel-based machine learning. *J. Chem. Phys.* **2012, 136** (17), 174101.

(21) Hermann, J.; Schätzle, Z.; Noe, F. Deep-neural-network solution of the electronic Schrödinger equation. *Nat. Chem.* **2020, 12** (10), 891–897.

(22) Han, J.; Zhang, L.; E, W. Solving many-electron Schrödinger equation using deep neural networks. *J. Comput. Phys.* **2019, 399,** No. 108929.

(23) Schutt, K. T.; Gastegger, M.; Tkatchenko, A.; Muller, K. R.; Maurer, R. J. Unifying machine learning and quantum chemistry with a deep neural network for molecular wavefunctions. *Nat. Commun.* **2019, 10** (1), 5024.

(24) Gastegger, M.; McSloy, A.; Luya, M.; Schutt, K. T.; Maurer, R. J. A deep neural network for molecular wave functions in quasi-atomic minimal basis representation. *J. Chem. Phys.* **2020, 153** (4), No. 044123.

(25) Zhou, Y.; Wu, J.; Chen, S.; Chen, G. Toward the Exact Exchange-Correlation Potential: A Three-Dimensional Convolutional Neural Network Construct. *J. Phys. Chem. Lett.* **2019, 10** (22), 7264–7269.

(26) Dick, S.; Fernandez-Serra, M. Machine learning accurate exchange and correlation functionals of the electronic density. *Nat. Commun.* **2020, 11** (1), 3509.

(27) Gastegger, M.; Behler, J.; Marquetand, P. Machine learning molecular dynamics for the simulation of infrared spectra. *Chem. Sci.* **2017, 8** (10), 6924–6935.

(28) Gao, P.; Zhang, J.; Peng, Q.; Zhang, J.; Glezakou, V. A. General Protocol for the Accurate Prediction of Molecular (13)C/(1)H NMR Chemical Shifts via Machine Learning Augmented DFT. *J. Chem. Inf. Model.* **2020, 60** (8), 3746–3754.

(29) Dral, P. O.; Barbatti, M. Molecular excited states through a machine learning lens. *Nat. Rev. Chem.* **2021, 5**, 388–405.

(30) Bonfanti, M.; Worth, G. A.; Burghardt, I. Multi-Configuration Time-Dependent Hartree Methods: From Quantum to Semiclassical and Quantum-Classical. In *Quantum Chemistry and Dynamics of Excited States: Methods and Applications*; González, L., Lindh, R., Eds.; Wiley, 2021; pp 383–411.

(31) Mai, S.; Marquetand, P.; González, L. Surface Hopping Molecular Dynamics. In *Quantum Chemistry and Dynamics of Excited States: Methods and Applications*; González, L., Lindh, R., Eds.; Wiley, 2021; pp 499–530.

(32) Dral, P. O.; Ge, F.; Xue, B. X.; Hou, Y. F.; Pinheiro, M., Jr.; Huang, J.; Barbatti, M. Meltom 2: An Integrative Platform for Atomistic Machine Learning. *Top Curr. Chem.* **2021, 379** (4), 27.

(33) Barbatti, M.; Ruckenbauer, M.; Plasser, F.; Pittner, J.; Granucci, G.; Persico, M.; Lischka, H. Newton-X: a surface-hopping program for nonadiabatic molecular dynamics. *Wiley Interdiscip. Rev. Comput. Mol. Sci.* **2014, 4** (1), 26–33.

(34) Westermayr, J.; Gastegger, M.; Marquetand, P. Combining SchNet and SHARC: The SchNarc Machine Learning Approach for Excited-State Dynamics. *J. Phys. Chem. Lett.* **2020, 11** (10), 3828–3834.

(35) Mai, S.; Marquetand, P.; Gonzalez, L. Nonadiabatic dynamics: The SHARC approach. *Wiley Interdiscip. Rev.: Comput. Mol. Sci.* **2018, 8** (6), e1370.

(36) Pinheiro, M. J., Jr.; Ge, F.; Ferre, N.; Dral, P. O.; Barbatti, M. Choosing the right molecular machine learning potential. *Chem. Sci.* **2021, 12** (43), 14396–14413.

(37) Huix-Rotllant, M.; Ferré, N.; Barbatti, M. Time-Dependent Density Functional Theory. In *Quantum Chemistry and Dynamics of Excited States: Methods and Applications*; González, L., Lindh, R., Eds.; Wiley, 2021; pp 13–46.

(38) Huix-Rotllant, M.; Nikiforov, A.; Thiel, W.; Filatov, M. Description of Conical Intersections with Density Functional Methods. *Top Curr. Chem.* **2015, 368**, 445–76.

(39) Levine, B. G.; Ko, C.; Quenneville, J.; Martínez, T. J. Conical intersections and double excitations in time-dependent density functional theory. *Mol. Phys.* **2006, 104** (5–7), 1039–1051.

(40) Vogtliatzis, K. D.; Ma, D.; Olsen, J.; Gagliardi, L.; de Jong, W. A. Pushing configuration-interaction to the limit: Towards massively parallel MCSCF calculations. *J. Chem. Phys.* **2017, 147** (18), 184111.

(41) Helmich-Paris, B. Benchmarks for Electronically Excited States with CASSCF Methods. *J. Chem. Theory Comput.* **2019, 15** (7), 4170–4179.

(42) Gomez, S.; Ibele, L. M.; Gonzalez, L. The 3s Rydberg state as a doorway state in the ultrafast dynamics of 1,1-difluoroethylene. *Phys. Chem. Chem. Phys.* **2019, 21** (9), 4871–4878.

(43) Roos, B. O.; Merchan, M.; McDiarmid, R.; Xing, X. Theoretical and Experimental Determination of the Electronic Spectrum of Norbornadiene. *J. Am. Chem. Soc.* **1994, 116** (13), 5927–5936.

(44) Kidwell, N. M.; Li, H.; Wang, X.; Bowman, J. M.; Lester, M. I. Unimolecular dissociation dynamics of vibrationally activated CH₃CHOOC Criegee intermediates to OH radical products. *Nat. Chem.* **2016, 8** (5), 509–14.

(45) Westermayr, J.; Gastegger, M.; Vörös, D.; Panzenboeck, L.; Joerg, F.; González, L.; Marquetand, P. Deep learning study of tyrosine reveals that roaming can lead to photodamage. *Nat. Chem.* **2022**, DOI: 10.1038/s41557-022-00950-z.

(46) Behler, J. Four Generations of High-Dimensional Neural Network Potentials. *Chem. Rev.* **2021, 121** (16), 10037–10072.

(47) Schutt, K. T.; Sauceda, H. E.; Kindermans, P. J.; Tkatchenko, A.; Muller, K. R. SchNet - A deep learning architecture for molecules and materials. *J. Chem. Phys.* **2018, 148** (24), 241722.

(48) Unke, O. T.; Meuwly, M. PhysNet: A Neural Network for Predicting Energies, Forces, Dipole Moments, and Partial Charges. *J. Chem. Theory Comput.* **2019, 15** (6), 3678–3693.

(49) Gao, X.; Ramezanghorbani, F.; Isayev, O.; Smith, J. S.; Roitberg, A. E. TorchANI: A Free and Open Source PyTorch-Based Deep Learning Implementation of the ANI Neural Network Potentials. *J. Chem. Inf. Model.* **2020, 60** (7), 3408–3415.

(50) Zhang, L.; Han, J.; Wang, H.; Saidi, W. A.; Car, R.; Weinan, E. End-to-end symmetry preserving inter-atomic potential energy model for finite and extended systems. In *Proceedings of the 32nd International Conference on Neural Information Processing Systems*; Curran Associates, 2018; pp 4441–4451.

(51) Chmiela, S.; Sauceda, H. E.; Muller, K. R.; Tkatchenko, A. Towards exact molecular dynamics simulations with machine-learned force fields. *Nat. Commun.* **2018, 9** (1), 3887.

(52) Koner, D.; Meuwly, M. Permutationally Invariant, Reproducing Kernel-Based Potential Energy Surfaces for Polyatomic Molecules: From Formaldehyde to Acetone. *J. Chem. Theory Comput.* **2020, 16** (9), 5474–5484.

(53) Bartok, A. P.; Payne, M. C.; Kondor, R.; Csanyi, G. Gaussian approximation potentials: the accuracy of quantum mechanics, without the electrons. *Phys. Rev. Lett.* **2010, 104** (13), 136403.

(54) Xie, Y.; Vandermause, J.; Sun, L.; Cepellotti, A.; Kozinsky, B. Bayesian force fields from active learning for simulation of inter-dimensional transformation of stanene. *npj Comput. Mater.* **2021, 7** (1), No. 40.

(55) Westermayr, J.; Faber, F. A.; Christensen, A. S.; von Lilienfeld, O. A.; Marquetand, P. Neural networks and kernel ridge regression for
