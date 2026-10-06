
# A Combination of Ensemble with MCDM Approach

- **Identify optimum negative and positive solutions:** The positive and negative ideal solution sets (LR), represented by the symbols $X^+$ and $X^-$, respectively, can be identified from Eq. (7.6) as

```
$X^+ = [p_1^+, p_2^+, p_3^+, \dots, p_v^+] \quad (7.7)$
```

```
$X^- = [p_1^-, p_2^-, p_3^-, \dots, p_v^-] \quad (7.8)$
```

where

```
$p_v^+ = \begin{cases} \max p_{av}, \text{if } v \text{ is a benefit attribute} \\ \min p_{av}, \text{if } v \text{ is a cost attribute} \end{cases} \quad (7.9)$
```

```
$p_v^- = \begin{cases} \min p_{av}, \text{if } v \text{ is a benefit attribute} \\ \max p_{av}, \text{if } v \text{ is a cost attribute} \end{cases} \quad (7.10)$
```

- **Obtain the separation values (SVs):** The SV, which is determined by using the Euclidean distance theory, is the distance between each option rating and the (positive, negative) ideal solutions. Eqs. (7.10) and (7.11) illustrate the steps in computing positive and negative separation, respectively.

```
$Q_u^+ = \sqrt{\sum_{v=1}^v (p_{av} - p_v^+)^2} \quad (7.11)$
```

```
$Q_u^- = \sqrt{\sum_{v=1}^v (p_{av} - p_v^-)^2} \quad (7.12)$
```

- **Determine the total score for preferences:** Eq. (7.13) provides the overall preference score $S_u$ for every alternative $X_u$. Higher $S_u$ values are used to rank the alternatives.

```
$S_u = \frac{Q_u^+}{Q_u^+ + Q_u^-} \quad (7.13)$
```

In this approach, we have used 18 different classifiers like (k–NN) [27], DT [28], logistic regression (LR) [29], RF [30], naive bayes (NB) [31], SVM with linear kernel (SVM:Linear) [32], SVM with RBF kernel (SVMRBF) [33], adaboost [34], bagging [35], stochastic gradient descent (SDG) [36], preceptor (PREPT) [37], passive aggressive classifier (PAC) [38], ridge classifier (RC) [39], quadratic discriminant analysis (QDA) [40], Gaussian process classification (GPC) [41], extra trees classifier (ETC) [42], gradient boosting classifier (GBDC) [43], and multi-layer perceptron (MLP) [44]. We have used precision, recall, accuracy, F1-score, and geometric measures are discussed for choosing the best classifier through TOPSIS. These performance measures are discussed in Section 7.3.2.

# 7.3 EXPERIMENTAL RESULTS WITH DISCUSSION

This section has been categorized into various subsets. Section 7.3.1 will discuss the data-set description. Section 7.3.2 will give an idea of the performance measures used in this research. Finally, Section 7.3.3 will highlight the various experiments that have been performed in this research.

## 7.3.1 DATASET DESCRIPTION

