TABLE XI: The performance of representative methods for UDA-RS$^\text{Seg}$ task. $mIoU$ (%) is adopted as metric. The model with the best performance is denoted in bold.

| Method | Source | Tasks on ISPRS dataset (w/ "Clutter") | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | P $\to$ V\textsection1 | V $\to$ P\textsection1 | P $\to$ V\textsection2 | V $\to$ P\textsection2 | | |
| CS-Lg [108] | TIGRS 2021 | 52.03 | 47.87 | 48.06 | 43.17 | | |
| IrgDA [118] | TIGRS 2021 | 54.10 | 50.14 | 52.20 | 40.80 | | |
| DNf [102] | TIGRS 2024 | 54.19 | 43.74 | 52.63 | 41.45 | | |
| STADA [45] | GRSL 2023 | 48.05 | 46.69 | | | | |
| MDMden [119] | TIGRS 2023 | 51.68 | 47.59 | 45.93 | 41.20 | | |
| FGUDA [109] | IJSTAR 2023 | 53.63 | 50.94 | 50.18 | 45.86 | | |
| Restaban [15] | RS 2023 | 55.83 | | 46.63 | | | |
| iJDAT [107] | TIGRS 2024 | 55.52 | 51.30 | 52.10 | 45.79 | | |
| CPC-A [116] | TIGRS 2024 | 60.75 | 50.72 | 47.67 | | | |
| ST-DaSegNet [46] | JAG 2024 | 64.33 | 59.65 | 58.16 | 56.86 | | |
| PFM-JOneT [51] | TIGRS 2024 | 66.86 | 61.21 | 56.61 | 57.60 | | |
| DAF [120] | TIGRS 2024 | 66.69 | 63.93 | 66.81 | **60.18** | | |
| MEB5 [114] | TIGRS 2024 | 72.28 | 67.06 | 69.77 | | | |

| Method | Source | Tasks on ISPRS dataset (w/o "Clutter") | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | P $\to$ V\textsection | V $\to$ P\textsection | P $\to$ V\textsection2 | V $\to$ P\textsection2 | | |
| MlDAan [112] | TIGRS 2022 | 62.25 | | 59.82 | 59.01 | | |
| MlEE-GAN [105] | TIGRS 2024 | 63.50 | | 53.31 | 48.32 | | |
| DEGLAN [110] | TIGRS 2024 | **68.09** | | **63.09** | **62.17** | | |

| Method | Source | Tasks on LoveDA dataset | | |
| :--- | :--- | :--- | :--- | :--- |
| | | U $\to$ R | R $\to$ U | |
| DCA [103] | TIGRS 2022 | 45.17 | | 46.36 | |
| iJDAT [107] | TIGRS 2022 | 47.31 | | 47.12 | |
| ST-DAsegNet [46] | JAG 2024 | **50.08** | | 50.28 | |
| DEGLan [110] | TIGRS 2024 | 38.58 | | **55.50** | |

benchmark datasets. ISPRS [8] and LoveDA [6] datasets. The results are summarized in Tab. XI.

ISPRS [8] is the most widely used benchmark dataset for the UDA-RS$^\text{Seg}$ task. It provides comprehensive coverage for DA tasks, with Potsdam offering large-scale multi-modal VHR images (IR-R-G and R-G-B) and Vaihingen contributing IR-R-G images. Existing methods generally follow two evaluation settings on this dataset: some methods consider all 6 categories including “Clutter” (w/ “Clutter”), while others adopt a 5-class setting that excludes it (w/o “Clutter”). The DA tasks on this dataset are listed as follows.

+   Adapt Potsdam IR-R-G to Vaihingen IR-R-G (P $\to$ V\textsection1).
Adapt Vaihingen IR-R-G to Potsdam IR-R-G (V $\to$ P\textsection1).
Adapt Potsdam R-G-B to Vaihingen IR-R-G (P $\to$ V\textsection2).
Adapt Vaihingen IR-R-G to Potsdam R-G-B (V $\to$ P\textsection2).

LoveDA [6] is another notable benchmark dataset for DA-RS$^\text{Seg}$ task. It supports two cross-domain tasks (listed as follows) and its test set is evaluated through an online server $^2$.

+   Adapt Urban to Rural (U $\to$ R).
Adapt Rural to Urban (R $\to$ U).

As shown in Tab. XI, the following observations can be made: (1) On the ISPRS dataset, MEB5 [114] achieves the best performance under the “w/ Clutter” setting, and DeGL-GAN [110] outperforms all other methods in the “w/o Clutter” configuration. In addition, DEGLAN shows strong results on the “R $\to$ U” task of the LoveDA dataset, while ST-DAsegNet [46] attains the best performance on the “U $\to$ R” task. (2) PFM-JOnet [51] does not reach state-of-the-art performance, highlighting that methods based on foundation

