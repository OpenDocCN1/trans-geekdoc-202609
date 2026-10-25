

生成器模型，称为循环损失。最后，当提供来自目标域的示例时，生成器模型预期输出未经翻译的图像，称为身份损失。总的来说，每个生成器模型通过四个输出和四个损失函数的组合进行优化：

- 对抗损失（L2 或均方误差）。
- 身份损失（L1 或平均绝对误差）。
- 前向循环损失（L1 或平均绝对误差）。
- 后向循环损失（L1 或平均绝对误差）。

这可以通过定义一个复合模型来实现，该模型用于训练每个生成器模型，仅负责更新该生成器模型的权重，尽管需要与相关判别器模型和另一个生成器模型共享权重。这是在 `define_composite_model()` 函数中实现的，该函数接受一个已定义的生成器模型（`g_model_1`）以及用于生成器模型输出的已定义判别器模型（`d_model`）和另一个生成器模型（`g_model_2`）。其他模型的权重被标记为不可训练，因为我们只关心更新第一个生成器模型，即这个复合模型的重点。

判别器连接到生成器的输出，以便将生成的图像分类为真实或假冒。复合模型的第二个输入定义为来自目标域（而非源域）的图像，生成器预期为身份映射输出未经翻译的图像。接下来，前向循环损失涉及将生成器的输出连接到另一个生成器，该生成器将重建源图像。最后，后向循环损失涉及用于身份映射的来自目标域的图像，该图像也通过另一个生成器，其输出连接到我们的主生成器作为输入，并输出该目标域图像的重建版本。

总而言之，复合模型有两个输入，分别用于 Domain-A 和 Domain-B 的真实照片，以及四个输出，分别用于判别器输出、身份生成图像、前向循环生成图像和后向循环生成图像。仅更新复合模型中第一个或主生成器模型的权重，这是通过所有损失函数的加权和来完成的。循环损失的权重比对抗损失大（10 倍），如论文中所述，身份损失始终使用循环损失权重的一半（5 倍），与官方实现源代码一致。

```python
# define a composite model for updating generators by adversarial and cycle loss
def define_composite_model(g_model_1, d_model, g_model_2, image_shape):
    # ensure the model we're updating is trainable
    g_model_1.trainable = True
    # mark discriminator as not trainable
    d_model.trainable = False
    # mark other generator model as not trainable
    g_model_2.trainable = False
    # discriminator element
    input_gen = Input(shape=image_shape)
    gen1_out = g_model_1(input_gen)
    output_d = d_model(gen1_out)
    # identity element
    input_id = Input(shape=image_shape)
    output_id = g_model_1(input_id)
    # forward cycle
    output_f = g_model_2(gen1_out)
    # backward cycle
    gen2_out = g_model_2(input_id)
    output_b = g_model_1(gen2_out)
    # define model graph
    model = Model([input_gen, input_id], [output_d, output_id, output_f, output_b])
    # define optimization algorithm configuration
    opt = Adam(lr=0.0002, beta_1=0.5)
    # compile model with weighting of least squares loss and L1 loss
    model.compile(loss=['mse', 'mae', 'mae', 'mae'], loss_weights=[1, 5, 10, 10],
                  optimizer=opt)
    return model
```

清单 26.9：定义用于训练生成器的复合模型的函数示例。

我们需要为每个生成器模型创建一个复合模型，例如，用于斑马到马翻译的 Generator-A（BtoA）和用于马到斑马翻译的 Generator-B（AtoB）。在两个域之间来回进行所有这些前向和后向操作会让人感到困惑。下面是每个复合模型的所有输入和输出的完整列表。身份损失和循环损失计算为每个翻译序列中输入图像和输出图像之间的 L1 距离。对抗损失计算为模型输出与真实目标值 1.0 和假冒目标值 0.0 之间的 L2 距离。定义模型是 CycleGAN 的难点；其余部分是标准的 GAN 训练，相对简单。接下来，我们可以以压缩 NumPy 数组格式加载配对图像数据集。这将返回一个包含两个 NumPy 数组的列表：第一个用于源图像，第二个用于对应的目标图像。

