# Approach

# Main Features

| Approach | Main Features |
|---|---|n| Data Augmentation | Reduces variance and acts as implicit regularization, more limited for tabular data than images. |
| L1/L2 Regularization | Reduces weight size by adding a penalty to the loss function, helping with model complexity and preventing overfitting. |
| Per-Weight Regularization | Allows regularization for each weight to reduce the impact of specific features and improve model interpretability. |
| Batch Normalization (BN) | Fixes the variance and magnitude of the inputs, helps generalization, and acts as implicit regularization. |
| Label Smoothing / Noise Injection | Helps in calibration and reduces noise by introducing noise into the training process. |
| Dropout | Randomly disables neurons during training to prevent overfitting and encourage sparse representations. |
| Sparsity Regularization | Encourages sparsity and feature selection through techniques like stochastic gates and prior knowledge. |
| Stochastic Depth | Extends depth by randomly dropping units or layers (e.g., residual blocks) to prevent overfitting. |
| Self-normalizing Neural Networks (SNNs) | Uses SelU (Scaled Exponential Linear Units) to maintain activations and allow self-normalization during training. |
| Early Stopping | Stops training when there is no further improvement, reducing training time and preventing overfitting underfitting if the curve is not smooth. |
| Entropy Regularization | Reduces variance and makes the model more responsive to events. |
| Harmonic Loss | Alternative to cross-entropy loss, designed to enhance performance and accelerate convergence discouraging overfitting. |
| Pretraining Strategies | Evaluates primitives, including self-selection and contrastive learning, to improve model performance and reduce overfitting. |
| Combination of Regularization Techniques | Using multiple techniques to increase model performance, and sometimes tree-based models. |

Table 5: Different examples of regularization approaches

ing tasks, particularly for high-dimensional challenges such as image classification and solving partial equations (PDEs) [203]. For the authors, ReLU and Sigmoid functions (often used in MLPs), the Cauchy activation focuses a localized, decaying property that allows it to better approximate local data and achieve greater accuracy (in comparison to MLP and KANs). This is particularly effective for tasks requiring fine-grained data representation and higher-order convergence (over which MLPs and KANs would be less effective, especially in high-dimensional scenarios). RealMLP [259] introduces an enhanced MLP for tabular data through parameter optimization, showing that different elements allow a synergistic boost of MLPs. In this work, we use one-hot encoding, scale features, categorical embedding, and specific embedding for numerical features, using a scaling layer, linear layers, and parameter by size), and SelU as an activation function. RealMLP shows to be competitive with GBDTs but higher computational cost compared with MLP. On the other

hand, has only been tested on a limited number of datasets. staTab [287] uses prior knowledge to inject sparsity into the neural network and a tabular attention mechanism to make networks more competitive, agile in training, and more interpretable. The attention mechanism allows the most important features to be extracted and stabilizes the training. In the case, if prior knowledge is not available, we use an algorithm to induce sparsity and define modality.
Fully differentiable models. Those that are differentiable with respect to all parameters. This is desirable because they allow end-to-end optimization by gradient descent for training and inference, which is possible for these models to be trained on GPUs. Neural Objective Machine [267] can be considered a generalization of CatBoost [271], where obvious decisions use the same splitting function for all nodes at the same layer. To be fully differentiable, NODE uses ents and soft functions, allowing it to be trained with back-

18