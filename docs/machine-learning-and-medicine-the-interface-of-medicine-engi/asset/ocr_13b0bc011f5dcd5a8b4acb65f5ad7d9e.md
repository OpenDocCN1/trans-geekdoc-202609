Nevertheless, NLG-oriented metrics may lack precision in clinical settings as they do not gauge syntax, semantics, or the comprehension of report meanings. Consequently, metrics tailored to the RRG task, like F1cXb and F1RG_ER, have emerged to evaluate pathologies’ presence, absence, or uncertainty and their relationships within reports. These chest-RRG-oriented metrics offer a more accurate report quality assessment than NLG-oriented metrics. For instance, despite minimal differences in BLEU4 scores between Delbrouck et al. [12] and our approach in MIMIC-CXR, a significant gap is observed when measured with chest-RRG-oriented metrics. Another example of the imprecision of NLG-oriented metrics in assessing report quality can be seen in nearly identical BLEU4 scores between Miura et al. [11]’s models trained with NLL and RL in MIMIC-CXR, yet exhibiting a 12-point difference in F1cXb. High values in NLG-oriented metrics do not reflect the quality of a report, as neither BLEU4 nor ROUGE-L measures whether the mentioned pathologies are present, absent, or uncertain.

Table 3. Comparison of our model, SwinB+BERT9k, against top state-of-the-art models for chest RRG on the MIMIC-CXR test set and Open-i dataset. The metric values are provided in (%). Bold font indicates the best result obtained for each metric.

| State of the Art | Chest-RRG-Oriented F1cXb | Chest-RRG-Oriented F1RG_ER | NLG-Oriented BLEU4 | NLG-Oriented ROUGE-L |
|---|---|---|---|---|
| **MIMIC-CXR: NLL models** | | | | |
| Yang et al. [28] | - | - | 11.5 | 28.4 |
| Pan et al. [29] | - | - | 11.2 | 28.8 |
| Yang et al. [30] | - | - | 11.1 | 27.4 |
| Zhao et al. [31] | - | - | 10.9 | 27.5 |
| Nicolson et al. [32] | - | - | 12.7 | 28.6 |
| Liu et al. [5] | 29.2 | - | 7.6 | - |
| Chen et al. [9] | 34.6 | - | 8.6 | 27.7 |
| Miura et al. [11] | 44.7 | - | 11.5 | - |
| Chen et al. [10] | 40.5 | - | 10.6 | 27.8 |
| Delbrouck et al. [12] | 44.8 | 20.2 | 10.5 | 25.3 |
| **Ours: NLL stage** | **57.8** | **27.1** | 10.3 | 22.8 |
| **MIMIC-CXR: RL models** | | | | |
| Miura et al. [11] (BERTscr+fact_ENT) | 56.7 | - | 11.1 | - |
| Miura et al. [11] (BERTscr+fact_ENTNLI) | 56.7 | - | 11.4 | - |
| Delbrouck et al. [12] (BERTscr+F1 RG_ER) | 62.2 | 34.7 | 11.4 | 26.5 |
| **Ours: RL stage (BERTscr+F1 RG_ER)** | **66.2** | **37.8** | **13.2** | **27.1** |
| **Open-i: NLL models** | | | | |
| Miura et al. [11] | 32.2 | - | **12.1** | 28.8 |
| Chen et al. [10] | - | - | 12.0 | **29.8** |
| Alfarghaly et al. [26] | - | - | 11.1 | 28.9 |
| Donahue et al. [49] | - | - | 9.9 | 27.8 |
| Delbrouck et al. [12] | 33.1 | 26.4 | 11.4 | - |
| **Ours: NLL stage** | 46.6 | **34.5** | 11.2 | 23.4 |
| **Open-i: RL models** | | | | |
| Miura et al. [11] (BERTscr+fact_ENT) | 48.3 | - | 12.0 | - |
| Miura et al. [11] (BERTscr+fact_ENTNLI) | 47.8 | - | 13.1 | - |
| Delbrouck et al. [12] (BERTscr+F1 RG_ER) | 49.1 | 41.2 | 13.9 | 32.7 |
| **Ours: RL stage (BERTscr+F1 RG_ER)** | 54.7 | 45.6 | **15.1** | **34.3** |

# 4. Discussion

This study presents an efficient workflow for training VED models explicitly designed for chest RRG. This workflow demonstrates remarkable performance in chest-RRG-oriented metrics. One pivotal finding lies in our analysis of the proposed architectures, where we show that utilizing the SwinB encoder yields superior radiograph representations. Notably, the word-based approach proves more competitive in the decoder component