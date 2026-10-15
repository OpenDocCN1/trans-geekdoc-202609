
我们使用 PyTorch 库 `[204](#refbib.xhtml#refbib204)` 开发了我们的框架，并在两块 Nvidia GeForce RTX 2080 Ti GPU 上运行。我们在 MNIST `[118](#refbib.xhtml#refbib118)` 和 Fashion-MNIST `[284](#refbib.xhtml#refbib284)` 数据集上进行了测试。两个数据集均包含 60,000 个训练样本和 10,000 个测试样本。MNIST 是手写数字的集合，而 Fashion-MNIST 是灰度服装产品的集合。每个训练 epoch 结束后进行一次测试。每个 epoch 开始时，训练样本会随机打乱，而测试样本则保持相同的顺序。准确率是通过取 5 次训练运行的平均值来计算的。每个训练运行持续 30 个 epoch，每个策略的设置与 `[Section 3.1.4.1](#chapter3.xhtml#sec3_1_4_1)` 中描述的相同。结果如 `[Table 3.2](#chapter3.xhtml#tbl3_2)` 和 `[Figure 3.5](#chapter3.xhtml#fig3_5)` 所示。

`[Table 3.2:](#chapter3.xhtml#b3tbl3_2)` 使用 CapsNet 对 MNIST 和 Fashion-MNIST 数据集进行不同提出的解决方案时的准确率结果。

| 准确率 | | 达到最高准确率的 epoch 数 | 参数 | 权重共享 |
| --- | --- | --- | --- | --- |
| *FashionMNIST* | *MNIST* | *FashionMNIST* | *MNIST* |
| 90.99% | 99.37% | 17 | 29 | Fixed (Baseline) | No |
| --- | --- | --- | --- | --- |
| 91.47% | 99.45% | 27 | 8 | WAB | No |
| 90.47% | 99.26% | 17 | 26 | Fixed (Baseline) | Yes |
| 90.67% | 99.38% | 20 | 11 | WAB | Yes |

![Figure 3.5: The legend is common for all the figures. (a,b) Comparison of different optimization types integrated in our FasTrCaps framework, on the basis of accuracy, training time and number of parameters. The training time is computed as the number of epochs to reach the maximum accuracy, multiplied by time (in seconds) per epoch. The abbreviated terms WAB and WS stand for WarmAdaBatch and WeightSharing, respectively, with WeightSharing including also the small-decoder optimization. (c,d) Accuracy improvements / changes over the training epochs for different optimization solutions. (a,c) Results for MNIST. (b,d) Results for Fashion-MNIST.](images/fig3_5.jpg)

