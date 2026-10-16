
本研究从使用 FreeSurfer [48] 中的结果表明，提取自海马、杏仁核和下丘脑的体积特征在使用 Logistic 回归和 SVM 进行侧化时提供了最高精度。同时，将腹状核作为第四个体积特征加入后，LR 方法的精度未提升，而 SVM 的精度下降。

研究结构的体积特征的绝对值（均值和标准差），发现这些特征既不能用于**侧化**，也不能用于**左/右侧化**，无论是**海马萎缩（HS-P）**患者还是**非海马萎缩（HS-N）**患者。相反，由 **Eq. (6.3)** 计算得到的**归一化体积特征**在**海马**上显示出**HS-P**组内左右侧患者之间**不存在重叠**。因此，**海马萎缩**的归一化体积特征能够在 **HS-P** 患者中**100%** 精确地侧化 **mTLE**。然而，**归一化体积特征**并未能够**完全区分 HS-N** 组内的左右侧患者。

总体而言，研究各结构萎缩与**癫痫侧性**之间的关系的结果表明，**归一化体积特征**——包括**海马**、**杏仁核**和**丘脑**——**单独**无法**唯一确定**癫痫侧性的**侧**。

在 **Ref. 61** 中，基于多结构体积特征的 **mTLE** 侧位化采用了 **Eq. (6.4)** 中简化的 **logistic probability function**。68 名患者的参数估计和位置结果如 **Figure 6.4a** 所示。判别阈值被设定为 **logistic probability function** 等于 **0.5**：

$${Pr\left\lbrack L \middle| \operatorname\left\lbrack {f_{1},\operatorname{}f_{2},\operatorname{}f_{3}} \right\rbrack \right\rbrack = \frac{e^{\beta_{0}^{L} + \beta_{1}^{L}f_{1} + \beta_{2}^{L}f_{2} + \beta_{3}^{L}f_{3}}}{1 + e^{\beta_{0}^{L} + \beta_{1}^{L}f_{1} + \beta_{2}^{L}f_{2} + \beta_{3}^{L}f_{3}}} = 0.5}\mspace{54mu}\operatorname{(6.5)}$$

这导致在三维特征空间中出现一个**平面**，即 `β_0^L + β_1^L f_1 + β_2^L f_2 + β_3^L f_3 = 0`。该平面可以在二维特征空间中投影，例如 **海马–杏仁核** 和 **海马–丘脑** 空间。 **Figure 6.4b** 展示了三维特征空间中左、右 **TLE** 患者的散点图以及决策平面。为了更好地说明，决策平面在对应的二维特征空间中投影，分别在 **Figure 6.4c** 和 **d**。

![FIGURE 6.4 Illustration of logistic regression of multi-structural volumetric features for mTLE lateralization. (a): Left lateralization probability based on Eq. (6.4) for all mTLE cases (left mTLE cases shown by blue rectangles and right mTLE by red triangles). (b): Scatter plot of the mTLE patients in the three-dimensional feature space defined by the volumetric features of hippocampus, amygdala, and thalamus. Since the decision plane is parallel to the view angle, it is seen as a line. (c and d): Decision plane projected onto the two-dimensional feature spaces defined by the volumetric features of the hippocampus and amygdala, and hippocampus and thalamus, respectively.](img/fig6_4.jpg)

FIGURE 6.4 Illustration of logistic regression of multi-structural volumetric features for mTLE lateralization. (a): Left lateralization probability based on Eq. (6.4) for all mTLE cases (left mTLE cases shown by blue rectangles and right mTLE by red triangles). (b): Scatter plot of the mTLE patients in the three-dimensional feature space defined by the volumetric features of hippocampus, amygdala, and thalamus. Since the decision plane is parallel to the view angle, it is seen as a line. (c and d): Decision plane projected onto the two-dimensional feature spaces defined by the volumetric features of the hippocampus and amygdala, and hippocampus and thalamus, respectively.

## 6.4 Discussion

在本章中，我们回顾了旨在**开发结构生物标志物**以**侧化 mTLE** 的研究。其目标是通过**提取、选择和修改结构性和纹理特征**，来**诊断癫痫**或**侧位化 mTLE 患者**。

