
### Robustness results against affine transformations 的结果。

| 网络 | MNIST40 | GTSRB | CIFAR10 | AffNIST | AffGTSRB | AffCIFAR |
| --- | --- | --- | --- | --- | --- | --- |
| DeepCaps without dynamic routing | `**99.27%**` | `**96.27%**` | 91.47% | 87.72% | `**84.54%**` | `**79.86%**` |
| --- | --- | --- | --- | --- | --- | --- |
| DeepCaps with dynamic routing | 99.19% | 95.29% | `**91.52%**` | 87.60% | 84.14% | 78.66% |
| DeepCaps with self routing | 99.25% | 95.60% | 90.5% | `**88.15%**` | 83.17% | 77.37% |

We can derive that the dynamic routing in CapsNets does not contribute significantly to the robustness against affine transformations. Indeed, it makes the DeepCaps much computationally heavier. The functionality of dynamic routing is to inhibit the propagation of the activation vectors with lower contribution by lowering the values of the coupling coefficients in such connections. Instead, the transformation matrix learns the relationship between objects during the training. It could wrongly recognize some relationships between the inputs and a wrong output label, which the dynamic routing amplifies, together with the correct agreements. As a consequence, it increases the prediction confidence of the incorrect label.

#### 4.1.6.2 Adversarial Attacks

The comparison analysis for the PGD attack applied to the MNIST, GTSRB, and CIFAR10 datasets are shown in Figure 4.7a, b, and c, respectively.

![Figure 4.7: PGD results: comparison of the DeepCaps response for (a) MNIST, (b) GTSRB, and (c) CIFAR10 datasets.](img/fig4_7.jpg)

Figure 4.7: PGD results: comparison of the DeepCaps response for **(a)** MNIST, **(b)** GTSRB, and **(c)** CIFAR10 datasets.

For the MNIST dataset, the DeepCaps with dynamic routing is slightly more robust than the version without it. On the contrary, for the CIFAR10, the accuracy of the DeepCaps without dynamic routing decreases faster when increasing the perturbation *ε*. We can conclude that increasing the complexity of the dataset, from MNIST toward the CIFAR10, the dynamic routing does not improve the classification capability when the input starts to be perturbed.

Table 4.5 shows the results of the CW attack. The self-routing seems to confer robustness with such an attack, even if the architecture with dynamic routing is outperformed by the one without it. Since the fooling rate is lower and the mean distortion is higher without dynamic routing, we can derive that the dynamic routing does not improve the robustness against such an attack. It confirms that dynamic routing does not contribute much to the generalization.

Table 4.5: Robustness results against the CW attack.

|  | MNIST | GTSRB | CIFAR10 |
| --- | --- | --- | --- |
| Network | Mean Distortion | Fooling Rate | Mean Distortion | Fooling Rate | Mean Distortion | Fooling Rate |
| DeepCaps with dynamic routing | 1.24 | 86.8% | 1.16 | 98.8% | 0.34 | 100% |
| --- | --- | --- | --- | --- | --- | --- |
| DeepCaps without dynamic routing | 1.62 | 74.0% | 1.27 | 84.11% | 0.46 | 100% |
| DeepCaps with self routing | **2.28** | **48.6**% | 1.02 | **54.4**% | **0.52** | **99.2**% |

### 4.1.7 Summary

The proposed RobCaps methodology systematically studies the robustness of advanced DNN models, such as CNNs and CapsNets, against adversarial attacks and affine transformations. To evaluate the robustness against affine transformations, a methodology to generate the image transformation is proposed. The evaluations indicate that the DeepCaps model exhibits higher robustness than a similar-size CNN and the ResNet20 model. This observation is noticed since the DeepCaps shows higher accuracy than other DNN models in the presence of affine transformations and adversarial attacks. Such higher robustness is also obtained when adversarial training is employed. In this section, the robustness against existing adversarial attack algorithms has been studied, while the following Section 4.2 and Section 4.3 investigate the robustness against new adversarial attack methodologies.

## 4.2 Capsattacks: a Study on the Security Vulnerabilities of Capsnets Against Adversarial Attacks

