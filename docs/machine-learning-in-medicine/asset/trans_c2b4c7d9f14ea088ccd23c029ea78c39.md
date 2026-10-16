
为解决上述问题，我们将注意力门控 U‑Net 与一种全新的焦点损失函数相结合，该焦点损失更适合小病变的分割。我们提出了一种全新的聚焦 Tversky 损失函数（FTL），在焦点损失的基础上加入 Tversky 指数，以改善小病变分割效果。该指数用于解决焦点损失函数中精确率与召回率的失衡问题 \[[7](#C16_chapter9.xhtml#ref9_7)\]。随后，我们将该损失函数与深度监督的注意力 U‑Net \[[20](#C16_chapter9.xhtml#ref9_20)\] 结合，该 U‑Net 进一步通过多尺度输入图像金字塔提升中间特征表示的质量。[²](#C16_chapter9.xhtml#fn9_2)

我们在 Ref. \[[18](#C16_chapter9.xhtml#ref9_18)\] 中描述的 Dice 损失（DL）函数存在局限性，即它对假阳性（FP）和假阴性（FN）检测同样加权。对 FP 与 FN 同样加权会导致分割图像精确率高，但召回率下降。医学分割数据（如病灶分割）中，前景像素（即真实标注的前景）数量极少，即使少量前景像素被错误标记，召回率也会大幅下降。因此，若想提升召回率，需要在 FN 相对于 FP 上赋予更大的权重。Tversky 指数可以帮助实现 FP 与 FN 之间更好的权衡：

$$TI_{c}=\frac{\sum_{i=1}^{N}p_{ic}g_{ic}+\epsilon}{\sum_{i=1}^{N}p_{ic}g_{ic}+\alpha\sum_{i=1}^{N}p_{i\overline{c}}g_{ic}+\beta\sum_{i=1}^{N}p_{ic}g_{i\overline{c}}+\epsilon}\\operatorname{(9.2)}$$

其中 *p*[*i*c] 表示像素 *i* 属于类别 *c*（病灶）的概率，*p*[*i*<o>c</o>] 表示像素 *i* 属于非病灶类别的概率，同理 *g*[*i*c] 与 *g*[*i*<o>c</o>》分别为真实标签的概率。 *N* 为图像中总像素数。超参数 *α* 与 *β* 可调节以改变对 FN 与 FP 的侧重，从而在大类别失衡时提升召回率。

将 Tversky 指数转化为损失函数（TL）时，在 Ref. \[[7](#C16_chapter9.xhtml#ref9_7)\] 中通过最小化 $\\sum_{c}(1-TI_{c})$ 实现。

Dice 损失的另一个缺点是，它在分割极小的感兴趣区域（ROI）时表现不佳，因为这些区域对损失贡献有限。为解决此问题，我们提出了 FTL，由 *γ* 参数控制，以在易背景和难 ROI 训练样本之间取得平衡。Ref. \[[1](#C16_chapter9.xhtml#ref9_1)\] 中的焦点损失通过对交叉熵损失进行指数化，使难以检测的类别（概率低）的损失被放大。焦点损失已被引入到 DL 函数中 \[[21](#C16_chapter9.xhtml#ref9_21)\]，我们采用类似的思路定义 FTL：

$$FTL_{c}=\\sum_{c}\\left(1-TI_{c}\\right)^{1/\\gamma}\\operatorname{(9.3)}$$

其中 *γ* 的取值范围为 {1,3}。实际中，若像素的 Tversky 指数较大且被错误分类，FTL 几乎不受影响；但当 Tversky 指数很小且像素被错误分类时，FTL 会显著下降。

当 *γ* > 1 时，损失函数更关注那些预测不准确、已被误分类的像素。然而，当模型接近收敛、类别准确率高时，FTL 会出现过度抑制现象。为缓解此问题，我们尝试使用更大的 *γ* 值，最终发现 $\\gamma = \\frac{4}{3}$ 在所有实验中表现最佳，并在此工作的所有实验中采用该值。为进一步防止 FTL 的过度抑制，我们并未在所有层上使用 FTL，而是仅在中间层使用；最后一层则改用 Tversky 损失，以提供强的误差信号，防止次优收敛。我们假设，增大 *α* 在广义损失函数中可以通过将焦点从 FP 转移至 FN 来提升模型收敛性。因此，我们在所有实验中使用 *α* = 0.7、*β* = 0.3。值得注意的是，当 *α* = *β* = 0.5 时，Tversky 指数简化为 DSC（Dice Similarity Coefficient）；当 *γ* = 1 时，FTL 退化为 TL（Tversky Loss）。

为进一步提升精度和召回率，我们遵循 Ref. \[[20](#C16_chapter9.xhtml#ref9_20)\] 中对 U‑Net 的改进措施，并将其与 FTL 相结合。即使在采用注意力基模型后，仍发现多层卷积会导致小病灶细节在解码阶段被模糊丢失。为此，我们使用软注意力门控机制，从低层特征图中识别并传递相关空间信息到解码阶段。为了让不同尺度的细节更易获取，我们直接将输入图像的多尺度版本（通过构建图像金字塔）喂给编码器层。结合深度监督，该方法在小 ROI 特征容易在卷积过程中被丢失的数据集上提升分割精度，并帮助网络学习更具局部感知性的特征，从而改善分割效果。所提网络架构可见 [Figure 9.2](#C16_chapter9.xhtml#f9_2)。

![FIGURE 9.2 The proposed attention U-Net architecture.](images/fig9_2.jpg)

**FIGURE 9.2 The proposed attention U-Net architecture.**

为验证所提 FTL 与注意力 U‑Net 的有效性，我们在 Breast Ultrasound Lesions 2017 数据集 B（BUS）上进行实验，该数据集中病灶占比为 4.84% ± 5.43%。[Table 9.2](#C16_chapter9.xhtml#t9_2) 展示了结果。相较于基线 U‑Net，我们的方法使 Dice 分数提升了 25.7%。这一结果凸显了解决类别失衡对分割的重要性，并表明该问题值得进一步探索。

**TABLE 9.2 Results on the Bus 2017 Dataset for the Proposed FTL and Attention U-Net Compared to DL**

| **Model** || **DSC** || **Precision** || **Recall** |
| --- | --- | --- | --- |
| U-Net + DL || 0.547 || 0.653 || 0.658 |
| U-Net + FTL || 0.669 || 0.775 || 0.715 |
| Attn U-Net + DL || 0.615 || 0.675 || 0.658 |
| Proposed (Attn U-Net + multi-input + FTL) || **0.804** || **0.829** || **0.022** |

