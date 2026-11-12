| Model | Prompt | Proj. | ImageNet | Caltech101 | OxfordPets | StandfordCars | Flowers102 | Food101 | FGVCAircraft | SUN397 | DTD | EuroSAT | UCF101 | Average |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1. MaPLe | $P \to \hat{P}$ | | 72.63 | 96.12 | 96.67 | 72.82 | 81.55 | 90.83 | 29.79 | 79.03 | 61.90 | 80.93 | 80.40 | |
| | $\hat{P} \to P$ | | 73.23 | 96.01 | 96.68 | 72.87 | 82.45 | 91.08 | 35.96 | 79.21 | 65.74 | 63.30 | 81.16 | |
| | $|\Delta|$ | | 0.60 | 0.11 | 0.01 | 0.05 | 0.90 | 0.25 | 6.17 | 0.18 | 3.84 | 17.63 | 0.76 | 2.77 |
| 2. MaPLe w/ ER | $P \to \hat{P}$ | | 72.58 | 96.58 | 96.67 | 72.31 | 81.98 | 91.13 | 29.16 | 78.90 | 61.42 | 80.60 | 80.59 | |
| | $\hat{P} \to P$ | | 73.30 | 95.95 | 96.57 | 72.59 | 82.00 | 91.25 | 29.46 | 79.46 | 66.87 | 61.07 | 80.18 | |
| | $|\Delta|$ | | 0.72 | 0.63 | 0.10 | 0.28 | 0.02 | 0.12 | 0.30 | 0.56 | 5.45 | 19.53 | 0.41 | 2.56 |
| 3. SCP w/o ER | $P \to \hat{P}$ | | 90.53 | 90.12 | 97.82 | 70.23 | 80.57 | 98.80 | 37.81 | 89.66 | 67.86 | 72.70 | 82.96 | |
| | $\hat{P} \to P$ | | 89.26 | 92.35 | 97.03 | 70.61 | 84.32 | 96.13 | 37.28 | 90.87 | 70.30 | 75.32 | 81.62 | |
| | $|\Delta|$ | | 1.27 | 2.23 | 0.79 | 0.38 | 3.75 | 2.67 | 0.53 | 1.21 | 2.44 | 2.62 | 1.34 | 1.75 |
| 4. SCP | $P \to \hat{P}$ | | 90.02 | 91.49 | 97.53 | 70.70 | 82.05 | 99.21 | 37.81 | 89.82 | 68.41 | 74.46 | 82.74 | |
| | $\hat{P} \to P$ | | 90.13 | 91.70 | 97.70 | 70.99 | 81.63 | 98.51 | 34.92 | 90.92 | 71.50 | 72.16 | 80.93 | |
| | $|\Delta|$ | | 0.11 | 0.21 | 0.17 | 0.29 | 0.42 | 0.70 | 2.89 | 1.10 | 3.09 | 2.30 | 1.81 | 1.19 |

datasets indicates that the groups employing the ER exhibit a reduced disparity across different directions of modality conversion for both the SCP and MaPLe. Besides, we compare ER with a non-ER group and a modified energy-based regulation version instead of entropy-based as illustrated in Table 6. The results shows that entropy-based ER effectively enhances generalization performance.

| Regulation | Base | New | HM |
|---|---|---|---|
| w/o ER | 83.91 | 76.95 | 80.28 |
| Energy-based | 54.13 | 52.73 | 53.42 |
| Entropy-based | 84.41 | 77.45 | 80.78 |

| Domain Resist. | Prompt Augment. | Base | New | HM |
|---|---|---|---|---|
| - | - | 81.91 | 73.04 | 77.22 |
| $\checkmark$ | - | 83.46 | 77.11 | 80.16 |
| - | $\checkmark$ | 81.19 | 72.08 | 76.37 |
| $\checkmark$ | $\checkmark$ | 83.81 | 76.87 | 80.19 |

**Effect of Self-generated Proxy Alignment.** Table 7 explore all four combinations in terms of the adoption of two modules (Domain Resistance and Prompt Augmentation). It can be clearly seen that solely employing the DR appears to enhance generalization capability, in contrast to the less favourable performance of only using PA. However, the combination of both DR and PA achieves higher generalization performance in the Base and HM than others.

| Templates | Base | New | HM |
|---|---|---|---|
| "a photo of a" | 83.81 | 76.87 | 80.19 |
| "this is a picture of" | 83.89 | 76.94 | 80.26 |
| "X X X X" | 84.79 | 78.67 | 81.62 |