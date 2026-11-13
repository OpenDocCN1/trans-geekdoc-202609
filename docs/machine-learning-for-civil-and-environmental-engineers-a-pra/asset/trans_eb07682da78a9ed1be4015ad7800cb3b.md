

### Step 3: DataRobot 自动运行 Autopilot 模式。此分析的结果可以在 Leaderboard 选项卡下查看。如您所见，RandomForest Classifier (Gini) (BP43) 评分最高。您还可以看到 DataRobot 推荐该模型用于部署。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_232_0.png)

### Step 4: 让我们现在通过 Evaluate 选项卡访问混淆矩阵，来检查该模型的性能。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_232_1.png)

### Step 5: 查看每个特征的重要性以及特征对模型预测的影响。[34] 您可以使用 Select Class 选项来可视化特征对整个数据集（Aggregation）或特定类别的影响及效果。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_233_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_233_1.png)

[34] 我意识到此处未涵盖这些概念。我将把讨论留到下一章。目前，您可以将这些视为帮助我们理解模型如何得出预测的一种手段。

### Step 6: 最后，您可以查看 Data Quality Handling 报告，了解模型如何处理数据/数据集中出现的任何问题（例如，缺失值等）。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_234_0.png)

## 示例 2 [DataRobot, 回归]: 预测 CFST 的轴向强度。

第二个示例旨在使用机器学习预测充填混凝土钢管（CFST）的轴向抗压强度。我们的数据集中有 1260 个 CFST。每个列具有以下特征：列直径 D（mm）、列厚度 t（mm）、列长度 L（mm）、混凝土抗压强度 f_c'（MPa）和钢材屈服强度 f_y（MPa）。每个列的目标是轴向抗压强度 N（kN）。

请跟随接下来的几个代码片段，在此回归示例中使用 DataRobot，我们将使用随机森林算法。

### Step 1: 数据集上传后，选择 N 作为目标。您会注意到分析已更改为回归。选择手动建模模式并开始分析。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_234_1.png)

[35] 这是一种柱子类型，由充满混凝土的钢管组成。在此系统中，两种材料协同作用，复合柱可以发展出显著的轴向强度承载能力。

### Step 2: 转到 Repository 选项卡，选择 Random Forest Regressor (BP 75) 并运行任务。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_235_0.png)

### Step 3: 分析完成后，访问 Evaluate 选项卡，然后选择 Residuals。将 Data Selection 更新为 Validation（或 Holdout）。您还可以根据 DataRobot 采用的各种指标检查模型性能。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_235_1.png)

### Step 4: 将视图从 Residuals 分布更改为 Predictions 分布，并检查 Highlight in yellow residuals。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_236_0.png)

### Step 5: 要使用此模型对新数据进行预测，或预测数据集中所有观测值的轴向承载力，请导航至 Predict 选项卡。上传新表格以预测新观测值，只需选择 compute predictions 即可。下图显示了用于验证和保留数据的后者。然后，下载预测结果。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_236_1.png)

## 示例 3 [DataRobot, 异常检测] [36]: 预测 RC 柱的耐火性异常。

在此示例中，我们试图识别观察到的耐火性方面的异常行为。例如，在数据集中可用的 RC 柱中，是否有柱子的耐火程度可以被视为异常？

以下是我们数据集的一些信息，该数据集汇编了 144 个 RC 柱的数据：列宽 W（mm）、钢筋配筋比 r（mm）、列长度 L（mm）、混凝土抗压强度 fc（MPa）、钢材屈服强度 fy（MPa）、通过有效长度系数表示的约束条件、钢筋保护层 C（mm）、主轴方向施加载荷的偏心距 ex（mm）、施加载荷的大小 P（kN）和耐火性 FR（min）。

让我们前往 DataRobot 平台并按以下步骤操作。我们将应用带校准的局部异常因子异常检测和带校准的孤立森林异常检测算法。

### Step 1: 上传数据集并选择 No target？以切换到无监督分析。然后，选择 Anomalies。选择建模模式：Manual。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_237_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_237_1.png)

[36] 目前，DataRobot 的学生版不包含聚类。因此，我将展示此异常检测示例来涵盖无监督学习。我们将在 BigML 和 Exploratory 中重新讨论聚类。

### Step 2: 带校准的局部异常因子异常检测 (BP 8) 和带校准的孤立森林异常检测 (BP7) 算法。[37]

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_238_0.png)

### Step 3: 就 Synthetic AUC 指标比较分析结果。[38]

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_238_1.png)

[37] 此外，欢迎尝试算法章节中未涵盖的其他算法。

[38] 根据 DataRobot [33]：此指标从验证样本生成两个合成数据集——一个更正常，一个更异常，并相应地对样本进行标记。然后模型使用人工标签作为基准真值，对两个样本计算异常分数预测。例如，如果模型的 Synthetic AUC 为 0.9，则很可能优于 Synthetic AUC 分数为 0.5 的另一个模型。

### Step 4: 离开 *Leaderboard* 选项卡并导航至 *Insights* 选项卡。查看 *Anomaly scores。* [39] 在两个模型之间切换以评估每个模型的分数。您可以从 *Predict* 选项卡下的 *Make Predictions* 选项中简单地下载数据集的分数。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_239_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_239_1.png)

[39] 分数越大，表示异常倾向越高。

## 示例 4 [DataRobot, 分类]: 裂缝检测的计算机视觉。

DataRobot 为用户提供了一种简单的方法，将计算机视觉应用于视频。在此示例中，我有一个包含约 120 张裂缝和无裂缝混凝土构件图像的数据集。目标是构建一个能够识别给定图像中裂缝的机器学习分类器。让我们使用 Quick 选项快速检查各种机器学习模型的性能。

### Step 1: 上传提供的数据集。选择 Class 作为目标。为交叉验证选项选择 2（注意，由于图像数量较少，我们选择 2，实际上需要一个更大的图像池）。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_240_0.png)

### Step 2: 通过选择 Images 探索上传的图像。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_240_1.png)

### Step 3: 开始分析。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_241_0.png)

### Step 4: 等待分析完成。如您所见，DataRobot 推荐 Elastic-Net Classifier (L2/Binomial Deviance) (BP 35) 模型，因为其在 AUC 方面表现良好。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_241_1.png)

### Step 5: 检查模型性能，可在 Evaluate 选项卡下的 ROC Curve 选项卡中找到。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_242_0.png)

### Step 6: 打开 Activation Maps 选项以可视化模型如何识别裂缝。如您所见，模型在图像上应用与裂缝对齐（暖色）的轮廓。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_242_1.png)

这完成了我们使用 DataRobot 的示例。

