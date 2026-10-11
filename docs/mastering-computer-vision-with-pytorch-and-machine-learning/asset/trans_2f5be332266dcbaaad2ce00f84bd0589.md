

#### 7.3.2 交并比 (IOU) 与损失函数

每张图像的边界框由 `7 × 7` 网格单元编码。对于包含 13 个类别的 Chess 数据集，每个网格单元有 `(13 + 5 × 2)` 个立方体。模型预测中每个网格单元的最后五个立方体（第 18 到 22 个）用于另一个预测对象的边界框。模型预测的每个网格单元可预测两个边界框。然而，我们仅使用与同一网格单元中真实边界框具有较高 IOU 值的那个边界框来计算损失函数值。我们需要回顾一下第 [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2) 章中关于图像分类的 IOU。

假设我们有两张纸，大小相同：`10 × 10 cm²`。如果上面的纸覆盖了另一张纸 1/4 的面积，则两张纸的相交面积为 `25 cm²`。此时我们可以计算两张纸的 IOU：`IOU = 25/(100 + 100 − 25) = 1/7`。当它们完全重叠时，IOU 值为 1。计算机的处理方式不同。使用 Cell 04 第 17 行的代码，我们获得一批变换后的图像及其编码在网格单元中的边界框，用于训练数据加载器中的一批样本。这批边界框即为我们的目标。将这批变换后的图像输入 Cell 05 第 15 行的 `ResNet18` 模型，我们可以获得形状为 `N × 1127` 的模型输出 `y_hat`，其中 `N` 为批次大小：`8`。随后 `y_hat` 和目标被送入第 7.3.3 节 Cell 06（第 07 行）定义的损失类中。根据 Cell 06 第 10、12 和 14 行的代码，我们得到一批真实边界框、两批预测边界框。定义在 `Utility_fn(1/5)` 中的以下 IOU 函数将利用每个边界框的中心坐标 (`x_c`, `y_c`)、宽度 (`w`) 和高度 (`h`) 按照以下公式计算 IOU 值：

$$
\begin{matrix} 
{x_{1\min} = x_{1c} - \frac{1}{2}w_{1}} \\ 
{y_{1\min} = y_{1c} - \frac{1}{2}h_{1}} \\ 
{x_{1\max} = x_{1c} + \frac{1}{2}w_{1}} \\ 
{y_{1\max} = y_{1c} + \frac{1}{2}h_{1}} 
\end{matrix}
\begin{matrix} 
{x_{2\min} = x_{2c} - \frac{1}{2}w_{2}} \\ 
{y_{2\min} = y_{2c} - \frac{1}{2}h_{2}} \\ 
{x_{2\max} = x_{2c} + \frac{1}{2}w_{2}} \\ 
{y_{2\max} = y_{2c} + \frac{1}{2}h_{2}} 
\end{matrix}
$$

graphic style="width:15.9375em;" xlink:href="bk978-0-7503-6244-3ch7ueqn6.gif" position="float"/

$$
\begin{matrix} 
{x_{3\min} = {\max}\left( {x_{1\min},x_{2\min}} \right)} \\ 
{y_{3\min} = {\max}\left( {y_{1\min},y_{2\min}} \right)} \\ 
{x_{3\max} = {\min}\left( {x_{1\max},x_{2\max}} \right)} \\ 
{y_{3\max} = {\min}\left( {y_{1\max},y_{2\max}} \right)} 
\end{matrix},
\begin{matrix} 
{w_{3} = x_{3\max} - x_{3\min}} \\ 
{h_{3} = y_{3\max} - y_{3\min}} \\ 
{A_{12} = w_{1}h_{1} + w_{2}h_{2}} \\ 
{{IOU} = \frac{w_{3}h_{3}}{A_{12} - w_{3}h_{3}}} 
\end{matrix}
$$

graphic style="width:19.875em;" xlink:href="bk978-0-7503-6244-3ch7ueqn7.gif" position="float"/

