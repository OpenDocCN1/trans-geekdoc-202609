# Multi-Criteria Decision-Making with Machine Learning

![](bbox=[0.218, 0.093, 0.768, 0.396])

FIGURE 4.6 The tensile strength of the first validation sample.

# 4.4.5 Developing the Response Surface MODEL

The Taguchi method represents a potent and efficient tool capable of quantifying the relative importance of each individual factor as identifying enhanced parameter combinations to maximize the tensile strength of printed samples. However, the Taguchi method confines the optimized values to specific levels among the available options for each factor. Consequently, we used response surface methodology (RSM) to further optimize the tensile strength of the PLA samples. In this investigation, we constructed a first-order response model based on the experimental outcomes presented in Table 4-3. Employing the least-squares method, we calculated all model coefficients and arrived at the simplified model in Equation 4.3:

> $MaxStress = 12.574 + 1.192 \times A + 0.882 \times B + 4.712 \times C - 0.545 \times D + 0.046 \times E + 0.061 \times F + 0.130 \times G$

Within this model, we calculated that layer thickness has the most substantial influence, as indicated by its largest coefficient. The earlier findings derived from the S/N ratio analysis using the Taguchi method and the ANOVA. Notably, the first-order model underscores the greater importance of infill type than of printing density in maximizing tensile strength. This observation was reinforced by the relatively modest error margin ($R^2 = 0.984$) in the regression analysis, suggesting the potential for further model refinement, even though there is limited scope for improvement.

# 4.4.6 THE SECOND VALIDATION EXPERIMENT

In the pursuit of enhancing the RSM model, the subsequent phase of the analysis incorporated second-order terms for all factors. Notably, by the absence