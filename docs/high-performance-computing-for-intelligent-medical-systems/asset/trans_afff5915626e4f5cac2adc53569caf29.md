

utilized for myoelectric control and the operation of these muscles can be used for prosthesis control. Any useful characteristics can be derived from the EMG signals that provide prosthesis control information about muscle function [35]. Because EMG-controlled assistive devices aid disabled people who have trouble navigating user interfaces, such as joysticks and keyboards, more sophisticated hands-free human–machine interfaces are required. In a control system, sEMG signals can be used to trigger robotics and recovery equipment [36, 33].

## 2.3 背景

### 2.3.1 离散余弦变换

The DCT is one of the widely used transformations for signals and images. It helps to obtain transformation coefficients of the signals using cosine based equations. The JPEG algorithm, as the mostly known image compression method, uses DCT. In this study we used 1D-DCT because sEMG signals are used for hand movement recognition [37].

DCT是信号和图像中广泛使用的变换之一。它有助于使用基于余弦的方程获取信号的变换系数。作为最著名的图像压缩方法，JPEG算法使用DCT。在本研究中，我们使用了1D-DCT，因为sEMG信号用于手部动作识别[37]。

### 2.3.2 快速傅里叶变换

Cooley and Tukey proposed FFT in 1965 to decrease processes of the Discrete Fourier Transform (DFT). This process led to a rapid rise in DFT applications in digital signal processing and other fields. It has also led to the development of other algorithms. All these algorithms are known as FFT algorithms. The number of operations required for the DFT account has been greatly reduced and ease of operation is provided with FFT. FFT is an effective and economical algorithm for calculating DFT. It is one of the phenomena of signal processing. Hence, we used it in the proposed SN [38].

Cooley和Tukey于1965年提出了FFT，以减少离散傅里叶变换（DFT）的计算过程。这一过程导致DFT在数字信号处理和其他领域的应用急剧增加。它还促进了其他算法的发展。所有这些算法都称为FFT算法。DFT所需的运算次数大大减少，FFT提供了操作简便性。FFT是计算DFT的一种有效且经济的算法。它是信号处理的一个现象。因此，我们在拟议的SN中使用了它[38]。

### 2.3.3 奇异值分解

SVD is a matrix factorization method and it generates three components from a matrix. Generally, the singular values have been utilized to construct feature vectors. It is a widely used method in signal processing, image processing, face recognition, perceptual hashing and Google page rank algorithms [39, 40].

SVD是一种矩阵分解方法，它从矩阵中生成三个分量。一般来说，奇异值已被用于构造特征向量。它是信号处理、图像处理、人脸识别、感知哈希和Google页面排名算法中广泛使用的方法[39, 40]。

### 2.3.4 三值模式

Texture recognition and analysis are a major problem for image processing and several methods have been presented to solve this problem [41]. One practical solution of the texture analysis is textural descriptors.

纹理识别和分析是图像处理中的一个主要问题，已经提出了几种方法来解决这个问题[41]。纹理分析的一个实际解决方案是纹理描述符。

### 2.3.5 支持向量机

The SVM has various versions and it is a commonly used classifier in the literature. It is a conventional and parametric classifier. The widely used activation functions of the SVM are linear, quadratic, cubic, radial basis and Gaussian [42, 43].

SVM有多种版本，是文献中常用的分类器。它是一种传统的参数分类器。SVM广泛使用的激活函数包括线性、二次、三次、径向基和高斯[42, 43]。

### 2.3.6 线性判别分析

LDA is a linear dimension reduction and supervised machine learning technique, which seeks to find vectors in the space in which classes are best separated using class information of data objects. It is a nonparametric classifier. It is simple, fast and effective. Hence, many methods have been used [44].

LDA是一种线性降维和监督机器学习技术，旨在利用数据对象的类别信息，在类别间分离最好的空间中寻找向量。它是一种非参数分类器。它简单、快速且有效。因此，已经使用了许多方法[44]。

### 2.3.7 KNN

KNN is a distance-based classifier. Variable distances are utilized in KNN such as Euclidean, city block, Minkowski, Spearman, Chi-square. It is one of the simplest classification methods. However, it is a lazy classifier because it is not efficient for big data. It is suitable for small datasets. However, KNN proves success of the methods for large datasets using a small dataset [45].

KNN是一种基于距离的分类器。KNN中使用了可变距离，例如欧氏距离、城市街区距离、闵可夫斯基距离、斯皮尔曼距离、卡方距离。它是最简单的分类方法之一。然而，它是一个懒惰分类器，因为它对大数据不高效。它适用于小数据集。然而，KNN证明了使用小数据集对大数据集的方法的成功[45]。

### 2.3.8 人工神经网络

Artificial neural network (ANN) is inspired by bio-neurological systems and it is utilized as a classifier and regressor in the literature. ANN is one of the phenomena of machine learning and it has many variations. It uses input, weights and actual output for prediction. Basic mathematical notation of it was shown in equation (2.1) [46].

