Table 6 presents the hyperparameter tuning results. To select the best hyperparameters, we established the following prioritization: (1) Accuracy, (2) AUC, and (3) low epoch. Considering the characteristics of MLP and to avoid overfitting, the learning needs to stop when the accuracy does not increase. Regarding the network design, models with three hidden layers could not be tested because WSE produced a model that contained only the label data. According to the results of Table 6, we selected "c", 0.76, and 73 as the values of network design, learning rate, and epoch, respectively, for the EEG-GSR combined dataset. For the EEG dataset, "i", 0.19, and 489 were the best values of network design, learning rate, and epoch, respectively. Finally, "i", 0.95, and 321 were defined as the values of hyperparameters for the GSR dataset.

# Table 6. MLP hyperparameter tuning results.

| Layer Node | Learning Rate | Epoch | Accuracy (%) | AUC |
|---|---|---|---|--|
| EEG-GSR | a | 0.47 | 444 | 76.79 | 0.771 |
| | i | 0.90 | 215 | 82.14 | 0.794 |
| | o | 0.47 | 444 | 76.79 | 0.771 |
| | t | 0.76 | 73 | 83.95 | 0.765 |
| | i | 0.59 | 572 | 82.14 | 0.795 |
| | i, a | 0.49 | 1351 | 82.14 | 0.764 |
| | o, t | 0.91 | 192 | 76.79 | 0.737 |
| EEG | a | 0.40 | 452 | 76.79 | 0.733 |
| | i | 0.19 | 489 | 83.93 | 0.822 |
| | o | 0.21 | 654 | 82.14 | 0.791 |
| | t | 0.48 | 163 | 82.14 | 0.706 |
| | i, a | 0.43 | 405 | 78.57 | 0.710 |
| | o, t | 0.21 | 265 | 75.00 | 0.710 |
| | t, i | 0.99 | 320 | 78.57 | 0.692 |
| GSR | a | 0.44 | 312 | 75.00 | 0.767 |
| | i | 0.44 | 312 | 75.00 | 0.767 |
| | o | 0.44 | 312 | 75.00 | 0.767 |
| | t | 0.95 | 321 | 76.79 | 0.759 |
| | i, a | 0.64 | 1120 | 73.21 | 0.663 |
| | o, t | 0.90 | 231 | 71.43 | 0.642 |
| | t, i | 0.91 | 255 | 71.43 | 0.641 |



Table 7 presents the tuning results of the NB hyperparameters for dataset. Weka’s NB API has two major options, which are mutually exclusive: whether to use a kernel density estimator rather than the normal distribution for numeric attributes (“Kernel” in Table 7), and whether to use a supervised discretization to process numeric attributes (“Discretization” in Table 7).

As the parameter tuning processes for RF and MLP, we also tested all possible combinations of the NB hyperparameters options. Thus, we trained and tested nine models in total, and found that the parameters should be disabled for the EEG-GSR combined, EEG, and GSR datasets.