
to shortage of information that is information loss. The WNN (Weighted Nuclear Norm) assigns various weights to various solitary values and can solve this issue. For noise decomposition, the WNN technique is used as it is considered to be robust to the noise. The redefined form is shown below based on WNN:

$$b = \mathcal{A}\mathit{M}_b \{ \| Y = LR_{D}\overline{\widehat{LR}_{C}} - SP_{D}\overline{\widehat{SP}_{C}} \|^{2}_{G} + P_{3} \| LR_{D}\overline{\widehat{LR}_{C}} \|_{*} + P_{4} \| SP_{D}\overline{\widehat{SP}_{C}} \|_{/ , *} + P_{1} \| \overline{\widehat{LR}_{C}} \|_{I} + P_{2} \| \overline{\widehat{SP}_{C}} \|_{I} \} \tag{5.6}$$

Here, the WNN is defined as $\| \cdot \|_{*,*} \triangleq \sum_{i}\sigma_{i}\omega_{i}(\cdot)$ and $\sigma_{i}$ is considered as the i$^{\text{th}}$ remarkable data of $\cdot$ and $\omega_{i}$ which is greater than zero represents the i$^{\text{th}}$ weight to $\sigma_{i}$. The parameter $P_{4}$ controls the involvement in the WNN. In order to retain the edge details of input image during de-noising, the WNN assigns various weights to various particular or remarkable data. While removing noise, significant information may smoothen out. The boundary details of an image are nothing but sparse modules and fusion techniques can enhance this significant information. The boundary details are retained and can be enhanced with the help of following method.

$$(b) = \mathcal{A}\mathit{M}_{b} \{ \| LR - LR_{D}\overline{\widehat{LR}_{C}} - SP_{D}\overline{\widehat{SP}_{C}} \|^{2}_{G} + P_{4} \| SP_{D}\overline{\widehat{SP}_{C}} \|_{W,*} + P_{3} \| LR_{D}\overline{\widehat{LR}_{C}} \|_{*} + P_{5} \| SP_{D}\overline{\widehat{SP}_{C}} \|_{I} + P_{1} \| \overline{\widehat{LR}_{C}} \|_{I} + P_{2} \| \overline{\widehat{SP}_{C}} \|_{I} \} \tag{5.7}$$

The primary function of the CS block is to adapt and recalibrate the features of source images by forming interdependencies among channels. Initially, the CS block compressing feature as follows

$$\underline{E}_{d} = \frac{1}{IV} \sum_{I=1}^{I} \sum_{V=1}^{V} y_{d}(t, u) \tag{5.8}$$

Where, E$_{d}$ denotes the compressed feature corresponding to the d$^{\text{th}}$ feature map $y_{d}$, 'I' denotes height and 'V' denotes the width of $y_{d}$. The compressed features are given as input to a three layered NN. The output dimension is same as dimension of the layer. The following expression depicts the actual CS block function:

$$V_{s} = O(E) = \sigma \left(V_{2}\delta \left(V_{1}, E\right)\right) \tag{5.9}$$

Where $V_{s} = [v_{1}, v_{2}, v_{1}, \dots v_{s}]$ represents the scale vector of actual feature maps and $O(\cdot)$ denotes the actual activation function. $\mathbf{E} = [e_{1}, e_{2}, e_{1} \dots e_{s}]$ represents the feature vector of source image. $\sigma$ denotes the sigmoid function and $\delta$ represents the ReLU function. $V_{1}$ and $V_{2}$ represent the weight of the source layer and destination layer, respectively. The final outcome of CS block is attained with:

$$\overline{y}_{d} = y_{d} \cdot V_{d} \tag{5.10}$$

Here the element-wise layers are represented by ‘ : ’, or the dot. The actual activation function doesn’t exploit the response of the concealed layer. O (E) starts its series from zero to one. The several CS blocks are fixed in a NN, and O (E) of (0, 1) will construct the response of the center layers. This will corrupt the act of the network. In order to avoid this disadvantage, the following function is used to get the improved CS block.

