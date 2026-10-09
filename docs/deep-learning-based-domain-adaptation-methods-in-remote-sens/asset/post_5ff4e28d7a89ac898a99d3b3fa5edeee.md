
## TABLE IX: The performance of representative methods on aerial and satellite optical datasets for UDA-RSCls task. “5/6/8-c” denotes that 5, 6, or 8 common categories are extracted from the selected datasets. OA is adopted as metric.

| Tasks | UDA-RSCls Methods on Aerial and Satellite Optical Image Datasets | | | | | | | |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| | | **5-c** | | **6-c** | | | **8-c** |
| | **DFEINET** [71] | **DATSNET** [95] | **MLDAN** [96] | **AMRAN** [97] | **SRETT** [98] | **DDCI** [99] | **ADA-ODA** [70] |
| | TGRS 2022 | TGRS 2021 | TGRS 2022 | TGRS 2022 | TGRS 2023 | TGRS 2025 | TGRS 2022 |
| **U→A** | - | 76.3 | 90.8 | 94.0 | 95.3 | 98.6 | 77.8 |
| **A→U** | - | 82.6 | 89.1 | 88.2 | 84.8 | 89.3 | 87.5 |
| **U→W** | - | 92.1 | 96.1 | 89.6 | 94.0 | 96.5 | - |
| **W→U** | - | 83.1 | 89.1 | 85.2 | 88.3 | 96.5 | - |
| **A→W** | - | 99.4 | 99.8 | 99.7 | 98.7 | 99.0 | - |
| **W→A** | - | 95.8 | - | 94.8 | 97.0 | 98.3 | - |
| **U→N** | - | - | - | - | - | - | 74.8 |
| **N→U** | - | - | - | - | - | - | 89.6 |
| **A→N** | - | - | - | - | - | - | 90.7 |
| **N→A** | - | - | - | - | - | - | 92.0 |
| **U→R** | 85.1 | 60.6 | 78.6 | 69.0 | 74.5 | 75.3 | - |
| **R→U** | 88.5 | 88.7 | 90.9 | 87.6 | 89.2 | 91.3 | - |
| **A→R** | 90.7 | 77.0 | 85.1 | 81.0 | 85.3 | 82.0 | - |
| **R→A** | 94.1 | 90.5 | 96.9 | 94.5 | 98.4 | 97.7 | - |
| **N→R** | 92.6 | - | - | - | - | - | - |
| **R→N** | 95.0 | - | - | - | - | - | - |
| **W→R** | - | 76.0 | 87.0 | 79.5 | 85.6 | 79.2 | - |
| **R→W** | - | 95.9 | 97.4 | 94.6 | 96.8 | 98.4 | - |

*Note: Based on the text description, "MRDAN" in the text likely corresponds to "MLDAN" [96] in the table, and "SRKT" likely corresponds to "SRETT" [98]. The table below preserves the reference numbers from the original OCR.*

## TABLE X: The performance of representative methods on SAR datasets for UDA-RSCls task. The model with the best performance is denoted in bold.

| Method | Source | Tasks | OA (%) |
| :--- | :--- | :---: | :---: |
| | | **THE SAMPLE Dataset** | |
| PEDA [75] | GRSL 2022 | S→M | 97.81 |
| VSFA [80] | TGRS 2023 | S→M | **98.18** |
| | | **The Hangzhou-Shanghai Dataset** | |
| TSIC [208] | GRSL 2022 | F→O / O→F | 71.4/74.2 |
| DST [86] | GRSL 2024 | F→O / O→F | **75.6/77.5** |

### Tasks Configuration
- Adaptation between AID and WHU-RS19
  - (A → W & W → A).
- Adaptation between AID and NWPU-RESISC45
  - (A → N & N → A).
- Adaptation between UC-Merced and RSSCN7
  - (U → R & R → U).
- Adaptation between AID and RSSCN7
  - (A → R & R → A).
- Adaptation between NWPU-RESISC45 and RSSCN7
  - (N → R & R → N).
- Adaptation between WHU-RS19 and RSSCN7
  - (W → R & R → W).

