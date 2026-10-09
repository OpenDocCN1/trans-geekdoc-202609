TABLE VIII: The performance of representative methods on HSI datasets for UDA-RSCIs task. The model with the best performance is denoted in bold. Methods marked with \*\* are trained with only 5% of the source samples, while others utilize the full set of labeled samples.

| Method | Source | Tasks | OA (%) |
| :--- | :--- | :--- | :--- |
| **The Houston Datasets** | | | |
| TSNet* [81] | TNNLS 2021 | / | 75.34/88.38 |
| S^DL [90] | TNNLS 2025 | / | 72.10/ |
| DAN_MFAC* [94] | KBS 2025 | HS13---HS18 | 79.88/81.50 |
| TAADA [74] | TGRS 2022 | / | 81.63/ |
| SDNet [93] | TGRS 2023 | HS18---HS13 | 79.96/ |
| MLUDA [88] | TGRS 2024 | / | 76.64/ |
| S^2AMNet [91] | TGRS 2024 | / | 82.70/ |
| **The HyRANK Dataset** | | | |
| TSNet* [81] | TNNLS 2021 | Dioní---Loukia | 63.31/ |
| S^DL [90] | TNNLS 2025 | / | 65.00/ |
| DAN_MFAC* [94] | KRS 2025 | Loukia---Dioni | 64.24/68.55 |
| TAADA [74] | TGRS 2022 | / | 68.03/ |
| **The Hangzhou-Shanghai Dataset** | | | |
| TSNet* [81] | TNNLS 2021 | / | 90.36/ |
| S^DL [90] | TNNLS 2025 | HZ---SH | 92.40/ |
| TAADA [74] | TGRS 2022 | / | 94.17/ |
| MLUDA [88] | TGRS 2024 | SH---HZ | 92.15/ |
| S^2AMNet [91] | TGRS 2024 | / | 90.62/ |
| **The Pavia University and Center Datasets** | | | |
| DAN_MFAC* [94] | KRS 2025 | PU---PC | 75.56/69.78 |
| UCANNet [72] | TGRS 2020 | / | 88.25/ |
| JDA [68] | ISLARS 2021 | / | 83.55/ |
| TAADA [74] | GRSL 2022 | PC---PU | 92.57/78.04 |
| SDNet [93] | TGRS 2023 | / | 81.94/ |
| MLUDA [88] | TGRS 2024 | / | 91.26/ |
| S^2AMNet [91] | TGRS 2024 | / | 86.18/ |
| **The Botswana Datasets** | | | |
| CDA [67] | TGRS 2020 | May---June/ June---May/ May---July/ June---July/ July---June | 92.62/87.85/91.27 79.70/85.05/93.14 94.11/92.91/91.11/ 83.54/95.35/46.70 91.41/85.25/91.70/ 83.29/85.78/93.96 89.69/81.39/90.30/ 80.63/90.81/91.82 |
| JCGNN [30] | ISLARS 2021 | | |
| CMC [69] | ISLARS 2021 | | |
| JDA [68] | ISLARS 2021 | | |

+   - Adapt Pavia University to Pavia Center (PU → PC).
- Adapt Pavia Center to Pavia University (PC → PU).
In the Botswana dataset, three subsets (May, June, July) are used as source and target domains with 9 consistent land cover categories. Each subset can serve as source while the other two act as target, resulting in 6 domain adaption tasks.
- Adapt May to June (May → June).
- Adapt May to May (June → May).
- Adapt June to May (May → July).
- Adapt May to July (May → May).
- Adapt July to May (July → May).
- Adapt July to June (June → July).
- Adapt June to July (June → July).
- Adapt July to June (July → June).

From the performance comparison in Tab. VIII, we conduct an in-depth analysis from the following perspectives. (1) TSNet [81], S^DL [90] and DAN_MFAC [94] investigate the challenging scenario of training with only 5% of source samples, and demonstrate competitive performances on “Houston”, “HyRANK”, “Hangzhou-Shanghai”, and “Pavia University and Center” datasets. In contrast, the other methods do not follow this restricted setting, enabling a more direct comparison under full supervision. TAADA [74] achieves the highest performance on the adaption task of the HyRANK dataset. On the “HZ→SH” and “SH→HZ” tasks, TAADA [74] and MLUDA [88] achieve the best results, respectively. UCANA [72] represents the state-of-the-art on the Pavia University and Center datasets. For the Botswana dataset, JCGNN [30] demonstrates clear superiority, securing the best results on 5 out of 6 tasks. (2) In the DA-RSCls task on HSI datasets, experimental configurations differ considerably across methods. Therefore, we recommend checking each paper’s implementation details carefully when following these methods. (3) The preprocessing stage of hyperspectral data plays a crucial role. Therefore, the comparison of methods is not merely about deep learning techniques, but rather constitute a comprehensive evaluation encompassing preprocessing, hyperparameter settings, and other relevant factors. (4) Some datasets have only been explored in isolated methods, and systematic or continuous explorations are relatively limited. Therefore, the results on all HSI datasets are not presented in the Tab. VIII.

cover categories are extracted from the Houston2013 scene to correspond with the Houston2018 scene. The 2 domain adaptation tasks are listed as follows:
- Adapt Houston2013 to Houston2018 (HS13 → HS18).
- Adapt Houston2018 to Houston2013 (HS18 → HS13).

In the HyRANK dataset, Dioní and Loukia are respectively served as source and target sets. 12 consistent land cover categories between Dioní and Loukia are extracted. The 2 domain adaptation tasks are listed as follows:
- Adapt Dioní to Loukia (Dioní → Loukia).
- Adapt Loukia to Dioní (Loukia → Dioní).

In the Hangzhou-Shanghai dataset, Hangzhou and Shanghai are respectively served as source and target sets. 3 consistent land cover categories between Hangzhou and Shanghai are extracted. The 2 domain adaptation tasks are listed as follows:
- Adapt Hangzhou to Shanghai (HZ → SH).
- Adapt Shanghai to Hangzhou (SH → HZ).

In the Pavia University and Center Datasets, Pavia University and Pavia Center are respectively served as source and target sets. 7 consistent land cover categories between Pavia University and Pavia Center are extracted. The 2 domain adaptation tasks are listed as follows:

# Benchmark Performance on Aerial and Satellite Optical Image datasets

Tab. IX summarizes the performance of representative UDA-RSCls methods on the aerial and satellite optical benchmark datasets listed in Tab. V.

As shown in Tab.IX, we select 5 widely applied datasets, namely AID (A) [1], UC-Merced (U) [229], WHU-RS19 (W) [230], NWPV-RESISC45 (N) [2] and RSCNC7 (R) [232] to construct the following UDA-RSCls tasks. Since different methods employ different combinations of datasets in their experiments, the number of shared categories varies. Therefore, we present a comprehensive summary in Tab. IX.
- Adaptation between UC-Merced and AID (A → U & U → A).
- Adaptation between UC-Merced and WHU-RS19 (U → W & W → U).
- Adaptation between UC-Merced and NWPV-RESISC45 (U → N & N → U).