$s = O_m(E) = \{l_1 \times [\sigma(V_2 \delta (V_1, E))] + l_2 \times \sigma(E)\} \times 2 \quad (5.11)$

Notable improvements in CS block:

- The enduring function of (4) makes use of inputs and the outputs of the three-layered network. The complexity faced in the training routine is reduced.
- The weakening of significant information caused by performing several manipulations can be reduced.

### 5.3.2 ENHANCED EFFECTIVE GENERATIVE ADVERSARIAL NETWORKS

The SR technique comprises GAN framework and the boosted CS block. This block is attached with producer and divider, followed by the fusion function. The Figure 5.1 depicts the proposed method.

### 5.3.3 THE PRODUCER AND THE DISCRIMINATOR

The EDSR technique implemented by Lim et al. was simplified to perform producer of GAN model. The novel EDSR has Resblocks and kernels. Then, the boosted CS block was appended with the CNN. The discriminator comprises eight convolutional layers with kernels. Later, the fusion block merges the extracted features from the least 3 layers. The discriminator processes the low level frequency details, and the unwanted details are subsequently reduced. The classification process is accomplished by processing pooling function, convolution constructions and Sigmoid triggering function. The following block diagram Figure 5.2 depicts the proposed method.

### 5.3.4 FUSION SCHEME

The WNN construction in the image decomposition technique, the learned $\mathrm{SP_c}$, is clear. The reformed image done by $\mathrm{SP_c}\mathrm{SP_d}$ is noiseless. $\mathrm{LR_c}\mathrm{SP_c}$ are the coefficients with higher norm values which correspond to the patches with prominent information.

The fusion operation for training GAN technique is performed. The loss function is used to combine loss (L), comparative opposition loss, sensitivity loss and MSEL (Mean Square Error loss).

![](img/93c6e2919cb9917d1bdd8f6271e04df4_104_0.png)

**图 5.1** 所示方法架构图。

![](img/93c6e2919cb9917d1bdd8f6271e04df4_104_1.png)

**图 5.2** 所示方法框图。

$$\mathbf{T}_{\mathrm{img}}=\mathbf{C}_{\mathrm{L}}+\mathbf{C}_{\mathrm{L}} \mathbf{C O}_{\mathrm{L}}+\mathbf{S}_{\mathrm{L}}+\mathbf{C}_{\mathrm{ME}} \mathbf{M E}_{\mathrm{L}} \quad(5.12)$$

其中，$\mathbf{T}_{\mathrm{img}}$ 代表目标图像，$\mathbf{C}$、$\mathbf{C}_{\mathbf{L}}$、$\mathbf{C}_{\mathbf{M E}}$ 是常数。这些常数用于表示控制损失的超参数。比较性对数损失（comparative opposition loss） 使用语义特征代替像素级特征。这种特征细节与感知相似性相同。变量 $\mathbf{C}_{\mathbf{L}}$ 实现了从基础源图像检索细节的网络。另外两个变量 $\left(\mathbf{C}_{\mathbf{L}} \mathbf{C O}_{\mathbf{L}} + \mathbf{S}_{\mathbf{L}}\right)$ 提高了重构图像的 PSNR。最后一个变量 $(\mathbf{C}_{\mathbf{M E}} \mathbf{M E}_{\mathbf{L}})$ 用于减少目标图像与其对应源图像之间的 MSE。判别性 $\mathrm{LR}$ 和 $\mathrm{SP}$ 以及 $\mathrm{LR}$ 和稀疏分解算法分别在图5.3和图5.4中给出。

### Algorithm for Discriminative LR Sparse DL