From the performance comparison in Tab. IX, we will analyze in the following points. (1) DATSNET [95], MLDAN [96], AMRAN [97], SRETT [98], DDCI [99] adopt similar task configurations and implementation details. Among them, DDCI [99] achieves the best overall performance. (2) In UDA-RSCls tasks, adversarial learning mechanisms are often employed for feature alignment, but they may be less economical for this setting. Since classification relies on global semantic features rather than fine-grained local details, adversarial training can introduce unnecessary complexity and instability. In contrast, more direct distribution measurement algorithms can provide a simpler and more stable way to reduce the domain gap while maintaining efficiency.

## Benchmark Performance on SAR datasets. Although research on UDA-RSCls with SAR datasets is relatively limited, we still summarize representative UDA-RSCls methods on the SAR benchmark datasets in Tab. X.

In the SAMPLE [234] dataset, the UDA-RSCls task is carried out between the synthetic and measured subsets, with the synthetic subset serving as the source and the measured subset as the target.
- Adapt synthetic to measured (S → M).
- The reverse setting (M → S) is not considered since it lacks practical relevance.

In the UDA SAR ship classification task, FUSAR-Ship [235] and OpenSARShip [236] are utilized. To ensure consistency, five shared classes are selected. The tasks are formulated by adapting across the two datasets.
- Adapt FUSAR-Ship to OpenSARShip (F → O).
- Adapt OpenSARShip to FUSAR-Ship (O → F).

As shown in Tab. X, PEDA [75], VSFA [80], TSIC [208] and DST [86] provide insights into the domain adaptation for SAR image classification. Among them, VSFA [80] and DST [86] achieve the best performance on their respective experimental settings.

### 2) Benchmark Performance on DA-RSseg. In DA-RSseg task, model performance is evaluated using IoU/mIoU and F1/mF-score. For class $i$, $IoU_i = tp_i/(tp_i + fp_i + fn_i)$, where $tp_i$, $fp_i$, and $fn_i$ denote true positive, false positive, and false negative, respectively. $mIoU$ is the average across all classes. The F1-score is defined as $2 \times Precision \times Recall/(Precision + Recall)$, and mF-score is its mean over all classes. To ensure fair and consistent comparison across methods, this survey primarily reports results using mIoU as the main evaluation metric.

As previously noted, most recent DA-RSseg methods focus on HR aerial and satellite optical images. In this survey, we systematically compare their performance on two notable benchmark datasets: ISPRS [8] and LoveDA [6]. The results are summarized in Tab. XI.

ISPRS [8] is the most widely used benchmark dataset for the UDA-RS$^\text{Seg}$ task. It provides comprehensive coverage for DA tasks, with Potsdam offering large-scale multi-modal VHR images (IR-R-G and R-G-B) and Vaihingen contributing IR-R-G images. Existing methods generally follow two evaluation settings on this dataset: some methods consider all 6 categories including “Clutter” (w/ “Clutter”), while others adopt a 5-class setting that excludes it (w/o “Clutter”). The DA tasks on this dataset are listed as follows.
- Adapt Potsdam IR-R-G to Vaihingen IR-R-G (P $\to$ V\textsection1).
- Adapt Vaihingen IR-R-G to Potsdam IR-R-G (V $\to$ P\textsection1).
- Adapt Potsdam R-G-B to Vaihingen IR-R-G (P $\to$ V\textsection2).
- Adapt Vaihingen IR-R-G to Potsdam R-G-B (V $\to$ P\textsection2).

LoveDA [6] is another notable benchmark dataset for DA-RS$^\text{Seg}$ task. It supports two cross-domain tasks (listed as follows) and its test set is evaluated through an online server[^2].
- Adapt Urban to Rural (U $\to$ R).
- Adapt Rural to Urban (R $\to$ U).

