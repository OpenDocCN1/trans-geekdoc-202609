# Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

![](bbox=[0.126, 0.093, 0.873, 0.269])

![](bbox=[0.105, 0.287, 0.873, 0.606])

FIGURE 6.8 Multi-signal fault diagnosis with different DCNN architectures. (a) Architecture with multi-channel input, and (b) architecture with separate convolutional units and merged in the fully connected layer.

model. Training epoch is set as 30, and the batch size is set as 32. Accuracy and training loss are calculated to evaluate the performances of each architecture, and the fusion matrix is used to show the classification accuracy for each category. In order to investigate the model stability, results from 50 trials are recorded, as shown in Table 6.3 and Figure 6.9. The confusion matrix is shown in Figure 6.10. The classification results

# TABLE 6.3 Classification Results in Multi-signal Model

| Classification Accuracy Mean (Standard Deviation) | Computation Time |
|---|---|---||
| | Train | Test | Train | Test |
| Vibration | 100% (0.00) | 99.22 (0.26) | 135 s | 0.8 s |
| Current | 100% (0.00) | 99.83 (0.16) | 225 s | 0.9 s |