A large body of work has investigated adversarial examples for CNNs, but their effectiveness on CapsNets has not yet been investigated systematically. In our work, we study the vulnerabilities in CapsNets to adversarial attacks. These perturbations, added to the inputs, are small and imperceptible to humans but can fool the network into mispredicting. We propose a greedy algorithm to generate imperceptible adversarial examples in a black-box attack scenario automatically. We show that this attack applied to the GTSRB and CIFAR10 datasets misleads CapsNets in making a correct classification. This outcome can be catastrophic for smart CPS, like autonomous vehicles. Moreover, we apply the same adversarial attacks to a 5-layer CNN (LeNet), a 9-layer CNN (VGGNet), and a 20-layer CNN (ResNet). We analyze the outcome compared to the CapsNets, to study their different behaviors under adversarial attacks.

### 4.2.1 System Overview

In this section, we aim to address the following **key research questions:**

1. Is a CapsNet vulnerable to adversarial examples? If yes, how, why, and to what extent?

2. How does the CapsNets’ vulnerability to adversarial attacks differ from that of the traditional CNNs?

Studying the vulnerability of the CapsNet to such adversarial attacks for the GTSRB dataset is crucial for autonomous vehicle use cases. Moreover, to our knowledge, we are the first to automatically generate an attack image for such CapsNet in a black-box scenario. We compare the CapsNet robustness with the CNNs with 5 and 9 layers, and the DeepCaps robustness with a 20-layer ResNet.

*In a nutshell, our Novel Contributions are:*

1. We develop a **novel algorithm to generate targeted imperceptible and robust adversarial examples automatically**.

2. We **analyze the robustness** behavior of the CapsNet, the DeepCaps, a 5-layer CNN (LeNet), a 9-layer CNN (VGGNet), and a 20-layer CNN (ResNet), under **adversarial attacks** applied to the input images of the CIFAR10 and GTSRB datasets, and study their differences.

3. We **compare the robustness** of the CapsNets with traditional CNNs, under the **adversarial examples** generated by our algorithm.

In summary, our results show that the CapsNet has comparable robustness to a much deeper CNN like the VGGNet, while the LeNet is much more vulnerable to adversarial attacks, while the DeepCaps is more robust than the ResNet. Therefore, a fundamental step forward for the security of safety-critical applications can be done by employing deep and complex networks such as the DeepCaps.

### 4.2.2 Generation of Targeted Imperceptible and Robust Adversarial Examples

An efficient adversarial attack can generate *imperceptible* and *robust* examples to fool the network. Before discussing the details of our algorithm, we describe the importance of these two aspects.

#### 4.2.2.1 Imperceptibility and Robustness

