uses basic and rule-based intensity. Table 4 shows the NLL of two categories. The introduction of NFA universally improve model performance across datasets, with the sole exception of AKI. The standard metrics employed in AKI evaluation underrepresent clinically significant intermediate events. This limitation is compounded by NFA focus on global rule coverage rather than domain-specific critical pattern recognition. These findings validate the effectiveness of numerical intensity in medical event modeling.

# Table 4. Ablation study of NFA for NLL performance.

| Category | State | AKI | Stroke | Sepsis | CAD |
|---|---|---|---|---|---|
| Category I | w/o NFA | **7.41** | 15.26 | 12.83 | 6.30 |
| | with NFA | **7.41** | **15.24** | **12.73** | **5.96** |
| Category II | w/o NFA | **7.43** | 15.26 | 12.77 | 6.12 |
| | with NFA | **7.43** | **15.14** | **12.72** | **5.84** |

# 6 Conclusion

This paper proposes Hybrid-Rule Temporal Point Processes (HRTPP), a novel framework that integrates rule-based reasoning with numerical feature modeling. The proposed approach effectively incorporates domain expertise through temporal logic rules, while leveraging numerical feature encoder to capture complex event dependencies. By integrating a structured rule mining and optimization strategy, HRTPP refines the rule search process, ensuring both efficiency and robustness in modeling event sequences. Experimental results demonstrate that HRTPP achieves superior predictive accuracy and interpretability compared to baseline methods, making it a valuable tool for medical diagnosis. Future work will focus on adaptive rule learning mechanisms to improve flexibility and generalization.

**Acknowledgements.** This work is supported by National Natural Science Foundation of China (62406270), Shanghai Rising-Star Program (24YF2748800).

# References

+   1. Agrawal, R., Srikant, R.: Fast algorithms for mining association rules. In: Proceedings of the 20th International Conference on Very Large Data Bases, vol. 1215, pp. 487–499 (1994)
+   
+   2. Bruce, B.C.: A model for temporal references and its application in a question answering program. Artif. Intell. **3**, 1–25 (1972)
+   
+   3. Che, Z., Purushotham, S., Cho, K., Sontag, D., Liu, Y.: Recurrent neural networks for multivariate time series with missing values. Sci. Rep. **8**(1), 6085 (2018)