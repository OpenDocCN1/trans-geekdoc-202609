![](bbox=[0.13, 0.12, 0.87, 0.43])

Figure 12. Comparison of the results of the DNN-based TM algorithm in different preprocessing methods: (a) radiance map; (b) ACC [21]; (c) AdaLogT.

![](bbox=[0.28, 0.52, 0.5, 0.71])

Figure 13. TMQI final score of the DNN-based TM algorithm in different preprocessing methods.

# 6. Conclusions

This paper proposed an adaptive logarithmic normalization transformation, AdaLogT, for TM algorithms in order to compensate for the defects caused by the preprocessing. Based on the analysis of classical preprocessing methods, the parameter *p* was introduced in order to obtain the appropriate log-normalized curve. The optimal parameter *p* was calculated by proposed objective functions. Considering the TM algorithms based on luminance or gradient domain, the objective functions based on luminance and gradient-domain features were constructed, respectively. Furthermore, a joint domain-aware objective function was presented for DNN-based TM algorithms. The proposed preprocessing algorithm ensures that the image luminance conforms to the HVS perception of the scene brightness. State-of-the-art luminance, gradient-domain, and DNN-based algorithms were selected for the experiments, which used different preprocessing methods. The experiments were conducted by combining subjective qualitative and objective quantitative. The results show