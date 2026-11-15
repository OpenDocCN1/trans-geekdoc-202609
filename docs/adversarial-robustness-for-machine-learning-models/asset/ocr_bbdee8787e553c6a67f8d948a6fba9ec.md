Table 15.3 AUC values for TrojanNet detection and target label detection, given in the format (..). The detection index for each class is selected as quantile Q = 0.25, Q = 0.5, and Q = 0.75 of the similarity scores.

| | CIFAR-10 | GTSRB | R-ImgNet | Total |
|---|---|---|---|---|
| Q = 0.25 | (1, 1) | (0.99, 0.99) | (1, 1) | (1, 0.99) |
| Q = 0.5 | (1, 0.99) | (1, 1) | (1, 1) | (1, 0.99) |
| Q = 0.75 | (1, 0.98) | (1, 1) | (0.99, 0.97) | (0.99, 0.98) |

Table 15.4 Comparisons between DL-TND (Wang et al., 2020d) and NC (Wang et al., 2019b) on TrojanNets and cleanNets using T1 = 0.7. The results are reported in the format (number of correctly detected models)/(total number of models).

| | | DL-TND (clean) | DL-TND (Trojan) | NC (clean) | NC (Trojan) |
|---|---|---|---|---|---|
| CIFAR-10 | ResNet-50 | 20/20 | 20/20 | 11/20 | 13/20 |
| | VGG16 | 10/10 | 9/10 | 5/10 | 6/10 |
| | AlexNet | 10/10 | 10/10 | 6/10 | 7/10 |
| GTSRB | ResNet-50 | 12/12 | 12/12 | 10/12 | 6/12 |
| | VGG16 | 9/9 | 9/9 | 6/9 | 7/9 |
| | AlexNet | 9/9 | 8/9 | 5/9 | 5/9 |
| ImageNet | ResNet-50 | 5/5 | 5/5 | 4/5 | 1/5 |
| | VGG16 | 5/5 | 4/5 | 3/5 | 2/5 |
| | AlexNet | 4/5 | 5/5 | 4/5 | 1/5 |
| Total | | **84/85** | **82/85** | 54/85 | 48/85 |

Table 15.4 shows the comparisons of DL-TND to Neural Cleanse (NC) (Wang et al., 2019b) on TrojanNets and cleanNets (T1 = 0.7). The results for DF-TND can be found in (Wang et al., 2020d).

Finally, after detecting a trained model has backdoors, we can apply the model sanitization technique proposed by Zhao et al. (2020a), which uses limited clean dataset to mitigate the Trojan effects while maintaining high clean accuracy.

# 15.4 Extended reading

+   - Yang et al. (2020a) study how self-attention U-Net can enhance the characterization of adversarial audio examples.