```python
# load and prepare training images
def load_real_samples(filename):
    # load the dataset
    data = load(filename)
    # unpack arrays
    X1, X2 = data['arr_0'], data['arr_1']
    # scale from [0,255] to [-1,1]
    X1 = (X1 - 127.5) / 127.5
    X2 = (X2 - 127.5) / 127.5
    return [X1, X2]
```

清单 26.10：加载准备好的数据集的函数示例。

在每次训练迭代中，我们都需要来自每个域的真实图像样本作为判别器和复合生成器模型的输入。这可以通过选择一个随机批次的样本来实现。下面的 generate_real_samples() 函数实现了此功能，它接受一个域的 NumPy 数组作为输入，并返回请求数量的随机选定图像，以及指示图像为真实的 PatchGAN 判别器模型的目标（target = 1.0）。因此，还提供了 PatchGAN 输出的形状，在 256 × 256 图像的情况下，它将是 16，即 16 × 16 × 1 的激活图，由 patch_shape 函数参数定义。

```python
# select a batch of random samples, returns images and target
def generate_real_samples(dataset, n_samples, patch_shape):
    # choose random instances
    ix = randint(0, dataset.shape[0], n_samples)
    # retrieve selected images
    X = dataset[ix]
    # generate 'real' class labels (1)
    y = ones((n_samples, patch_shape, patch_shape, 1))
    return X, y
```

清单 26.11：选择真实图像样本的函数示例。

同样，在每次训练迭代中，还需要一个生成图像样本来更新每个判别器模型。下面的 `generate_fake_samples()` 函数基于生成器模型和源域的真实图像样本生成此样本。同样，为每个生成的图像提供了带有 PatchGAN 正确形状的目标值，指示它们是假冒或生成的（`(target = 0.0)`）。

```python
# generate a batch of images, returns images and targets
def generate_fake_samples(g_model, dataset, patch_shape):
    # generate fake instance
    X = g_model.predict(dataset)
    # create 'fake' class labels (0)
    y = zeros((len(X), patch_shape, patch_shape, 1))
    return X, y
```

清单 26.12：使用生成器创建合成图像样本的函数示例。

通常，GAN 模型不会收敛；相反，在生成器和判别器模型之间会达到一种平衡。因此，我们无法轻易判断训练是否应该停止。因此，我们可以保存模型，并在训练期间定期使用它生成示例图像到图像的翻译，例如每一或五个训练周期。然后，我们可以在训练结束时查看生成的图像，并使用图像质量来选择最终模型。下面的 `save_models()` 函数将每个生成器模型以 H5 格式保存到当前目录，并在文件名中包含训练迭代编号。

```python
# save the generator models to file
def save_models(step, g_model_AtoB, g_model_BtoA):
    # save the first generator model
    filename1 = 'g_model_AtoB_%06d.h5' % (step+1)
    g_model_AtoB.save(filename1)
    # save the second generator model
    filename2 = 'g_model_BtoA_%06d.h5' % (step+1)
    g_model_BtoA.save(filename2)
    print('>Saved: %s and %s' % (filename1, filename2))
```

清单 26.13：将生成器模型保存到文件的函数示例。

下面的 `summarize_performance()` 函数使用给定的生成器模型生成几个随机选定的源照片的翻译版本，并将图表保存到文件。源图像绘制在第一行，生成的图像绘制在第二行。同样，图表文件名包含训练迭代编号。

```python
# generate samples and save as a plot and save the model
def summarize_performance(step, g_model, trainX, name, n_samples=5):
    # select a sample of input images
    X_in, _ = generate_real_samples(trainX, n_samples, 0)
    # generate translated images
    X_out, _ = generate_fake_samples(g_model, X_in, 0)
    # scale all pixels from [-1,1] to [0,1]
```

