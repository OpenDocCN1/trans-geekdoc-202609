
-   `η` inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-2244-7ch9ieqn37.gif"/ 是学习参数。由核过程生成的像素强度作为每个人工神经网络（ANN）的输入模式。对每个图像，对 `3 × 3`、`7 × 7` 和 `11 × 11` 大小的三个核分别按像素逐一移动，以收集邻近像素强度的上下文信息。卷积是另一种称呼，图 [9.4](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9fig4) (iii) 展示了使用 `3 × 3` 核的工作方式。地面真实是通过手动分割 CCA 图像并标注每个像素是否代表 cIMT 边界来获取的像素类别信息。因此，输入分别通过三个 ANN 进行训练和测试。每个 ANN 产生一个二进制图像作为输出。随后，这三个二进制图像合并，再对合并后的图像应用一个 `3 × 3` 大小的核，再送入第四个 ANN 生成最终的二进制面具。图 [9.4](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9fig4) (iv) 展示了完整过程的一个典型模型。最后阶段涉及识别 LI 和 MA 边界（如图 [9.4](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9fig4) (v) 所示）并计算 cIMT。像素距离、平均绝对距离和中心距分别为 `0.03670 ± 0.02429` inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch9ieqn38.gif"/ mm、`0.03763 ± 0.02518` inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch9ieqn39.gif"/ mm 和 `0.03683 ± 0.02450` inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch9ieqn40.gif"/ mm。

![Figure 9.4. (i) ROI extraction, (ii) ANN, (iii) convolution operation, (iv) stage 2 ANN ensemble network, (v) outputs of \[92\]. ((i)–(iv) Reproduced with permission of Springer from \[162\]. Copyright 2021 Society for Imaging Informatics in Medicine. (v) Reproduced with permission of Springer from \[92\]. Copyright 2013 International Federation for Medical and Biological Engineering.](images/bk978-0-7503-2244-7ch9f4_online.jpg)

**Figure 9.4.** (i) ROI extraction, (ii) ANN, (iii) convolution operation, (iv) stage 2 ANN ensemble network, (v) outputs of \[[92](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib92)\]. ((i)–(iv) Reproduced with permission of Springer from \[[162](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib162)\]. Copyright 2021 Society for Imaging Informatics in Medicine. (v) Reproduced with permission of Springer from \[[92](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib92)\]. Copyright 2013 International Federation for Medical and Biological Engineering.

#### 9.3.2 Extreme learning machine radial basis neural network model for cIMT region detection

Rosa *et al* \[[93](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib93)\] 使用径向基神经网络（RBNN）\[[98](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib98)\] 从 25 个超声波 CCA 图像中估计 cIMT 区域。RBNN 是一种前向神经网络，包含一个输入层、一个隐藏层和一个输出层，隐藏层的数量仅限于一层，这是其与普通 ANN 的根本区别之一。RBNN 的基本工作原理是将 `r` 个训练点 `x^(*r*)` 对应的目标变量 `y^(*r*)` 进行插值。输入 `x^(*t**s*)` 的输出函数为

$$
\\widehat{f}\\left( x \\right) = \\sum\\limits\_{r = 1}^{N}{w\_{r}\\varphi\_{r}\\left( {\\parallel {x^{ts} - x^{r}} \\parallel} \\right),}
$$

(9.3) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch9eqn45.gif" position="float"/

其中 `φ[r]` inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch9ieqn46.gif"/ 是隐藏层实现的高斯径向基函数，`w[r]` inline-graphic style="height:0.875em;" xlink:href="bk978-0-7503-2244-7ch9ieqn47.gif"/ 是隐藏层到输出层的权重，`φ[r]` inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch9ieqn48.gif"/ 是径向基函数，给出为

$$
\\varphi\\_{r}\\left( {\\parallel {x^{ts} - x^{r}} \\parallel} \\right) = \\exp\\ \\left( \\frac{{\\parallel {x^{ts} - x^{r}} \\parallel}^{2}}{2\\vartheta^{2}} \\right)
$$

(9.4) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch9eqn49.gif" position="float"/

其中 `ϑ` inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch9ieqn50.gif"/ 表示宽度。方程 ([9.3](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9eqn3)) 可化为矩阵形式，

**W**`φ` = `T`，

(9.5) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch9eqn51.gif" position="float"/

其中 **T** inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch9ieqn52.gif"/ 为目标向量。未知的权重可通过标准矩阵求反得到，

**W** = `φ^(−1)T`，

(9.6) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch9eqn53.gif" position="float"/

采用经过最优剪枝的极端学习机（OP-ELM）\[[99](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib99), [100](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib100)\]，用于初始化隐藏节点的高斯参数（隐藏节点数量、中心点以及每个径向单元的偏差）。根据子节 [9.3.1](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9s9-3-1) 中描述的技术，恢复了 25 幅 CCA 图像的真实信息和感兴趣区域（ROI）。核生成输入模式，与前文技术相同 \[[92](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9bib92)\]。实验使用了从 3 到 23 的核尺寸范围，优化后的核窗口大小为 `19 × 19` inline-graphic style="height:1em;" xlink:href="bk978-0-7503-2244-7ch9ieqn54.gif"/。经验丰富的放射科医生手动描绘地面真实。对每幅 CCA 图像，分别评估 LI 边界上的像素、LI 与 MA 边界之间的像素以及 MA 墙上的像素。最终，如图 [9.4](#Chapter_9.xhtml#bk978-0-7503-2244-7ch9fig4)(vi) 所示，各类像素被恢复并在原始图像上定位。本次实验的 cIMT 偏差为 `0.065 ± 0.046` inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch9ieqn55.gif"/ mm。

#### 9.3.3 Fuzzy *K*‑means classifier for cIMT region extraction

