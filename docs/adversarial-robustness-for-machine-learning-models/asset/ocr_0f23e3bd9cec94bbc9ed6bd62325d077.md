# Table 17.3 Cross-dataset performance of AdvCL (dark gray color), compared with supervised (white color) and self-supervised (light gray) baselines in AA, RA, SA on STL-10 with ResNet-18.

| Method | Fine-tuning | \multicolumn{3}{c}{CIFAR-10 → STL-10} | \multicolumn{3}{c}{CIFAR-100 → STL-10} |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | AA (%) | RA (%) | SA (%) | AA (%) | RA (%) | SA (%) |
| Supervised | SLF | 22.26 | 30.45 | 54.70 | 19.54 | 23.63 | **51.11** |
| RoCL (Kim et al., 2020) | | 18.65 | 28.18 | 54.56 | 12.39 | 21.93 | 47.86 |
| ACL (Jiang et al., 2020) | | 25.29 | 31.80 | 55.81 | **21.75** | 26.32 | 45.91 |
| AdvCL (Fan et al., 2021) | | **25.74** | **35.80** | **63.73** | 20.86 | **30.35** | 50.71 |
| Supervised | AFF | 33.10 | 36.7 | 62.78 | 29.18 | 32.43 | 55.85 |
| RoCL (Kim et al., 2020) | | 29.40 | 34.65 | 61.75 | 27.55 | 31.38 | 57.83 |
| ACL (Jiang et al., 2020) | | 32.50 | 35.93 | 62.65 | 28.68 | 32.41 | 57.16 |
| AdvCL (Fan et al., 2021) | | **34.70** | **37.78** | **63.52** | **30.51** | **33.70** | **61.56** |

# Table 17.4 Performance (RA and SA) of AdvCL (in dark gray color) and baseline approaches on CIFAR-10 under different linear finetuning strategies, SLF and adversarial linear finetuning (ALF).

| Method | \multicolumn{2}{c}{SLF} | \multicolumn{2}{c}{ALF} |
| :--- | :--- | :--- | :--- | :--- |
| | RA (%) | SA (%) | RA (%) | SA (%) |
| Supervised | 44.40 | 79.77 | 46.75 | 79.06 |
| RoCL (Kim et al., 2020) | 39.54 | 79.90 | 43.11 | 77.33 |
| ACL (Jiang et al., 2020) | 42.87 | 77.88 | 45.40 | 77.71 |
| AdvCL (Fan et al., 2021) | **50.45** | **80.85** | **52.01** | **79.39** |

Robustness transferability across datasets. In Table 17.3, we next evaluate the robustness transferability across different datasets, where \( A \rightarrow B \) denotes the transferability from pretraining on dataset \( A \) to finetuning on another dataset \( B (\neq A) \) of representations learned by AdvCL. Here the pretraining setup is consistent with Table 17.2. We observe that AdvCL yields better robustness and standard accuracy than almost all baseline approaches under both SLF and AFF finetuning settings. In the case of CIFAR-100 \( \rightarrow \) STL-10, although AdvCL yields 0.89% AA drop compared to ACL (Jiang et al., 2020), it yields a much better SA with 4.8% improvement.

Linear finetuning types. We also study the robustness difference when different linear finetuning strategies: Standard linear finetuning (SLF) and