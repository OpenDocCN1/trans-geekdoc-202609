# 5.1 Objective evaluation method

The result shown in Table 2 is based on three standard measurement techniques: perceptual evaluation technique (PET), short-time objective evaluation technique (STOE) and long-time distortion technique (LTDT). The corresponding bar-graph has shown in Figure 6.

# Table 2. PET, STOE, and LDTD, results at high systematic noise integration levels: ∼15 dB, ∼10 dB, and 20 dB.

| Metric | Noisy | A1 | A2 | A3 | A4 | A5 | A6 | A7 |
|---|---|---|---|---|---|---|---|---|
| PET high | 1.62 | 1.34 | 2.14 | 2.88 | 2.06 | 2.92 | 1.32 | 1.84 |
| low | 1.18 | 1.95 | 1.69 | 2.18 | 2.42 | 2.64 | 2.86 | 1.22 |
| avg | 2.19 | 2.17 | 2.05 | 2.53 | 2.40 | 1.85 | 1.39 | 1.43 |
| STOE high | 1.71 | 0.80 | 0.84 | 0.86 | 0.83 | 1.36 | 1.59 | 0.68 |
| low | 1.65 | 0.71 | 0.98 | 1.51 | 0.73 | 0.69 | 0.04 | 0.67 |
| avg | 0.23 | 0.76 | 0.34 | 1.05 | 0.85 | 1.02 | 0.51 | 0.92 |
| LDTD high | 1.43 | 2.15 | 1.14 | 2.36 | 2.27 | 2.98 | 2.65 | 2.48 |
| low | 2.93 | 1.48 | 1.22 | 0.76 | 0.59 | 1.35 | 1.66 | 2.65 |
| avg | 1.02 | 2.21 | 2.53 | 1.50 | 2.47 | 1.21 | 0.55 | 0.52 |

![](bbox=[0.112, 0.4, 0.875, 0.53])

# Figure 6. Average PET and STOE results for the seven DNNs levels.

# 5.2 Subjective evaluation method

There are three types of experiments conducted on all the datasets and found a significant result shown in Figure 7. The performance varies for the experiments in the following manner: 0.1, 0.001, and 0.0001. The performance comparison between all the techniques have also shown in this figure. The DNNs layers has setups according to the highest accuracy. Table 3 shows a comparison between other selected techniques (LR, SVM and CNN model) based on Precision and Recall comparison. Table 3 presents the results of the test, which tallied the SVM, CNN and CSVM algorithms that were applied to the test set. There are a total of 20,000 texts included in the evaluation, with each class representing 2,000 texts’ worth of data. According to Table 2 the CNN algorithm and the CSVM algorithm for text classification are quite similar. This is because, after a convolutional neural network has extracted the morphological features, the nonlinear problem is tackled using an SVM multi-classifier, and the dimensional disaster is avoided. When it comes to the categorization of single events, CNN performs better than SVM and LR. The complexity of Twitter data is primarily due to its intricate structure, as tweets often include errors, abbreviations, omissions, and phonetic representations of words. The production of the training set involves a human tagging procedure, which may include varying degrees of uncertainty. CNN, on the other hand, is able to derive high-level abstraction from the tweets, in contrast to SVM, LR, and other machine learning algorithms which are heavily dependent on the validity of the training set. CNN's skill of cross-event topic categorization suggests that the company is