- [对抗性示例](https://example.org)通常被认为是`imperceptible`的，如果原始样本的修改非常小，以至于人类无法察觉，或者仅仅是很难被识别。为了创建对抗性示例，我们需要在图像中像素的标准差最高的位置添加扰动。在高方差区域添加的扰动不易被注意，比在低方差像素上应用的扰动更难检测。对于一个由`M` · `N`像素`x`组成的区域，像素`x[i, j]`的标准差（`SD`，方程（4.1））可以表示为平方根的形式，其中`μ`是`M` · `N`像素的平均值：

$$\begin{array}{l} {SD(x\_{i,j}) = \\sqrt{\\frac{\\sum\\limits\_{k = 1}^{M}\\sum\\limits\_{l = 1}^{N}(x\_{k,l} - \\mu)^{2} - (x\_{i,j} - \\mu)^{2}}{M \\cdot N}}} \\\\ \\end{array}$$

(4.1)

因此，如果像素位于高方差区域，其标准差较高，检测该像素修改的概率较低。为了量化不可感知性，我们定义原始样本`X`与对抗样本`X*`之间的距离（`D`，方程（4.2）），其中`δ[i, j]`是对像素`x[i, j]`添加的扰动：

$$\begin{array}{l} {D(X^{\\ast},X) = \\sum\\limits\_{i = 1}^{M}\\sum\\limits\_{j = 1}^{N}\\frac{\\delta\_{i,j}}{SD(x\_{i,j})}} \\\\ \\end{array}$$

(4.2)

该值表示在考虑范围内所有像素上添加的总扰动量。我们定义`D[M**A**X]`为人眼能容忍的最大总扰动。`D[M**A**X]`的值可能因数据集或图像而异，因为它取决于分辨率和相邻像素的对比度。

对抗性示例通常被称为`robust`，如果差距函数（即目标类概率与最大类概率之间的差距，见方程（4.3））得到最大化：

$$\\begin{array}{l} {GAP = P(\\text{target class}) - \\max\\{ P(\\text{other classes})\\}} \\\\ \\end{array}$$

(4.3)

当差距函数值更高时，对抗性示例更具鲁棒性，因为图像变换（如缩放或压缩）导致的概率变化不易影响分类。也就是说，如果差距很高，概率的微小变化不足以导致误分类。

#### 4.2.2.2 对抗性示例的生成

同时实现不可感知性和鲁棒性是一件复杂的事。通常，鲁棒攻击需要可感知的输入改动，而不可感知攻击对分类影响不大。我们提出了一种在黑盒场景下自动生成目标不可感知且鲁棒的对抗性示例的迭代方法，即攻击者仅拥有输入图像和输出概率向量，但**不**拥有网络模型。我们的攻击生成方法如图 4.8 所示 Figure 4.8。详情见 Algorithm 13。我们的方法目标是最大化差距函数（即*不可感知性*），直到原始示例与对抗示例之间的距离低于`D[M**A**X]`（即*鲁棒性*）。

![Figure 4.8: 我们的生成对抗性示例的方法论。](img/fig4_8.jpg)

Figure 4.8: 我们的生成对抗性示例的方法论。

![](img/comp04_1.jpg)

#### 4.2.2.3 攻击方法讨论

该算法假设每个像素包含三个不同的值，因为图像基于三个通道（红、绿、蓝：RGB）。与 145 中提出的算法相比，我们的攻击在每次迭代中针对标准差最高的像素集合进行扰动，从而实现不可感知的噪声。此外，**我们的算法会自动判断根据两个参数`GA P(+)`和`GA P(-)`的值，是否更有效地通过添加或减去噪声来最大化差距**，从而提升攻击的不可感知性和鲁棒性。为便于说明，我们以更完整的形式给出了计算标准差的公式。

**我们的算法按以下步骤运行：**

1. 选取子集*P*，包含在`M` · `N`区域中每个 RGB 通道标准差最高的像素，使得其可能的修改难以被察觉。

2. 计算差距函数，即目标类概率与最大输出概率之差。

3. 对于*P*中的每个像素，计算`GA P(+)`和`GA P(-)`：这两个值分别表示在对该像素分别添加或减去一个扰动单位后的差距估计。根据这两个值，决定是否将噪声加或减更有效。对于*P*中的每个像素，我们取`GA P(+)`与`GA P(-)`中的最大值，以最大化两类概率之间的距离。

4. 对于*P*中的每个像素，计算**变化优先级**（Variation Priority），即差距差值与该像素标准差的乘积。该值反映了像素扰动的有效性。

5. 对每个通道，对*P*的变化优先级进行排序，并对最高的*V*值进行扰动。

6. 仅对总共`3 · P`的*V*值进行扰动。噪声的加减依据之前计算的`GA P(+)`与`GA P(-)`中较高的那个值来决定。

7. 当原始输入图像被替换为对抗示例后，下一次迭代开始。迭代在距离`D`超过`D[M**A**X]`时停止。

### 4.2.3 CapsAttack 方法的评估

#### 4.2.3.1 实验设置

为分析 GTSRB 数据集，我们采用了 CapsNet \[236\]。我们在 TensorFlow 中实现它，用于对 GTSRB 数据集进行图像分类，准确率为 97.6%。该数据集包含大小为 32 × 32 的图像，分为 34 799 张训练样本和 12 630 张测试样本，每个像素强度值范围为 0 到 1，类别数为 43。为评估，我们将 CapsNet 与 5 层 CNN（LeNet）\[118〕、训练 30 个时代的 9 层 CNN（VGGNet）\[276〕进行比较，它们在干净测试图像上的准确率分别为 91.3%和 97.7%。

为分析 CIFAR10 数据集，我们采用 DeepCaps 架构 \[220〕，该架构包含 18 层。我们在 TensorFlow 中实现它，其在 CIFAR10 数据集 \[112〕上的分类准确率为 91.52%。CIFAR10 数据集包含 50 000 张训练图像和 10 000 张测试图像，尺寸为 32 × 32，分为 10 类。我们将其与 20 层 ResNet \[84〕进行比较，ResNet 在干净测试图像上的准确率为 91.48%。

我们将前文所述的 Algorithm 13 方法应用于上述 CapsNet、DeepCaps、LeNet、VGGNet 和 ResNet。我们在两个不同的例子上进行测试，以验证算法的工作原理。我们设定`M` = `N` = 32，因为 GTSRB 和 CIFAR10 数据集均由 32 × 32 图像组成，`P` = 100，`V` = 20。`δ`等于所有像素中最大值的 10%。`D[M**A**X]`取决于输入图像像素的标准差，其值随每个例子而变化，因为`D(X^*, X)`在不同示例中并不以相同的方式增长。

- 我们在 GTSRB 数据集的两个不同示例上对 CapsNet 进行了测试，分别显示在 [Figure 4.9a（示例 1）和 Figure 4.9e（示例 2）。为了验证我们的方法是否独立于目标类的选择，我们区分了两种情况：]

![Figure 4.9: Images for the attack applied to the CapsNet: (a) Original input image of Example 1. (b) Image misclassified by the CapsNet at iteration 13 for Case I. (c) Image misclassified by the CapsNet at iteration 16 for Case I. (d) Image at iteration 12 for Case II. (e) Original input image for Example 2. (f) Image at iteration 5, applied to the CapsNet. (g) Image misclassified by the CapsNet at iteration 21.](img/fig4_9.jpg)

Figure 4.9: Images for the attack applied to the CapsNet: **(a)** Original input image of Example 1. **(b)** Image misclassified by the CapsNet at iteration 13 for Case I. **(c)** Image misclassified by the CapsNet at iteration 16 for Case I. **(d)** Image at iteration 12 for Case II. **(e)** Original input image for Example 2. **(f)** Image at iteration 5, applied to the CapsNet. **(g)** Image misclassified by the CapsNet at iteration 21.

1. **Case I:** the target class is the class relative to the second highest initial output probability.

2. **Case II:** the target class is the class relative to the fifth highest probability between all the initial output probabilities.

**By analyzing Case I and Case II, we can make the following key observations:**

1. The CapsNet classifies the input image shown in Figure 4.9a as “120 km/h speed limit” (S8) with a probability equal to 0.0370. For Case I, the target class is “Double curve” (S21) with a probability equal to 0.0297. After 13 iterations of our algorithm, the image (Figure 4.9b) is classified as “Double curve” with a probability equal to 0.0339. Hence, *the probability of the target class has overcome the initial one*, as shown in Figure 4.10a. At this step, the distance *D*(*X*^(\*), *X*) is equal to 434.20. By increasing the number of iterations, the robustness of the attack increases because the gap between the two probabilities increases, but also, the perceptibility of the noise becomes more evident. After the iteration 16, the distance grows above *D*[*M**A**X*] = 520. The sample is represented in Figure 4.9c. This analysis shows that there is a tradeoff between robustness and imperceptibility.

For Case II, the probability relative to the target class “Beware of ice/snow” (S30) is equal to 0.0249, as shown in Figure 4.10b. The gap between the maximum probability and the probability of the target class is higher than the gap in Case I. After 12 iterations, the network has not misclassified the image yet (Figure 4.9d). In Figure 4.10b, we can observe that the gap between the two classes has decreased, but not enough for a misclassification. However, at this iteration, the value of the distance overcomes *D*[*M**A**X*] = 520. In this case, we show that our algorithm would need more iterations to misclassify at the cost of slightly perceivable perturbations.

2. The CapsNet classifies the input image shown in Figure 4.9e as “Children crossing” (S28) with a probability equal to 0.042. The target class is “60 km/h speed limit” (S3) with a probability equal to 0.0331. After 5 iterations, the distance overcomes *D*[*M**A**X*] = 250, while the network has not misclassified the image yet (Figure 4.9f) because the probability of the target class does not overcome the initial maximum probability, as shown in Figure 4.10c. The misclassification appears at the iteration 21 (Figure 4.9g). However, the perturbation is highly perceivable. Therefore, if this noise perception is not acceptable, such a solution would be discarded by our methodology, and a new solution would be searched, for which an adaptation of the constraints may be required, or a different input image is captured in a real-world system (e.g., a new image at a different distance from the camera).

![Figure 4.10: CapsNet results for the GTSRB dataset: (a) Output probabilities of Example 1—Case I: blue bars represent the starting probabilities, orange bars the probabilities at the point of misclassification, and yellow bars at the D\_{MAX}. (b) Output probabilities of Example 1—Case II: blue bars represent the starting probabilities, and orange bars are the probabilities at the D\_{MAX}. (c) Output probabilities of Example 2: blue bars represent the starting probabilities, and orange bars the probabilities at the D\_{MAX}.](img/fig4_10.jpg)

Figure 4.10: CapsNet results for the GTSRB dataset: **(a)** Output probabilities of Example 1—Case I: blue bars represent the starting probabilities, orange bars the probabilities at the point of misclassification, and yellow bars at the *D*[*M**A**X*]. **(b)** Output probabilities of Example 1—Case II: blue bars represent the starting probabilities, and orange bars are the probabilities at the *D*[*M**A**X*]. **(c)** Output probabilities of Example 2: blue bars represent the starting probabilities, and orange bars the probabilities at the *D*[*M**A**X*].

#### 4.2.3.3 Our Methodology Applied to the VGGNet and the LeNet

To compare the robustness of the CapsNet and the 9-layer VGGNet, we choose to evaluate the previous two examples, which have been applied to the CapsNet. For Example 1, we consider only Case I as the benchmark because Case II shows a similar behavior. The VGGNet classifies the input images with different output probabilities compared to the ones obtained by the CapsNet. Therefore, our metric to evaluate the resistance of the VGGNet against our attack is based on the value of the gap at the same distance.

To compare the robustness of the CapsNet and the 5-layer LeNet, we consider only Example 1 (Figure 4.11a) because Example 2 (Figure 4.11d) is already classified incorrectly by the LeNet. Note that the image of Example 2 belongs to the subset of images that are correctly classified by the CapsNet and the VGGNet, but incorrectly by the LeNet. Applying our algorithm to the LeNet, we observe that it is more vulnerable than the CapsNet and the VGGNet.

![Figure 4.11: Images for the attack applied to the CNNs: (a) Original input image for Example 1. (b) Image at the iteration 3, applied to the VGGNet. (c) Image at the iteration 9, misclassified by the VGGNet. (d) Original input image for Example 2. (e) Image at the iteration 2, applied to the VGGNet. (f) Image at the iteration 6, misclassified by the LeNet. (g) Image at the iteration 13, misclassified by the LeNet.](img/fig4_11.jpg)

Figure 4.11: Images for the attack applied to the CNNs: **(a)** Original input image for Example 1. **(b)** Image at the iteration 3, applied to the VGGNet. **(c)** Image at the iteration 9, misclassified by the VGGNet. **(d)** Original input image for Example 2. **(e)** Image at the iteration 2, applied to the VGGNet. **(f)** Image at the iteration 6, misclassified by the LeNet. **(g)** Image at the iteration 13, misclassified by the LeNet.

**From our experiments, we make these key observations:**

1. VGGNet 将输入图像（`Figure 4.11a`）分类为“120 km/h 限速”（S8），概率为 0.976。目标类是“100 km/h 限速”（S7），概率为 0.021。经过 3 次迭代后，距离超过了 `*D*[*M**A**X*]` = 520，而 VGGNet 仍未误判该图像（`Figure 4.11b`）。因此，我们的算法在误导 VGGNet 之前需要进行更多迭代，因为两个初始概率差距很大，如 `Figure 4.12a` 所示。该情形在 9 次迭代后出现（`Figure 4.11c`），目标类的概率为 0.483。

2. VGGNet 将输入图像（`Figure 4.11d`）分类为“Children crossing”（S28），概率为 0.96。目标类是“Beware of ice/snow”（S30），概率为 0.023。经过 2 次迭代后，距离超过了 `*D*[*M**A**X*]` = 250，而 VGGNet 仍未误判该图像（`Figure 4.11e`）。与前例相同，这一情形是由于初始概率差距很大，如 `Figure 4.12b` 所示。我们还可以注意到，VGGNet 在迭代次数上比 CapsNet 达到 `*D*[*M**A**X*]` 所需的次数更少。

3. LeNet 将输入图像（`Figure 4.11d`）分类为“120 km/h 限速”（S8），概率为 0.672。目标类是“30 km/h 限速”（S1），概率为 0.178。经过 6 次迭代后，扰动使 LeNet 被误导，因为图像（`Figure 4.11f`）被分类为目标类，概率为 0.339。扰动在 13 次迭代后变得可感知（`Figure 4.11g`），此时距离超过了 `*D*[*M**A**X*]` = 520。

![Figure 4.12: CNNs results for the GTSRB dataset: (a) Output probabilities of Example 1 on the VGGNet: blue bars represent the starting probabilities, orange bars the probabilities at the point of misclassification, and yellow bars at the D\_{MAX}. (b) Output probabilities of Example 2 on the VGGNet: blue bars represent the starting probabilities and orange bars the probabilities at the D\_{MAX}. (c) Output probabilities of Example 1 on the LeNet: blue bars represent the starting probabilities, orange bars the probabilities at the point of misclassification, and yellow bars at the D\_{MAX}.](img/fig4_12.jpg)

Figure 4.12: CNNs results for the GTSRB dataset: **(a)** Output probabilities of Example 1 on the VGGNet: blue bars represent the starting probabilities, orange bars the probabilities at the point of misclassification, and yellow bars at the `*D*[*M**A**X*]`. **(b)** Output probabilities of Example 2 on the VGGNet: blue bars represent the starting probabilities and orange bars the probabilities at the `*D*[*M**A**X*]`. **(c)** Output probabilities of Example 1 on the LeNet: blue bars represent the starting probabilities, orange bars the probabilities at the point of misclassification, and yellow bars at the `*D*[*M**A**X*]`.

#### 4.2.3.4 Our Methodology Applied to the DeepCaps and ResNet20 on the CIFAR10 Dataset

We test the DeepCaps and ResNet on two different images of the CIFAR10 dataset, shown in `Figure 4.13a` (Example 3) and in `Figure 4.13d` (Example 4). Both analyses have been conducted by choosing the target class as the second highest probability between the initial output probabilities.

![Figure 4.13: Images for the attack applied to the DeepCaps and ResNet20: (a) Original input image for Example 3. (b) Image at the iteration 11, misclassified by the DeepCaps. (c) Image at the iteration 8, misclassified by the ResNet20. (d) Original input image for Example 4. (e) Image at the iteration 9, applied to the DeepCaps. (f) Image at the iteration 14, misclassified by the DeepCaps. (g) Image at the iteration 9, misclassified by the ResNet20.](img/fig4_13.jpg)

Figure 4.13: Images for the attack applied to the DeepCaps and ResNet20: **(a)** Original input image for Example 3. **(b)** Image at the iteration 11, misclassified by the DeepCaps. **(c)** Image at the iteration 8, misclassified by the ResNet20. **(d)** Original input image for Example 4. **(e)** Image at the iteration 9, applied to the DeepCaps. **(f)** Image at the iteration 14, misclassified by the DeepCaps. **(g)** Image at the iteration 9, misclassified by the ResNet20.

**The following key observations can be derived from our experiments:**

1. For Example 3, both the DeepCaps and the ResNet correctly classify the input image (`Figure 4.13a`) as “truck” (S9), and for both networks, the target class is “ship” (S8). As shown in `Figure 4.14a`, *the DeepCaps is fooled by the attack*. After 6 iterations of the attack, the image is classified as “ship” with a probability of 0.421. Increasing the number of iterations increases the gap between the probabilities, thus making the attack more robust. After 11 iterations, the distance has overcome `*D*[*M**A**X*]` = 520, and the adversarial example generated at this point is shown in `Figure 4.13b`. Similarly, *the attack also fools the ResNet*. After 5 iterations, it is classified as “ship” with a probability of 0.376. At the iteration 8 (see `Figure 4.13c`), the probability associated to the class “ship” is 0.433, while the distance has overcome `*D*[*M**A**X*]` = 520.

2. Example 4 (`Figure 4.13d`) is correctly classified as a “bird” by the DeepCaps, with a probability equal to 0.847. The second highest probability, which will be the attack's target class, is associated with the class “horse” (S7). After 9 iterations, the distance overcomes `*D*[*M**A**X*]` = 450, while the image shown in `Figure 4.13e` is still correctly classified as a “bird” by the DeepCaps with a probability equal to 0.524. The yellow bars in `Figure 4.14c` show that the image in `Figure 4.13f` is classified as a “horse” with a probability equal to 0.365, but the distance is way beyond `*D*[*M**A**X*]`. Hence, *only a perceptible noise can mislead the DeepCaps*.

3. The Example 4 (`Figure 4.13d`) is correctly classified as a “bird” by the ResNet, with a probability equal to 0.910. The target class is “deer” (S4). After 9 iterations, *the probability of the target class has overcome the initial one*. As shown in `Figure 4.14d`, the ResNet classifies the image in `Figure 4.13g` as a “deer” with a probability equal to 0.483. At this point, the distance has also reached `*D*[*M**A**X*]` = 450.

![Figure 4.14: CIFAR10 results: (a) Output probabilities of Example 3 on the DeepCaps: blue bars represent the starting probabilities, orange bars represent the probabilities at the point of misclassification, and yellow bars denote probabilities at the D\_{MAX}. (b) Output probabilities of Example 3 on the ResNet20: blue bars represent the starting probabilities, orange bars represent the probabilities at the point of misclassification, and yellow bars denote probabilities at the D\_{MAX}. (c) Output probabilities of Example 4 on the DeepCaps: blue bars represent the starting probabilities, orange bars denote the probabilities at the D\_{MAX}, and yellow bars represent the point of misclassification with D(X^{\\ast},X) > D\_{MAX}. (d) Output probabilities of Example 4 on the ResNet20: blue bars represent the starting probabilities, orange bars denote the probabilities at the point of misclassification, which coincides with the D\_{MAX}.](img/fig4_14.jpg)

Figure 4.14: CIFAR10 结果：**(a)** 在 DeepCaps 上对示例 3 的输出概率：蓝色条表示起始概率，橙色条表示误判时的概率，黄色条表示在 *D*[*M**A**X*] 时的概率。**(b)** 在 ResNet20 上对示例 3 的输出概率：蓝色条表示起始概率，橙色条表示误判时的概率，黄色条表示在 *D*[*M**A**X*] 时的概率。**(c)** 在 DeepCaps 上对示例 4 的输出概率：蓝色条表示起始概率，橙色条表示在 *D*[*M**A**X*] 时的概率，黄色条表示误判点且 *D*(*X*^(\*), *X*) > *D*[*M**A**X*]。**(d)** 在 ResNet20 上对示例 4 的输出概率：蓝色条表示起始概率，橙色条表示误判时的概率，该概率与 *D*[*M**A**X*] 相同。

#### 4.2.3.5 CapsNet 与 CNN 的攻击脆弱性比较

从我们的分析可以看出，9 层 VGGNet 对我们的对抗攻击的脆弱性略低于 CapsNet，因为后者需要更明显的扰动才能被欺骗。我们的观察在 Figure 4.15 中得到验证，其中 *D*(*X*^(\*), *X*) 的值对 VGGNet 的上升更陡峭，而 CapsNet 的上升相对平缓。因此，图像中感知的噪声可以通过 *D*(*X*^(\*), *X*) 除以迭代次数来衡量。请注意，VGGNet 的噪声在几次迭代后即可被感知。此外，我们还可以看到目标类的选择在攻击成功率中起关键作用。

![Figure 4.15: D(X^{\\ast},X) 行为 (a) 示例 1，和 (b) 示例 2。](img/fig4_15.jpg)

Figure 4.15: *D*(*X*^(\*), *X*) 行为 **(a)** 示例 1，和 **(b)** 示例 2。

我们还注意到其他特征导致 VGGNet 与 CapsNet 之间的差异。VGGNet 更深，参数数量更多，而 CapsNet 可以在更小的模型规模下实现相似的准确率。这种差异导致两个网络在预测置信度上存在差距。虽然 CapsNet 的学习能力远高于 VGGNet，但这种差异并未体现在预测置信度上。事实上，对比 Figure 4.10 和 Figure 4.12 可以发现，CapsNet 的输出概率彼此非常接近，甚至比 LeNet 还要接近。然而，扰动对 CapsNet 的输出概率影响不如对 CNN 的影响显著。尽管 LeNet 的深度和参数数量与 CapsNet 相似，它仍然比 CapsNet 更易受攻击。

通过比较 DeepCaps 与 ResNet20，我们可以看到，尽管 ResNet 的置信度略高，但 DeepCaps 对这些扰动的鲁棒性更强。例如，如在 Figure 4.14 中观察到的，运行 9 次攻击后对示例 4，ResNet 被欺骗，而 DeepCaps 仍然正确分类。

### 4.2.4 总结

本节介绍了提出的 CapsAttacks 方法，用于生成目标性、imperceptible（ imperceptible）且 robust（ robust）的对抗示例。该过程是一个迭代程序，在黑盒场景下对图像进行扰动。评估在多种 CNN 和 CapsNet 模型上进行，并详细分析了不同攻击迭代之间的输出概率变化。与之前 Section 4.1 的观察保持一致，CapsNet 表现出比 CNN 更高的对抗鲁棒性。特别是，DeepCaps 的鲁棒性优于 ResNet20。后续对 CNN 与 CapsNet 的鲁棒性比较将在 Section 4.3 中讨论。

### 4.3 Fakeweather：用于模拟摄像头镜头天气条件的 Dnns 对抗攻击

近年来，DNN 在许多应用中取得了显著成果，但一些研究表明它们易受恶意攻击的影响。本节我们模拟自然天气条件的效果，以引入合理的扰动，误导 DNN。通过观察这些天气扰动对相机的影响，我们将这些模式建模为不同的面具，模拟雨、雪、雹等大气条件。虽然我们的攻击注入的扰动是可见的，但由于其与自然事件的关联，人眼往往忽视其存在。我们在多种 CNN 和 CapsNet 模型上测试了拟议的 *fakeWeather* 攻击，并报告了当这些对抗扰动应用时会出现显著的准确率下降。本文提出了一种新的 DNN 安全威胁，尤其对安全关键应用和自主系统来说尤为严重。

### 4.3.1 系统概览

对抗攻击的核心目标及其在实际应用中的可行性是：不被识别为对抗性，而是被视为自然/common。最直接的做法是注入极小幅度的扰动，使得清晰图像和对抗图像对人眼不可辨。然而，攻击者需要获取以下信息：DNN 模型结构和参数、输入与输出（即 *white-box* 设置），或仅输入与输出（即 *black-box* 设置）。即使是最先进的基于决策的黑盒攻击仍然需要获取每张图像的 DNN 预测类别。但实际上，获取这些信息可能很困难，因为 DNN 系统开发者通常会应用保护机制。另一个关键限制是，即使是最查询高效的算法 \[279\] 也需要进行一定数量的查询（即推理通道）来生成对抗扰动，这在实时约束严格的场景中可能不切实际，因为查询带来的延迟开销。

考虑到这些对抗攻击在注入不可感知扰动时的局限性，我们采用不同的策略。*我们的创新思想是将扰动引入输入图像，使其看起来像是摄像头捕获的自然场景，从而不被视为对抗性。* 即使清晰图像和对抗图像之间的差异可能被注意到，对抗图像也很难被归类为“对抗性”，因为它仅仅呈现一种可信的自然状态。原因在于传统的对抗机器学习评估的是对抗图像与原始图像的比较。但在实际场景中，我们无法获取原始图像，只能看到摄像头记录的图像。我们的方法相较于以往工作的优势在于它在所谓的 *true black-box setting*（真黑盒设置）中进行，即攻击者既没有关于 DNN 结构和参数的信息，也没有访问其输出，唯一需要的信息是输入图像的尺寸，以便生成相应大小的对抗面具。此外，我们的攻击算法不需要任何查询，因而可以在运行时轻松应用。

- [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**Richard Feynman**。

1. 运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。

```
