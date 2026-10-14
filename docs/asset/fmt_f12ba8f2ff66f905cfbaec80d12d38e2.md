
2. 然后应用快速傅里叶变换（FFT）并计算 FFT 结果的共轭。之后，计算镶嵌后图像的高度和宽度等参数。

3. 镶嵌后，加载图像以进行进一步处理并将镶嵌图像保存在数据库中。

4. 然后对镶嵌指纹图像进行细节点提取。

5. 对查询图像进行细节点提取处理。

6. 然后比较两幅图像，匹配算法将检查该过程的有效性。

7. 对该过程进行性能分析。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_892_0.png)

图 29.5 GUI 界面。

#### 29.7.1.3 实验结果

以下屏幕截图代表指纹镶嵌过程：

1. 图形用户界面（图 29.5）。
2. 指纹图像被加载（图 29.6）。
3. 生成镶嵌图像（图 29.7）。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_892_1.png)

图 29.6 在坐标轴中加载指纹图像。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_893_0.png)

图 29.7 镶嵌图像。

4. 镶嵌图像生成后，它被保存在数据库中以进行匹配过程（图 29.8）。
5. 用于模板匹配的另一个 GUI 被调用（图 29.9）。
6. 查询图像和存储图像正在被比较，为此图像从数据库中获取（图 29.10）。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_893_1.png)

图 29.8 保存镶嵌图像。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_894_0.png)

图 29.9 匹配的 GUI。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_894_1.png)

图 29.10 加载用于匹配的指纹图像。

7. 对加载的指纹图像进行直方图均衡化（图 29.11）。
8. 对生成的图像执行 FFT（图 29.12）。
9. 对指纹图像进行二值化，即将其转换为 0 和 1 的形式（图 29.13）。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_895_0.png)

图 29.11 直方图均衡化图像。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_895_1.png)

图 29.12 第一次傅里叶变换指纹图像。

- 10. 找到脊线方向 (图 29.14)。
- 11. 计算感兴趣区域 (ROI) (图 29.15)。
- 12. 进行脊线细化 (图 29.16)。
- 13. 细化处理后去除 H-Breaks (图 29.17)。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_896_0.png)

图 29.13 图像二值化。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_896_1.png)

图 29.14 脊线方向。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_897_0.png)

图 29.15 ROI 图像。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_897_1.png)

图 29.16 细化图像。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_898_0.png)

图 29.17 去除 H-breaks 的指纹图像。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_898_1.png)

图 29.18 去除尖峰图像。

- 14. 删除指纹图像中可能造成脊线存在假象的尖峰 (图 29.18)。
- 15. 进行细节点提取 (图 29.19)。
- 16. 去除上述图像中存在的假细节点，并提取有助于匹配过程的真实细节点 (图 29.20)。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_899_0.png)

图 29.19 提取细节点图像。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_899_1.png)

图 29.20 提取真实细节点图像。

- 17. 将提取细节点的图像保存到数据库中 (图 29.21)。
- 18. 调用匹配程序以将查询模板与存储的图像进行匹配 (图 29.22)。
- 19. 匹配过程的输出 (图 29.23)。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_900_0.png)

图 29.21 图像保存在数据库中。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_900_1.png)

图 29.22 指纹模板匹配。

## 29.7.2 利用离散小波变换进行指纹质量改进

### 29.7.2.1 图像增强方法

在指纹识别过程中，去噪是一个关键问题。有不同去噪方法用于使指纹图像平滑或无噪声。其中大多数用于使图像无失真。通常，噪声/失真

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_901_0.png)

图 29.23 匹配结果。

与从指纹数据捕获的原始信号的频率不同。指纹图像增强过程用于提高完整图像的强度，然后通过映射特定阈值对其进行归一化。为此目的使用图像增强算法。因此，需要分割过程将指纹保持在指定区域的框架内 [37]。为此目的，指纹图像分解以非重叠方式使用。这种分解和所涉及的方差分析用于分离前景和背景部分，分别包括脊线和谷线。以下步骤被考虑用于图像增强：

- 1. **归一化**
- 2. **小波分解**
- 3. **每个块的噪声去除**
- 4. **与阈值匹配**
- 5. **图像重建**

脊线方向和频率是主要关注的问题。脊线方向是用于指纹识别的主要特征 [37]。就频域而言，指纹脊线和谷线负责形成一种正弦波，具有一定的频率、方向、角度，并且在准确性方面对识别系统至关重要。从该领域的研究可以明显看出，为了有效地分析信号的频率谱并实现其适当应用，可以使用离散小波变换 (DWT)。一种本质上为低通的有限脉冲响应 (FIR) 滤波器由尺度滤波器表示并定义为正交小波。

