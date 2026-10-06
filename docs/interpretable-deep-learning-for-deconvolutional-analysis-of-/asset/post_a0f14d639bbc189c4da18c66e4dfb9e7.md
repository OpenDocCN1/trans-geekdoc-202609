
# CellPress

# Neuron

deep-learning architectures, providing an efficient and scalable tool for single-trial neural data analysis. Research Foundation (NARSAD) Young Investigator grant no. 305 to S.M.; and the Harvard Brain Behavior Initiative to P.M.; This research was carried out in part thanks to the Canada Research Excellence Fund, awarded to P.M. through the Healthy Brains Lives Initiative at McGill University.

Our framework is flexible, requiring the selection of a few hyperparameters (e.g., sparsity regularizer, number of unrolling iterations, smoothing regularization, and number of kernels). We provide guidance for parameter selection. For example, the appropriate number of kernels can be determined by identifying and quantifying the cross-correlation between layers. Importantly the number of kernels and kernel time window must be specified—no additional parameterization is needed. Previous methods³ DUNL can learn any kernel (also see). When the amount of entries is known, DUNL's k-sparse operation with its unrolling architecture is robust to the choice of parameters.

# AUTHOR CONTRIBUTIONS

- Conceptualization, B.T., S.M., P.M., and D.B.
- methodology, B.T. and D.B.
- formal analysis, B.T. and S.M.
- visualization (in vivo experiments), S.M., H.W., and S.T.
- research, N.U., V.N., and D.B.
- data curation, B.T., S.M., H.W., and S.T.
- B.T., S.M., V.N., V.A., P.M., and D.B.
- project administration, P.M. and D.B.
- funding acquisition, S.M., N.U., V.A., P.M., and D.B..

With the k-sparse operation, j can be tuned using a variational set. For a detailed discussion on DUNL's limitations, see the supplementary material.

# DECLARATION OF INTEREST

The authors declare no competing of interests.

To demonstrate our model's versatility, we applied it to different experimental settings, highlighting functionalities in existing tools. Our framework can extend beyond the sparsity regime to provide interpretable representations. For more complex models, such as Kalman-based neural networks, or 2D filters with adaptive constants, our work makes a first step toward leveraging advantages in deep learning via convolutional dictionary learning to gain mechanistic insights into neural dynamics and their computations.

# DECLARATION OF AI AND AI-ASSISTED METHODS

During the preparation of this work, the authors did not use any technologies for reasoning or content generation. The authors take full responsibility for the content of the publication.

# STAR*

Detailed methods are provided in the online version of this paper and include the following:

- KEY RESOURCES TABLE
- METHOD DETAILS
- In vivo experiments
- Notation
- Data Distribution
- Generative Model
- Smooth Sparse Convolutional Learning
- Interpretable unrolled neural network (DUNL)
- Evaluation
- Interpretability in deep learning
- DUNL Limits
- D.U.N.L., Prior works for analysis of neural signals
- QUANTIFICATION AND STATISTICAL ANALYSIS
- Simulation details
- Experiment details
- Model comparison
- Model training details

# RESOURCE AVAILABILITY

# Lead contact

Requests for further information and resources should be directed to the lead contact, Dean Baamba (baamba@seas.harvard.edu).

# Materials available

No new reagents have been generated in this study.

# Data and Code Availability

- All code and model have been deposited in a GitHub repository: https://github.com/debaamba/dunl-model.
- Part of the data from this study has been deposited to a data repository at https://doi.org/10.1763/zenodo.39253
- Any additional information required to use the data is available from the lead contact upon request.

# ACKNOWLEDGMENTS

