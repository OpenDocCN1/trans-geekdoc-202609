

# 机器学习第 5 章：深入研究 Turi

当你运行此单元格时，你会发现特征提取的速度比上一章快得许多。这是因为 SqueezeNet 仅从 227×227 像素的图像中提取了 1000 个特征，而 VisionFeaturePrint_Screen 从 299×299 的图像中提取了 2048 个特征。

然而，你可能会对训练和验证准确率感到失望：

| 迭代次数 | 次数 | 步长 | 耗 | 训练准确率 | 验证准确率 |
|---|---|---|---|---|---|
| 9 | 16 | 1.000000 | 2.250278 | 0.447152 | 0.373901 |
| 24 | 41 | 1.000000 | 5.490575 | 0.597476 | 0.533058 |
| 49 | 77 | 1.000000 | 11.472903 | 0.706684 | 0.648760 |
| 74 | 113 | 1.000000 | 17.694513 | 0.755657 | 0.661157 |
| 99 | 162 | 1.000000 | 25.050267 | 0.803525 | 0.670412 |

> 注意：你得到的结果可能与书中显示的略有不同。请记住，未训练的模型（例如模型中的逻辑回归部分）是用随机数初始化的。这会导致不同训练运行之间存在差异。如果你得到的训练准确率远低于65%，请尝试重新运行。机器学习高级用户实际上会利用这些训练运行之间的差异，将多个模型组合成集成模型，从而提供更稳健的预测。

与 Create ML 一样，Turi Create 随机选择 5% 的训练数据作为验证数据，因此验证准确率在不同训练运行之间可能会很大差异。模型在你自己选择的较大的固定验证数据集上可能会表现更好（你将在本章中完成这一点）。

评估模型并显示指标：

```
metrics = model.evaluate(test_data)
print("Accuracy: ")
```

并没有意外 —— 率与验证准确率非常接近：

Accuracy: 0.6470588235294188
Precision: 0.644134936364582
Recall: 0.6445289115646259

# 获取单个预测结果

到目前为止，你只是重复了上一章的步骤。`evaluate()` 指标让你对模型的整体准确率有个大致的了解；你可以获取关于单个预测的更多信息。特别有趣的预测是那些模型错误但对自己正确非常有信心的情况。知道模型在哪里出错可以帮助你改进训练数据集。

![](img/5720be5c3cca252e12448e68d25607b5_169_0.png)

为了更深入地了解发生的情况，请运行以下单元格：

```
metrics.explore()
```

这会打开一个新窗口（仅限 Mac），让你能够可视化地检查准确率和其他指标。它还显示了正确分类以及——更有趣的是——错误分类的图像示例。非常有用！

| 模型 | 迭代次数 | 准确率 | F1 分数 | 总测试数 |
| :--- | :--- | :--- | :--- | :--- |
| squeezeneet_v1 | 135 | 64.71% | 64.43% | 952 |
| 类别名称 | 示例图像 | 准确率 | F1 分数 | 测试数量 |
| 芬 | | 46% | 47% | |
| 冰淇淋 | | 48% | 50% | |
| 蛋糕 | | 48% | 50% | |
| 饼干 | | 50% | 55% | |
| 椒盐结 | | 55% | 57% | 23 |
| 糖果 | | 55% | 64% | |
| 草莓 | | 61% | 62% | |

交互式评估窗口

# 预测与分类

Turi Create 模型除了 `evaluate()` 之外还有其他函数。在下一个单元格中输入并运行这些命令，然后等一会儿：

```
model.predict(test_data)
```

它显示了测试集中每张图像的实际预测：

[ 'apple', 'grape', 'orange', 'orange', 'orange', 'apple', 'orange', 'apple', 'candy', 'apple', 'grape', 'apple', 'strawberry', 'apple', 'apple', 'carrot', 'candy', 'ice cream', 'apple', 'apple', 'apple', ... ]

