
like architectures such as Inception V2 or V3 which are far more complex to define. An open-source implementation of Xception using Keras and TensorFlow is provided as part of the Keras Applications module², under the MIT license.

## 4. Experimental evaluation

We choose to compare Xception to the Inception V3 architecture, due to their similarity of scale: Xception and Inception V3 have nearly the same number of parameters (table 3), and thus any performance gap could not be attributed to a difference in network capacity. We conduct our comparison on two image classification tasks: one is the well-known 1000-class single-label classification task on the ImageNet dataset [14], and the other is a 17,000-class multi-label classification task on the large-scale JFT dataset.

### 4.1. The JFT dataset

JFT is an internal Google dataset for large-scale image classification dataset, first introduced by Hinton et al. in [5], which comprises over 350 million high-resolution images annotated with labels from a set of 17,000 classes. To evaluate the performance of a model trained on JFT, we use an auxiliary dataset, FastEval14k.

FastEval14k is a dataset of 14,000 images with dense annotations from about 6,000 classes (36.5 labels per image on average). On this dataset we evaluate performance using Mean Average Precision for top 100 predictions (MAP@100), and we weigh the contribution of each class to MAP@100 with a score estimating how common (and therefore important) the class is among social media images. This evaluation procedure is meant to capture performance on frequently occurring labels from social media, which is crucial for production models at Google.

### 4.2. Optimization configuration

A different optimization configuration was used for ImageNet and JFT:

- On ImageNet:
  - Optimizer: SGD
  - Momentum: 0.9
  - Initial learning rate: 0.045
  - Learning rate decay: decay of rate 0.94 every 2 epochs

- On JFT:
  - Optimizer: RMSprop [22]
  - Momentum: 0.9
  - Initial learning rate: 0.001
  - Learning rate decay: decay of rate 0.9 every 3,000,000 samples

For both datasets, the same exact same optimization configuration was used for both Xception and Inception V3. Note that this configuration was tuned for best performance with Inception V3; we did not attempt to tune optimization hyperparameters for Xception. Since the networks have different training profiles (figure 6), this may be suboptimal, especially on the ImageNet dataset, on which the optimization configuration used had been carefully tuned for Inception V3.

Additionally, all models were evaluated using Polyak averaging [13] at inference time.

### 4.3. Regularization configuration

- Weight decay: The Inception V3 model uses a weight decay (L2 regularization) rate of 4e-5, which has been carefully tuned for performance on ImageNet. We found this rate to be quite suboptimal for Xception and instead settled for 1e-5. We did not perform an extensive search for the optimal weight decay rate. The same weight decay rates were used both for the ImageNet experiments and the JFT experiments.

- Dropout: For the ImageNet experiments, both models include a dropout layer of rate 0.5 before the logistic regression layer. For the JFT experiments, no dropout was included due to the large size of the dataset which made overfitting unlikely in any reasonable amount of time.

- Auxiliary loss tower: The Inception V3 architecture may optionally include an auxiliary tower which back-propagates the classification loss earlier in the network, serving as an additional regularization mechanism. For simplicity, we choose not to include this auxiliary tower in any of our models.

### 4.4. Training infrastructure

All networks were implemented using the TensorFlow framework [1] and trained on 60 NVIDIA K80 GPUs each. For the ImageNet experiments, we used data parallelism with synchronous gradient descent to achieve the best classification performance, while for JFT we used asynchronous gradient descent so as to speed up training. The ImageNet experiments took approximately 3 days each, while the JFT experiments took over one month each. The JFT models were not trained to full convergence, which would have taken over three months per experiment.

Figure 5. The Xception architecture: the data first goes through the entry flow, then through the middle flow which is repeated eight times, and finally through the exit flow. Note that all Convolution and SeparableConvolution layers are followed by batch normalization [7] (not included in the diagram). All SeparableConvolution layers use a depth multiplier of 1 (no depth expansion).

![](img/d2b50980707c5839cfd8800315c444b8_4_0.png)

## 4.5. Comparison with Inception V3

### 4.5.1 Classification performance

All evaluations were run with a single crop of the input images and a single model. ImageNet results are reported on the validation set rather than the test set (i.e. on the non-blacklisted images from the validation set of ILSVRC 2012). JFT results are reported after 30 million iterations (one month of training) rather than after full convergence. Results are provided in table 1 and table 2, as well as figure 6, figure 7, figure 8. On JFT, we tested both versions of our networks that did not include any fully-connected layers, and versions that included two fully-connected layers of 4096 units each before the logistic regression layer.

On ImageNet, Xception shows marginally better results than Inception V3. On JFT, Xception shows a 4.3% relative improvement on the FastEval14k MAP@100 metric. We also note that Xception outperforms ImageNet results reported by He et al. for ResNet-50, ResNet-101 and ResNet-

Table 1. Classification performance comparison on ImageNet (single crop, single model). VGG-16 and ResNet-152 numbers are only included as a reminder. The version of Inception V3 being benchmarked does not include the auxiliary tower.

| | Top-1 accuracy | Top-5 accuracy |
|---|---|---|
| VGG-16 | 0.715 | 0.901 |
| ResNet-152 | 0.770 | 0.933 |
| Inception V3 | 0.782 | 0.941 |
| Xception | **0.790** | **0.945** |

The Xception architecture shows a much larger performance improvement on the JFT dataset compared to the ImageNet dataset. We believe this may be due to the fact that Inception V3 was developed with a focus on ImageNet and may thus be by design over-fit to this specific task. On the other hand, neither architecture was tuned for JFT. It is likely that a search for better hyperparameters for Xception on ImageNet (in particular optimization parameters and reg-

| Model | FastEval14k MAP@100 |
|---|---|
| Inception V3 - no FC layers | 6.36 |
| Xception - no FC layers | 6.70 |
| Inception V3 with FC layers | 6.50 |
| Xception with FC layers | 6.78 |

![](img/d2b50980707c5839cfd8800315c444b8_5_0.png)

![](img/d2b50980707c5839cfd8800315c444b8_5_1.png)

V3 and Xception. Parameter count is reported on ImageNet (1000 classes, no fully-connected layers) and the number of training steps (gradient updates) per second is reported on ImageNet with 60 K80 GPUs running synchronous gradient descent. Both architectures have approximately the same size (within 3.5%), and Xception is marginally slower. We expect that engineering optimizations at the level of the depthwise convolution operations can make Xception faster than Inception V3 in the near future. The fact that both architectures have almost the same number of parameters indicates that the improvement seen on ImageNet and JFT does not come from added capacity but rather from a more efficient use of the model parameters.

![](img/d2b50980707c5839cfd8800315c444b8_5_2.png)

ularization parameters) would yield significant additional improvement.

### 4.5.2 Size and speed

| | Parameter count | Steps/second |
|---|---|---|
| Inception V3 | 23,626,728 | 31 |
| Xception | 22,855,952 | 28 |

In table 3 we compare the size and speed of Inception