We thank the reviewers for their constructive feedback. We thank Ignacio Sanchez-Sánchez for conceptual and technical collaboration in the dopaminergic regions. We thank all the members of the Lab, Murthy, and others for helpful discussions, particularly Carlos Janevatin-Zadeh, Adam S. Lowell, and Henry S. Ford for help on the statistical analysis (https://doi.org/10.5291/zenodo.392953). We thank the funding agencies that supported this work: US UK DO, MOQ, and European Research Council (ERC) the ERCPIERC (Grant 11-WFF-1516-8) and Canadian Foundation Science Program (L10000/2018) to S.M.; the Brain and Behavior Foundation

# SUPPLEMENTAL INFORMATION

Supplemental information can be found at https://doi.org/10.1016/j.neuron.2022.05.006.

# REFERENCES

1. Jun, J.J., Sternnetz, N.A., Siegle, J.H., Derman, D.J., Bauza, M., Barbardt, L., Bee, K.A., Anastasiou, C.A., Andrews, Y., Adyn, C., et al. (2017). Fully integrated spike photometry for high-resolution recording of neural activity. Science 355, 222–236. https://doi.org/10.1126/science24636

2. Steinmetz, N., Koch, C., Haris, K., and Carandin, M. (2018). Population error models and large-scale experiences for neurosprobes. Curr. Opin. Neurobi., 50, 92–100. https://doi.org/10.1016/j.conneuro.2018.01.009.

3. Wong, O., Ohnason, H., Skayten, E., Eneqvist, E., H., Wang, L., Varge, J. R., Miller, M. and., and E. (22). Large two-neuron error models explain decision making in visual cortex. Cell, 185, 1236–1250. https://doi.org/10.1016/j.cell.2022.06.017.

4. Rigotti, M., Barak, A., Morgan, R., Wang, J., Davis, N. D., Miller, E. K., and Fuis, S. (2013). The impact of selectivity in complex coding strategies. Nature, 497, 595–600. https://doi.org/10.1038/nature12160.

5. Hiroiwaka, J., Hassawa, A., Mastet, P., Ott, T., and Kipp, A. (2019). Frontal cortex neural types encode single decision variables. Nature, 576, 473–478. https://doi.org/10.1038/s41586-019-1816-9.

6. Zhang, A., and Adams, A. M. (2023). The neural representation of free moving in both sensory and sensory task variables. Nature Communications, 14, 4153. https://doi.org/10.1038/s41467-023-39518-z.

7. Dubreil, A. L., Beiran, M., Mastet, P., Faustopoulos, G., and Ott, S. (2022). The role of population structure in computations through neural dynamics. Nat. Neurosci., 25, 77–83. https://doi.org/10.1038/s41593-022-01784-x.

8. Langdon, C., and Earl, S. H. (2015). Latent information from heterogeneous neural networks during decision tasks. Nature Neurosci, 18, 1055–1060. https://doi.org/10.1038/nns4003.

9. Kaufman, K. T., Miller, E. K., Right, M., Stefani, F., Shen, S., and Chang, A. (2012). The decoding of choice and intention from representational geometries. Curr. Opin. Neurobi., 22, 1024–1030. https://doi.org/10.1016/j.conneuro.2012.0604.

10. Lee, R. S., Saily, Y., England, G., Winter, L. B., and Day, N. D. (2024). A task-driven prediction error in dopaminergic neurons during decision making. Nat Neurosci., 20, 482–494. https://doi.org/10.1038/s41593-017-0060-w.

11. Lee, R. S., Saily, Y. Prediction error in dopaminergic neurons. Nat. Neurosci., 27, 1571–1578. https://doi.org/10.1038/s41593-014-0268-1.

12. Schwartz, S. (2016). Decoding-driven prediction error: a conceptual perspective. Nat. Neurosci, 19, 177–183. https://doi.org/10.1038/nn4315-5.

13. Matsumoto, S., Han, J., Uchida, N., and Wadato, M. (2006). Dopamine neurons reveal a significant signal in reward-based learning. Science, 294, 973–976. https://doi.org/10.1126/science.112933.

14. Williams, A. H., and Linderman, S. W. (2001). Statistical neuroscience in the single cell. Opin. Neurobi., 78, 203–215. https://doi.org/10.1016/j.conneuro.2001.0617.

15. Czerniak, G. E., Itzen, Y., Sinha, S., Muka, W. B., and Brown, E. R. (2008). Population activity models for decision making in high-dimensional neural space. J. Neurosci., 29, 2762–2769. https://doi.org/10.1523/jneuro1.

16. Miller, C. G., Dore, K., Huck, A., Leopold, D., Ska, M., Tursen, T., and Miles, J. (2002). Neural language of the brain. Cell, 32, 482–493. https://doi.org/10.1016/j.cell.2002.031.

17. Green, C., and Konrath, A. (2012). Calling in neurons. Nature Reviews Neuroscience, 13, 693–702. https://doi.org/10.1038/n4156-012-2.

18. Helmholtz, H. (1867). Handbook of German optics (v). The theory of perceptual errors. Phils. Soc. B, 364, 815–839. https://doi.org/10.1098/rspb.2006.0135.

19. Neiser, U. (1967). Cognitive psychology, attention cycles and memory. In nature and psychology of P. W. Shehan, ed. (Academic Press), pp. 95–961.

20. Martin, A. F., Qian, Q. L., Rocha, U., Ueda, N., and M, C. (2016). Deep principal analysis of neural population data. cell, 5, e11754. https://doi.org/10.1016/j.cell.2016.0754.

21. Xu, J. B., and Wei, X. J. (2008). Unsupervised decoding of cortical activity. Nat. Commun., 14, 769–778. https://doi.org/10.1038/nature07698.

22. Lee, D. D., and Shen, S. H. (1999). Using deconvolution methods for the analysis of objects by non-linear factors. Nature, 407, 799–804. https://doi.org/10.1038/348585.

23. Bu, M. V., Cunningham, J. A., Riley, S. L., Shen, Y., and Saharis, M. (2009). Population factor analysis for low-dimensional signal extraction from motor populations. J. Neurosci., 29, 615–634. https://doi.org/10.1523/J.NESCI.2008.0411.

24. Zhou, Y., and Park, M. I. (2017). Variational factor analysis for recovering low-dimensional dynamics from population spike trains. Neural, 30, 989–996.

25. Asi, M. C., Miller, V., and Plowfin, J. W. (2008). Prefrontal cortex stabilizes multidimensional encoding during decision-making. Nat. Neurosci., 23, 1410–1420. https://doi.org/10.1038/n4193-008-0496-2.

26. Czerniak, G. E., Itzen, Y., Sinha, S., Muka, W. B., and Brown, E. R. (2008). Population activity models for decision making in high-dimensional neural space. J. Neurosci., 29, 2762–2769. https://doi.org/10.1523/jneuro1.

27. Gomez-Mazo, A., Alan, J. P., Kemp, A. R., Costa, M., and Medina, Z. G. (2022). Developmental biology: ethology, and the foundations of neuroscience. Nat. Neurosci., 17, 1445–1452. https://doi.org/10.1038/nn3812.

28. Dennis, E. D., Hajhaj, A., Ahmed, C., Avero, D. L., Troberg, G. J., and Datta, S. S. (2021). Systems of neural behavior in

29. Smaragdos, P. (2000). Non-negative matrix factor extraction: decomposition of signals from overlapping sources. Component Analysis and Blind Signal Separation: International Conference, ICA 2004, Geneva, Spain, September 22–24, 2004.

30. Smaragdos, P. (2007). Convolutional Source Separation and their Application to Speech Separation. Audio Signal Process., 15, 1–12. https://doi.org/10.1016/j.aasp.2006.11.009.

31. Mackveus, E. L., Bach, H. A., Williams, A. H., Gu, S. G., Denarko, N., and Johnston, J. A. (2014). Decoding temporal sequences in high-dimensional dynamics: applications to neuroscience. Science e, 8(7), e1214847. https://doi.org/10.1126/science.1214847.

Neuron 1174, 15–1151, 1618, 2023