小波由小波函数 Ψ(t)（即母小波）和时域中的尺度函数 Φ(t)，父小波定义 [10]。

图像滤波对于图像平滑和噪声去除是必要的。由于使用低通滤波器来减小像素值之间的差异，因此使用正交小波低通 FIR 滤波器进行噪声去除/图像平滑。滤波器的一般公式为：

F(t) = 1 ; if  f < (threshold − ω)

F(t) = 0 ; if  f > (threshold − ω)

- f 表示滤波器
- ω 表示小波的波长
- 阈值用于小波系数阈值处理

在不同类型的小波变换中，DWT 是临界采样且使用最广泛的 [5,11]。

以下伸缩和小波方程用于表示多分辨率框架：尺度函数和小波也通过它表示。

φ(t) = √2 Σ₁ⁿ h0(n) φ(2t − n)

Ψ i(t) = √2 Σ₁ⁿ hi(n) φ(2t − n)

- i = 1, 2
- hi(n), n ∈ ℤ

φ(t) 表示为尺度函数，Ψ i(t) 表示伸缩后的小波，而 hi 表示为数字滤波器组的滤波器。如果 hi(n) 满足下面给出的完美重建条件，并且 φ(t) 足够规则，则 Ψ i(t) 的二进伸缩和平移构成 L²(R) 的紧框架。

研究人员讨论了过度采样时间和频率的扩展小波变换，在本例中该因子为 2。该变换具有中间尺度，即临界采样 DWT 的每对尺度之间有一个尺度。小波框架有两个生成器 (t)；其中 i = 1, 2，这意味着第一个小波的频谱集中在第二个小波的频谱与其伸缩版本频谱之间，即 Ψ i(t) 集中在 Ψ 2(t) 和 Ψ 2(2t) 之间。第二个小波由整数的一半倍数平移，而不是整数倍。

现在我们的目标很简单，即开发一组生成紧小波框架的滤波器，为此我们将找到滤波器的条件。考虑 Z 变换的低通滤波器 h0。如果我们认为 P(n) 和 Q(n) 分别是输入和输出信号的值，则 Z 变换为

$Q(Z)=\sum_{k=0}^{n} q(n) Z^{-k}$

整理后，

$Q(n)=\sum_{k=0}^{n} q[k]\delta[n-k] \rightarrow Q[Z]=\sum_{0}^{n} q[k](Z^{-1})^{k}$

这推导出低通滤波器 ho 不是最大平坦线性相位滤波器的因子，在本例中 ho 是有限脉冲响应滤波器，且 h0 和 h1 是反对称的。δ[n−k] 表示从 k = 0 到 n 累加的时间延迟脉冲。

指纹图像去噪过程使用如下结构：

- 1. 将图像分解为若干块。
- 2. 用离散小波变换对每个块进行去噪
- 3. 重建指纹图像

本章中，小波的构造将取决于消失矩。消失矩是小波的特征。

### 29.7.2.2 图像增强算法：归一化 – 归一化图像

- 1. 计算迭代快速傅里叶变换，然后对功率谱的每个片段取其平方。
- 2. 按片段大小和总能量对其进行归一化。
- 3. 应用 Gabor 滤波器滤除图像的失真部分。
- 4. 图像质量值可以通过图像每个片段的二维滤波谱之和来计算。
- 5. 对于每幅图像，识别出图像质量最高的片段。
- 6. 将此图像质量转换为归一化图像质量以实现等效。
- 7. 用平均灰度值的平方对图像质量加权。
- 8. 对图像的每个片段进行图像质量交叉检查，如果出现不均匀分布，则相应调整图像质量。
- 9. 缩放图像。

### 29.7.2.3 算法实现后的结果 (图 29.24)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_904_0.png)

图 29.24 图像增强前后的指纹图像。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_905_0.png)

Figure 29.24 (Continued) 指纹图像在图像增强前后的图像。

(续)

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_906_0.png)

Figure 29.24 (Continued) 指纹图像在图像增强前后的图像。

## 29.8 结论

本章描述并讨论了生物识别提供的不同安全方面。广泛讨论的安全技术是指纹水印和指纹镶嵌。

提取细节点在计算指纹识别系统可靠性方面发挥着关键作用。细节点提取过程的精度与安全系统的可靠性成正比。本章提出了一种算法，通过整合同一图像的多次印记并据此创建复合图像来构建镶嵌模板。提取的细节点用于匹配目的，以确定用户的身份是否得到验证。本章讨论的镶嵌算法描述了从多张点触图像创建复合图像的过程，并有效解决了因部分采集的指纹图像而遇到的低效和不准确问题，这些问题可能导致识别无效。还讨论了一种处理断裂脊线/虚假细节点及其去除的过程，以提供系统的改进安全性。

## 参考文献

