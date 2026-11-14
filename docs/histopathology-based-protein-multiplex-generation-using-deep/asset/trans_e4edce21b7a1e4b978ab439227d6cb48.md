

WSI并避免后台处理。每个瓦片可选择使用Macenko方法^60进行可选的染色归一化，以减少染色变异性并确保图像间的颜色一致性。然后，通过训练好的HistoPlexer模型处理瓦片以预测蛋白多重影像。预测后，将生成的瓦片拼接在一起，以多种分辨率重建完整的WSI。我们还生成质量控制图像，以可视化瓦片和分割结果，并保存瓦片的坐标以供复现。对于可视化，我们使用训练集的最小-最大值对所有标记进行最小-最大归一化。

### Ulivue数据集

为了在WSI上对HistoPlexer进行定性评估，我们使用Ulivue InSituPlex技术，通过Immuno8和MDSC FixVue面板获取多重影像。Immuno8面板侧重于免疫景观特征分析，使用的标记物包括CD3、CD4、CD8、CD68、PD-1、PD-L1、FoxP3和PanCK/SOX10。MDSC面板使用CD11b、CD14、CD15和HLA-DR标记物来识别髓源性抑制细胞。Ulivue图像以每像素0.325 µm的分辨率获取。为了评估，我们使用CD3、SOX10、CD8a和HLA-DR标记物来评估生成的蛋白多重影像与Ulivue图像之间的视觉相似性。