As shown in Tab. XI, the following observations can be made: (1) On the ISPRS dataset, MEB5 [114] achieves the best performance under the “w/ Clutter” setting, and DeGL-GAN [110] outperforms all other methods in the “w/o Clutter” configuration. In addition, DEGLAN shows strong results on the “R $\to$ U” task of the LoveDA dataset, while ST-DAsegNet [46] attains the best performance on the “U $\to$ R” task. (2) PFM-JOnet [51] does not reach state-of-the-art performance, highlighting that methods based on foundation models do not always surpass specialized models on specific downstream tasks. (3) Class-wise $IoU$ results in UDA-RS$^\text{Seg}$ task provide a more detailed view of model performance across different categories, which can be referred to original papers for further analysis. (4) It should be noted that the LoveDA leaderboard contains many methods, but not all of them are associated with published papers.

[^2]: https://github.com/June-Je/Wang/LoveDA

### TABLE XI: The performance of representative methods for UDA-RS$^\text{Seg}$ task. $mIoU$ (%) is adopted as metric. The model with the best performance is denoted in bold.

| Method | Source | Tasks on ISPRS dataset (w/ "Clutter") | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | **P $\to$ V\textsection1** | **V $\to$ P\textsection1** | **P $\to$ V\textsection2** | **V $\to$ P\textsection2** | |
| CS-Lg [108] | TIGRS 2021 | 52.03 | 47.87 | 48.06 | 43.17 | |
| IrgDA [118] | TIGRS 2021 | 54.10 | 50.14 | 52.20 | 40.80 | |
| DNf [102] | TIGRS 2024 | 54.19 | 43.74 | 52.63 | 41.45 | |
| STADA [45] | GRSL 2023 | 48.05 | 46.69 | - | - | |
| MDMden [119] | TIGRS 2023 | 51.68 | 47.59 | 45.93 | 41.20 | |
| FGUDA [109] | IJSTAR 2023 | 53.63 | 50.94 | 50.18 | 45.86 | |
| Restaban [15] | RS 2023 | 55.83 | - | 46.63 | - | |
| iJDAT [107] | TIGRS 2024 | 55.52 | 51.30 | 52.10 | 45.79 | |
| CPC-A [116] | TIGRS 2024 | 60.75 | 50.72 | 47.67 | - | |
| ST-DaSegNet [46] | JAG 2024 | 64.33 | 59.65 | 58.16 | 56.86 | |
| PFM-JOneT [51] | TIGRS 2024 | 66.86 | 61.21 | 56.61 | 57.60 | |
| DAF [120] | TIGRS 2024 | 66.69 | 63.93 | 66.81 | **60.18** | |
| MEB5 [114] | TIGRS 2024 | **72.28** | **67.06** | **69.77** | - | |

| Method | Source | Tasks on ISPRS dataset (w/o "Clutter") | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | **P $\to$ V\textsection** | **V $\to$ P\textsection** | **P $\to$ V\textsection2** | **V $\to$ P\textsection2** | |
| MlDAan [112] | TIGRS 2022 | 62.25 | - | 59.82 | 59.01 | |
| MlEE-GAN [105] | TIGRS 2024 | 63.50 | - | 53.31 | 48.32 | |
| DEGLAN [110] | TIGRS 2024 | **68.09** | - | **63.09** | **62.17** | |

| Method | Source | Tasks on LoveDA dataset | | |
| :--- | :--- | :--- | :--- | :--- |
| | | **U $\to$ R** | **R $\to$ U** | |
| DCA [103] | TIGRS 2022 | 45.17 | 46.36 | |
| iJDAT [107] | TIGRS 2022 | 47.31 | 47.12 | |
| ST-DAsegNet [46] | JAG 2024 | **50.08** | 50.28 | |
| DEGLan [110] | TIGRS 2024 | 38.58 | **55.50** | |

### Benchmark Performance on DA-RS$^\text{Det}$. In the DA-RS$^\text{Det}$ task, model performance is commonly evaluated using $AP_i/mAP$, $AR_i/mAR$, and $F_1/mF_1$-score. For each class $i$, the Average Precision ($AP_i$) is defined as the area under the precision-recall curve, while the Mean Average Precision ($mAP$) is the average of $AP_i$ across all classes. The Average Recall ($AR_i$) reflects the proportion of correctly detected objects, and $mAR$ is its mean across classes. The $F_1$-score is defined as $2 \times \frac{Precision \times Recall}{Precision + Recall}$, with $mF_1$-score denoting the mean across classes. In this survey, $mAP@50$ ($mAP_{50}$) is adopted as the primary evaluation metric, as it is used by most existing methods.