人工神经网络（ANN）受生物神经系统启发，在文献中被用作分类器和回归器。ANN是机器学习的一个现象，并有许多变体。它使用输入、权重和实际输出进行预测。其基本数学表示在等式（2.1）中显示[46]。

```
Y = \varphi(X_* w^T + \text{bias}) (2.1)
```

where \varphi(.) is activation function, X defines input vector, w is weights, Y is output.

其中，\varphi(.)是激活函数，X定义输入向量，w是权重，Y是输出。

## 2.4 蜘蛛网络

The key objective of the developed model is to obtain a cognitive model for basic hand movement recognition. We want to extract low, middle, and high level features using a cognitive method. As we know from the literature, DCT and FFT are effective methods for signal processing. Hence, these are used in a preprocessing step to obtain frequency coefficients of the sEMG signals. Also, TP and SVD are effective feature extraction methods and are used as such. After these processes, large feature sets are obtained. To select distinctive of them, an NCA-based feature reduction method is utilized. The proposed SN uses several classifiers for comparison purposes. These classifiers are chosen to validate the feature extraction power of the proposed SN because these are conventional classifiers. The key objectives of the proposed SN are given below.

开发该模型的关键目标是获得基本手部动作识别的认知模型。我们希望使用认知方法提取低、中、高级特征。根据文献，DCT和FFT是信号处理的有效方法。因此，这些方法用于预处理步骤，以获取sEMG信号的频率系数。此外，TP和SVD是有效的特征提取方法，并被用作此类方法。经过这些过程后，获得了大型特征集。为了从中选出独特的特征，采用了基于NCA的特征降维方法。拟议的SN使用多个分类器进行比较。这些分类器被选中用于验证拟议SN的特征提取能力，因为这些是传统分类器。拟议SN的关键目标如下。

- Obtain high classification accuracy.
- Propose a lightweight signal recognition network

- 获得高分类准确率。
- 提出一个轻量级信号识别网络

The SN includes preprocessing, feature extraction, feature reduction, feature concatenation and classification stages. The pictorial description of the SN is shown in figure 2.1.

SN包括预处理、特征提取、特征降维、特征连接和分类阶段。SN的图示在图2.1中显示。

As shown in figure 2.1, signal concatenation, DCT and FFT are used in preprocessing to generate secondary signals. SVD and TP are chosen as feature extractors. The extracted SVD-based and TP-based features are concatenated and two types of features are obtained. These are SVD-based and TP-based features. Finally, 2560 TP-based and 80 SVD-based features are extracted from an sEMG signal. In the feature reduction phase, firstly NCA generates weights then these weights and a tangent sigmoid-based feature reduction method are applied onto TP- and SVD- based features. 10-fold cross-validation is employed to obtain results. The milestones of the SN are explained in the subsection.

如图2.1所示，在预处理中使用信号连接、DCT和FFT来生成二次信号。SVD和TP被选为特征提取器。提取的基于SVD和基于TP的特征被连接，得到两种类型的特征。这些是基于SVD和基于TP的特征。最后，从sEMG信号中提取了2560个基于TP的特征和80个基于SVD的特征。在特征降维阶段，首先NCA生成权重，然后将这些权重和基于正切Sigmoid的特征降维方法应用于基于TP和SVD的特征。采用10倍交叉验证来获得结果。SN的里程碑在子节中解释。

![](img/75406d5bb714dfd3e68fbbc717bd8f67_61_0.png)

Figure 2.1. The block diagram of the SN.

图2.1. SN的框图。

## 2.4.1 预处理

The steps of the pre-processing phase are presented below.

预处理阶段的步骤如下。

- Step 1: Concatenate channel-1 and channel-2 sEMG signals.

- 步骤1：连接通道-1和通道-2的sEMG信号。

$S^C = S^1 | S^2$ (2.2)

where $S^C, S^1$ and $S^2$ are first channel, second channel and concatenated signals, respectively. | is concatenation operator.

其中，$S^C、S^1$和$S^2$分别为第一通道、第二通道和连接信号。|为连接运算符。

To prevent memorization and show success of the proposed SN, sEMG signals recorded from channel-1 and channel-2 are concatenated. By using this strategy, 30 samples are obtained for each hand movement. In the literature, many methods have used this strategy.

为防止记忆并证明拟议SN的成功，将从通道-1和通道-2记录的sEMG信号进行连接。使用此策略，每个手部动作可获得30个样本。在文献中，许多方法都使用了此策略。

- Step 2: Apply DCT to concatenated signal to obtain transform coefficients.

- 步骤2：对连接信号应用DCT以获取变换系数。

$C = DCT(S^C)$ (2.3)

where $C$ is DCT coefficient of the signal and DCT(.) is function of the discrete cosine transform.

其中，$C$是信号的DCT系数，DCT(.)是离散余弦变换函数。

- Step 3: Apply FFT to concatenated signal to obtain transform coefficients.

- 步骤3：对连接信号应用FFT以获取变换系数。

$[IR] = FFT(S^C)$ (2.4)

$S^F = I^2 + R^2$ (2.5)