第一个预测对应于 `test_data[0]` 中的图像，第二个对应于 `test_data[1]`，依此类推。前 50 张图像全都是苹果，但模型将第二张图像分类为“grape（葡萄）”，请看一眼这张图像。在下一个单元格中输入并运行此命令：

```
plt.imshow(test_data[1]["image"])
```

这显示了第二张图像 —— 它看起来像葡萄吗[](img/5720be5c3cca252e12448e68d25607b5_170_0.png) 也许模型也不确定。输入并运行这些命令：

```
output = model.classify(test_data)
output
```

`classify()` 函数可以获取每个预测的概率，但只获取最高概率值，即模型对该类别的置信度：

| class | 概率 |
|---|---|
| apple | 0.432638513286321 |
| grape | 0.699958450277612 |
| orange | 0.414882190250213 |
| orange | 0.930059713409588 |
| orange | 0.378171352817196 |
| apple | 0.991564313975763 |
| orange | 0.426020382492679 |

带有分类的 SFrame 头部

模型有 69.9% 的确定认为第二张图像是“grape（葡萄）”！有 93% 的确定认为第四张图像是“orange（橙子）”！但对标记为“orange”的其他图像确定性小于 50%。查看每个预测对应的图像是有帮助的。输入并运行这些命令：

```
imgs_with_pred = test_data.add_columns(output)
imgs_with_pred.explore()
```

第一个命令将 output 列添加到原始 test_data 中。然后显示合并后的 SFrame。`label` 列是正确类别，`class` 列是模型最高置信度的预测，你可以在下一页看到：

# Turi Create 可视化

| 路径 | 图像 | 标签 | 类别 | 概率 |
|---|---|---|---|---|
| 0 | snacks/test/apple/00341c3c582... | | apple | 0.43269 |
| 1 | snacks/test/apple/004be96d798... | | apple | 0.699598 |
| 2 | snacks/test/apple/01ac2ac2a2... | | apple | orange | 0.414882 |
| 3 | snacks/test/apple/02bf0b1c06b... | | apple | orange | 0.93006 |
| 4 | snacks/test/apple/09d54b36ea... | | apple | orange | 0.378171 |

最有趣的图像是那些标签不一致但概率很高（超过90%）的行，例如。输入以下命令：

```
imgs_filtered = imgs_with_pred[(imgs_with_pred["probability"] > 0.9) & (imgs_with_pred["label"] != imgs_with_pred["class"]).explore()
```

此命令过滤 SFrame，仅包含高概率预测的行。第一项选择概率列值大于90%的行，第二项选择 label 和 class 列不相同的行。匹配行的子集被保存到新的 SFrame，然后显示：

# 第 5 章：深入研究 Turi Create

# Turi Create 可视化

| 路径 | 图像 | 标签 | 类别 | 概率 |
|---|---|---|---|---|
| 35 | snacks/test/pretzel/4698786386... | ![image]() | pretzel | hot dog | 0.964394 |
| 36 | snacks/test/salad/00af886b0e9... | ![image]() | salad | carrot | 0.952237 |
| 37 | snacks/test/salad/0bfde18d940... | ![image]() | salad | carrot | 0.908241 |
| 38 | snacks/test/strawberry/0d14011... | ![image]() | strawberry | | 0.973804 |
| 39 | snacks/test/strawberry/0d1e9... | ![image]() | | | |
| 40 | snacks/test/strawberry/2454732... | ![image]() | | | |
| 41 | snacks/test/waffle/2a3d34be4b... | ![image]() | | muffin | 0.905807 |
| 42 | snacks/test/watermelon/0200c7... | ![image]() | watermelon | carrot | 0.91499 |
| 43 | snacks/test/watermelon/7409d... | ![image]() | watermelon | strawberry | 0.939163 |

# 过滤后的分类结果

高亮图像的真实标签是“strawberry（草莓）”，但模型有 97% 的确定它是“juice（果汁）”，可能是因为那杯牛奶（？）比草莓大得多。

