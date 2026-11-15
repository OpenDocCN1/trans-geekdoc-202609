

```
Epoch 9/30
29409/29409 [==============================] - 108s 4ms/step - loss: 0.0535
- acc: 0.9874 - val_loss: 0.1015 - val_acc: 0.9780
Epoch 10/30
29409/29409 [==============================] - 109s 4ms/step - loss: 0.0414
- acc: 0.9913 - val_loss: 0.0927 - val_acc: 0.9801
Epoch 11/30
29409/29409 [==============================] - 108s 4ms/step - loss: 0.0415
- acc: 0.9917 - val_loss: 0.0912 - val_acc: 0.9807
Epoch 12/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.0341
- acc: 0.9933 - val_loss: 0.1054 - val_acc: 0.9769
Epoch 13/30
29409/29409 [==============================] - 108s 4ms/step - loss: 0.0266
- acc: 0.9946 - val_loss: 0.0811 - val_acc: 0.9842
Epoch 14/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.0207
- acc: 0.9965 - val_loss: 0.0790 - val_acc: 0.9845
Epoch 15/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.0221
- acc: 0.9955 - val_loss: 0.0780 - val_acc: 0.9841
Epoch 16/30
29409/29409 [==============================] - 109s 4ms/step - loss: 0.0169
- acc: 0.9974 - val_loss: 0.0753 - val_acc: 0.9854
Epoch 17/30
29409/29409 [==============================] - 109s 4ms/step - loss: 0.0137
- acc: 0.9982 - val_loss: 0.0777 - val_acc: 0.9863
Epoch 18/30
29409/29409 [==============================] - 109s 4ms/step - loss: 0.0114
- acc: 0.9986 - val_loss: 0.0757 - val_acc: 0.9863
Epoch 19/30
29409/29409 [==============================] - 109s 4ms/step - loss: 0.0101
- acc: 0.9990 - val_loss: 0.0775 - val_acc: 0.9867
Epoch 20/30
29409/29409 [==============================] - 108s 4ms/step - loss: 0.0086
- acc: 0.9993 - val_loss: 0.0786 - val_acc: 0.9862
Epoch 21/30
29409/29409 [==============================] - 110s 4ms/step - loss: 0.0077
- acc: 0.9994 - val_loss: 0.0776 - val_acc: 0.9859
Epoch 22/30
29409/29409 [==============================] - 110s 4ms/step - loss: 0.0071
- acc: 0.9995 - val_loss: 0.0774 - val_acc: 0.9862
Epoch 23/30
29409/29409 [==============================] - 109s 4ms/step - loss: 0.0066
- acc: 0.9996 - val_loss: 0.0779 - val_acc: 0.9862
Epoch 24/30
29409/29409 [==============================] - 110s 4ms/step - loss: 0.0062
- acc: 0.9997 - val_loss: 0.0783 - val_acc: 0.9860
Epoch 25/30
29409/29409 [==============================] - 114s 4ms/step - loss: 0.0059
- acc: 0.9997 - val_loss: 0.0786 - val_acc: 0.9859
Epoch 26/30
29409/29409 [==============================] - 115s 4ms/step - loss: 0.0056
- acc: 0.9998 - val_loss: 0.0791 - val_acc: 0.9861
Epoch 27/30
29409/29409 [==============================] - 117s 4ms/step - loss: 0.0053
- acc: 0.9998 - val_loss: 0.0793 - val_acc: 0.9860
Epoch 28/30
29409/29409 [==============================] - 115s 4ms/step - loss: 0.0051
- acc: 0.9998 - val_loss: 0.0794 - val_acc: 0.9862
Epoch 29/30
29409/29409 [==============================] - 114s 4ms/step - loss: 0.0050
- acc: 0.9998 - val_loss: 0.0795 - val_acc: 0.9864
Epoch 30/30
29409/29409 [==============================] - 113s 4ms/step - loss: 0.0048
- acc: 0.9998 - val_loss: 0.0796 - val_acc: 0.9865
```

训练30个epoch后，模型训练良好，在测试集上达到了98.65%的准确率。
在RStudio查看器窗格中，我们也可以实时查看每个epoch的分类性能：

![](img/da8fb67f2acf661518076e08b6ffd9b9_92_0.png)

## 使用脱校法减少过拟合

你可能会注意到，我们在MXNet解决方案中使用了L2正则化，它通过对大权重施加惩罚来避免过拟合；但我们在此Keras解决方案中未这样做。这导致测试集上的分类准确率略有差异（99.30%对98.65%）。我们将在此Keras解决方案中采用正则化，这次具体使用**脱校法**。

