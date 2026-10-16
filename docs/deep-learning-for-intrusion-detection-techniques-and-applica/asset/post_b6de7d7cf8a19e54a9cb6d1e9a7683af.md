
![](img/a13b588839130d750aecd8a32b6143d9_130_0.png)

**Figure 4.4**  The pipeline of the general CNN architecture.

gradients based on the error. The learning process continues for a predefined number of iterations before it is halted.

CNNs have been widely utilized for intrusion detection. For example, Shen et al. [30] introduced a compressed CNN model named CSCNN for image classification. This model integrates compressive sensing theory into the input layer of CNN models, optimizing resource usage while enhancing accuracy. The evaluation, conducted using the MNIST and CIFAR-10 datasets, demonstrated improved training efficiency and classification accuracy. Similarly, Praanna et al. [31] developed a hybrid model combining CNN and LSTM algorithms, evaluated using the KDD99 dataset. The experimental results showed that this approach outperformed other models, including SVM, CNN, and DBN, achieving a 99.78% accuracy rate. Furthermore, Nguyen and Kim [32] proposed a novel NIDS based on a genetic algorithm (GA)-driven exhaustive search and fuzzy C-means clustering. This method identified the optimal CNN structure, referred to as the deep feature extractor, through GA-based optimization. The study concluded that implementing this approach in real-world internet networks could enhance security by detecting and categorizing malicious activities. However, a notable drawback of this method was the computational time required to execute the exhaustive GA-based search for selecting optimal features and CNN configurations.

Some of the commonly used CNN architectures are given in Table 4.1.

## 4.4.5 Recurrent Neural Networks

RNNs are a class of neural network models designed to process sequential data by maintaining a form of memory through cycles in their architecture. Unlike traditional feed-forward networks, RNNs process inputs one at a time while preserving contextual information from previous inputs, allowing them to model dependencies over time. A sequence of length *n* can be represented as (*x*¹, *x*², …, *x*ⁿ). As depicted in Figure 4.5, a standard RNN processes each element sequentially using a neural network block that receives not only the current element but also information from the preceding step. This enables information from earlier sequence positions to propagate through the entire sequence. Each block within an RNN is structurally identical, and an output y(i) can be generated at each step i, though this is not a requirement for all RNN models.

Table 4.1 Various CNN architectures.

| Architecture | Network depth | Remarks | No. of parameters |
|---|---|---|---|
| AlexNet [33] | 8 | Utilizes dropout for overfitting and ReLU | 60M |
| NIN [34] | 3 | Utilizes MLPConv layers to convolve the input and a global average pooling layer instead of fully connected layers | 2M |
| VGG-16 | 16 | Uses ReLU after every convolutional layer, which significantly cuts the training time | 138M |
| VGG-19 [35] | 19 | Uses ReLU after every convolutional layer, which significantly cuts the training time | 143M |
| ZFNet [36] | 8 | Visualization idea of intermediate feature layers and the operation of the classifier. | 6M |
| GoogLeNet [37] | 22 | Block concept, increased depth, concatenation concept, different filter size | 6M |
| Highway [38] | 19 | Makes use of gating functions to regulate the information flow. | 2.3M |
| Highway [38] | 32 | Makes use of gating functions to regulate the information flow. | 1.25M |
| ResNet50 [39] | 50 | Introduced the concept of skip connections that mitigates the problem of vanishing gradient by taking alternate shortcut path for gradient to flow | 25.6M |
| ResNet101 | 101 | Introduced the concept of skip connections that mitigates the problem of vanishing gradient by taking alternate shortcut path for gradient to flow | 44.7M |
| ResNet152 | 152 | Introduced the concept of skip connections that mitigates the problem of vanishing gradient by taking alternate shortcut path for gradient to flow | 60.4M |
| InceptionV3 [40] | 159 | The larger convolutions in the model are factorized into smaller convolutions. The auxiliary classifiers act as a regularizer and improve the convergence of model | 23.8M |
| InceptionResNetV2 [41] | 572 | Incorporates residual connections. Inception-Res-Net models were able to achieve higher accuracies at a lower epoch | 55.87M |
| Xception [42] | 126 | Replaces the standard inception modules with depth-wise separable convolutions | 22.9M |
| Residual attention network [43] | 452 | Utilizes multiple attention modules which generate attention-aware features. The attention-aware features change adaptively as layers go deeper | 8.6M |
| DenseNet121 [44] | 121 | Alleviate the vanishing-gradient problem | 8M |
| DenseNet169 | 169 | Alleviate the vanishing-gradient problem | 14.31M |
| DenseNet201 | 201 | Performs well when training data is insufficient | 20.2M |