IOU 函数的输入为真实边界框和预测边界框的参数。它们具有相同的结构：`[…, x_c, y_c, w, h]`。三个点表示数据加载器中一批数据内某图像的索引、图像 `7 × 7` 网格单元的行索引和列索引。两个矩形的相交区域仍为矩形。相交区域左上角和右下角的坐标可从上述公式获得，其中变量下标 1、2、3 分别代表预测边界框、真实边界框及其相交区域。要使用这些公式，我们应使每个边界框的四个参数处于同一尺度。然而，每个边界框的中心坐标归一化因子为 `64`，宽度和高度归一化因子为 `448`。Cell 06 第 10、12 和 14 行的常量 `self.S` 用于将它们设置为同一标量。要计算同一图像不同网格单元中两个边界框的 IOU，我们还需分别将各网格单元的行索引和列索引考虑进 `y_c` 和 `x_c` 中。请注意数据结构：IOU 函数中的 `boxes_preds[…, 0:1]`。采用这种张量结构，我们保留了原始张量的形状，从而可以对 4D 张量进行计算而无需 for 循环，以节省计算时间。若数据结构像 `boxes_preds[…, 0]` 这样，我们将丢失原始张量的最后一个维度，并在大量 for 循环中浪费时间。数据集中所有图像所有类别的平均 IOU 值即为 mAP 指标。Aladdin Persson 拥有关于 [IOU](https://www.youtube.com/watch?v=XXYG5ZWtjj0…list=RDCMUCkzW5JSFwvKRjXABI-UTAkQ…index=3)、[mAP](https://www.youtube.com/watch?v=FppOzcDvaDI…list=RDCMUCkzW5JSFwvKRjXABI-UTAkQ…index=2)、非极大值抑制 ([NMS](https://www.youtube.com/watch?v=YDkjWEN8jNA…list=RDCMUCkzW5JSFwvKRjXABI-UTAkQ…index=4)) 等内容的非常有用的 YouTube 视频。以下部分代码受其 MIT 许可的 [GitHub](https://github.com/aladdinpersson/Machine-Learning-Collection/tree/a2ee9271b5280be6994660c7982d0f44c67c3b63/ML/Pytorch/object_detection/YOLO) 代码启发。

![](images/bk978-0-7503-6244-3ch7uf10a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf10b_pr.gif)

在模型训练期间，以下损失函数的五个部分（Redmon *et al* [2016](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib6)）由均方误差算法优化。显而易见，第一部分针对边界框中心坐标的误差，第二部分针对边界框尺寸（宽度和高度）平方根的误差。使用尺寸的平方根是为了平衡较大和较小边界框之间的误差。因为在 YOLO 编码中边界框的尺寸值小于 `1.0`，平方根运算会非线性地放大尺寸误差，且较小尺寸的误差被放大得更多。从 `(0.1)^(1/2)` 和 `(0.01)^(1/2)` 的值中，你就能明白为什么不在损失函数的第二部分直接使用边界框的尺寸。一个较大的超参数 `λ[coord] = 5` 用于增强边界框的坐标误差和尺寸误差。

$$
\begin{matrix} 
{L = \lambda_{coord}\sum\limits_{i = 0}^{48}{\sum\limits_{j = 0}^{1}{1_{ij}^{obj}\left\lbrack {\left( {x_{i} - {\widehat{x}}_{i}} \right)^{2} + \left( {y_{i} - {\widehat{y}}_{i}} \right)^{2}} \right\rbrack}} + \lambda_{coord}\sum\limits_{i = 0}^{48}{\sum\limits_{j = 0}^{1}{1_{ij}^{obj}\left\lbrack {\left( {\sqrt{w_{i}} - \sqrt{{\widehat{w}}_{i}}} \right)^{2} + \left( {\sqrt{h_{i}} - \sqrt{{\widehat{h}}_{i}}} \right)^{2}} \right\rbrack}}} \\ 
{+ \ \sum\limits_{i = 0}^{48}{\sum\limits_{j = 0}^{1}{1_{ij}^{obj}\left( {{\widehat{C}}_{i} - C_{i}} \right)^{2}}} + \lambda_{noobj}\sum\limits_{i = 0}^{48}{\sum\limits_{j = 0}^{1}{\left( {1 - 1_{ij}^{obj}} \right)\left( {{\widehat{C}}_{i} - C_{i}} \right)^{2}}} + \sum\limits_{i = 0}^{48}{1_{ij}^{obj}\sum\limits_{c \in {classes}}\left( {p_{i}\left( c \right) - {\widehat{p}}_{i}\left( c \right)} \right)^{2}}} 
\end{matrix}
$$

graphic style="width:33.8125em;" xlink:href="bk978-0-7503-6244-3ch7ueqn8.gif" position="float"/

