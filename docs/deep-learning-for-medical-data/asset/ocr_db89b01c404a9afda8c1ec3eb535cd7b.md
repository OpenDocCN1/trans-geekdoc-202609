# 24 ROTATION EQUIVARIANT CNNS FOR DIGITAL PATHOLOGY

| Table 2.1: Performance on Network | K | #W | NLL | Acc | AUC |
|---|---|---|---|---|---||
| PCam, measured by negative log-likelihood, accuracy and AUC. Experiments | P4M-DenseNet | 64 | 119K | 0.260 | 89.8 | 96.3 |
| with data augmentation with 90° rotations and reflections are marked by + | P4M-DenseNet M | 24 | 19K | 0.273 | 89.3 | 95.8 |
| | P4M-DenseNet | 48 | 125K | 0.329 | 89.0 | 94.5 |
| | DenseNet+ | 24 | 128K | 0.306 | 88.1 | 95.1 |
| cats matching number of | DenseNet+ M | 64 | 902K | 0.365 | 87.2 | 94.6 |
| Z² maps, #W number of | DenseNet | 24 | 128K | 0.315 | 87.6 | 95.5 |
| maps per layer. | | | | | |

# 2.3.3 P4M-DenseNet Performance PatchCamleon

We assess the performance of our main contribution, the P4M-DenseNet architecture, on the PCam dataset. Table 2.1 reports the performance. P4M-DenseNet outperforms other models, closely followed by P4-DenseNet, indicating that both rotation and reflection are useful inductive biases, that cannot be learned by data augmentation alone. Keeping the number of Z² fixed in the baseline degrades performance further, demonstrating the sample-efficiency of the P4M model.

# Camleon16

We evaluate our patch-based model on the slide-level tumor localization task of the Camleon16 challenge. Fig. 2.4 reports the performance on the FROC score, to that of a pathologist (Ehtesami Bejnordi et al., 2017) and the state-of-the-art approaches on this dataset, including Liu et al., Wang et al., 2016. For the baseline DenseNet, the training data is augmented with 90° rotations and reflection. We experiment with multiple data regimes, where the number of WSIs in the training set is incrementally reduced by a factor of two.

The results indicate that the proposed method performs consistently better than all compared methods in terms of the FROC metric. Comparing to the baseline DenseNet results, we see that the superiority of our proposed architecture is predominantly due to the increased parameter sharing by the p4m