在 **Study I** 中，采用**线性判别器**利用 **FLAIR** 和**体积特征**区分**右侧**与**左侧** mTLE。海马的 **FLAIR 均值信号强度** 和 **标准差** 组合能够**有效**区分 mTLE 患者的**侧向**（**准确率 98%**），而**海马体积特征**仅能达到 **83%** 的准确率。该准确率是在**不存在双侧患者**且**未考虑对照组**的情况下获得的。当使用对照组来确定不确定的边界时，准确率下降至 **75%**（详情请参见 **Table 6.1**）。基于本研究提供的证据，我们得出结论：**海马 FLAIR 强度的不对称性（均值和标准差）** 可能为**海马萎缩（HS）**及**癫痫侧向**提供**额外生物标志物**，除了**海马体积不对称**之外。

除了海马的均值和标准差外，本研究还提取了 **四种传统纹理特征**（**共现矩阵、运行长度矩阵、绝对梯度、直方图**）来研究 **FLAIR 强度** 的纹理特征。由 **Eq. (6.1)** 定义的**小波变换能量特征**能够以 **94%** 的准确率正确分类**单侧海马萎缩**为**右侧**和**左侧** mTLE，这表明**小波基特征提取**具备用于 mTLE 侧位化的能力。关于本研究可能引发的三个问题：(1) **样本量小**（36 名患者，20 左侧、16 右侧），(2) **未将双侧病例作为额外类别**，(3) **依赖于分割准确性**。

在 **Study II** [37]，当**海马萎缩不存在**时，采用**杏仁核 FLAIR 强度特征**进行侧位化。仅使用杏仁核特征时，**侧向**的**准确率仅为 29%**；而使用**海马**的类似特征则可达到 **70%** 的准确率。值得注意的是，**22%** 的**无法**以**信心**侧位化的**海马 FLAIR** 案例，能够**信心**地使用**杏仁核 FLAIR** 特征进行侧位化，这可能是**以往报告** [64] 的有力证据。此外，结果表明**自动化杏仁核分割**足以满足本研究需求，所有**错误侧位**的患者均落在**不确定边界**内。由于本研究使用的数据来自不同扫描仪（1.5T 和 3T），若**未校正 FLAIR 图像的强度不均匀**，扫描仪差异可能会影响结果。

与 **Study I** 类似，本研究**未考虑双侧病例**，因为重点在于**Engel Ia 结果**的患者。这意味着**前一研究缺乏双侧类别**的局限性仍未得到解决，而另外两项局限性已得到适当处理。该研究的另一局限性是**未探讨与 mTLE 相关的杏仁核体积变化**。