We select the datasets in Tab. VII to systematically report the performance of UDA-RS$^\text{Det}$ methods, with the detailed tasks listed as follows.
- Adaptation between xView and DOTA (xView $\to$ DOTA-3).
- Adaptation between DIOR and DOTA (DIOR $\to$ DOTA-10).
- Adaptation between NWPU VHR-10 and DIOR (NWPU VHR-10 $\to$ DIOR).
- Adaptation between UCAS-AOD and CARPK (UCAS-AOD $\to$ CARPK & CARPK $\to$ UCAS-AOD).
- Adaptation between UCAS-AOD and ISPRS Potsdam (UCAS-AOD $\to$ ISPRS Potsdam).

### TABLE XII: The performance of representative methods for UDA-RS$^\text{Det}$ task. $mAP_{50}$ (%) is adopted as the metric.

| Method | Source | Tasks on xView and DOTA datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | **xView $\to$ DOTA-3** | | | | | | | | | | | |
| FADA [133] | TIGRS 2022 | | | | | | | | | | | 52.5 | |
| REST [141] | TIGRS 2024 | | | | | | | | | | | 65.3 | |
| ML-UDA [139] | IJSTAR 2024 | | | | | | | | | | | 66.2 | |
| CDTF [121] | TIGRS 2024 | | | | | | | | | | | 72.8 | |
| FiE-Net [143] | TIGRS 2025 | | | | | | | | | | | 55.1 | |

| Method | Source | Tasks on DIOR and DOTA datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | **DIOR $\to$ DOTA-10** | | | | | | | | | | | |
| DeCLSA [138] | IJSTAR 2024 | | | | | | | | | | | 50.6 | |
| FiE-Net [143] | TIGRS 2025 | | | | | | | | | | | 57.3 | |

| Method | Source | Tasks on NWPU VHR-10 and DIOR datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | **NWPU VHR-10 $\to$ DIOR** | | | | | | | | | | | |
| RFA-Net [134] | TIGRS 2022 | | | | | | | | | | | 51.6 | |
| MGDAN [140] | RS 2025 | | | | | | | | | | | 55.1 | |

| Method | Source | Tasks on UCAS-AOD and CARPK datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | **UCAS-AOD $\to$ CARPK** | **CARPK $\to$ UCAS-AOD** | | | | | | | | | | |
| RST [141] | TIGRS 2024 | 76.2 | | | | | | | | | | 75.6 | |
| FiE-Net [143] | TIGRS 2025 | 79.4 | | | | | | | | | | 78.9 | |

| Method | Source | Tasks on UCAS-AOD and ISPRS Potsdam datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | **UCAS-AOD $\to$ ISPRS Potsdam** | | | | | | | | | | | |
| ML-UDA [139] | TIGRS 2024 | | | | | | | | | | | 91.8 | |
| CDTF [121] | TIGRS 2024 | | | | | | | | | | | 92.6 | |

| Method | Source | Tasks on HRISD and SSTD datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | **HRISD $\to$ SSTD** | | | | | | | | | | | |
| HiSNet [128] | TIGRS 2021 | | | | | | | | | | | 58.1 | |
| REST [141] | TIGRS 2024 | | | | | | | | | | | 58.5 | |
| FiE-Net [143] | TIGRS 2025 | | | | | | | | | | | 58.5 | |

| Method | Source | Tasks on LEVIR and SSTD datasets | | | | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | | **LEVIR $\to$ SSTD** | | | | | | | | | | | |
| HiSNet [128] | TIGRS 2022 | | | | | | | | | | | 58.2 | |
| iDA [128] | TIGRS 2023 | | | | | | | | | | | 55.1 | |
