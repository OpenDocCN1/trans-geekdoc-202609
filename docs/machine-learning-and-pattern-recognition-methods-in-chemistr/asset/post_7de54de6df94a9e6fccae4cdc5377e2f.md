
LeCun, Y.,er, B., Denker, J. S., Henderson, D., Howard, R. E., Hubbard, W., et al. (2019). Backpropagation applied to handwritten zip code recognition. *Neural Computation*, 1(4), 541–551.

Liu, Y., Deng, Y., Li, C., Cheng, J., Song, R., Wan, F., et al. (2020). Multi-channel EEG-based emotion recognition via a multi-level features capsule network. *Computers in Biology and Medicine*, 123, 103927.

Mitchell, T. (1997). Machine learning. McGraw Hill.

Mobiny, A., Lu, H., Nguyen, V. H., Roysam, B., & Varadarajan, N. (2019). Automated classification of apoptosis in phase contrast microscopy using capsule network. *IEEE Transactions on Medical Imaging*, 39(1), eaq7885.

Popova, M., Isayev, O., & Trophsa, A. (2018). Deep reinforcement learning for de novo drug design. *Science Advances*, 4(7), eaau7785.

Quinlan, J. R. (1986). Induction of decision trees. *Machine Learning*, 1(1), 81–110.

Rogers, D., & Hahn, M. (2010). Extended-connectivity fingerprints. *Journal of Chemical Information and Modeling*, 50(5), 742–754.

Sabour, S., Frost, N., & Hinton, G. E. (2017). Dynamic routing between capsules. *arXiv preprint arXiv:1710.09829.

Srivastava, N., Hinton, G., Keshavsky, A., Sutskever, I., & Salakhdinov, R. (2014). A simple method to prevent neural networks from overfitting. *Journal of Machine Learning Research*, 15(1), 1929–1958.

Szegedy, C., Liu, W., Jia, Y., Sermanet, P., Reed, S., Anguelov, D., et al. (2015). Going deeper with convolutions. In *IEEE Conference on Computer Vision and Pattern Recognition* (pp. 1–9).

Wang, H., Wang, J., Wang, J., Zhao, M., Zhang, W., Zhang, F., et al. (2018). Graphigan: Graph representation learning with generative adversarial nets. *AAAI Conference on Artificial Intelligence*, 32(1).

Yang, H., Chen, R., Li, D., & Wang, Z. (2021). Subtype-GAN: A deep learning approach for integrative cancer subtyping of multi-omics data. *Bioinformatics*, 37(16), 2231–2237.

Yang, C., Tarkhov, A., Marusczyk, J., Bienfait, B., Gasteiger, J., Kleinoeder, T., et al. (2015). New publicly available chemical language, CSRML, to support chemotype representations for data mining and modeling. *Journal of Chemical Information and Modeling*, 35(3), 510–528.

# CHAPTER 4

# Tuning the apparent thermodynamic parameters of chemical systems

Hamid Abdollahiᵃ, Somaieh Khodadadi Karimvandᵇ, and Somaye Vali Zadeᶜ

ᵃDepartment of Chemistry, Institute for Advanced Studies in Basic Sciences (IASBS), Zanjan, Iran
ᵇDepartment of Chemistry, Institute for Advanced Studies in Basic Sciences, Zanjan, Iran
ᶜHald Research Center of IRI, Food and Drug Administration, Ministry of Health and Medical Education, Tehran, Iran

# 1. Introduction

For many equilibrium systems, it is customary to use a simplified apparent, instead of a complete but rather complex, equilibrium system. The resulting apparent equilibrium constants are altered or controlled by changes of the chemical system, usually modifying the concentration of auxiliary agents, but the variation in other parameters such as the intensity of light in photo-controlled reactions, types and concentration of solvents or composition of mixed solvents, the ionic strength of the chemical media, etc. is also possible.

It is common to use the conditional formation constant, or the effective formation constant in interactions between metal ions and protons of synthetic chelating agents such as EDTA, EGTA, and with pH indicators. For example the following equilibrium exhaustively describe all interactions between metal ion Ca²+ with pH indicator Murexid (M) in aqueous solution (Ringbom, 1963) (Fig. 4.1).

The collection of 8 equilibrium constants (K₁, K₂, K₃, K₄, K₅, K₆, K₇, and K₈) together with the total concentrations for the three components quantitatively defines the species in any solution of the three components. For the most relevant applications, i.e., complexometric titrations, this complex equilibrium system is reduced to an apparent simple equilibrium under the condition of constant pH. Most titrations are conducted at a certain pH in buffered solutions.

Ca²+ + Mur ⇌ CaMur K' = [CaMur] / [Ca²⁺][Mur] (4.1)

Machine Learning and Pattern Recognition Methods in Chemistry from Multivariate and Data Driven Modeling
https://doi.org/10.1016/B978-0-323-90408-0.00008-3

Copyright 2023 Elsevier Inc.
All rights reserved.
73

**Fig. 4.1** The equilibrium reactions between Ca²⁺ ions and Murexid in aqueous solution.

K' is the conditional formation constant, which describes the action quantitatively as long as the pH is constant (Tammelin & Mogensen, 1952), and its value is pH dependent. In other words, there is a range of the apparent equilibrium constant, K', which can be tuned by adjusting the pH in a predefined value. However, the color of solution of indicator depends on two factors: the kind of metal ion and the pH of solution.

The concept of equilibrium reactions is extremely important in chemistry as many main applications of chemistry processes are based on the laws that govern the equilibrium reactions. In a typical equilibrium reaction, the amount of activities of involved components is determined by the relevant thermodynamic constant. As the activities of involved components in the equilibrium reaction are controlled by the thermodynamic parameters, tuning the relevant equilibrium constants can control the efficiency of the equilibria-based process like chemical sensing. The main goal of this chapter is to quantitatively investigate the effects of side equilibria in order to find the tunable range of the apparent or conditional constants of different chemical equilibrium systems.

# 2. General strategy for tuning the apparent constant (Karimvand, Maeder, and Abdollahi, 2019)

To further investigate the issues of using apparent equilibrium constants, quantitatively analyze a simpler equilibrium system.

A + B ⇌ C, Kc = [C] / [A][B]

Consider a situation where both the reactant and the product are involved in competitive equilibrium reactions with an interferent I, which is represented in Fig. 4.2.

![](img/1aed977a858463e62fc6af1793e4677c_83_0.png)

**Fig. 4.2** The basic equilibrium A+B=C. The basic equilibrium A+B=C, with two auxiliary equilibrium A+B=C, with two auxiliary equilibrium A and C. (Note: OCR for caption/description seems repetitive in source, preserved per instructions).

In addition to the initial equilibrium, there are now two additional interactions of A and C:

$K_{A,I} = \frac{[AI]}{[A][I]}$ (4.3)

$K_{C,I} = \frac{[CI]}{[C][I]}$ (4.4)

The apparent equilibrium and its constant $K'$ are defined as:

$K' = \frac{[C] + [CI]}{([A] + [AI])([B] + [I])}$ (4.5)

The hypothetical components $A'$ are defined as:

$[A'] = [A] + [AI]$ (4.6)

And:

$[C'] = [C] + [CI]$ (4.7)

Thus, in the presence of side reactions, the total concentrations of all components are defined by:

$K'_c = \frac{[C']}{[A'][B]}$ (4.8)
