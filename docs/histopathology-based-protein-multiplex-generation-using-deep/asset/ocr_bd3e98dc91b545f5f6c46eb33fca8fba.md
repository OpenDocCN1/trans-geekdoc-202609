# # Reporting Summary

Nature Portfolio wishes to improve the reproducibility of the work that we publish. This form provides structure for consistency and transparency in reporting. For further information on Nature Portfolio policies, see our Editorial Policies and the Editorial Policy Checklist.

# ## Statistics

For all statistical analyses, confirm that the following items are present in the figure legend, table legend, main text, or Methods section.

+   - [x] The exact sample size (n) for each experimental group/condition, given as a discrete number and unit of measurement
+   - [x] A statement on whether measurements were taken from distinct samples or whether the same sample was measured repeatedly
+   - [x] The statistical test(s) used AND whether they are one- or two-sided
+     *Only common tests should be described solely by name; describe more complex techniques in the Methods section.*
+   - [x] A description of all covariates tested
+   - [x] A description of any assumptions or corrections, such as tests of normality and adjustment for multiple comparisons
+   - [x] A full description of the statistical parameters including central tendency (e.g. means) or other basic estimates (e.g. regression coefficient) AND variation (e.g. standard deviation) or associated estimates of uncertainty (e.g. confidence intervals)
+   - [x] For null hypothesis testing, the test statistic (e.g. F, t, r) with confidence intervals, effect sizes, degrees of freedom and P value noted
+     *Give P values as exact values whenever suitable.*
+   - [x] For Bayesian analysis, information on the choice of priors and Markov chain Monte Carlo settings
+   - [x] For hierarchical and complex designs, identification of the appropriate level for tests and full reporting of outcomes
+   - [x] Estimates of effect sizes (e.g. Cohen's d, Pearson's r), indicating how they were calculated

*Our web collection on statistics for biologists contains articles on many of the points above.*

# ## Software and code

Policy information about availability of computer code

| Data collection | For qualitative evaluation of HistoPlexer on whole slide image level, we employed Ultivue InSituPlex technology to obtain multiplexed images using the Immuno8 and MDSC FixVue panels for 10 samples from the Tumor Profiler Study. The images were acquired at a resolution of 0.325 µm/pixel. |
| Data analysis | The data processing and model training was done on NVIDIA A100 40GB GPU. The deep learning models were trained using PyTorch (1.13.1) and the pipeline was implemented in Python (3.8.12).
The source code and trained models weights for HistoPlexer are available at https://github.com/ratschlab/HistoPlexer and via Zenodo at https://doi.org/10.5281/zenodo.15110117. |

For manuscripts utilizing custom algorithms or software that are central to the research but not yet described in published literature, software must be made available to editors and reviewers. We strongly encourage code deposition in a community repository (e.g. GitHub). See the Nature Portfolio guidelines for submitting code & software for further information.