```
^2https://github.com/June-Je/Wang/LoveDA
```

TABLE XII: The performance of representative methods for UDA-RS$^\text{Det}$ task. $mAP_{50}$ (%) is adopted as the metric.

| Method | Source | Tasks on xView and DOTA datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | xView $\to$ DOTA-3 | | | | | | | | | | | |
| FADA [133] | TIGRS 2022 | | | | | | | | | | | 52.5 | |
| REST [141] | TIGRS 2024 | | | | | | | | | | | 65.3 | |
| ML-UDA [139] | IJSTAR 2024 | | | | | | | | | | | 66.2 | |
| CDTF [121] | TIGRS 2024 | | | | | | | | | | | 72.8 | |
| FiE-Net [143] | TIGRS 2025 | | | | | | | | | | | 55.1 | |

| Method | Source | Tasks on DIOR and DOTA datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | DIOR $\to$ DOTA-10 | | | | | | | | | | | |
| DeCLSA [138] | IJSTAR 2024 | | | | | | | | | | | 50.6 | |
| FiE-Net [143] | TIGRS 2025 | | | | | | | | | | | 57.3 | |

| Method | Source | Tasks on NWPU VHR-10 and DIOR datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | NWPU VHR-10 $\to$ DIOR | | | | | | | | | | | |
| RFA-Net [134] | TIGRS 2022 | | | | | | | | | | | 51.6 | |
| MGDAN [140] | RS 2025 | | | | | | | | | | | 55.1 | |

| Method | Source | Tasks on UCAS-AOD and CARPK datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | UCAS-AOD $\to$ CARPK | UCARP $\to$ UCAS-AOD | | | | | | | | | | |
| RST [141] | TIGRS 2024 | 76.2 | | | | | | | | | | 75.6 | |
| FiE-Net [143] | TIGRS 2025 | 79.4 | | | | | | | | | | 78.9 | |

| Method | Source | Tasks on UCAS-AOD and ISPRS Potsdam datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | UCAS-AOD $\to$ ISPRS Potsdam | | | | | | | | | | | |
| ML-UDA [139] | TIGRS 2024 | | | | | | | | | | | 91.8 | |
| CDTF [121] | TIGRS 2024 | | | | | | | | | | | 92.6 | |

| Method | Source | Tasks on HRISD and SSTD datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | HRISD $\to$ SSTD | | | | | | | | | | | |
| HiSNet [128] | TIGRS 2021 | | | | | | | | | | | 58.1 | |
| REST [141] | TIGRS 2024 | | | | | | | | | | | 58.5 | |
| FiE-Net [143] | TIGRS 2025 | | | | | | | | | | | 58.5 | |

| Method | Source | Tasks on LEVIR and SSTD datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | LEVIR $\to$ SSTD | | | | | | | | | | | |
| HiSNet [128] | TIGRS 2022 | | | | | | | | | | | 58.2 | |
| iDA [128] | TIGRS 2023 | | | | | | | | | | | 55.1 | |

models do not always surpass specialized models on specific downstream tasks. (3) Class-wise $IoU$ results in UDA-RS$^\text{Seg}$ task provide a more detailed view of model performance across different categories, which can be referred to original papers for further analysis. (4) It should be noted that the LoveDA leaderboard contains many methods, but not all of them are associated with published papers.

# Benchmark Performance on DA-RS$^\text{Det}$. In the DA-RS$^\text{Det}$ task, model performance is commonly evaluated using $AP_i/mAP$, $AR_i/mAR$, and $F_1/mF_1$-score. For each class $i$, the Average Precision ($AP_i$) is defined as the area under the precision-recall curve, while the Mean Average Precision ($mAP$) is the average of $AP_i$ across all classes. The Average Recall ($AR_i$) reflects the proportion of correctly detected objects, and $mAR$ is its mean across classes. The $F_1$-score is defined as $2 \times \frac{Precision \times Recall}{Precision + Recall}$, with $mF_1$-score denoting the mean across classes. In this survey, $mAP@50$ ($mAP_{50}$) is adopted as the primary evaluation metric, as it is used by most existing methods.

We select the datasets in Tab. VII to systematically report the performance of UDA-RS$^\text{Det}$ methods, with the detailed tasks listed as follows.

+   Adaptation between xView and DOTA (xView $\to$ DOTA-3).
Adaptation between DIOR and DOTA (DIOR $\to$ DOTA-10).
Adaptation between NWPU VHR-10 and DIOR (NWPU VHR-10 $\to$ DIOR).
Adaptation between UCAS-AOD and CARPK (UCAS-AOD $\to$ CARPK & CARPK $\to$ UCAS-AOD).
Adaptation between UCAS-AOD and ISPRS Potsdam (UCAS-AOD $\to$ ISPRS Potsdam).