脱校法是神经网络中的一种正则化技术，最初由Geoffrey Hinton等人于2012年提出（Improving Neural Networks by Preventing Co-adaptation of Feature Detectors in Neural and Evolutionary Computing）。顾名思义，它在训练期间忽略神经网络中随机选取的一小部分神经元（可以是隐藏层或可见层神经元）。*被丢弃的*神经元暂时不对下游神经元的激活或反向传播时的神经元权重更新做出贡献。那么，脱校法技术如何防止过拟合呢？

请回顾，在标准神经网络中，神经元在训练期间与相邻神经元相互依赖。而且神经元的权重会针对网络中的特定上下文进行调整，这限制了每个神经元的个体能力。这种对上下文的依赖可能导致模型过于专门化于训练数据。当网络中此类神经元不被考虑时，神经元的权重对其他神经元的权重变得不那么敏感。神经元被迫更独立地学习有用信息。训练数据上的共适应会受到惩罚。

使用脱校法很简单。在训练阶段，对于具有脱校率*p*的层，在每次迭代中，我们随机关闭比例*p*的神经元。在测试阶段，我们使用所有神经元，但将其激活值按因子*q = 1 - p*进行缩放，以解释训练阶段中被丢弃的激活值。

下面是一个标准神经网络（第一张图）和带有脱校法的同一网络（第二张图）：

![](img/da8fb67f2acf661518076e08b6ffd9b9_94_0.png)

![](img/da8fb67f2acf661518076e08b6ffd9b9_94_1.png)

在此示例中，脱校法应用于可见层（即输入层），此外还应用于隐藏层。

在实践中，脱校率通常设置为20%至50%。脱校率过低的层影响不大，而过高的比率会导致欠拟合。

现在让我们通过使用函数`layer_dropout(p)`将脱校法应用到我们的Keras解决方案中。我们定义一个函数来初始化和编译带有脱校法的CNN模型（以供复用）：

```r
init_cnn_dropout <- function() {
  model_dropout <- keras_model_sequential()
  model_dropout %>%
  layer_conv_2d(
    filter = 32, kernel_size = c(5, 5),
    input_shape = c(32, 32, 1)
  ) %>%
  layer_activation("relu") %>%
  layer_max_pooling_2d(pool_size = c(2, 2)) %>%
  # Second hidden convolutional layer
  layer_conv_2d(filter = 64, kernel_size = c(5, 5)) %>%
  layer_activation("relu") %>%
  # Use max pooling
  layer_max_pooling_2d(pool_size = c(2, 2)) %>%
  layer_dropout(0.25) %>%
  # Flatten and feed into dense layer
  layer_flatten() %>%
  layer_dense(1000) %>%
  layer_activation("relu") %>%
  layer_dropout(0.25) %>%
  # Outputs from dense layer
  layer_dense(43) %>%
  layer_activation("softmax")

  opt <- optimizer_sgd(lr = 0.005, momentum = 0.9)

  model_dropout %>%
    compile(
      loss = "categorical_crossentropy",
      optimizer = opt,
      metrics = "accuracy"
    )

  return(model_dropout)
}
```

### 获取新模型：

```r
> model_dropout <- init_cnn_dropout()
```

我们在第二个最大池化层和全连接隐藏层中分别使用25%的脱校法。通过调用summary(model_dropout)，我们可以看到第二个MaxPooling2D层下方以及第一个密集层和激活层下方分别有两个脱校法层。

### 继续进行模型训练：

```r
> model_dropout %>% fit(
+ x_train, y_train,
+ batch_size = 100,
+ epochs = 30,
+ validation_data = list(x_test, y_test),
+ shuffle = FALSE
+ )
Train on 29409 samples, validate on 9800 samples
Epoch 1/30
29409/29409 [==============================] - 108s 4ms/step - loss: 3.1078
- acc: 0.1987 - val_loss: 1.4475 - val_acc: 0.6487
Epoch 2/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.9772
- acc: 0.7337 - val_loss: 0.4570 - val_acc: 0.8934
Epoch 3/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.5194
- acc: 0.8598 - val_loss: 0.3043 - val_acc: 0.9310
Epoch 4/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.3606
- acc: 0.9037 - val_loss: 0.2058 - val_acc: 0.9529
Epoch 5/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.2828
- acc: 0.9250 - val_loss: 0.1677 - val_acc: 0.9640
Epoch 6/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.2272
- acc: 0.9406 - val_loss: 0.1424 - val_acc: 0.9707
Epoch 7/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.1910
- acc: 0.9494 - val_loss: 0.1138 - val_acc: 0.9793
Epoch 8/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.1560
- acc: 0.9602 - val_loss: 0.0986 - val_acc: 0.9797
Epoch 9/30
29409/29409 [==============================] - 106s 4ms/step - loss: 0.1423
- acc: 0.9621 - val_loss: 0.0956 - val_acc: 0.9804
Epoch 10/30
```

