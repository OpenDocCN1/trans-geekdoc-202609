
# 190 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

![](img/f29bba55de4872c43f26af4667e705f2_200_0.png)

FIGURE 10.12 Classification accuracy change of different training episodes. (a) OA of different training episodes and (b) change of std.

classification accuracy and diagnostic stability are all gradually increasing. When the episode arrives at 100, the OA of each speed-load case is over 99.5. Compared with other diagnostic tasks, it can be found that fault diagnosis is easier to realize in B20_0, B30_2, and G40_0 conditions. In a small episode, this method still has higher accuracy in these subtasks. Therefore, the episodes could appropriately be reduced to prevent the agent's overestimation in these subtasks. Since the bearing-gear mixture dataset is a 9-classification task and has samples, a bigger episode is needed for the agent to explore the experiences by trial and error. This is the reason why the accuracy is rising slowly in the mixed diagnostic tasks, especially in the C30_2 scenario. Moreover, it can be found that this method performs better in low speed or no load by comparing C20_0 with C30_2 and C40_0 situations. In practical terms, the training episode can be set as a bigger number to increase the agent's interaction with the environment, and thereby improve the accuracy in complex diagnostic tasks.

Change of Discount Factor γ Unlike the Atari games, the correlation of adjacent states in the formed "guessing game" is however, the classification agent in this "guessing game" cares about more immediate rewards. It is the reason why a small γ value (γ=0.1) is selected in this task. To verify the effect of parameter γ on the diagnostic performance, the proposed method is carried out in the above datasets, with the parameters change from 0.1 to 0.9. Other settings are set as illustrated in Section 10.4, and the model is conducted 3 times on each speed-load case. The change of OA and Std in different parameters is shown in Figure 10.13.

From Figure 10.13(a), the diagnostic performance on nine datasets is all decreasing when the discount factor γ is increasing. When γ is greater than or equal to 0.5, the diagnostic accuracy drops significantly on all subtasks. Specifically, when γ is equal to 0, the model's OA on nine datasets is 87.13%, 89.11%, 87.71%, 84.81%, 85.63%, 88.91%, 79.32%, 84.54%, 84.16%, respectively. Compared with γ equal to 0.1, the diagnostic OA in nine situations decreased by 12.87%, 10.89%, 12.23%, 15.35%, 14.29%, 11.09%, 20.63%, 15.35%, 15.74%, respectively. From Figure 10.13(b), it can also be inferred that a similar conclusion holds for the diagnostic stability of the method. Therefore, however further verified the correctness of the above-reason why a small γ (γ=0.1) is selected in this task. Importantly, it gives a reference to how choose parameters in similar tasks.

# Reinforcement Learning for Intelligent Fault Diagnosis — 191

B20_0 --- B30_2 --- B40_0 --- G20_0 --- G30_2
... G40_0 ... C20_0 ... B30_2 ... C40_0

![](img/f29bba55de4872c43f26af4667e705f2_201_0.png)

FIGURE 10.13 Results of the proposed method in different parameters $\gamma$. (a) Change of OA and (b) stability comparisons of std.

Resultant Comparisons of Different Methods Additionally, several existing methods are also conducted as follows:

- RTD + MLP: Raw-domain data (RTD) as input to MLP, and the layer sizes of MLP are set to [1280→128→5 or 9].
- Backpropagation (BP): Using 29 time- and frequency-domain features (TFFs) extracted, i.e., mean value, kurtosis, skewness, maximum value, peak-peak value, variance, mean frequency, and BP neural network classifier with the layer size of [29→12→5 or 9].
- Learning vector vector quantization (LVQ): Using the LVQ method and the above 29 TFFs to realize fault diagnosis.
- SVM: Using the above TFFs and SVM classifier with radial basis function (RBF) kernel to complete the fault diagnosis.
- Probabilistic neural network (PNN): Utilizing the above 29 TFFs and PNN to realize fault diagnosis.

# 192 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

f. Wavelet network (WNN): Using the above TFFs and WNN with the structure of [29→20→5 or 9].

g. WPT + MLP: Combining node WPT with MLP for fault diagnosis, i.e., 256 energy features are used as the input of MLP, 8-decompositions of WPT, which has two hidden layers set to [32→64].

h. WPT + CNN: Using 256 energy features which are reshaped to 16 × 16 size of feature matrix as the input of CNN for realizing fault diagnosis

i. RTD + DNN: RTD as input to DNN, and the layer sizes of DNN are set to [1280→800→512→128→64→5 or 9].

