
![](img/fe161b7f6e96e35e7e853eece52c6dce_158_0.png)

FIGURE 3.9 This figure presents how we can use image-level weak annotations for domain adaptation in two different ways – either estimated, i.e., pseudo-weak labels (Unsupervised Domain Adaptation, UDA) or acquired from a human oracle (Weakly-supervised Domain Adaptation (WDA)).
图 3.9 本图展示了我们如何以两种不同的方式使用图像级弱标注进行域适应——要么是估计的，即伪弱标签（无监督域适应，UDA），要么是从人工 oracle 获取的（弱监督域适应，WDA）。

The weakly-supervised domain adaptation (WDA) paradigm as shown in Fig. 3.9. The target annotation cost in UDA is zero, and in the WDA case is very low, as we will see subsequently.
弱监督域适应（WDA）范式如图 3.9 所示。UDA 中目标标注成本为零，而在 WDA 情况下成本非常低，如后续将看到的那样。

The literature in domain adaptation for semantic segmentation models has been only around unsupervised methods (UDA), and it can be summarized under three categories – pixel-level adaptation (Hoffman et al., 2018; Murez et al., 2018; Wu et al., 2018), which aims at aligning the input image space, pseudo-label training (Zou et al., 2018; Sadat Saleh et al., 2018; Lian et al., 2019), which aims at labeling the unlabeled target data using the source model and using it for adaptation, and feature or output space adaptation (Tsai et al., 2018; Chen et al., 2018; Tsai et al., 2019; Du et al., 2019), which aims at aligning the output space between the source and target domains. The performance of these methods is quite low compared to methods with strong supervision. In the text below we present our method (Paul et al., 2020) which can be used for both unsupervised and weakly-supervised domain adaptation, and bridging the performance gap with minimal or no annotation cost. We start with the formal problem definition.
语义分割模型域适应的文献仅围绕无监督方法（UDA），可归纳为三类——像素级适应（Hoffman et al., 2018; Murez et al., 2018; Wu et al., 2018），旨在对齐输入图像空间，伪标签训练（Zou et al., 2018; Sadat Saleh et al., 2018; Lian et al., 2019），旨在使用源模型对未标注的目标数据进行标注并用于适应，以及特征或输出空间适应（Tsai et al., 2018; Chen et al., 2018; Tsai et al., 2019; Du et al., 2019），旨在对齐源域和目标域之间的输出空间。与强监督方法相比，这些方法的性能相当低。下面我们介绍我们的方法（Paul et al., 2020），该方法可用于无监督和弱监督域适应，并在最小或无标注成本的情况下弥合性能差距。我们从形式化问题定义开始。

## Problem definition
## 问题定义

We have two domains – source and target. The goal is to adapt a segmentation model learned on the source domain to the target domain. In the source domain, we have images and pixel-wise labels denoted as I_s = {X_s^i, Y_s^i}_{i=1}^{N_s}. Our target dataset contains images and only image-level labels as I_t = {X_t^i, y_t^i}_{i=1}^{N_t}. X_s, X_t ∈ ℝ^{H×W×3}, Y_s ∈ 𝔹^{H×W×C} are pixel-wise one-hot vectors, y_t ∈ 𝔹^C is a multihot vector representing the categories present in the image and C is the number of categories, for both the source and target datasets. Note that in a one-hot vector, only one of the element of the vector is 1, and remaining are zero, while in multihot vectors, multiple elements of the vector can be 1. Such image-level labels y_t are termed as weak labels, as they are a much weaker form of label compared to pixel-wise labels. We can either estimate them, in which case we call them pseudo-weak labels (Unsupervised Domain Adaptation, UDA), or acquire them from a human oracle and call them oracle-weak labels (Weakly-supervised Domain Adaptation, WDA). We will further discuss
我们有两个域——源域和目标域。目标是将在源域上学习到的分割模型自适应到目标域。在源域中，我们有图像和像素级标签表示为 I_s = {X_s^i, Y_s^i}_{i=1}^{N_s}。我们的目标数据集包含图像和仅图像级标签 I_t = {X_t^i, y_t^i}_{i=1}^{N_t}。X_s, X_t ∈ ℝ^{H×W×3}，Y_s ∈ 𝔹^{H×W×C} 是像素级 one-hot 向量，y_t ∈ 𝔹^C 是表示图像中存在的类别的多热向量，C 是源域和目标域数据集的类别数。注意，在 one-hot 向量中，向量的元素只有一个为 1，其余为零，而在多热向量中，向量的多个元素可以为 1。此类图像级标签 y_t 被称为弱标签，因为与像素级标签相比，它们是一种更弱的标签形式。我们可以估计它们，在这种情况下我们称它们为伪弱标签（无监督域适应，UDA），也可以从人工 oracle 获取并称之为 oracle 弱标签（弱监督域适应，WDA）。我们将进一步讨论

We compute the category-wise binary cross-entropy loss:
我们计算类别级二元交叉熵损失：