where $I, R$ and $S^F$ are imaginary, real and Fourier signals, respectively. FFT(.) generates imaginary and real signals.

其中，$I、R$和$S^F$分别为虚部信号、实部信号和傅里叶信号。FFT(.)生成虚部和实部信号。

After this phase, a total of five signals are constructed, and these are $S^C, C, I, R$ and $S^F.

经过此阶段，总共构建了五个信号，即$S^C、C、I、R$和$S^F。

## 2.4.2 特征提取

In this phase, SVD and TP are employed as feature extractors. These extractors are applied to the generated five signals. The steps of the SVD-based feature extraction process are presented below.

在此阶段，SVD和TP被用作特征提取器。这些提取器应用于生成的五个信号。基于SVD的特征提取过程的步骤如下。

- Step 1: The input signals are shaped into two-dimensional signals. For instance, the length of the used signals in this study are 6000. We reshaped them into $60 \times 100$. This step is called a vector-to-matrix transformation.

- 步骤1：将输入信号塑形为二维信号。例如，本研究中使用的信号长度为6000。我们将其重塑为$60 \times 100$。此步骤称为向量到矩阵的转换。

- Step 2: The obtained matrix is divided into $15 \times 25$ sized non-overlapping blocks.

- 步骤2：将得到的矩阵分为$15 \times 25$大小的非重叠块。

- Step 3: SVD is applied onto each $15 \times 25$ sized block.

- 步骤3：对每个$15 \times 25$大小的块应用SVD。

$[USV] = SVD(block)$ (2.6)

where $U, S, V$ are components of the SVD and SVD(.) is singular value decomposition function.

其中，$U、S、V$是SVD的分量，SVD(.)是奇异值分解函数。

- Step 4: Store maximum singular value as a feature.

- 步骤4：将最大奇异值存储为特征。

$feat^S_L(i) = max(S), i = \{1, 2, ... , 16\},$

$L = \{S^C, C, I, R, S^F\}$ (2.7)

where $feat_k^S$ represents $i$th feature of a signal by SVD. As seen in equation (2.5), the SVD based method extracts 16 features from a signal. This feature extraction method is applied to $S^C, C, I, R$ and $S^F$ signals. Hence, 80 features are extracted in this phase. The final feature of this phase is called $feat^S.

其中，$feat_k^S$表示由SVD提取的信号的第$i$个特征。如等式（2.5）所示，基于SVD的方法从信号中提取16个特征。此特征提取方法应用于$S^C、C、I、R$和$S^F$信号。因此，此阶段提取了80个特征。此阶段的最终特征称为$feat^S。

The second feature extractor is TP. TP uses nine sized non-overlapping windows and ternary functions to extract features. The main problem of TP is to set threshold value. To adjust an automatic threshold value, standard deviation is used in this chapter. The definition of the automatic threshold calculation strategy is given in equations (2.8)-(2.10).

第二个特征提取器是TP。TP使用九大小的非重叠窗口和三值函数来提取特征。TP的主要问题是设置阈值。为了调整自动阈值，本章使用了标准差。自动阈值计算策略的定义在等式（2.8）至（2.10）中给出。

$thr = h \times SD(\text{signal}), h = \{0.1, 0.2, ..., 1\} \quad (2.8)$

$SD(\text{signal}) = \frac{1}{n-1} \sqrt{\sum_{i=1}^n (\text{signal}_i - \overline{\text{signal}})^2} \quad (2.9)$

$\overline{\text{signal}} = \frac{\sum_{i=1}^n \text{signal}_i}{n} \quad (2.10)$

where $\overline{\text{signal}}$ is mean of the signal, $SD(.)$ is function of the standard deviation, thr represents threshold value and $h$ is multiplier. The pseudo code of the 1D-TP is shown in Algorithm 2.1

其中，$\overline{\text{signal}}$为信号的均值，$SD(.)$为标准差函数，thr表示阈值，$h$为乘数。1D-TP的伪代码如算法2.1所示。

### Algorithm 2.1: Pseudo code of the 1D-TP

### 算法2.1：1D-TP的伪代码

```
Input: Signal (S) with size L, threshold value (t)
Output: Feature vector of the TP ($feat^{TP}$) with length of 512.
1: Load signal.
2: for i=1 to L-8 do
3:     $window = S(i:i + 8)$; // Divide signal into 9 sized non-overlapping windows.
4:     $center = window(5)$; // Assign center value.
5:     $counter = 1$; // Assign counter to calculate lower and upper signals.
6:     $L(i) = 0; U(i) = 0$; // Define Lower and Upper values.
6:     for j=1 to 9 do
7:         if j != 5 then
8:             if $window(j) - center < -t$ then
9:                 $L(i) = L(i) + 2^{8-counter}$;
11:             else if $window(j) - center > t$ then
12:                 $H(i) = H(i) + 2^{8-counter}$;
13:             end if
14:             $counter = counter + 1$;
15:         end if
16:     end for j
17: end for i
18: Extract histograms of the L and U.
19: Concatenated the histograms extracted and obtain $feat^{TP}$.
```

