| Model | CNN Architecture | Acc | R | P | F1 | H-loss |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Proposed model** | **VGG16 and DenseNet121** | **1.00** | **1.00** | **1.00** | **1.00** | **0.00** |
| Majid et al. [52] | ResNet50 | 0.82 | 0.71 | 1.00 | 0.83 | 0.18 |
| Majid et al. [52] | VGG16 | 0.64 | 1.00 | 0.64 | 0.78 | 0.36 |
| Saeed et al. [53] | Adaboost-LBP | 1.00 | 1.00 | 1.00 | 1.00 | 0.00 |
| Muhammad et al. [54] | AlexNet | 0.64 | 1.00 | 0.64 | 0.78 | 0.36 |
| Khan et al. [55] | VGG16 | 0.64 | 1.00 | 0.64 | 0.78 | 0.36 |
| Wang et al. [56] | VGG16 | 0.98 | 1.00 | 0.98 | 0.99 | 0.02 |
| He et al. [57] | Residual learning | 0.95 | 0.95 | 0.97 | 0.96 | 0.05 |

| Model | CNN Architecture | Parameters |
| :--- | :--- | :--- |
| **Proposed CNN model** | **VGG16 and DenseNet121** | **10,553,346** |
| Majid et al. [52] | ResNet50 | 70,786 |
| Majid et al. [52] | VGG16 | 70,786 |
| Saeed et al. [53] | Adaboost-LBP | 171,110,274 |
| Muhammad et al. [54] | AlexNet | 171,110,274 |
| Khan et al. [55] | VGG16 | 72,142,146 |
| Wang et al. [56] | VGG16 | 8,237,442 |
| He et al. [57] | Residual learning | 4,194,690 |

the same reference image dataset. The proposed model used color maps as well as an image dataset. For comparing the proposed CNN model with Majid et al. [52], the attention layers of their model have been removed. These comparisons show that the propounded algorithm demonstrates better performance than the other existing models. It is observed that Table 10.1 depicts a satisfactory accuracy score of 1.00 for the proposed framework, while the model of Saeed et al. [53] also provides an accuracy score of 1.00 but requires more than 17 times the number of parameters as compared to the proposed model. This validates the applicability of the proposed framework.

In the last experiment, the performance of the proposed CNN model against various existing models is illustrated in Figures 10.6–10.8 in terms of learning and ROC curves. It can be seen that in case of learning curves for the proposed CNN model, the training and validation curves converge and coincide after only 4 epochs, while the other models either take more