配对的H&E和Ulivue WSI是通过首先在一个组织切片上进行H&E染色，然后对十个样品的连续切片获取Immuno8和MDSC数据生成的。每个样品均包含一份扁桃体组织作为阳性对照。H&E和Ulivue WSI之间的图像配准使用无监督多模态方法^51进行，利用Ulivue中的DAPI核染色与H&E图像对齐。Ulivue和生成的IMC图像均经过最小-最大归一化和直方图均衡化。此外，对Ulivue图像应用了自适应阈值处理，以减少噪声并提取真实信号。具有假信号的区域，特别是那些对应于H&E中的出血、出血或红细胞的区域，已被手动标注并从分析中排除。该数据集（包括H&E和Ulivue图像、对齐矩阵和标注的排除区域）公开可用，可以在Hugging Face (https://huggingface.co/datasets/CTPLab-DBE-UniBas/HistoPlexer-Ulivue) 上访问。该数据集可为该领域提供有价值的基线。

### TCGA-SKCM

从TCGA数据库（https://portal.gdc.cancer.gov/）下载了共472例SKCM的诊断WSI。还下载了SKCM样本的临床数据，包括年龄、性别、样本类型（原发肿瘤/转移性）和疾病特异性生存率。对于生存预测，我们排除了诊断WSI分辨率低或疾病特异性生存数据缺失的病例，总共剩余360例。对于免疫亚型预测，我们保留了共有免疫亚型标签的257例病例。对于每个任务，我们按年龄、性别和样本类型分层随机划分病例，以4:1的训练-验证集比例创建5倍交叉验证。

## HistoPlexer架构

HistoPlexer基于cGAN，以H&E图像作为输入条件，生成多重IMC图像，每张图像对应空间分辨的蛋白表达图谱。HistoPlexer的转换器是一个完全卷积的U-Net^32，由编码器和解码器组成。编码器包含六个下采样块，每个块含有一个步长为2、卷积核大小为3的卷积层。解码器包含五个上采样块，每个块包含最近邻插值，随后接一个步长为1、卷积核大小为3的卷积层。每个层之后均接一个批量归一化层和ReLU激活。鉴别器由六个块组成，每个块包含一个卷积层，随后接一个谱归一化层和ReLU激活。我们使用从模板匹配的H&E和IMC ROI对中提取的补片来训练HistoPlexer，并通过三个目标优化模型：对抗损失以强制图像级一致性，高斯金字塔损失以强制像素级一致性，以及补片级对比损失以强制补片级一致性。

### 对抗损失

我们采用LSGAN^33提出的最小二乘损失作为对抗损失，并使用二进制编码方案，其中0和1分别作为生成（即假）和真实IMC图像的标签。我们还采用多尺度梯度方法^54，该方法允许在多个尺度（即分辨率）上同时进行梯度传播。考虑一组尺度 {s ∈ S}，转换器G和鉴别器D的多尺度对抗损失定义为

$$L_G^{adv} = \frac{1}{|S|} \mathbb{E}_{x_p \sim X_p} \left[ (D(G^{(s)}(x_p)|x_p) - 1)^2 \right],$$

$$L_D^{adv} = \frac{1}{|S|} \sum_{s \in S} \left[ \mathbb{E}_{x_p \sim X_p} \left[ (D(y_p|x_p) - 1)^2 \right] + \mathbb{E}_{x_p \sim X_p} \left[ (D(G^{(s)}(x_p)|x_p))^2 \right] \right],$$

$$y_p \sim Y_p$$

(1)

其中 X_p = {x_p ∈ X_ROI} 和 Y_p = {y_p ∈ Y_ROI} 分别表示从模板匹配的H&E和IMC ROI中采样的配对训练补片；G^(s)(·) 和 D(·) 分别表示由转换器（在输出尺度s上）和鉴别器参数化的映射函数；|·| 表示集合的基数。

### 高斯金字塔损失

我们还按ref. 23实现了像素级L1损失。由于我们的H&E和GT IMC图像未在像素级对齐，我们通过计算生成和GT IMC图像的多分辨率表示上的L1损失^12，放宽了像素对像素对应关系的约束，该损失称为高斯金字塔损失^12。具体来说，通过迭代高斯平滑和下采样构建高斯金字塔。每个分辨率级别，称为一个八度，包含一系列平滑度递增的图像。分辨率之间的过渡是通过将当前八度最高平滑度级别的图像下采样来启动下一个级别：

$$y_{p,1}^{s+1} = \text{Downsample} \left( y_{p,\#gs}^s \right)$$

其中 #gs 表示一个分辨率下的高斯平滑次数。注意，对于生成的IMC图像，我们仅在最终输出尺度上计算了高斯金字塔。考虑一组分辨率 {r ∈ R}，高斯金字塔损失是对每个八度主层计算的L1损失的加权和，定义为

$$L^{gp} = \sum_{r \in R} w_r \mathbb{E}_{x_p \sim X_p} \left\| y_{p,1}^r - y_{p,1}^{r\prime} \right\|_1.$$

$$y_p \sim Y_p$$

(2)

其中 y_p 表示生成的IMC图像补片，w_l 表示分辨率级别，w_l 是该级别L1损失的权重。

### 补片级对比损失

我们进一步引入了受ref. 21启发的补片级对比损失。具体来说，我们首先使用预训练特征编码器提取多层特征，并通过一个小型投影头（例如多层感知机）对提取的特征进行变换，以丰富其表达性^35。然后，我们为每个特征层随机选择一组像素位置。通过聚合每个层的选定补片特征，我们可以分别获得生成和GT IMC图像的两组特征。

令 z'_i 表示从特征编码器的第l层提取的生成IMC图像第i个补片的锚特征；z'_i^+ 和 z'_i^- 分别表示从同一层提取的相应补片（即相同像素位置）的正特征和非相应补片集合（即不同像素位置）的负特征。我们的补片级对比损失定义为

$L_{\text{contrast}} = \mathbb{E}_{x_p \sim X_p} \frac{1}{\#\text{layer}} \frac{1}{\#\text{patch}} \sum_{i=1}^{\#\text{layer}} \sum_{i=1}^{\#\text{patch}} w_i(z_t^i, z_t^j) \ell_{\text{InfoNCE}}(z_t^i, z_t^j, z_t^j), \quad y_p \sim Y_p$

其中

$\ell_{\text{InfoNCE}}(\mathbf{z}, \mathbf{z}^+, \mathbf{z}^-) = - \log \frac{\exp(\mathbf{z} \cdot \mathbf{z}^+ / \tau)}{\exp(\mathbf{z} \cdot \mathbf{z}^+ / \tau) + \sum_{n=1}^N \exp(\mathbf{z} \cdot \mathbf{z}_n^- / \tau)}$

是InfoNCE目标^56，且

$w_t(z_t^i, z_t^j) = \left(1 - g\left(\frac{t}{T}\right)\right) \times 1.0 + g\left(\frac{t}{T}\right) \times h\left(\text{sim}(z_t^i, z_t^j)\right)$

是自适应补片权重^21。在此，#layer 和 #patch 分别表示提取特征的层数和补片数，_t_ 和 _T_ 分别表示当前和总训练步数，$h(\cdot)$ 表示某个加权函数，sim($\cdot$, $\cdot$) 是某个相似度测量。

虽然HistoPlexer转换器输出所有选定IMC标记物的预测，但在使用预训练特征编码器时，我们遇到了一个实际限制，该编码器通常需要RGB图像作为输入。为规避此问题，我们首先提取输出IMC图像的每个通道（即标记物），并沿通道维度复制它以创建伪RGB图像。然后将每个通道传递给特征编码器。最终的补片级对比损失是各通道损失之和。

G和D的总损失定义为

$L_G = L_G^{\text{adv}} + \lambda_{gp} L^{gp} + \lambda_{\text{contrast}} L_{\text{contrast}} \quad L_D = L_D^{\text{adv}} + \lambda_{R_1} R_1$

其中

$R_1 = \mathbb{E}_{x_p \sim X_p} \left\| \nabla_y D(y_p | x_p) \right\|_2^2 \quad y_p \sim Y_p$

是梯度惩罚^57，$\lambda_{gp}$、$\lambda_{\text{contrast}}$ 和 $\lambda_{R_1}$ 分别为高斯金字塔损失、补片级对比损失和梯度惩罚的权重。

## 实现和训练细节

该模型使用ADAM优化器^58训练了100个时代，动量参数为 $\beta_1 = 0.5$ 和 $\beta_2 = 0.999$，转换器和鉴别器网络的学习率分别为0.004和0.0008。权重使用Xavier初始化进行初始化。批量大小设置为16，IMC的补片大小为256，H&E图像的补片大小为1,024，以适应后者的更高分辨率。我们通过采用数据增强（包括颜色增强、随机翻转、小平移和旋转）来提高模型的泛化能力。我们采用了最小二乘GAN目标。损失项的权重如下：$\lambda_{gp} = 5.0$，$\lambda_{\text{contrast}} = 1.0$ 和 $\lambda_{R_1} = 1.0$。对于模型推理和评估，我们使用了模型训练结束时的最新检查点。

## 评估指标

为了评估生成图像的质量，我们使用了三种广泛采用的指标：PSNR、MS-SSIM和RMSE-SW。

### PSNR

PSNR用于通过量化最大可能信号功率与损坏噪声功率之间的比率来衡量重建质量。它以分贝表示，值越高表示图像质量越好。PSNR的计算公式为

$\text{PSNR} = 10 \log_{10} \left( \frac{L^2}{\text{MSE}} \right)$

其中 $L$ 是像素值的动态范围（例如，8位图像为255），MSE表示原始图像 $I$ 与生成图像 $I'$ 之间的MSE

$\text{MSE} = \frac{1}{N} \sum_{i=1}^N (I(i) - I'(i))^2$

### MS-SSIM

MS-SSIM通过引入多个尺度来扩展传统的SSIM指标，以捕捉不同分辨率下的结构相似性。两张图像 $I$ 和 $I'$ 之间的SSIM定义为

$\text{SSIM}(I, I') = \frac{(2\mu_I \mu_{I'} + C_1)(2\sigma_{II'} + C_2)}{(\mu_I^2 + \mu_{I'}^2 + C_1)(\sigma_I^2 + \sigma_{I'}^2 + C_2)}$

其中 $\mu_I$ 和 $\mu_{I'}$ 是均值，$\sigma_I^2$ 和 $\sigma_{I'}^2$ 是方差，$\sigma_{II'}$ 是两幅图像之间的协方差。$C_1$ 和 $C_2$ 是用于稳定除法的小常数。在MS-SSIM中，结构相似性在多个尺度上计算，最终分数是这些尺度上SSIM值的加权乘积：

$\text{MS-SSIM}(I, I') = \prod_{j=1}^M \left(\text{SSIM}_j(I, I')\right)^{\alpha_j}$

其中 $M$ 是尺度数量，$\alpha_j$ 是尺度 $j$ 的加权因子。MS-SSIM值越高，表示感知相似性越好。

### RMSE-SW

RMSE-SW是一种用于评估原始图像 $I$ 与生成图像 $I'$ 之间相似性的图像质量指标。与传统RMSE不同，传统RMSE在整个图像上全局计算误差，而RMSE-SW通过在图像上移动固定大小的窗口，在局部区域内计算误差。两张图像 $I$ 和 $I'$ 之间的RMSE-SW定义为

$\text{RMSE-SW} = \sqrt{\frac{1}{N} \sum_{k=1}^N \frac{1}{w \times h} \sum_{i=0}^{w-1} \sum_{j=0}^{h-1} (I(x_k + i, y_k + j) - I'(x_k + i, y_k + j))^2}$

其中 $w \times h$ 表示带定义步幅在图像上移动的窗口大小，得到 $N$ 个窗口。对于每个窗口，我们计算了 $I$ 和 $I'$ 对应像素值之间的MSE。

这些指标对生成图像的像素级准确性和感知相似性进行了全面评估。Frechet inception distance和kernel inception distance是评估生成图像质量的广泛使用的指标；然而，它们在小数据集上效果较差，因为它们依赖于队列的均值和协方差。因此，在评估HistoPlexer时未使用这些指标。

为了量化域专家的评估，我们使用了HYPE分数，它衡量人类将生成图像误认为真实图像或反之的错误率。它定义为

$\text{HYPE} = \left( \frac{\text{TP} + \text{FN}}{\text{TP} + \text{TN} + \text{FP} + \text{FN}} \right) \times 100 \quad \text{HYPE}_{\text{fake}} = \left( \frac{\text{FP}}{\text{TN} + \text{FP}} \right) \times 100 \quad \text{HYPE}_{\text{real}} = \left( \frac{\text{FN}}{\text{TP} + \text{FN}} \right) \times 100$

其中 TP 为真正例数，TN 为真反例数，FP 为假正例数，FN 为假反例数。

