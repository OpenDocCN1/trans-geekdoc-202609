

图像随后使用cv2包中cvtColor方法的COLOR_BGR2GRAY选项转换为灰度图像。这样做会将图像中的所有颜色转换为不同的灰色阶，从而在降噪、处理时间以及比较所需资源方面简化图像比较过程，且不会丢失为我们的目的所需的任何信息。生成的灰度图像如图11.3和图11.4所示。

![](img/08e33f9814ed09d3c1bb11cd99f09e86_222_0.png)

图11.3 亚马逊雨林：灰度图像 – 2000年

![](img/08e33f9814ed09d3c1bb11cd99f09e86_222_1.png)

图11.4 亚马逊雨林：灰度图像 – 2021年

### 11.3.4 用于变化检测的方法

为识别两幅图像之间的差异，使用结构相似性度量（SSIM）。SSIM在名为“图像质量评估：从误差可见性到结构相似性”的研究论文中被提出。19自那时起，它已成为图像处理和计算机视觉社区中的一个流行指标，许多研究论文都使用它进行图像比较。它已被超过15,000篇论文和250项专利引用。

历史上，研究人员已探索了许多变化检测技术，例如差分、比率、主成分分析、慢特征分析以及更多。本章的范围是仅使用SSIM演示变化检测。

如果我们分解变化检测的概念，用最细致、最简单的术语来说，我们要查明图像中的像素是否与被比较图像中相同位置的像素不同。在更复杂的实现中，我们进一步运用这一思路，整体检查像素及其周围像素组是否基于底层图像的上下文遵循相同的模式/行为。两幅图像中的像素可能以多种方式不同，具体取决于亮度、光度、角度、对比度、强度、反射、阴影等特征。像素值之间的差异程度可能在“极小”差异到“极大”差异的范围内变化。大多数变化检测方法都承认这种主观性，并允许手动设置阈值来决定变化是否显著。根据执行变化检测的上下文，可以突出显示或忽略变化。在此情况下，我们将显示图像之间的所有结构差异，而不考虑其严重程度。

SSIM遵循检查像素组以评估两幅图像之间结构相似性的原则。通过这样做，它在很大程度上本质上解决了由于图像中的微小差异引起的噪声问题。SSIM基于三个关键参数来测量两幅图像之间的相似性：

- 1. 亮度
- 2. 对比度
- 3. 结构

假设我们有两幅图像A和B，Wang等人研究中提出的SSIM公式如下所示：

$SSIM(A,B) = \frac{(2*\mu_A * \mu_B + C_1)(2*\sigma_{AB} + C_2)}{(\mu_A^2 + \mu_B^2 + C_1)(\sigma_A^2 + \sigma_B^2 + C_2)}$

- 其中，
- \(\mu_A\) 是A的平均值
- \(\mu_B\) 是B的平均值
- \(\sigma_A^2\) 是A的方差
- \(\sigma_B^2\) 是B的方差
- \(\sigma_{AB}\) 是A和B的协方差
- \(C_1 = (K_1 * L)^2\) 和 \(C_2 = (K_2 * L)^2\) 是比率稳定器
- \(L\) 是像素值范围（每像素2位 – 1）
- \(K_1 = 0.01\) 和 \(K_2 = 0.03\)

本公式的推导超出了本章的范围。然而，读者可以在Wang等人的原始研究论文中找到更多详细信息。^19

SSIM值介于0和1之间，其中0表示图像之间完全没有结构相似性，而1表示图像完全相同。Python中的Scikit-image库已经有一个名为“structural_similarity”的方法，可在给定两幅图像作为输入时计算SSIM值。在数据收集步骤中选定的亚马逊雨林图像的变化检测中也使用了相同的方法。structural_similarity函数返回SSIM分数以及突出显示输入图像中差异的图像。

### 11.3.5 代码