[Figure 3.5:](#chapter3.xhtml#b3fig3_5) *The legend is common for all the figures.* **(a,b)** Comparison of different optimization types integrated in our *FasTrCaps* framework, on the basis of accuracy, training time and number of parameters. The training time is computed as the number of epochs to reach the maximum accuracy, multiplied by time (in seconds) per epoch. The abbreviated terms WAB and WS stand for *WarmAdaBatch* and *WeightSharing*, respectively, with *WeightSharing* including also the small-decoder optimization. **(c,d)** Accuracy improvements / changes over the training epochs for different optimization solutions. **(a,c)** Results for MNIST. **(b,d)** Results for Fashion-MNIST.

#### 3.1.5.2 Accuracy Results for the MNIST dataset

**Evaluating Learning Rate Policies**: Among the state-of-the-art learning policies that we enhanced for CapsNets, the *warm restarts* are the most promising one, as the maximum accuracy improved by 0.074%. The CapsNet with *warm restarts* reaches the maximum accuracy of the baseline (with fixed learning rate) in 6 epochs rather than in 29 epochs as required by the baseline, thereby providing a training time reduction of 62.07%.

**Evaluating Adaptive Batch Size**: Different combinations of batch sizes in *adaptive batch size* algorithm have been tested since the smaller the batch size is, the faster the initial convergence. However, large batch sizes lead to slightly higher accuracy after 30 epochs and, most importantly, to a reduced training time. A CapsNet training epoch with batch size 1 lasts for 7 minutes, while with batch size 128, it lasts for only 28 seconds. Batch size 16 is a good tradeoff between fast convergence and short training time (i.e., 49 sec/epoch). The best results, applying *adaptive batch size*, are obtained using batch size 1 for the first three epochs and then increasing it to 16 for the remaining part of the training. With this parameter selection, the accuracy increases by 0.04% w.r.t. the baseline and the maximum baseline accuracy is reached in 5 epochs instead of 29 epochs as required by the baseline. However, the first three epochs take a longer time (88% longer) because of the reduced batch size. Hence, the *adaptive batch size* alone is not convenient. However, the total training time is reduced by 30% compared to the baseline.

**Evaluating WarmAdaBatch**: As for the batch, the first cycle of the learning rate lasts for 3 epochs and the second one for 27 epochs. Variations of batch size and learning rate cycles are synchronized. This solution allows a 0.088% gain in accuracy compared to the baseline CapsNet implementation, and the baseline maximum accuracy is reached by the CapsNet with the *WarmAdaBatch* in 3 epochs against 29 epochs. After the first three epochs, the batch size changes, and the learning rate is restarted. Hence, there is a drop in accuracy, which re-converges to the highest and most stable value in a few steps.

**Evaluating Weight Sharing**: By applying *weight sharing* to the ClassCaps layer, we can achieve a 15% reduction in the number of total parameters, decreasing from 8.2 million to 6.7 million. However, these reductions also lead to a slight decrease in the maximum accuracy, i.e., by 0.26%.

#### 3.1.5.3 Comparison of Different Optimization Types

On the CapsNet model with the MNIST dataset, we also compare the different types of optimizations in terms of accuracy and based on the training time to reach the maximum accuracy and the number of parameters. As we can see in `[Figure 3.5a](#chapter3.xhtml#fig3_5)`, we compare different optimization methods in a 3-dimensional space. This representation provides the Pareto-optimal solutions, depending on the optimization goals. We also compare, in `[Figure 3.5c](#chapter3.xhtml#fig3_5)`, the accuracy and the learning rate evolution in different epochs, for *AdaBatch, WarmRestarts* and *WarmAdaBatch*. Among the space of the potential solutions, we discuss the following two Pareto-optimal choices in detail, i.e., the *WarmAdaBatch* and the combination of *WarmAdaBatch* and *weight sharing*, which we call WAB+WS.

**WarmAdaBatch**: This solution provides the optimal point in terms of accuracy and training time because it achieves the highest accuracy (99.45%) in the shortest time (3 epochs). Varying the batch size boosts the accuracy in the first epoch, and the restart policy accelerates the training.

**WAB+WS**: The standalone *weight sharing* reduces the number of parameters by 15%. By combining it with *WarmAdaBatch*, the accuracy loss is compensated (99.38% vs. 99.37% of the baseline). At the same time, the training time is shorter than the baseline (18 epochs vs. 29 epochs) but longer than the simple *WarmAdaBatch*. Our framework chooses this solution if the parameter reduction is also included in the optimization goals.

#### 3.1.5.4 Accuracy Results for Fashion-MNIST

The results for the Fashion-MNIST dataset are shown in `[Table 3.2](#chapter3.xhtml#tbl3_2)` and `[Figure 3.5b](#chapter3.xhtml#fig3_5)`, `[d](#chapter3.xhtml#fig3_5)`. However, while the combination WAB+WS is the most effective policy for reducing the network parameters while keeping a relatively high accuracy, the WAB policy, the ExpDecay policy, and the One-Cycle-Policy show good accuracy and training time results. The WAB policy can keep the same training time as the best policies but at the cost of a slight accuracy loss. Hence, even though Fashion-MNIST and MNIST require an equivalent CapsNet architecture (i.e., without any changes), our WAB policy for Fashion-MNIST is comparable to other learning policies.

### 3.1.6 Summary