Here, we have taken the Alzheimer’s dementia recognition through spontaneous speech (ADReSSol) dataset for early prediction of AD. The ADReSSo dataset was carefully designed to reduce issues frequently caused by disagreements in assessment of AD detection techniques. These biases include imbalances in gender and age distribution, variations in audio quality, and repeated instances of speech from the same participant. The age distribution and the number of samples in the ADReSSo dataset are shown in Table 7.1. Figure 7.2 shows the graphical representation of the waveform and the sonogram of the samples from the ADReSSo dataset (https://dementia.talkbank.org/ADReSS-2020/).

## 7.3.2 PERFORMANCE MEASURES

At this stage, the predictive power of the suggested strategy will be evaluated. The goal problem, a binary classification problem, will be assessed using the measurements below. Positive and negative classes correspond to Alzheimer’s patients and normal people. Here, statistical quality measures have been employed, specifically precision, recall, and F-measure. Below is an expression of these metrics’ definitions and mathematical formulas.

- *Precision (Pr);* Pr can be defined as the percentage (%) of relevant occurrences among all retrieved instances. It determines the probability that a pattern is positively predicted will hold. Stated clearly, the Pr of a test compares the number of true positives to the total number of positive patterns found.

```
$Pr = \frac{e}{e + g}$
```

| TABLE 7.1 | The Age Distribution over the Samples in the ADReSSo Dataset | | |
| :--- | :--- | :--- | :--- |
| Age Gap | Total Samples AD | Total Samples Non-AD | |
| | Male | Female | Male | Female |
| 50 to 55 | 2 | 0 | 2 | 0 |
| 55 to 60 | 7 | 6 | 7 | 6 |
| 60 to 65 | 4 | 9 | 4 | 9 |
| 65 to 70 | 9 | 14 | 9 | 14 |
| 70 to 75 | 9 | 11 | 9 | 11 |
| 75 to 80 | 4 | 3 | 4 | 3 |
| Total | 35 | 43 | 35 | 43 |

img/7cacd601eea2ac8e53f091eef3f_171_0.png
img/7cacd601eea2ac8e53f091eef3f_171_1.png
img/7cacd601eea2ac8e53f091eef3f_171_2.png
img/7cacd601eea2ac8e53f091eef3f_171_3.png
img/7cacd601eea2ac8e53f091eef3f_171_4.png
img/7cacd601eea2ac8e53f091eef3f_171_5.png
img/7cacd601eea2ac8e53f091eef3f_171_6.png
img/7cacd601eea2ac8e53f091eef3f_171_7.png

**Figure 7.2** Waveform, sonogram, amplitude histogram, and spectrogram of audio samples from the ADReSS dataset: (a) Audio waveform of Alzheimer's patient. (b) Audio Waveform of non-Alzheimer's patient. (c) Audio sonogram of Alzheimer's patient. (d) Audio sonogram of non-Alzheimer's patient. (e) Amplitude histogram of Alzheimer's patient. (f) Amplitude histogram of non-Alzheimer's patient. (g) Audio spectrogram of Alzheimer's patient. (h) Audio spectrogram of non-Alzheimer's patient.

- **Recall (Re):** referred to as sensitivity, is the proportion of recovered instances among all instances. Otherwise, it is the proportion of positive patterns that are recognized as such.

```
$Re = \frac{e}{e+h}$
```

- **Accuracy (Acc):** It shows what proportion of samples are correctly classified.

```
$Acc = \frac{e+f}{e+f+h}$
```

- **F-measure (FI):** It is a statistic that considers both $Pr$ and $Re$. Both the $Pr$ and the $Re$ have the same weight.

```
$F1 = 2 * \frac{Pr * Re}{Pr + Re}$
```

- **Geometric mean (GM):** The arithmetic mean of the Information represented by $Pr$ and $Re$, is the information value of the $GM$ of $Pr$ and $Re$, which normalizes TP to the $GM$ of predicted positives and real positives.

```
$GM = \sqrt{Pr * Re}$
```

## 7.3.3 EXPERIMENTS PERFORMED

The several pre-processing tasks in Section 7.2.1 have been applied to the dataset to assess the suggested technique's robustness. 20% of the data was used for testing, and 80% were for training. The ensuing examinations and assessments have been completed.

- *Experiment I:* Here, after applying the pre-processing tasks (discussed in Section 7.2.1) and the SVM-SMOTE oversampling technique, various performance measures (discussed in Section 7.3.2) have been calculated via different classifiers (discussed in Section 7.2.4). Table 7.2 shows the experimental results for this experiment. Here, SVM(Linear)

| TABLE 7.2 | Performance Measures of the ADReSS Dataset through Various Classifiers | | | | |
| Classifier | Pr | Re | Acc | FI | GM |
| :--- | :--- | :--- | :--- | :--- | :--- |
| k-NN | 0.6818 | 0.6818 | 0.6818 | 0.6825 | 0.6818 |
| DT | 0.5312 | 0.5455 | 0.5445 | 0.5211 | 0.5338 |
| LR | 0.7286 | 0.5909 | 0.6818 | 0.6718 | 0.7048 |
| RF | 0.6026 | 0.5909 | 0.5909 | 0.5884 | 0.5967 |
| SGD | 0.2273 | 0.4545 | 0.4545 | 0.2841 | 0.3214 |
| NB | 0.5909 | 0.5909 | 0.5909 | 0.5918 | 0.5909 |
| SVM(Linear) | 0.7906 | 0.7727 | 0.7727 | 0.7713 | 0.7816 |
| SVM(RBBF) | 0.2273 | 0.4545 | 0.4545 | 0.2841 | 0.3214 |
| MLP | 0.6670 | 0.6364 | 0.6364 | 0.6303 | 0.6488 |
| AdaBoost | 0.7589 | 0.7273 | 0.7273 | 0.7227 | 0.7429 |
| Bagging | 0.6417 | 0.6364 | 0.6364 | 0.6364 | 0.6390 |
| GDBC | 0.6818 | 0.6818 | 0.6818 | 0.6825 | 0.6818 |
| ETC | 0.5625 | 0.5545 | 0.5535 | 0.5379 | 0.5539 |
| GPC | 0.6333 | 0.6364 | 0.6364 | 0.6364 | 0.6348 |
| QDA | 0.4810 | 0.5000 | 0.5000 | 0.4837 | 0.4904 |
| RC | 0.6238 | 0.5909 | 0.5909 | 0.5780 | 0.6071 |
| PAC | 0.7857 | 0.5909 | 0.5909 | 0.4793 | 0.6814 |
| PREPT | 0.2273 | 0.4545 | 0.4545 | 0.2841 | 0.3214 |
