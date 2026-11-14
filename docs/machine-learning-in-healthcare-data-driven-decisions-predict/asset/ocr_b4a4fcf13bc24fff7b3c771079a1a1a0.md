| Epoch | Training accuracy (%) | Validation accuracy (%) | Training loss | Validation loss | F1-score (%) | Time per epoch (s) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 81.3 | 78.9 | 0.623 | 0.701 | 77.6 | 18.2 |
| 2 | 87.4 | 84.1 | 0.482 | 0.568 | 83.9 | 17.8 |
| 3 | 91.5 | 88.7 | 0.351 | 0.421 | 88.5 | 17.9 |
| 4 | 94.2 | 92.4 | 0.262 | 0.318 | 92.3 | 18.1 |
| 5 | 96.1 | 94.6 | 0.187 | 0.226 | 94.5 | 18.0 |
| 6 | 97.4 | 96.2 | 0.135 | 0.173 | 96.0 | 17.7 |
| 7 | 98.2 | 97.0 | 0.102 | 0.138 | 96.9 | 18.3 |
| 8 | 98.5 | 98.0 | 0.087 | 0.111 | 97.8 | 17.6 |
| 9 | 98.7 | 98.4 | 0.073 | 0.098 | 98.3 | 17.5 |
| 10 | 98.9 | 98.7 | 0.062 | 0.084 | 98.5 | 17.9 |

| Iteration | Module configuration | Accuracy (%) | F1-score (%) | Precision (%) | Recall (%) | Feature map dim. (avg.) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| I1 | Baseline CNN (no fusion, no attention) | 91.3 | 91.0 | 90.6 | 90.5 | 64 × 64 × 128 |
| I2 | + Dual-branch CNN | 93.5 | 93.2 | 92.9 | 93.1 | 64 × 64 × 256 |
| I3 | + Hierarchical fusion blocks | 95.8 | 95.5 | 95.2 | 95.4 | 32 × 32 × 384 |
| I4 | + Cross-attention blocks (HCFEN full) | 98.7 | 98.5 | 98.2 | 98.2 | 32 × 32 × 512 |

which addresses imbalance issues commonly encountered in medical image datasets. With an F1-score of 98.5%, sensitivity of 98.2%, specificity of 99.0%, and overall accuracy of 98.7%, experimental testing on the Herlev dataset demonstrates HCFEN's effectiveness. These results confirm the reliability and efficacy of the proposed method and are a clear step forward from traditional baseline models. HCFEN is an effective method for computer-aided cervical cancer screening due to its high accuracy and interpretability, particularly in environments where there are limited experienced pathologists. This approach can enhance patient outcomes worldwide and continue early detection forward. For maximum real-world effect, future studies will explore multi-dataset validation, further optimization, and translation into clinical workflows.