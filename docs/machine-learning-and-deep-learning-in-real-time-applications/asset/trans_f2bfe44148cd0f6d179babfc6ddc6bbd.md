

## 步骤 3. 模型微调

现在，我们在 ResNet 架构的末尾添加了两个全连接层，后面跟一个 softmax 层，用于将对象分类为 10 个类别，而不是 1000 个。在开始，Cifar10 的输入图像需要放大三倍，然后才能通过 ResNet 层层。现在，获取 ResNet 层的输出，将其展平（flattened）并通过两个密集层（分别具有 128 和 64 个神经元）。在仅训练模型 5 个轮次（epochs）后，我们就达到了 98% 的准确率，这比前一节描述的从零开始构建的模型更高。

图 30。

```python
model = models.Sequential()
model.add(layers.UpSampling2D((2,2)))
model.add(layers.UpSampling2D((2,2)))
model.add(layers.UpSampling2D((2,2)))
model.add(layers.Conv2D(...))
model.add(layers.Flatten())
model.add(layers.Normalization())
model.add(layers.Dense(128, activation='relu'))
model.add(layers.Dropout(0.3))
model.add(layers.Normalization())
model.add(layers.Dense(64, activation='relu'))
model.add(layers.Dropout(0.3))
model.add(layers.Normalization())
model.add(layers.Dense(10, activation='softmax'))

model.compile(optimizer=optimizer.RMSprop(lr=1e-5), loss='binary_crossentropy', metrics=['acc'])
history = model.fit(x_train, y_train, epochs=5, batch_size=20, validation_data=(x_test, y_test))
```

```
Epoch 1/5
50000/50000 [==============================] - 189ms/sample - loss: 0.2629 acc: 0.9142 val_loss: 0.1890 val_acc: 0.9601
Epoch 2/5
50000/50000 [************** - 174ms/sample - loss: 0.2157 acc: 0.9434 val_loss: 0.1720 val_acc: 0.9756
Epoch 3/5
50000/50000 [************** - 174ms/sample - loss: 0.1197 acc: 0.9589 val_loss: 0.0508 val_acc: 0.9831
Epoch 4/5
50000/50000 [************** - 168ms/sample - loss: 0.0941 acc: 0.9604 val_loss: 0.0417 val_acc: 0.9865
Epoch 5/5
50000/50000 [==============================] - 175ms/sample - loss: 0.0756 acc: 0.9765 val_loss: 0.0395 val_acc: 0.9868
```

## 步骤 4. 模型评估

清楚地观察到，在同一数据集上使用迁移学习，测试准确率从 85.8% 大幅提升到 98.6%。

图 31。

```python
model.evaluate(x_test, y_test)

10000/10000 [====================] - 92ms/sample - loss: 0.0395 acc: 0.9868
[0.0394827925160527, 0.98679]
```

## 使用 Keras 进行深度学习

## 步骤 5. 绘制损失和准确率图

图 32。

```python
history_dict = history.history
loss_values = history_dict['loss']
val_values = history_dict['val_loss']
epochs = range(1, len(loss_values) + 1)
plt.figure(figsize=(14, 4))
plt.subplot(1,2,1)
plt.plot(epochs, loss_values, 'bo', label='Training Loss')
plt.plot(epochs, val_values, 'b', label='Validation Loss')
plt.title('Training and Validation Loss')
plt.xlabel('Epochs')
plt.legend()
acc = history_dict['val_acc']
epochs = range(1, len(acc) + 1)
plt.subplot(1,2,2)
plt.plot(epochs, acc, 'bo', label='Training Accuracy', c='orange')
plt.plot(epochs, val_acc, 'b', label='Validation Accuracy', c='orange')
plt.title('Training and Validation Accuracy')
plt.xlabel('Epochs')
plt.ylabel('Accuracy')
plt.legend()
```

图 33。![](img/5cbbc72cd5e7b92079ac36d85c78.png)

## TENSORFLOW VS. KERAS

TensorFlow 和 Keras 都是数据科学领域的框架，包含了不同的库和内置包（见图 1）。TensorFlow 是一个用于机器学习算法的开源框架，而 Keras 是一个用 Python 编写的神经网络库，运行在 TensorFlow 之上。

## 第 3 章 使用 PyTorch 进行深度学习

**Anmol Chaudhary** Jyoti Gajrani
印度 Ajmer 工程学院
印度 Malviya 国家理工学院

**Kuldeep Singh Chouhan** Bhavna Sharma
印度 Ajmer 工程学院
印度 贾普尔 JECRC 大学

## 摘要

在过去的十年中，由于图形处理器（GPU）计算能力的提升以及数据的普及，深度学习增长了指数级增长。本章旨在阐明深度学习的理论方面和实践方面。本章主要讨论了使用 PyTorch 的新技术。本文讨论了 PyTorch 与其他深度学习库的对比，并讨论了图像分类和机器翻译等实际应用。此外还讨论了基于 PyTorch 构建的各种框架。PyTorch 包含各种模型，提高了其灵活性和可用性，因此讨论了许多基于 PyTorch 的框架。作者认为，本章将帮助读者更好地理解使用 PyTorch 构建神经网络。

## 引言

深度学习是一个人工智能领域，通过大量数据来训练计算机，这是简单的编程算法无法实现的。由于 GPU 计算能力的飞跃，深度学习使计算机能够理解并更好地处理人类语言、图像内容，甚至以类似于人类的方式从环境中学习。尽管深度学习背后的理论和数学基础在计算机出现很久就已经存在，但由于计算机拥有足够的计算能力，它在 20 世纪代已成为现实。

深度学习催生了许多新技术创新，如交互式聊天机器人、自然翻译、人脸识别、疾病分类等。

深度学习领域的发展非常迅速。根据《2018 年人工智能指数年度报告》，自 1996 年以来，Scopus 论文增加了 7 倍。在此期间，计算机科学论文增加了 5 倍。

