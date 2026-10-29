# Table 11

Clustering Performance in terms of ACC, RI, NMI of Categorical Datasets.

| Algorithms | Soybean Dataset ACC | RI | NMI | Mushroom Dataset ACC | RI | NMI | Dermatology Dataset ACC | RI | NMI |
|---|---|---|---|---|---|---|---|---|---|
| EKP | 0.536 | 0.435 | 0.138 | 0.553 | 0.432 | 0.025 | 0.682 | 0.595 | 0.102 |
| K-Prototype | 0.542 | 0.439 | 0.141 | 0.581 | 0.487 | 0.032 | 0.562 | 0.528 | 0.092 |
| KL-FCM-GM | 0.648 | 0.518 | 0.172 | 0.764 | 0.724 | 0.273 | 0.584 | 0.547 | 0.081 |
| Fuzzy K-Prototype | 0.712 | 0.577 | 0.203 | 0.841 | 0.770 | 0.518 | 0.838 | 0.819 | 0.652 |
| OCIL | 0.834 | 0.909 | 0.745 | 0.818 | 0.759 | 0.649 | 0.697 | 0.606 | 0.181 |
| KMC... | 0.838 | 0.749 | 0.438 | 0.807 | 0.773 | 0.578 | 0.822 | 0.812 | 0.617 |
| KHMCMD | 0.841 | 0.762 | 0.449 | 0.886 | 0.782 | 0.582 | 0.855 | 0.826 | 0.677 |
| Khan & Ahmad | 0.957 | 0.928 | 0.917 | 0.881 | 0.832 | 0.829 | 0.773 | 0.763 | 0.742 |
| Liang Bai et al. | 1.000 | 1.000 | 1.000 | 0.890 | 0.878 | 0.872 | 0.776 | 0.749 | 0.737 |
| FSCMMI | 1.000 | 1.000 | 1.000 | 0.920 | 0.918 | 0.910 | 0.862 | 0.851 | 0.838 |
| RP-FSCMMI | 1.000 | 1.000 | 1.000 | 0.931 | 0.923 | 0.919 | 0.869 | 0.860 | 0.852 |
| IA-FSCMMI | 1.000 | 1.000 | 1.000 | 0.954 | 0.949 | 0.924 | 0.884 | 0.881 | 0.871 |

| Algorithms | Breast-Cancer Dataset ACC | RI | NMI | Lung-Cancer Dataset ACC | RI | NMI | Zoo Dataset ACC | RI | NMI |
|---|---|---|---|---|---|---|---|---|---|
| EKP | 0.542 | 0.529 | 0.517 | 0.551 | 0.532 | 0.519 | 0.678 | 0.652 | 0.647 |
| K-Prototype | 0.548 | 0.531 | 0.522 | 0.574 | 0.529 | 0.523 | 0.565 | 0.554 | 0.549 |
| KL-FCM-GM | 0.653 | 0.628 | 0.610 | 0.749 | 0.720 | 0.716 | 0.589 | 0.578 | 0.563 |
| Fuzzy K-Prototype | 0.722 | 0.719 | 0.708 | 0.832 | 0.818 | 0.797 | 0.837 | 0.826 | 0.820 |
| OCIL | 0.829 | 0.812 | 0.802 | 0.812 | 0.798 | 0.782 | 0.859 | 0.852 | 0.835 |
| KMC... | 0.921 | 0.915 | 0.905 | 0.518 | 0.502 | 0.496 | 0.862 | 0.849 | 0.829 |
| KHMCMD | 0.963 | 0.947 | 0.938 | 0.611 | 0.597 | 0.581 | 0.869 | 0.851 | 0.844 |
| Khan & Ahmad | 0.912 | 0.896 | 0.870 | 0.500 | 0.487 | 0.472 | 0.891 | 0.875 | 0.852 |
| Liang Bai et al. | 0.939 | 0.925 | 0.911 | 0.687 | 0.671 | 0.667 | 0.920 | 0.902 | 0.899 |
| FSCMMI | 0.956 | 0.942 | 0.936 | 0.871 | 0.865 | 0.849 | 0.938 | 0.917 | 0.904 |
| RP-FSCMMI | 0.962 | 0.956 | 0.942 | 0.883 | 0.873 | 0.862 | 0.952 | 0.944 | 0.937 |
| IA-FSCMMI | 0.971 | 0.961 | 0.951 | 0.926 | 0.912 | 0.905 | 0.967 | 0.953 | 0.941 |

