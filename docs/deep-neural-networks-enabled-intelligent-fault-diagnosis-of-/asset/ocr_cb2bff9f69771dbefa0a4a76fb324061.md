# Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

TABLE 10.3 Dataset Descriptions in Multi-Work Conditions

| Dataset Samples | Speed (Hz) | Load Size | Samples | Speed (Hz) | Load Size | Total Samples |
|---|---|---|---|---|---|---||
| Bearing A | 10,000 | 20/30 | 0/2 | 10,000 | 30/40 | 0/2 | 20,000 |
| | B | 10,000 | 30/40 | 2/0 | 10,000 | 30/40 | 2/0 | 20,000 |
| | C | 15,000 | 20/30 | 0/2 | 15,000 | 20/30 | 0/2 | 30,000 |
| Gear D | 10,000 | 20/30 | 2/5 | 5,000 | 30 | 1 | 15,000 |
| | E | 10,000 | 20/30 | 0/2 | 10,000 | 10/30 | 0/2 | 20,000 |
| | F | 10,000 | 30/40 | 2/0 | 10,000 | 30/40 | 2/0 | 20,000 |
| | G | 15,000 | 20/30 | 0/2 | 15,000 | 20/30 | 0/2 | 30,000 |
| | H | 10,000 | 2/5 | 5,000 | 30 | 1 | 15,000 |

data is mainly from the previously mentioned 20-0, 30-2, and 40-0 of bearing and gear diagnostic tasks. For datasets D and H, the training data is from the bearing or gear’s 30Hz-2 and -5 situations, the testing data is from the 30Hz-1. For D and H, the data splitting is the same as illustrated in Section IV, and each health type has 1000 samples. Detailed settings of the training set and testing set in each situation are introduced in Table 10.3. Each dataset can be deemed as a 5-classification guessing game.

Results of several methods in multiple working conditions are shown in Figure 10.15. In the method of "RDT+ CNN", 1D CNN with the layer size of [Conv1D (3, 32)→maxpooling1D(3)→Conv1D (6, 64)→maxpooling1D(2)→Conv1D (12, 38)→maxpooling1D(2)→Dense(5)] is utilized. Other methods’ settings are the same as those in the previous section. The model’s hyperparameters are the same as stated in Section 10.4. In experiments, OA of the proposed method is 99.999%, 99.78%, 99.94%, 99.99%, 99.82%, 99.77%, and 99.81%, respectively. From Figure 10.15(b), the AVG of these methods are 87.75%, 87.99%, 94.70%, 94.55%, 95.55%, 99.47%, and 99.87%, respectively. Compared with SVM, MLP, and CNN, the proposed RL-based method has a better overall diagnosis. In contrast to RDT+ CNN, the AVG of the proposed method

```
# TFF+SVM TFT+NN RDT+CNN WPT+MLP
# WPT+CNN SET+CNN Proposal
```

![](bbox=[0.118, 0.708, 0.882, 0.86])

Figure 10.15 Results of different methods on multiple working conditions. (a) OA comparisons of different methods and (b) AVG comparisons of eight tasks.