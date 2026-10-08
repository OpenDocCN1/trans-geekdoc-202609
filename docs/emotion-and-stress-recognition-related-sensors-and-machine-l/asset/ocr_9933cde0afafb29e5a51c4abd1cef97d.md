Table 6. Experimental results for the FF and DF methodologies in the FF methodology. Results obtained using LOSO. The column contains the results in terms of Accuracy (A), F-score (F1), and time (T) in seconds, per dataset for MAHNO-HCI [ITMDER], [DEAP]. The best results are shown in bold.

| | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence |
|---|---|---|---|---|---|---|---|---|---|---|---||
| | ITMDER | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence |
| | DEAP | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence |
| | MAHNO-HCI | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence |
| FF | 66.7 | 9.0 | 58.1 | 10.2 | 75.0 | 14.8 | 60.0 | 18.4 | 56.7 | 22.5 | 68.7 | 22.2 |
| A | 86.7 | 17.3 | 92.2 | 12.4 | 58.0 | 6.1 | 63.8 | 15.6 | 62.7 | 10.2 | 75.4 | 17.9 |
| F1 | | 50.9 | 23.5 | 95.0 | 12.9 | 71.8 | 7.8 | 72.9 | 14.1 | 72.5 | 24.7 |
| T | | | 1.35 | 0.0 | | | 0.6 | 0.7 | | | 0.01 | 0.0 |

Table 7. Classifier used per dataset and sensor modality for the Arousal and Valence dimension in the FF methodology. Results obtained using 4-fold CV.

| | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence |
|---|---|---|---|---|---|---|---|---|---|---|---||
| | ITMDER | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence |
| | DEAP | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence |
| | MAHNO-HCI | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence | Arousal | Valence |
| Classifier | SVM | | | | | | | | | | | |
| | GNB | | | | | | | | | | | |
| | QDA | | | | | | | | | | | |
| | GNB | | | | | | | | | | | |
| | DT | | | | | | | | | | | |
| | RF | | | | | | | | | | | |
| A | 86.7 | 17.3 | 92.9 | 12.0 | 57.0 | 55.2 | 56.9 | 8.2 | 62.7 | 35.9 | 68.7 | 22.6 |
| F1 | 19.4 | 34.4 | 95.9 | 10.7 | 53.8 | 23.3 | 70.7 | 6.0 | 62.5 | 16.6 | 67.5 | 22.0 |
| T | | | 0.02 | 0.0 | | | 0.07 | 0.02 | | | 0.01 | 0.03 |