where DIV(I_p^{CF}, KA) = (1 - CLO(I_p^{CF}, KA)) represents the divergence among I_p^{CF} and KA. Subsequently, we need to compute the impact of the numerical feature of Imp(I_p^{NF}). Let I_up^{NF} = (I_{up,1}^{NF}, I_{up,2}^{NF}, ..., I_{up,F_n}^{NF})^T and I_lo^{NF} = (I_{lo,1}^{NF}, I_{lo,2}^{NF}, ..., I_{lo,F_n}^{NF})^T be the upper and lower limit values correspondingly. These values can be computed by, I_{up,q}^{NF} = max_{1 <= p <= M} (I_{p,q}^{NF}) and I_{lo,q}^{NF} = min_{1 <= p <= M} (I_{p,q}^{NF}) (56) where q = 1,2,...,F. Suppose ECM(I_{up,q}^{NF}, I_{lo,q}^{NF}) represents the Euclidean closeness measure between I_{up,q}^{NF} and I_{lo,q}^{NF}. The numerical features of I_p^{NF} and I_q^{NF} in χ, can be represented as, ECM(I_p^{NF}, I_q^{NF}) <= ECM(I_{up}^{NF}, I_{lo}^{NF}). (57) Moreover, the divergence between I_p^{NF} and the kernel argument KA can be determined as, DIV(I_p^{NF}, KA) = min_{1 <= q <= n} ECM(I_p^{NF}, β_q^{NF}) / ECM(I_{up}^{NF}, I_{lo}^{NF}) (58) where DIV(I_p^{NF}, KA) is defined by the minimum closeness measure among I_p^{NF} and the numerical kernel argument KA. The closeness measure between I_p^{NF} and the cluster center C^{NF} can be determined as CLO(I_p^{NF}, χ) = CLO(I_p^{NF}, C^{NF}) = 1 - DIV(I_p^{NF}, C^{NF}) (59)

CLO(I_p^{NF}, χ) = 1 - min_{1 <= q <= k} ECM(I_p^{NF}, C_q^{NF}) / ECM(I_{up}^{NF}, I_{lo}^{NF}). (60) Then, we have Imp(I_p^{NF}) = DIV(I_p^{NF}, KA) + CLO(I_p^{NF}, χ). (61) Imp(I_p^{NF}) = min_{1 <= q <= n} ECM(I_p^{NF}, β_q^{NF}) / ECM(I_{up}^{NF}, I_{lo}^{NF}) + (1 - min_{1 <= q <= k} ECM(I_p^{NF}, C_q^{NF}) / ECM(I_{up}^{NF}, I_{lo}^{NF})). (62) Finally, according to the impact of mixed data I_p to be chosen as a clustering kernel argument is computed by, Imp(I_p) = Imp(I_p^{CF}) + Imp(I_p^{NF}). (63) Imp(I_p) = (1 - 1/F_c sum_{q=1}^{F_c} CLO(I_{pq}^{CF}, KA)) + (1/F_c sum_{q=1}^{F_c} CLO(I_{pq}^{CF}, χ)) + min_{1 <= q <= n} ECM(I_p^{NF}, β_q^{NF}) / ECM(I_{up}^{NF}, I_{lo}^{NF}) + (1 - min_{1 <= q <= k} ECM(I_p^{NF}, C_q^{NF}) / ECM(I_{up}^{NF}, I_{lo}^{NF})). (64) More specifically, when choosing the initial kernel argument which is an empty group, the closeness among the I_p and χ should be evaluated. That is, the initial kernel argument β_1 is designated based on, β_1 = argmax_{I_p ∈ χ} [CLO(I_p^{CF}, χ) + CLO(I_p^{NF}, χ)] (65) Moreover, the process of the initialization adaptation approach for mixed features can be summarized in Table 7. The time complexity of the proposed method is better than existing algorithms. Subsequently, the proposed algorithm will not cost for extensive calculation.

# 7. Experiments

In this section, we evaluate the performance of our instance-cluster