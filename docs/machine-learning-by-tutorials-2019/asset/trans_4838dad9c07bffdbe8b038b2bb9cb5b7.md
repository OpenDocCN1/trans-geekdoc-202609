

# 机器学习第 8 章：高级卷积神经网络

香蕉的召回率（recall）很高，为 0.96，因此包含香蕉的图像通常能被模型正确找到。冰激淋的召回率较低，仅为 74%，这意味着超过分之一的冰激淋图像被分类为了其他类别。在 Python 中验证这一点：

```python
# 获取冰激淋的类别索引
idx = test_generator.class_indices["ice cream"]

# 找到有多少图像应该是冰激淋
total_expected = np.sum(target_labels == idx)

# 我们找到了多少张冰激淋图像？
correct = conf[idx, idx]

# 召回率就是真正例除以
# 真正例 + 假阴例
recall = correct / total_expected
print(recall)
```

这应该打印 0.74。假阴例（即被错误地预测为不是类别 X 的物体）越多，X 类的召回率就越低。

分类报告还包含了 F1 分数。它是精确率（precision）和召回率的结合，如果你想获得两者的平均值，它非常有用。

F1 分数最高的类别是葡萄和汁，均为 0.95。你可以放地说，这个分类器处理葡萄或汁图像的效果非常好。F1 分数最低的类别是蛋糕，为 0.73。如果你想改进这个分类器，首先要做的寻找更多蛋糕类别的训练图像。

> 注意：能够编写一些 Python 代码是有用的。你通常需要像上面那样编写短代码来仔细观察预测结果。如果你对构建自己的模型，这非常有帮助！

# 哪些预测是最错误的？

混淆矩阵和精确率-召回率报告可以提供改进模型的提示。还有其他你可以做的。你已经看到蛋糕类别整体表现最差。查看那些被预测错误但置信度很高的图像也很有启发。为什么模型对这些图像如此自信却又错了？例如，你可以使用以下代码找到预测最错误的图像，这使用了一些 NumPy 魔法术：

```python
# 找到预测类别错误的图像
wrong_images = np.where(predicted_labels != target_labels)

# 对于每一个预测，找到最大的概率值；
# 这是该图像属于胜出类别的概率
probs_max = np.max(probabilities, axis=-1)

# 将错误预测从低到高排序
idx = np.argsort(probs_max[wrong_images])

# 反转顺序（从高到低），并保留前 5 个
idx = idx[::-1][:5]

index2class = {v:k for k,v in test_generator.class_indices.items()}

```python
for i in worst_predictions:
   print("%s was predicted as '%s' %.4f" % (
      test_generator.filenames[i],
      index2class[predicted_labels[i]],
      probs_max[i]))
```

这将输出：

strawberry/09d0141c00b309.jpg 被预测为 'salad' 0.9999
apple/61792276d2cee4.jpg 被预测为 'pineapple' 0.9907
muffin/3b2599aa3c7fabac.jpg 被预测为 'cake' 0.9889
apple/0eebbf64d79a23.jpg 被预测为 'banana' 0.9897
ake/bc41ce2f8c78cd5.jpg 被预测为 'waffle' 0.9885

实际查看这些图像也很有意义：

```python
from keras.preprocessing import image
img = image.load_img(test_data_dir + 
test_generator.filenames[worst_predictions[0]])
plt.imshow(img)
```

是的，很难看出模型在这里为什么会混乱。你可以很有理由地认为这张图像在测试集中标记是错误的——或者至少非常有误导性：

![](img/5720be5c3cca252e12448e68d2567b5_299_0.png)

最错误的预测……真的是这样吗？

# 关于不平衡类别的说明

关于图像分类器的内容比我们本书能容下的多得多。一个经常出现的话题是如何**处理不平衡数据。

在一个需要区分 X 光片中是否存在疾病（阳性）和不存在疾病（阴性）的二分类分类器中，大多数 X 光片不会显示任何疾病。这对患者来说是好事，但也增加了分类器的工作难度。如果疾病恰好发生在 1% 的患者身上，分类器可以简单地始终预测“无疾病”，并在 99% 的情况下都是正确的。但这样的分类器几乎毫无用……99% 的准确率听起来很惊人，但并不足够。

或者假设你想训练一个可以区分以下类的分类器：猫、狗、既不是猫也不是狗。为了训练这样的分类器，你显然需要猫和狗的照片，还需要不是猫也不是狗的物体照片。最后一个类别必须大得多，因为它需要涵盖各种物体，而分类器需要将它们所有归类为“既不是猫也不是狗”类别。风险是分类器只会学习一个大类别，而不会学习图像少得多的猫和狗类别。

你可以使用各种技术来处理类别不平衡，例如过采样（oversampling，更频繁地使用较小类别的图像）、欠采样（undersampling，使用较少的大型类别的图像），或对类别设置权重，使得较大类别对损失函数的影响更小。

Turi Create 和 Create ML 目前没有提供提供这些选项，因此如果你需要为不平衡数据集构建分类器，Keras 是更好的选择。

我们关于训练图像分类器的讨论到此结束。接下来，你将学习如何将训练好的 Keras 模型转换为 Core ML 模型，你可以在你的 iOS 和 macOS 应用程序中使用它。

# 转换为 Core ML

当你编写 `model.save("name.h5")` 或使用 `Checkpoint` 回调时，Keras 以其自己的格式 HDF5 保存模型。为了使用来自 Keras 的此模型，你必须将其转换为 `.model` 文件。这需要使用 `coremltools` Python 包。

`kerasenv` 环境已经安装了 `coremltools`。万一你需要手动安装，在命令行提示符输入：

```bash
pip install -U coremltools
```

你可以在 Jupyter notebook 中输入以下命令，或者参考 MobileNet.ipynb。本章的资源还包含一个独立的 Python 脚本 `convert-to-coreml.py`，用于加载模型。

首先，导入包：

```python
import coremltools
```

此时你可能会收到一些关于版本不兼容的警告信息。这些工具更新的速度比 coreml 跟快，但通常这些警告不是问题。

由于这是一个分类器模型，coreml 需要知道标签名称。重要的是这些名称要与 `train_generator.class_indices` 的顺序一致：

```python
labels = ["apple", "banana", "cake", "candy", "carrot", "cookie", "doughnut", "grape", "hot dog", "ice cream", "juice", "muffin", "orange", "pineapple", "popcorn", "salad", "waffle", "watermelon"]
```

现在，你可以使用 Keras 转换器创建一个 Core ML 模型：

```python
coreml_model = coremltools.convert.keras.convert(best_model, 
    input_names="image", 
    image_input_names="image", 
    output_names="labelProbability", 
    predicted_feature_name="label", 
    red_bias=-1, 
    green_bias=-1, 
    blue_bias=-1, 
    image_scale=2/255.0, 
    class_labels=labels)
```

