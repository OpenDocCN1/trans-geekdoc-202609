

在这种情况下，我们可以看到模型在训练集和测试集上的性能相当，准确率约为84%，与我们在上一节中看到的结果非常相似，甚至略好一些。

```
Train: 0.842, Test: 0.846
```

代码清单 9.21：在双圆问题上评估激活函数之后应用批量归一化的MLP的示例输出。

同时创建了一个学习曲线图，显示了每个训练周期在训练集和测试集上的分类准确率。在这种情况下，我们可以看到模型比上一节中不带批量归一化的模型更快地学会了该问题。具体来说，我们可以看到训练集和测试集的分类准确率在前20个周期内跃升至80%以上，而不带批量归一化的模型则需要30到40个周期。该图还显示了训练期间批量归一化的效果。我们可以看到训练数据集上的性能低于测试数据集：训练数据集上的得分低于训练结束时测试数据集上的性能。这很可能是每个小批量中收集和更新输入所造成的影响。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_229_0.png)

图 9.3：在训练和测试数据集上，激活函数后带批量归一化的MLP在训练周期内的分类准确率折线图。

我们还可以尝试模型的一个变体，其中批量归一化应用于隐藏层的激活函数之前，而不是之后。

```
# define model
model = Sequential()
model.add(Dense(50, input_dim=2, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(Dense(1, activation='sigmoid'))
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
```

代码清单 9.22：更新模型以在激活函数之前使用批量归一化的示例。

完成此模型更改的完整代码清单如下所示。

```
# mlp for the two circles problem with batchnorm before activation function
from sklearn.datasets import make_circles
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import Activation
from keras.layers import BatchNormalization
from keras.optimizers import SGD
from matplotlib import pyplot
# generate 2d classification dataset
X, y = make_circles(n_samples=1000, noise=0.1, random_state=1)
# split into train and test
n_train = 500
trainX, testX = X[:n_train, :], X[n_train:, :]
trainy, testy = y[:n_train], y[n_train:]
# define model
model = Sequential()
model.add(Dense(50, input_dim=2, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(Dense(1, activation='sigmoid'))
opt = SGD(lr=0.01, momentum=0.9)
model.compile(loss='binary_crossentropy', optimizer=opt, metrics=['accuracy'])
# fit model
history = model.fit(trainX, trainy, validation_data=(testX, testy), epochs=100, verbose=0)
# evaluate the model
_, train_acc = model.evaluate(trainX, trainy, verbose=0)
_, test_acc = model.evaluate(testX, testy, verbose=0)
print('Train: %.3f, Test: %.3f' % (train_acc, test_acc))
# plot loss learning curves
pyplot.subplot(211)
pyplot.title('Cross-Entropy Loss', pad=-40)
pyplot.plot(history.history['loss'], label='train')
pyplot.plot(history.history['val_loss'], label='test')
pyplot.legend()
# plot accuracy learning curves
pyplot.subplot(212)
pyplot.title('Accuracy', pad=-40)
pyplot.plot(history.history['acc'], label='train')
pyplot.plot(history.history['val_acc'], label='test')
pyplot.legend()
pyplot.show()
```

代码清单 9.23：在双圆问题上评估在激活函数之前应用批量归一化的MLP的示例。

运行该示例首先打印模型在训练和测试数据集上的分类准确率。

**注意：**由于学习算法的随机性，您的具体结果可能会有所不同。请考虑多次运行该示例并比较平均性能。

在这种情况下，我们可以看到模型在训练和测试数据集上的性能相当，但比不带批量归一化的模型略差。

```
Train: 0.832, Test: 0.834
```

代码清单 9.24：在双圆问题上评估在激活函数之前应用批量归一化的MLP的示例输出。

训练集和测试集上的学习曲线折线图也呈现了一个不同的情况。该图显示模型的学习速度可能与不带批量归一化的模型相同，但模型在训练数据集上的性能要差得多，准确率徘徊在70%到75%之间，这很可能又是每个小批量中收集和使用的统计数据所造成的影响。至少对于这个特定数据集上的这种模型配置，批量归一化在修正线性激活函数之后似乎更有效。

![](img/8b574b0ce3be1eda9e1c02c72f9c8a21_232_0.png)

图 9.4：在训练和测试数据集上，激活函数前带批量归一化的MLP在训练周期内的分类准确率折线图。

## 9.4 扩展

本节列出了一些你可能希望探索的扩展本教程的想法。

- **不带Beta和Gamma。** 更新示例，不在批量归一化层中使用beta和gamma参数，并比较结果。
- **不带动量。** 更新示例，在训练期间不在批量归一化层中使用动量，并比较结果。
- **输入层。** 更新示例，在模型输入之后使用批量归一化，并比较结果。

如果你探索了这些扩展中的任何一个，我很想知道。

## 9.5 延伸阅读

如果你想深入了解该主题，本节提供了更多相关资源。

### 9.5.1 书籍

- 第8.7.1节：批量归一化，*深度学习*，2016年。  
  https://amzn.to/2NJW3gE
- 第7.3.1节：高级架构模式，*Python深度学习*，2017年。  
  https://amzn.to/2Ck4ImT

### 9.5.2 论文

- *批量归一化：通过减少内部协变量偏移加速深度网络训练*，2015年。  
  https://arxiv.org/abs/1502.03167
- *批量重归一化：旨在减少批量归一化模型中的小批量依赖性*，2017年。  
  https://arxiv.org/abs/1702.03275
- *批量归一化如何帮助优化？（不，这与内部协变量偏移无关）*，2018年。  
  https://arxiv.org/abs/1805.11604

### 9.5.3 API

- Keras正则化器API。  
  https://keras.io/regularizers/
- Keras核心层API。  
  https://keras.io/layers/core/
- Keras卷积层API。  
  https://keras.io/layers/convolutional/
- Keras循环层API。  
  https://keras.io/layers/recurrent/
- BatchNormalization Keras API。  
  https://keras.io/layers/normalization/
- sklearn.datasets.make_circles API。  
  http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_circles.html

### 9.5.4 文章

- 批量归一化，维基百科。  
  https://en.wikipedia.org/wiki/Batch_normalization
- ReLU之前还是之后进行批量归一化？，Reddit。  
  https://www.reddit.com/r/MachineLearning/comments/67gonq/d_batch_normalization_before_or_after_relu/
- Keras的批量归一化层已损坏，Vasilis Vryniotis，2018年。  
  http://blog.datumbox.com/the-batch-normalization-layer-of-keras-is-broken/
- 激活函数之前和之后的批量归一化研究。  
  https://github.com/ducha-aiki/caffenet-benchmark/blob/master/batchnorm.md

## 9.6 总结

在本教程中，你了解了用于加速深度学习神经网络训练的批量归一化方法。具体来说，你学到了：

- 深度神经网络训练起来具有挑战性，尤其是因为先前层的输入在权重更新后可能会发生变化。
- 批量归一化是一种对网络输入进行标准化的技术，可以应用于前一层的激活或直接应用于输入。
- 批量归一化可以加速训练，在某些情况下可以将周期数减半（甚至更多），并提供一定的正则化效果，减少泛化误差。

### 9.6.1 下一步

在下一个教程中，你将了解如何通过贪婪的逐层预训练来开发更深的神经网络模型。

