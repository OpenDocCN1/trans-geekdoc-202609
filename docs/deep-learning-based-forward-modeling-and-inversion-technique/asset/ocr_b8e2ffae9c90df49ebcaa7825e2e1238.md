Reconstruction of Thermophysical Parameters Based on Deep Learning 139

![](bbox=[0.297, 0.175, 0.702, 0.375])

FIGURE 4.22
The generalization of space-related thermal conductivity.

#  4.5.2.4 Generalization Ability

Generalization ability is a term which describe a DL model's capability to react to new data after being trained on a given training set. In other words, whether a model can digest new examples and make reasonable predictions.
As the samples in the curated dataset have different variation trends with temperature or related materials models, this part merely concentrates on the space-related cases. Here, 1000 specimens with completely diverse samples from the original data set are employed to assess the generalization ability. In order to simulate the inversion of practical products, the data contains specimens with discrete conductivity.
Although the proposed network tends to give predictions with smooth thermal conductivity at the interface which distinctly expands the error to some extent. Nevertheless, the average error is still 8.8%. Although it is larger than the previous results, it demonstrates strong generalization ability since there is huge difference between the two datasets.

Figure 4.22 demonstrates the inversions of the constructed data.

#  4.5.2.5 Computational Speed

A significant superiority in utilizing the proposed network to recover the thermal commodities is that it makes the best of the parallel computing capability of GPUs to refrain from tedious iterations, making it feasible to acquire the forecasting results in real-time. Here, the time cost of each sub-network to handle 100 samples are counted, as exhibited in Table 4.4.