![](img/a13b588839130d750aecd8a32b6143d9_132_0.png)

Figure 4.5 The architecture of traditional RNNs.

Historically, RNNs posed challenges in training due to their large number of parameters and issues such as the vanishing gradient problem. However, advancements in network architectures, optimization techniques, and computational capabilities have significantly improved their scalability. Two groundbreaking developments in 1997 shaped modern RNN architectures. The first, LSTM networks, introduced by Hochreiter and Schmidhuber [45], were specifically designed to mitigate the vanishing gradient issue, allowing them to learn long-term dependencies more effectively. LSTM networks incorporate gating mechanisms that regulate the retention and updating of information, making them particularly useful for detecting anomalies over extended timeframes. Unlike traditional RNNs, LSTM networks feature memory cells that replace standard artificial neurons in the hidden layer, improving their training stability.

The second major development, bidirectional recurrent neural networks (BRNNs), introduced by [46], allows information from both past and future inputs to influence the current output. This contrasts with conventional RNNs, which rely solely on past inputs, making BRNNs highly effective for sequence labeling tasks in fields such as natural language processing. Another significant variation of RNNs is Gated recurrent units (GRUs), which share LSTMs’ ability to model long-term dependencies but with reduced computational complexity. GRUs use a simplified gating mechanism, which lowers computational overhead while maintaining strong performance in tasks such as network traffic analysis.

Several studies have explored the application of RNNs for intrusion detection [47] applied a DL-based RNN approach to the NSL-KDD dataset to detect various network attacks. Their results demonstrated that RNN-based IDSs outperformed traditional classification models such as support vector machines (SVMs) and ANNs in both binary and multi-class classification. However, to improve efficiency, future research should focus on reducing training time using GPU acceleration.

Arshad et al. [48] proposed a payload classification technique for attack detection that leveraged PL-CNN and PL-RNN models. These methods enabled end-to-end detection by learning feature representations directly from raw payload data, eliminating the need for feature engineering. When evaluated on the DARPA1998 dataset, PL-CNN and PL-RNN achieved classification accuracies of 99.36% and 99.98%, respectively, with PL-RNN demonstrating superior performance across multiple datasets. However, these models presented two primary challenges: they contained a higher number of parameters than conventional ML models, making parameter tuning complex, and they lacked interpretability, complicating the understanding of their decision-making processes. A neural network was fed real-time data using the IDS technique in [49]. They employed an RNN model and a deep multilayer perceptron, which both benefit from an LSTM hidden layer for understanding the temporal context of various attacks including DDoS and command injection. They developed a mathematical model to calculate the ideal time for their model’s computation offloading based on the detection delay.

## 4.5 Conclusion

IDSs play a crucial role in securing modern IT-based organizations. However, developing an efficient and high-performance IDS capable of handling a diverse range of security threats remains a significant challenge. In recent years, DL techniques have emerged as a powerful solution for intrusion detection, leading to the development of various DL-based IDS models. As a specialized branch of ML, DL utilizes multiple layers to perform nonlinear processing and extract hierarchical data representations. These networks can process raw input data and support various learning approaches, including unsupervised, semi-supervised, and supervised methods. This chapter has reviewed different intrusion detection strategies and explored various DL algorithms employed for detecting security threats.

## References

1 Ziegler, S. (ed.) (2019). Internet of things cybersecurity paradigm shift, threat matrix and practical taxonomy. In: Internet of Things Security and Data Protection, 1–7. Springer.