$$\mathcal{L}_c(X_t; \boldsymbol{G}) = \sum_{c=1}^{C} -y_t^c \log(p_t^c) - (1 - y_t^c) \log(1 - p_t^c). \tag{3.12}$$

This is shown at the bottom stream of Fig. 3.10. This loss function $\mathcal{L}_c$ helps to identify the categories which are absent/present in a particular image and enforces the segmentation network $\boldsymbol{G}$ to pay attention to those objects/stuff that are partially identified when the source model is used directly on the target images.
这在图 3.10 的底部流中显示。该损失函数 $\mathcal{L}_c$ 有助于识别特定图像中缺失/存在的类别，并强制分割网络 $\boldsymbol{G}$ 注意当源模型直接用于目标图像时部分识别到的那些物体/物质。

## 3.4.2 Weak labels for feature alignment
## 3.4.2 弱标签用于特征对齐

The classification loss using weak labels introduced in (3.12) regularizes the network focusing on certain categories. However, distribution alignment across the source and target domains is not considered yet. As discussed in the previous section, methods in the literature either align feature space (Hoffman et al., 2016) or output space (Tsai et al., 2018) across domains. However, such alignment is agnostic to the category, so it may align features of categories that are not present in certain images. Moreover, features belonging to different categories may have different domain gaps. Thus, performing category-wise alignment could be beneficial but has not been widely studied in UDA for semantic segmentation. To alleviate these issues, we use image-level weak labels to perform category-wise alignment in the feature space. Specifically, we obtain the category-wise features for each image via an attention map, i.e., segmentation prediction, guided by our classification module using weak labels, and then align these features between the source and target domains. We next discuss the category-wise feature pooling mechanism followed by the adversarial alignment technique.
使用弱标签引入的分类损失（3.12）对网络进行正则化，使其关注某些类别。然而，源域和目标域之间的分布对齐尚未考虑。如前一节所述，文献中的方法要么在域之间对齐特征空间（Hoffman et al., 2016），要么对齐输出空间（Tsai et al., 2018）。然而，这种对齐与类别无关，因此可能会对齐某些图像中不存在的类别的特征。此外，不同类别的特征可能具有不同的域差距。因此，进行类别级对齐可能是有益的，但在语义分割的 UDA 中尚未得到广泛研究。为缓解这些问题，我们使用图像级弱标签在特征空间中执行类别级对齐。具体而言，我们通过注意力图，即分割预测，使用弱标签的分类模块引导，为每个图像获得类别级特征，然后在源域和目标域之间对齐这些特征。接下来我们讨论类别级特征池化机制，然后是对抗对齐技术。

### Category-wise feature pooling
### 类别级特征池化

Given the last layer features $F \in \mathbb{R}^{H' \times W' \times 2048}$ and the segmentation prediction $A \in \mathbb{R}^{H' \times W' \times C}$, we obtain the category-wise features for the $c^{th}$ category as a 2048-dimensional vector by using the prediction as an attention over the features as follows:
给定最后一层特征 $F \in \mathbb{R}^{H' \times W' \times 2048}$ 和分割预测 $A \in \mathbb{R}^{H' \times W' \times C}$，我们通过将预测作为特征的注意力使用如下方式获得第 $c$ 个类别的类别级特征作为 2048 维向量：

$$\mathcal{F}^c = \sum_{h', w'} \sigma(A)^{(h', w', c)} F^{(h', w')}, \tag{3.13}$$

where $\sigma(A)$ is a tensor of dimension $H' \times W' \times C$, with each channel along the category dimension representing the category-wise attention obtained by the softmax operation $\sigma$ over the spatial dimensions. As a result, $\sigma(A)^{(h', w', c)}$ is a scalar and $F^{(h', w')}$ is a 2048-dimensional vector, while $\mathcal{F}^c$ is the summed feature of $F^{(h', w')}$ weighted by $\sigma(A)^{(h', w', c)}$ over the spatial map $H' \times W'$. Note that we drop the subscripts $s, t$ for source and target, as we employ the same operation to obtain the category-wise features for both domains. We next present the mechanism to align these features across domains. Note that we will use $\mathcal{F}^c$ to denote the pooled feature for the $c^{th}$ category and $\mathcal{F}^C$ to denote the set of pooled features for all the categories. Category-wise feature pooling is shown in the middle of Fig. 3.10.
其中 $\sigma(A)$ 是维度为 $H' \times W' \times C$ 的张量，其沿类别维度的每个通道表示通过空间维度上的 softmax 操作 $\sigma$ 获得的类别级注意力。因此，$\sigma(A)^{(h', w', c)}$ 是一个标量，$F^{(h', w')}$ 是一个 2048 维向量，而 $\mathcal{F}^c$ 是 $F^{(h', w')}$ 在空间图 $H' \times W'$ 上由 $\sigma(A)^{(h', w', c)}$ 加权求和的特征。注意，我们省略了源域和目标域的下标 $s, t$，因为我们采用相同的操作来获得两个域的类别级特征。接下来我们介绍跨域对齐这些特征的机制。注意，我们将使用 $\mathcal{F}^c$ 表示第 $c$ 个类别的池化特征，$\mathcal{F}^C$ 表示所有类别的池化特征集合。类别级特征池化显示在图 3.10 的中间。

