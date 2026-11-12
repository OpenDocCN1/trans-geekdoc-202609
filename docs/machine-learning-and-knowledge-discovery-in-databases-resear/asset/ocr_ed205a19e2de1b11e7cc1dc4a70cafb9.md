# Interpretable Hybrid-Rule Temporal Point Processes

Yunyang Cao, Juekai Lin, Hongye Wang, Wenhao Li<|unk|>, and Bo Jin<|unk|>

Tongji University, 200092 Shanghai, China

{whli,bjin}@tongji.edu.cn

**Abstract.** Temporal Point Processes (TPPs) are widely used for modeling event sequences in various medical domains, such as disease onset prediction, progression analysis, and clinical decision support. Although TPPs effectively capture temporal dynamics, their lack of interpretability remains a critical challenge. Recent advancements have introduced interpretable TPPs. However, these methods fail to incorporate numerical features, thereby limiting their ability to generate precise predictions. To address this issue, we propose Hybrid-Rule Temporal Point Processes (HRTPP), a novel framework that integrates temporal logic rules with numerical features, improving both interpretability and predictive accuracy in event modeling. HRTPP comprises three key components: basic intensity for intrinsic event likelihood, rule-based intensity for structured temporal dependencies, and numerical feature intensity for dynamic probability modulation. To effectively discover valid rules, we introduce a two-phase rule mining strategy with Bayesian optimization. To evaluate our method, we establish a multi-criteria assessment framework, incorporating rule validity, model fitting, and temporal predictive accuracy. Experimental results on real-world medical datasets demonstrate that HRTPP outperforms state-of-the-art interpretable TPPs in terms of predictive performance and clinical interpretability. In case studies, the rules extracted by HRTPP explain the disease progression, offering valuable contributions to medical diagnosis. The supplementary material is available at https://github.com/yy-c/HRTPP0.

**Keywords:** Temporal point processes · Interpretability · Event sequence modeling · Logic rules

# 1 Introduction

Event sequence data is prevalent in various domains, especially healthcare, including disease onset prediction [3, 21], progression analysis [6, 14], and clinical decision support [10, 20], where events occur asynchronously over time. Unlike traditional continuous-time series, which record values at regular intervals, event

J. Lin and H. Wang— Contributed equally to this work.

**Supplementary Information** The online version contains supplementary material available at https://doi.org/10.1007/978-3-032-06066-2_26.