- Step 1: LRP_D and BP (t=1 to Maximum iteration)
- Step 2: Initialize the Balance parameters
- Step 3: Update Z_d=AM {$\|$ Z-Z_d$\|+\|Z_d$\|*}]
- Step 4: Update Z_s=AM {$\|$ Z-Z_s$\|+\|Z_s$\|1}
- Step 5: Update LR_C=AM {$\|$ Z-LR_D LRC$\|+BF1 $\|$Z_s$\|1} and Update LRC=AM {$\|$ Z- SP_D SPD$\|+BF2 $\|Z_d$\|1}
- Step 6: Update X=AM[(BF5/$\|u$\|z$\|*+1/2)X-(LR_D+V/$\|^2)\|)
- Step 7: LR_D=(Jt+2/ $\mu$ LRC LRC^M)^{-1}/2($\mu$X1 LRC^M+X+U/$\mu$)
- Step 8: Repeat step 3 if the iteration reaches maximum value
- Step 9: Output SP_D, LRD

**FIGURE 5.3** Algorithm for Discriminative LR Sparse DL.

### Algorithm for Low Rank and Sparse Decomposition

- Step 1: Initiate Variables P, Q and R Parameters from 1...5
- Step 2: X not satisfied then do
- Step 3: Update Q1 and Q3
- Step 4: Update P=AM[{\|Q-R\|$\|2^2+E\|$ P\|$ \|w,*\|}
- Step 5: LRC=AM$\|$LRC{\|$P-LRDLRC$\|$2^2+E1$\|$ LRC$\|1} SP_C {$\|$Q-SP_DSPC$\|2^2+E2$\|$SPC$\|1}
- Step 6: Repeat Step 3 until the iteration reaches its maximum value
- Step 7: LRC, SP_C

**FIGURE 5.4** Algorithm for LR and Sparse Decomposition.

## 5.4 EXPERIMENTAL SETUP

The proposed Enhanced Effective Generative Adversarial Networks have been implemented using Ubuntu version 16.04 with PyTorch 0.4.1, NVIDIA 1080Ti, CUDA version 8 and CUDNN version 5.1. All experiments were done on a set of MRI datasets available from the internet. The 600 training dataset images were used to evaluate this proposed method. First, the effectiveness of the proposed method is processed by applying two algorithms. The Alg1 is applied for discriminating LRSP learning, and Alg2 is applied for LR and SP decompositions. Once the decomposition has been done, the producer and discriminator functions are applied followed by fusion technique.

### Applying Alg1:

Fixing parameters: First, the number of iterations is fixed, and the parameters used for these iterations are (t = 1,2,3,4,5) followed by BP1 = 0.005, BP2 = 0.005 and B5 = 1 in the DL. To perform the evaluation on these training data, the parameter for iteration is set to 10. That is Alg 1 is repeatedly executed till it satisfies the condition Max <= 10. The BP3 and BP4 parameters are included to take control over the LR and SP constraints. The BP3 and BP4 had produced different parameters when the constant parameters were assigned to BP1, BP2 and BP3 parameters. The Figure 5.3 depicts the algorithm for Discriminative LR Sparse DL.

### Applying Alg2:

After Alg1 has been processed, the Alg2 was applied and used up to 6 parameters and iterations. To obtain the value of noise in the image, the same procedure which is done in [10] was applied and, then, the P1, P2, P3 and P5 on the result image were examined. Initially, the value one is assigned to P3 and its post effect of P1 and P2 was examined. The resulting images during this process have been depicted in the Figure 5.5. If the P3 value was assigned to 1, satisfactory result from this second algorithm was obtained. Fixing P1 = 1, P2 = 1, P3 = 1 and P4 = 0, the result when P5 = 0.005, 0.01, 0.1, 1 are given in the Figure 5.5. If the number of iterations is set to 30 in this second algorithm, it produces noise-cum-grayscale images and five for spectral based images.

### 5.4.1 APPLYING ENHANCED EFFECTIVE GENERATIVE ADVERSARIAL NETWORKS

The results produced by the above described second algorithm images are applied to this improved CS block. The parameters are determined as 0.8 and 0.2. As per the second algorithm, the constant value of $C$, $C_{L}$ and $C_{ME}$ are varying from zero to ten. The average PSNR and SSIM of this proposed technique on all these sample images, a scaling factor of four is used as shown in the following Table 5.1.