### Category-wise feature alignment
### 类别级特征对齐

To learn the segmentation network $\boldsymbol{G}$ such that the source and target category-wise features are aligned, we use an adversarial loss while using category-specific discriminators $\boldsymbol{D}^C = \{\boldsymbol{D}^c\}_{c=1}^C$. The reason for using category-specific discriminators is to ensure that the feature distribution for each category could be aligned independently, which avoids the noisy distribution modeling from a mixture of categories. In practice, we train C distinct category-specific discriminators, to distinguish between category-wise features drawn from the source and target images. The loss function to train the discriminators D^C is as follows:
为了学习分割网络 $\boldsymbol{G}$ 使源域和目标域的类别级特征对齐，我们在使用类别特定判别器 $\boldsymbol{D}^C = \{\boldsymbol{D}^c\}_{c=1}^C$ 的同时使用对抗损失。使用类别特定判别器的原因是确保每个类别的特征分布可以独立对齐，这避免了来自类别混合的噪声分布建模。在实践中，我们训练 C 个不同的类别特定判别器，以区分从源图像和目标图像中提取的类别级特征。训练判别器 D^C 的损失函数如下：

$$\mathcal{L}_d^C(\mathcal{F}_s^C, \mathcal{F}_t^C; D^C) = \sum_{c=1}^C -y_s^c \log D^c(\mathcal{F}_s^c) - y_t^c \log(1 - D^c(\mathcal{F}_t^c)). \tag{3.14}$$

Note that, while training the discriminators, we only compute the loss for those categories which are present in the particular image via the weak labels y_s, y_t ∈ B^C that indicate whether a category occurs in an image or not. Then, the adversarial loss for the target images to train the segmentation network G can be expressed as follows:
注意，在训练判别器时，我们仅通过弱标签 y_s, y_t ∈ B^C 计算特定图像中存在的类别的损失，该标签指示类别是否出现在图像中。然后，用于训练分割网络 G 的目标图像的对抗损失可以表示如下：

$$\mathcal{L}_{adv}^C(\mathcal{F}_t^C; G, D^C) = \sum_{c=1}^C -y_t^c \log D^c(\mathcal{F}_t^c). \tag{3.15}$$

Similarly, we use the target weak labels y_t to align only those categories present in the target image. By minimizing L_adv^C, the segmentation network tries to fool the discriminator by maximizing the probability of the target category-wise feature being considered as drawn from the source distribution. These loss functions in (3.14) and (3.15) are obtained in the right of the middle box in Fig. 3.10.
同样，我们使用目标弱标签 y_t 仅对齐目标图像中存在的类别。通过最小化 L_adv^C，分割网络试图欺骗判别器，通过最大化目标类别级特征被认为是从源分布中提取的概率。这些损失函数（3.14）和（3.15）在图 3.10 中间框的右侧获得。

## 3.4.3 Network optimization
## 3.4.3 网络优化

### Discriminator training
### 判别器训练

We learn a set of C distinct discriminators for each category c. We use the source and target images to train the discriminators, which learn to distinguish between the category-wise features drawn from either the source or the target domain. The optimization problem to train the discriminator can be expressed as: min_{D^C} L_d^C(F_s^C, F_t^C). Note that each discriminator is trained only with features pooled specific to that particular category. Therefore, given an image, we update only those discriminators corresponding to those categories which are present in the image.
我们为每个类别 c 学习一组 C 个不同的判别器。我们使用源图像和目标图像来训练判别器，使其学会区分从源域或目标域提取的类别级特征。训练判别器的优化问题可以表示为：min_{D^C} L_d^C(F_s^C, F_t^C)。注意，每个判别器仅使用特定于该特定类别的池化特征进行训练。因此，给定一张图像，我们仅更新与图像中存在的类别相对应的那些判别器。

### Segmentation network training
### 分割网络训练

We train the segmentation network with the pixel-wise cross-entropy loss L_s on the source images, image classification loss L_c and adversarial loss L_adv^C on the target images. We combine these loss functions to learn G as follows:
我们使用源图像上的像素级交叉熵损失 L_s、目标图像上的图像分类损失 L_c 和对抗损失 L_adv^C 来训练分割网络。我们组合这些损失函数来学习 G 如下：

$$\min_G \mathcal{L}_s(X_s) + \lambda_c \mathcal{L}_c(X_t) + \lambda_d \mathcal{L}_{adv}^C(\mathcal{F}_t^C). \tag{3.16}$$

We follow the standard GAN training procedure (Goodfellow et al., 2014) to alternatively update G and D^C. Note that, computing L_adv^C involves the category-wise discriminators D^C. Therefore, we fix D^C and backpropagate gradients only for the segmentation network G.
我们遵循标准的 GAN 训练流程（Goodfellow et al., 2014）交替更新 G 和 D^C。注意，计算 L_adv^C 涉及类别级判别器 D^C。因此，我们固定 D^C 并仅对分割网络 G 反向传播梯度。