j. SET + CNN: Using a CNN with the same structure in Figure 10.3 and SET technique to realize fault diagnosis of the planetary gearbox. In the training of DNN, MLP, and CNN, the training epoch is 100 and the optimizer is as described in Section IV. The early stopping mechanism (monitor = "val_acc", patience = 10) is set in the early methods. Moreover, in the same datasets, results of several DL methods exist in studies (Shao et al. 2018; Zhao et al. 2017), as stacked auto-encoder (SAE-DNN), RNN, LGRU, combined CWT with deep learning (DTL) are also listed. These are shown in Table 10.2.

| TABLE 10.2 Comparisons of Different Methods (OA %) |
| Method | Bearing Dataset | Gear Dataset | Bearing Dataset | AVG |
| :--- | :--- | :--- | :--- | :--- |
| | 20Hz | 30Hz | 400Hz | 20Hz | 30Hz | 400Hz | 20Hz | 30Hz | 40Hz |
| RTD + MLP | 88.4 | 82.64 | 83.4 | 70.88 | 72.53 | 80.42 |
| BP | 99.24 | 99.90 | 86.96 | 84.60 | 83.70 | 86.16 | 81.91 | 89.79 |
| LVQ | 96.38 | 98.88 | 92.18 | 79.76 | 77.54 | 79.60 | 81.50 | 84.78 |
| SVM | 99.76 | 99.90 | 87.40 | 83.14 | 83.44 | 82.69 | 88.89 | 84.42 |
| PNN | 97.74 | 99.68 | 92.60 | 85.50 | 80.30 | 87.70 | 82.75 | 82.93 |
| WNN | 99.14 | 99.40 | 92.58 | 87.74 | 88.12 | 82.71 | 87.63 | 82.58 |
| WPT + MLP | 99.58 | 99.68 | 93.38 | 95.52 | 97.80 | 96.03 | 97.73 | 97.67 |
| RTD + DNN | 96.89 | 91.91 | 83.57 | 92.20 | 92.44 | 87.13 | 90.69 |
| SAE + DNN | 87.5 | 92.1 | 92.7 | 91.9 | | 91.05 |
| RNN | | 92.9 | 82.64 | 93.3 | | 91.63 |
| GRU | | 91.2 | 92.4 | 93.8 | 90.5 | | 91.98 |
| BGRU | | 93.0 | 94.6 | 93.8 | 90.7 | | 92.78 |
| LGRU | | 93.2 | 94.0 | 94.8 | 95.8 | | 94.45 |
| CNN + WPT | 99.20 | 99.22 | 98.82 | 94.82 | 97.70 | 95.71 | 97.94 | 97.03 |
| LfsCNN | 99.80 | 98.84 | 98.70 | 94.14 | 98.07 | 96.40 | 97.51 |
| CWT + DTL | 99.44 | 99.42 | 99.64 | 99.02 | 99.82 | 99.31 | 99.53 |
| SET + CNN | 99.82 | 99.80 | 99.19 | 99.21 | 99.13 | 99.63 | 99.39 | 99.35 |
| This chapter | 100 | 100 | 99.94 | 99.94 | 99.92 | 100 | 99.95 | 99.99 | 99.90 | 99.95 |

![](img/f29bba55de4872c43f26af4667e705f2_202_0.png)

# Reinforcement Learning for Intelligent Fault Diagnosis — 193

![](img/f29bba55de4872c43f26af4667e705f2_203_0.png)

FIGURE 10.14 AVG comparisons of different methods on multiple datasets.

From Table 10.2, it can be found that these methods using feature extraction have better accuracy than the ML-based method that uses raw data as input. In contrast to traditional ML-based fault diagnosis methods, such as BP, SVM, LVQ, BP, PNN, MLP, and WNN, DL-based methods without handcrafted features all have better fault diagnostic performance. Beside, these methods combining TFA with DL can realize the diagnostic OA of over 90% on multiple datasets. It further proves the advantages of DL in the fault diagnosis of the planetary gearbox. Especially, these three methods, namely CWT + DTL (Shao et al. 2018), SET + CNN, and the proposed method, have more remarkable diagnostic performance.

Compared with others, it can be found that the methods integrating SET and DL or DRL have better diagnostic effectiveness. In the nine subtasks of the single-load case, the OA of the proposed method is 100%, 99.94%, 99.94%, 99.92%, 100%, 99.95%, 99.89%, and 99.90%, Respectively. Especially, in the G30-2 dataset, the overall recognition rate of the proposed method rises 0.9% and 0.79% with CWT + DTL and SET + CNN, respectively. Compared with CNN + SET, the average (AVG) for OA of the proposed method in nine subtasks moves over 0.5%.

# Results and Analysis in Multi-Work Conditions

To further evaluate the performance of this method in more complex situations, experiments are carried out in multi-work conditions. The dataset setting and result analysis are as follows.

Dataset Setting Eight tasks in multi-work conditions are carried out. Except for datasets D and H, each subtask contains at least two single speed-load cases, where each single-load