- [综合研究](https://wiki.example.org/feynmans_learning_method)表明，在因 mTLE 而受影响的白质结构（cingulum、fornix 和 corpus callosum）中，FA 表现出相对于非癫痫患者的单侧和双侧 mTL 的独特模式。结果显示，fornix、cingulum 和 corpus callosum 的亚区 FA 可在所有单侧 mTLE 案例中确定癫痫侧别。此外，海马的体积和 FLAIR 强度变化表明，尽管这些特征有助于侧别定位，但无法区分单侧与双侧 mTLE 案例。

数据采用单台扫描仪收集，这明显降低了不良的变异性，并提供了稳定的分类结果。然而，拟议模型在多扫描仪/多中心研究中的适用性仍需验证。此外，尤其是双侧组的受试者样本量较小，可视为本研究的局限性。

Study IV 比较了基于统一分割和 Gram–Schmidt 方法获得的分割结果，对 mTLE 患者与对照组的准确性进行了评估。结果表明，统一分割法得到的区域纹理特征比 Gram–Schmidt 方法更具歧视性。它们成功在三维纹理特征中检测出 mTLE 案例，并且整体脑纹理特征优于海马纹理特征。

在本章最后讨论的研究 [61] 中，发现三个神经解剖区域的标准化体积最适合 mTLE 侧别定位。该研究表明，海马和杏仁核的标准化体积组合在 mTLE 侧别定位中实现了 94.1% 的准确率。若不整合杏仁核体积特征，仅用海马体积特征即可达到 82.4% 的准确率。此外，加入丘脑体积特征后，mTLE 侧别定位的准确率提升至 98.5%。

上述所有研究的训练阶段使用的患者均被诊断为 mTLE，因此拟议的机器学习模型适用于 mTLE 患者。它们可能不适用于其他类型的癫痫，例如额外时区癫痫。此外，拟议特征和分类模型的性能应在侧别、新皮层 TLE 患者中进一步研究。

## 6.5 Conclusion

本文所用的特征可归为四类：(1) 体积特征，包括研究 I–V 中使用的单一和多结构体积；(2) 第一阶和第二阶纹理特征，用于 Study IV；(3) DTI 特征，用于 Study III；(4) FLAIR 强度特征，包括研究 I–III 中的单一和多结构特征。我们描述了这些特征在药物难治性 mTLE 患者侧别定位中的作用。

Ref. [37,61] 中提出的多结构方法在降低患者成本和风险的同时，提供了高可靠性的癫痫侧别预测。基于这些结果，可以得出结论：结合 Ref. [37] 中的 FLAIR 强度特征以及 Ref. [61] 中提出的三结构成像生物标志物，可能进一步提升侧别准确率。然而，这些方法尚未在双侧癫痫的情形下得到验证。为纳入双侧病例，未来工作可采用类似 Ref. [20] 的方法进行扩展。

## References

1. D. Hirtz, D. J. Thurman, K. Gwinn-Hardy, M. Mohamed, A. R. Chaudhuri, and R. Zalutsky, “How common are the ‘common’ neurologic disorders?,” *Neurology*, vol. 68, no. 5, pp. 326–337, Jan. 2007.
2. G. S. Bell, A. Neligan, and J. W. Sander, “An unknown quantity – The worldwide prevalence of epilepsy,” *Epilepsia*, vol. 55, no. 7, pp. 958–962, 2014.
3. A. T. Berg, et al., “Revised terminology and concepts for organization of seizures and epilepsies: Report of the ILAE Commission on Classification and Terminology, 2005–2009,” *Epilepsia*, vol. 51, no. 4, pp. 676–685, 2010.
4. A. M. Harriott and W. O. Tatum, *Electroclinical Syndromes: Adolescent Onset*, Swaiman's Pediatric Neurology, 6th ed.: Elsevier Inc., 2017.
5. R. D. G. Blair, “Temporal lobe epilepsy semiology,” *Epilepsy Res. Treat.*, vol. 2012, pp. 1–10, 2012.
6. J. A. Hill and N. Venna, *Human Herpesvirus 6 and the Nervous System*, 1st ed., vol. 123: Elsevier B.V., 2014.
7. F. J. Rugg-Gunn, et al., “Diffusion tensor imaging in refractory epilepsy,” *Lancet*, vol. 359, no. 9319, pp. 1748–1751, 2002.
8. R. P. Carne, et al., “MRI-negative PET-positive temporal lobe epilepsy: A distinct surgically remediable syndrome,” *Brain*, vol. 127, no. 10, pp. 2276–2285, 2004.
9. J. C. Bulacio, et al., “Long-term seizure outcome after resective surgery in patients evaluated with intracranial electrodes,” *Epilepsia*, vol. 53, no. 10, pp. 1722–1730, 2012.
10. Engel J Jr, Van Ness PC, Rasmussen T, et al. Outcome with respect to epileptic seizures. In: Engel J Jr, editor. *Surgical Treatment of the Epilepsies*. 2nd ed. New York: Raven Press; 1993:609–622.
11. E. Achten, P. Boon, T. Van De Kerckhove, J. Caemaert, J. De Reuck, and M. Kunnen, “Value of single-voxel proton MR spectroscopy in temporal lobe epilepsy,” *Am. J. Neuroradiol.*, vol. 18, no. 6, pp. 1131–1139, 1997.
12. J. De Tisi, et al., “The long-term outcome of adult epilepsy surgery, patterns of seizure remission, and relapse: A cohort study,” *Lancet*, vol. 378, no. 9800, pp. 1388–1395, 2011.
13. G. D. Cascino, “Neuroimaging in partial epilepsy: Structural magnetic resonance imaging,” *J. Epilepsy*, vol. 11, no. 3, pp. 121–129, 1998.
14. M. Thom, “Review: Hippocampal sclerosis in epilepsy: A neuropathology review,” *Neuropathol. Appl. Neurobiol.*, vol. 40, no. 5, pp. 520–543, 2014.
15. M. Thom, “Hippocampal sclerosis: Progress since sommer,” *Brain Pathol.*, vol. 19, no. 4, pp. 565–572, 2009.
16. I. Blümcke, et al., “International consensus classification of hippocampal sclerosis in temporal lobe epilepsy: A Task Force report from the ILAE Commission on Diagnostic Methods,” *Epilepsia*, vol. 54, no. 7, pp. 1315–1329, 2013.