- 1. Ailisto, H. L. (2004). 指纹图像增强方法的综述。 International Journal of Image and Graphics, 3 (3): 401–424.
- 2. Simoncelli, E. P., Freeman, W. T., Adelson, E. H., and Heeger, D. J. (1992). 可平移的多尺度变换。 IEEE Transactions on Information Theory, 38 (2): 587–607.
- 3. Almansa, A. and Lindeberg, T. (2000). 指纹增强：通过形状自适应的尺度空间算子并结合自动尺度选择。 IEEE Transactions on Image Processing, 9 (12): 2027–2042.
- 4. Amayeh, G. B. (2009). 通过基于融合置信度的在线手指模板更新来改进基于手的验证。 IEEE Transactions on Pattern Recognition, 978–984.
- 5. Ang, R. S. (2002). 指纹方向场和奇异点计算的系统方法。 IEEE Transactions on Pattern Analysis and Machine Intelligence, 24 (7): 905–919.
- 6. Beveridge, J. R. (2009). 影响人脸识别大挑战中算法性能的因素。 Computer Vision and Image Understanding, 113 (6): 750–762.
- 7. Bhattacharya, A. K. (2001). 用于卫星图像的改进纹理滤波器。 Asian Conference on Remote Sensing, pp. 78–84.
- 8. Bian, Z. Z. (2002). 基于知识的指纹后处理。 International Journal Pattern Recognition Artificial Intelligence, 16 (1): 53–67.
- 9. Blotta, E. and Moler, E. (2004). 通过微分滞后处理增强指纹图像。 Forensic Science International, 141(2–3): 109–113.
- 10. Boerer, J. B. (2001). 基于多特征的指纹数据库索引。 Proceedings of Workshop on Circuits, Systems, and Signal Processing, pp. 58–66, 25–27 Nov 2003, Veldhoven, the Netherlands.
- 11. Bolle, R. M. and Pankanti, S. (2000). 基于生物识别的身份验证系统（FRR）的评估技术。 *Proceedings of International Conference on Pattern Recognition (ICPR)*, 2: 2831–2837, 3–7 Sept. 2000, Barcelona, Spain.
- 12. Bolle, R. C. (2002). 生物识别的隐患与补丁。 *Transaction of Pattern Recognition*, 35 (12): 2727–2738, October 2001, Exploratory Computer Vision Group, IBM Thomas J. Watson Research Center, Yorktown Heights, NY 10598, USA.
- 13. Cappelli, R. D. (2001). 指纹图像中塑性失真的建模。 *Advances in Pattern Recognition*, March 11–14, 369–376. Berlin, Germany: Springer, March 11–14, 2001, Springer-Verlag Berlin, Heidelberg.
- 14. Chang Huang, H. A. (2007). 高性能旋转不变多视角人脸检测。 *IEEE Transaction on Pattern Analysis and Machine Intelligence*, 671–686, IEEE Transactions.
- 15. Chikkerur, S. G. (2005). 使用可转向楔形滤波器对指纹图像中的细节点进行验证。 *IEEE Transaction on Pattern Recognition and Machine Intelligence*, 45–51, IEEE Transactions.
- 16. Clarke, R. (1994). 信息系统中的人类识别：管理挑战与公共政策问题。 *Information Technology & People*, 7 (4): 6–37, 4–7 December 1994, Canberra.
- 17. Dass, S. (2004). 指纹图像中方向场和奇异点提取的马尔可夫随机场模型。 *IEEE Transactions on Image Processing*, 13 (10): 1358–1367, IEEE Transactions.
- 18. Dodis, Y. R. (2004). 模糊提取器：如何从生物识别和其他噪声数据中生成强密钥。 *Proceedings of International Conference Theory and Applications of Cryptographic Techniques*, pp. 523–540. Berlin, Germany: Springer, 2–6 May 2004, Interlaken, Switzerland.
- 19. Eswara, R. B. (2007). 通过边缘方向运动上的简单模式进行纹理分类。 *International Journal of Computer Science and Network Security*, 7 (11): 220–225.
- 20. Farina, A. Z. (2001). 从骨架化二值图像中提取指纹细节点。 *Transaction of Pattern Recognition*, 32 (5): 877–889.
- 21. Fayyaz, A. M. (2004). 使用细节点匹配的指纹识别与验证系统。 *National Conference on Emerging Technologies*, 2: 141–146, 4–6 December, Karachi, Pakistan.
- 22. Feng, Y. C. (2010). 生成安全且具有区分度的人脸模板的混合方法。 *IEEE Transactions on Information Forensics and Security*, 201–212.
- 23. Galy, N. C. (2007). 用于单线扫描传感器的完整指纹验证系统。 *IEEE Sensor Journal*, 7 (7): 1054–1065.
