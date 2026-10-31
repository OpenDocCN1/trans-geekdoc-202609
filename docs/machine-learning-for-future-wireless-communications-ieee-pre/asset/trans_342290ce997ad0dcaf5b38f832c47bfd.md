
使用处理后的移动性数据训练三层 `LSTM` 网络可分为三个主要步骤。(i) 位置序列由全连接输入层处理，使得序列中的每个值都映射为多维特征张量。(ii) 处理后的序列被送入移动性模型的主要部分。(iii) 全连接输出层将每个时间步的最后一个 `LSTM` 层的输出 ![图像](images/c07-i0044.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>i</mi></mrow></math> 映射为位置点 ![图像](images/c07-i0045.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mrow><mover accent="true"><mi>p</mi><mo>&#732;</mo></mover></mrow><mi>i</mi></msub></mrow></math>，其维度与 ![图像](images/c07-i0046.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>p</mi><mi>i</mi></msub></mrow></math> 相同，以得到输出序列 ![图像](images/c07-i0047.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mover accent="true"><mi>p</mi><mo>&#732;</mo></mover><mo>=</mo><mo stretchy="false">&#123;</mo><msub><mrow><mover accent="true"><mi>p</mi><mo>&#732;</mo></mover></mrow><mn>0</mn></msub><mo>,</mo><msub><mrow><mover accent="true"><mi>p</mi><mo>&#732;</mo></mover></mrow><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mrow><mover accent="true"><mi>p</mi><mo>&#732;</mo></mover></mrow><mrow><mi>T</mi><mo>&#8722;</mo><mn>1</mn></mrow></msub><mo stretchy="false">&#125;</mo></mrow></math>，其中 ![图像](images/c07-i0048.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mrow><mover accent="true"><mi>p</mi><mo>&#732;</mo></mover></mrow><mi>i</mi></msub></mrow></math> 表示第 ![图像](images/c07-i0049.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>i</mi><mo>+</mo><mn>1</mn></mrow></math> 时间步的位置预测结果。训练目标是减小损失函数的值，该损失函数可以是当输入 ![图像](images/c07-i0050.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>p</mi><mi>i</mi></msub></mrow></math> 为二维坐标时的均方误差 (`MSE`)，或当 ![图像](images/c07-i0051.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><msub><mi>p</mi><mi>i</mi></msub></mrow></math> 为小区 ID 时在所有时间步上的交叉熵。Wang et al. ([2018](#c07.xhtml#c07-bib-0027)) 在两种空间粒度（即坐标级和小区级）上对不同的移动性预测方法进行了相关实验。

![图 7.7 LSTM 方案和移动性预测的基本框架。](images/c07f007.jpg)

[图 7.7](#c07.xhtml#R_c07-fig-0007) `LSTM` 方案和移动性预测的基本框架。

![图 7.8 在坐标级数据集上对移动性预测性能的比较，跨越五小时（在一小时观察之后），采用机器学习领域中两种具有代表性的可行算法：LSTM 和线性回归。前三小时为单步预测，最后两小时为多步预测。(a) 和 (b) 分别显示 x 坐标和 y 坐标的预测位置；(c) 和 (d) 分别表示单步预测和多步预测中的距离误差。](images/c07f008.jpg)

[图 7.8](#c07.xhtml#R_c07-fig-0008) 在坐标级数据集上对移动性预测性能的比较，跨越五小时（在一小时观察之后），采用机器学习领域中两种具有代表性的可行算法：`LSTM` 和线性回归。前三小时为单步预测，最后两小时为多步预测。(a) 和 (b) 分别显示 x 坐标和 y 坐标的预测位置；(c) 和 (d) 分别表示单步预测和多步预测中的距离误差。

就坐标级预测而言，[图 7.8](#c07.xhtml#c07-fig-0008) 展示了基于 `LSTM` 的框架与传统线性回归的性能比较。如 [图 7.8](#c07.xhtml#c07-fig-0008)a 和 b 所示，在一小时观察（左侧区域）之后，两种方法首先在每个时间步给定完全可观测的真实值（用户的实际位置）进行单步预测（中间区域）。然而，当位置测量变得不可用时，传统的线性回归算法无法跟随用户轨迹的实际演变，而 `LSTM` 方案产生的预测具有更高的准确性。[图 7.8](#c07.xhtml#c07-fig-0008)c 和 d 进一步显示了单步和多步预测中预测结果与真实值之间的距离误差；可以观察到，两种方法在大多数单步预测情况下表现良好，但在多步预测情况下，`LSTM` 方案的性能远优于线性回归。

![图 7.9 在小区级数据集上对移动性预测性能的比较。](images/c07f009.jpg)

[图 7.9](#c07.xhtml#R_c07-fig-0009) 在小区级数据集上对移动性预测性能的比较。

小区级预测的结果在 [图 7.9](#c07.xhtml#c07-fig-0009) 中通过比较五位用户在不同算法下的预测准确率来展示，其中准确率定义为预测结果正确的数值所占百分比。结果验证了基于 `LSTM` 的框架总体上相比其他方法具有更优的性能。

### 7.4.2.2 基于空间信息辅助的 `LSTM` 个体移动性预测框架

[图 7.10](#c07.xhtml#c07-fig-0010) 显示了个体移动性预测基本 `LSTM` 框架的改进版本。该新提出的版本主要由三个模块组成：用于提取地理特征的空间模块、用于提供辅助信息的属性模块以及用于处理时序特征的时序 `LSTM` 模块。由于坐标级轨迹相比小区级轨迹能更准确地捕捉位置变化，并且在实践中更常用，该改进框架仅考虑坐标级情况。