```
import numpy as np
from skimage.metrics import structural_similarity
import cv2
import matplotlib.pyplot as plt
def plot_image(image, factor=1):
    figure = plt.subplots(nrows=1, ncols=1, figsize=(15, 15))
    if np.issubdtype(image.dtype, np.floating):
        plt.imshow(image * factor)
    else:
        plt.imshow(image)
# load input images
image2000 = cv2.imread('C:/Users/patil/Desktop/GANESH/Book Chapter/Change detector/Images/Amazon Rainforest/Amazon rainforest 2000.jpg')
plot_image(image2000)
print(image2000.shape)
image2021 = cv2.imread('C:/Users/patil/Desktop/GANESH/Book Chapter/Change detector/Images/Amazon Rainforest/Amazon rainforest 2021.jpg')
plot_image(image2021)
print(image2021.shape)
# converting images to grayscale
grayA = cv2.cvtColor(image2000, cv2.COLOR_BGR2GRAY)
grayB = cv2.cvtColor(image2021, cv2.COLOR_BGR2GRAY)
# Find structural similarity using structural_similarity method
(score, diff) = structural_similarity(grayA, grayB, full=True)
diff = (diff * 255).astype("uint8")
print("SSIM:", score)
# Find threshold difference image
thresh = cv2.threshold(diff, 0, 255, cv2.THRESH_BINARY_INV | cv2.THRESH_OTSU)[1]
thresh1 = cv2.cvtColor(thresh, cv2.COLOR_BGR2RGB)
plot_image(thresh1)
```

## 11.4 结果与讨论

使用上述方法获得的SSIM和差异图像如图11.5和表11.2所示。

| 结构相似性指数（SSIM） | 0.7368 |
|---|---|

![](img/08e33f9814ed09d3c1bb11cd99f09e86_226_0.png)

图11.5 两个输入亚马逊雨林图像之间的差异。

0.7368的SSIM表明两幅图像之间存在显著差异。差异图像以黑色画布上的白色区域形式提供差异区域。通过肉眼检查两个输入图像可以证实，差异图像非常有效地捕捉了关键差异区域，如图11.5所示。

## 11.5 结论

本章介绍了计算机视觉在图像变化检测中的应用案例研究，以识别巴西亚马逊雨林的森林砍伐。首先，我们讨论了关于森林适当监测及其影响的问题。将此视为一个严重问题，并结合计算机视觉领域最近的进展所带来的机遇，探索了一种使用计算机视觉识别森林砍伐的方法。详细的文献综述向读者介绍了在使用卫星图像和计算机视觉解决一些现实问题（包括图像变化检测领域的开创性研究）方面正在进行的过去和现在研究的深度和广度。

随后，我们介绍了SSIM的概念，该概念在工业界广泛用于通过分析两幅图像之间的结构相似性来测量它们之间的相似性。通过实现一个使用OpenCV的cv2库和Scikit-image库中的结构相似性方法的Python代码，我们找出了2000年和2021年两幅亚马逊雨林卫星图像之间的差异。

因此，根据0.7368的SSIM指数并分析差异图像，可以得出结论：从2000年到2021年，亚马逊雨林发生了显著变化，需要密切关注以避免未来的任何损害。这表明，使用计算机视觉原则的简单实现和高效的开源库，可以帮助我们以前所未有的速度和准确性识别和解决某些关键问题。

本章讨论的用例演示了如何以最有效的方式使用计算机视觉来检测两幅图像之间的差异。经过一些修改和改进，此实现可应用于许多领域，例如欺诈检测、医疗诊断、评估自然灾害的影响、边境活动增加、土地分类变化等。仅本章中展示的森林砍伐监测应用就具有多种用途，包括但不限于避免/控制野火、识别新种植园区域、避免一些严重的气候风险、从长远防止洪水和干旱，以及拯救一些野生动物免于灭绝。

## 关键词

- 计算机视觉
- 亚马逊雨林
- 变化检测
- 结构相似性指数

