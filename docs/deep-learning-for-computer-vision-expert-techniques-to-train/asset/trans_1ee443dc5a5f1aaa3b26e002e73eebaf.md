

GAN 损失的梯度会被惩罚。然后，计算像素级损失并将其加到惩罚后的损失中。训练该模型创建了一个强大的自动编码器，可以用于图像压缩。

## 图像翻译

正如我们在应用章节中所学到的，图像可以转换为另一种图像。在构建此处 GAN 模型时，输入图像被交给判别器，而目标图像交给生成器，如下：

```
gan = tf.contrib.gan.gan_model(
get_generator,
get_discriminator,
real_images,
input_images)
```

除了像素级损失外，还使用了最小二乘损失来训练模型。可以使用以下代码进行计算：

```
loss = tf.contrib.gan.gan_loss(
gan,
tf.contrib.gan.losses.least_squares_generator_loss,
tf.contrib.gan.losses.least_squares_discriminator_loss)
```

```
l1_loss = tf.norm(gan.real_data - gan.generated_data, ord=1)
gan_loss = tf.contrib.gan.losses.combine_adversarial_loss(
loss, gan, l1_loss, weight_factor=1)
```

使用这种技术，图像可以转换为另一种图像。

## InfoGAN

InfoGAN 可以在没有任何显式监督训练的情况下生成所需标签的图像。infogan_model 接受非结构化和结构化的输入，如下所示：

```
info_gan = tf.contrib.gan.infogan_model(
get_generator,
get_discriminator,
real_images,
unstructured_input,
structured_input(
loss = tf.contrib.gan.gan_loss(
info_gan,
gradient_penalty_weight=1,
gradient_penalty_epsilon=1e-10,
mutual_information_penalty_weight=1)
```

由于训练是不稳定的，损失定义中带有惩罚。添加惩罚可以提高训练期间的稳定性。

## GAN 的缺点

GAN 生成的图像存在一些缺点，例如计数、透视全局结构。目前正在对此进行广泛研究以改进模型。

## 视觉对话模型

视觉对话模型 (VDM) 实现了基于图像的聊天。VDM 应用了计算机视觉、自然语言处理 (NLP) 和聊天机器人的技术。它已发现许多应用，例如向盲人解释图像、向医生解释医学扫描、虚拟伴等。接下来，我们将看到解决这一挑战的算法。

## VDM 算法

这里讨论的算法由 Lu 等人（https://research.fb.com/wp-content/uploads/2017/11/camera_ready_nips2017.pdf）提出了一种基于 GAN 的 VDM。生成器生成答案，判别器对这些答案进行计数。以下是该过程的示意图：

![](img/48c861eac4dc634fbf2a09fdbe884beb_246_0.png)

聊天历史、当前问题和图像被输入到生成器。接下来，我们将看到生成器是如何工作的。

## 生成器

生成器包含编码器和解码器。编码器接受图像、问题和历史作为输入。编码器首先关注来自 LSTM的历史，然后关注图像的输出。流程所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_247_0.png)

> 重复自 Lu 等人。

整个历史都是可用的，LSTM 关注聊天历史。输出通过图像关注产生嵌入。编码器生成的嵌入被解码器用于创建答案。解码器由 RNN 组成。编码器和解码器共同形成产生可能答案的生成器。接下来，我们将看到判别器是如何工作的。

## 判别器

判别器接收生成器生成的序列并对其进行排序。排序通过使用 n-pair loss 学到的嵌入完成。n-pair loss 与 triplet loss 相似，不同之处使用了几组正负对进行比较。以下是模型产生的一些结果。

![](img/48c861eac4dc634fbf2a09fdbe884beb_248_0.png)

![](img/48c861eac4dc634fbf2a09fdbe884beb_248_1.png)

![](img/48c861eac4dc634fbf2a09fdbe884beb_248_2.png)

问：是家里还是餐厅？
答：我觉得是餐厅。
G-MLE：不，告诉我。
我们的 (x1)：看起来像是一个餐厅。
我们的 (x2)：我看不出来，因为它离太近了。

问：你能看到他的脸吗？
答：我不确定。
G-MLE：不。
我们的 (x1)：我只能看到他的背影。
我们的 (x2)：不。
我们的 (x3)：他离太远了。

问：这个男人看起来多大年纪？
答：20多岁。
G-MLE：青少年后期。
我们的 (x1)：20多岁。
我们的 (x2)：在20多岁之间。
我们的 (x3)：25岁左右。

问：你能看到西兰花吗？
答：是的，有3 块较大的和一些小的块。
G-MLE：不，只有西兰花。
我们的 (x1)：我能看到西兰花，稍微被埋了。
我们的 (x2)：是的，有西兰花。
我们的 (x3)：是的，西兰花是绿色的。

重复自 Lu 等人。

结果是合理的，并且优于简单判别器产生的结果。

## 总结

在本章中，我们学习了生成模型及其大量的应用。我们实现了它们来在保留内容的同时将风格从一种转换到另一种。我们看到了 GAN 背后的直觉原理，并训练了模型来实现同样的操作。最后，我们学习了视觉对话系统。

在下一章中，我们将学习视觉对话系统。

