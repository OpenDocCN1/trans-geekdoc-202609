flow data fine-tuned models because of the lack of the mouse surrounding environment in the optical-flow data.

And for the “rest” behaviors, it is easy to understand why using a high portion of optical-flow data fine-tuned models give better performance as “rest” behaviors are different from other behaviors that they have no movement in the scenes.

Overall, the two deep learning models we investigated in this research outperform the previous research model in the Mouse behavior dataset as shown in Table 2. The accuracies of the two models with different fusion ratio are shown in Figure 10. Both models have best performances at fusion ratio of 40% RGB data fine-tuned models and 60% optical-flow data fine-tuned models. The I3D model achieves 96.9% of accuracy and the R(2 + 1) D achieves 96.3% of accuracy.

# Table 2. Comparison of performance of models

| No | Model | Accuracy (%) |
| :--- | :--- | :--- |
| 1 | MF + SVMHMM [1] | 93.0 |
| 2 | FV + NN [4] | 95.9 |
| 3 | I3D | 96.9 |
| 4 | R(2 + 1)D | 96.3 |

![](bbox=[0.22, 0.535, 0.785, 0.855])

# Figure 10. Accuracies of I3D models and R(2 + 1)D models with different two-stream fusion ratios.