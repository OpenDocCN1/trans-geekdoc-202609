
- 1. 条形生成器的输入是一个长度为 4 * Z_DIM 的向量。
- 2. 在将其通过 Dense 层后，我们重塑张量以便为转置卷积操作做好准备。
- 3. 首先我们沿时间步轴扩展张量...
- 4. ...然后沿音高轴扩展。
- 5. 最终层应用了 tanh 激活，因为我们将使用 WGAN-GP（该框架要求输出激活为 tanh）来训练网络。
- 6. 张量被重塑以添加两个大小为 1 的额外维度，以便与其它小节和音轨进行拼接。

## 综合起来

总之，MuseGAN 生成器接收四个输入噪声张量（和弦、风格、旋律和节奏型），并将其转换为多音轨、多小节的乐谱。构建 MuseGAN 生成器的 Keras 代码在示例 11-8 中给出。

### 示例 11-8. 构建 MuseGAN 生成器

```python
def Generator():
    chords_input = layers.Input(shape=(Z_DIM,), name='chords_input')
    style_input = layers.Input(shape=(Z_DIM,), name='style_input')
    melody_input = layers.Input(shape=(N_TRACKS, Z_DIM), name='melody_input')
    groove_input = layers.Input(shape=(N_TRACKS, Z_DIM), name='groove_input')

    chords_tempNetwork = TemporalNetwork()
    chords_over_time = chords_tempNetwork(chords_input)

    melody_over_time = [None] * N_TRACKS
    melody_tempNetwork = [None] * N_TRACKS
    for track in range(N_TRACKS):
        melody_tempNetwork[track] = TemporalNetwork()
        melody_track = layers.Lambda(lambda x, track = track: x[:,track,:])(
            melody_input
        )
        melody_over_time[track] = melody_tempNetwork[track](melody_track)

    barGen = [None] * N_TRACKS
    for track in range(N_TRACKS):
        barGen[track] = BarGenerator()

    bars_output = [None] * N_BARS
    c = [None] * N_BARS
    for bar in range(N_BARS):
        track_output = [None] * N_TRACKS

        c[bar] = layers.Lambda(lambda x, bar = bar: x[:,bar,:,:])(chords_over_time)
        s = style_input

        for track in range(N_TRACKS):
            m = layers.Lambda(lambda x, bar = bar: x[:,bar,:,:])(
                melody_over_time[track]
            )
            g = layers.Lambda(lambda x, track = track: x[:,track,:,:])(
                groove_input
            )
            z_input = layers.Concatenate(
                axis = 1, name = 'total_input_bar_{}_track_{}'.format(bar, track)
            )([c[bar],s,m,g])
            track_output[track] = barGen[track](z_input)
        bars_output[bar] = layers.Concatenate(axis = -1)(track_output)
    generator_output = layers.Concatenate(axis = 1, name = 'concat_bars')(
        bars_output
    )
    return models.Model(
        [chords_input, style_input, melody_input, groove_input], generator_output
    )
generator = Generator()
```

- 1. 定义生成器的输入。
- 2. 将和弦输入通过时序网络。
- 3. 将旋律输入通过时序网络。
- 4. 为每个音轨创建一个独立的小节生成器网络。
- 5. 遍历音轨和小节，为每种组合创建生成的小节。
- 6. 将所有内容拼接在一起形成单个输出张量。
- 7. MuseGAN 模型接收四个不同的噪声张量作为输入，并输出生成的多音轨、多小节乐谱。

## MuseGAN 判别器

与生成器相比，判别器架构要简单得多（这在 GAN 中很常见）。

判别器试图区分由生成器创建的完整多音轨、多小节乐谱与巴赫圣咏的真实片段。它是一个卷积神经网络，主要由 Conv3D 层组成，这些层将乐谱压缩为单个输出预测。

![](img/f0f0f5d89818fdddf117bbe758ac8143_352_0.png)

### Conv3D 层

到目前为止，本书中我们只使用过适用于三维输入图像（宽度、高度、通道）的 Conv2D 层。在这里我们必须使用 Conv3D 层，它类似于 Conv2D 层，但接受四维输入张量（n_bars, n_steps_per_bar, n_pitches, n_tracks）。

我们在判别器中不使用批量归一化层，因为我们将使用 WGAN-GP 框架训练 GAN，该框架禁止使用此操作。

构建判别器的 Keras 代码在示例 11-9 中给出。

### 示例 11-9. 构建 MuseGAN 判别器

```python
def conv(x, f, k, s, p):
    x = layers.Conv3D(filters = f
        , kernel_size = k
        , padding = p
        , strides = s
        , kernel_initializer = initializer
    )(x)
    x = layers.LeakyReLU()(x)
    return x

def Critic():
    critic_input = layers.Input(
        shape=(N_BARS, N_STEPS_PER_BAR, N_PITCHES, N_TRACKS),
        name='critic_input'
    ) ①

    x = critic_input
    x = conv(x, f=128, k = (2,1,1), s = (1,1,1), p = 'valid') ②
    x = conv(x, f=128, k = (N_BARS - 1,1,1), s = (1,1,1), p = 'valid')

    x = conv(x, f=128, k = (1,1,12), s = (1,1,12), p = 'same') ③
    x = conv(x, f=128, k = (1,1,7), s = (1,1,7), p = 'same')

    x = conv(x, f=128, k = (1,2,1), s = (1,2,1), p = 'same') ④
    x = conv(x, f=128, k = (1,2,1), s = (1,2,1), p = 'same')

    x = conv(x, f=256, k = (1,4,1), s = (1,2,1), p = 'same')
    x = conv(x, f=512, k = (1,3,1), s = (1,2,1), p = 'same')

    x = layers.Flatten()(x)

    x = layers.Dense(1024, kernel_initializer = initializer)(x)
    x = layers.LeakyReLU()(x)

    critic_output = layers.Dense(
        1, activation=None, kernel_initializer = initializer
    )(x) ⑤

    return models.Model(critic_input, critic_output)

critic = Critic()
```

- 1. 判别器的输入是多音轨、多小节乐谱的数组，每个形状为 [N_BARS, N_STEPS_PER_BAR, N_PITCHES, N_TRACKS]。
- 2. 首先，我们沿小节轴压缩张量。我们在整个判别器中使用 Conv3D 层，因为我们处理的是 4D 张量。
- 3. 接下来，我们沿音高轴压缩张量。
- 4. 最后，我们沿时间步轴压缩张量。
- 5. 输出是一个具有单个单元且无激活函数的 Dense 层，这是 WGAN-GP 框架所要求的。

## MuseGAN 分析

我们可以通过生成一个乐谱，然后调整一些输入噪声参数来观察对输出的影响，从而对 MuseGAN 进行一些实验。

生成器的输出是一个范围在 [−1, 1] 的值数组（由于最终层的 tanh 激活函数）。为了将其转换为每个音轨的单个音符，我们为每个时间步选择 84 个音高中的最大值。在原始 MuseGAN 论文中，作者使用 0 作为阈值，因为每个音轨可以包含多个音符；然而，在此设置中，我们可以简单地取最大值，以保证每个时间步每个音轨恰好有一个音符，就像巴赫圣咏的情况一样。

图 11-16 显示了模型从随机正态分布噪声向量生成的乐谱（左上）。我们可以找到数据集中最接近的乐谱（按欧几里得距离），并检查生成的乐谱是否不是数据集中已存在的音乐的复制品——最接近的乐谱显示在其下方，我们可以看到它与生成的乐谱不相似。

### 生成的乐谱

![](img/f0f0f5d89818fdddf117bbe758ac8143_354_0.png)

### 更改风格噪声

![](img/f0f0f5d89818fdddf117bbe758ac8143_354_1.png)

### 最接近的真实乐谱

![](img/f0f0f5d89818fdddf117bbe758ac8143_354_2.png)

### 更改旋律噪声
仅限顶线

![](img/f0f0f5d89818fdddf117bbe758ac8143_354_3.png)

### 更改和弦噪声

![](img/f0f0f5d89818fdddf117bbe758ac8143_354_4.png)

### 更改节奏型噪声
仅限底线

![](img/f0f0f5d89818fdddf117bbe758ac8143_354_5.png)

图 11-16. MuseGAN 预测乐谱示例，显示训练数据中最接近的真实乐谱以及输入噪声变化如何影响生成的乐谱

现在让我们尝试调整输入噪声以微调生成的乐谱。首先，我们可以尝试更改和弦噪声向量——图 11-16 中左下方的乐谱显示了结果。我们可以看到每个音轨都发生了变化，正如预期的那样，而且两个小节也表现出不同的特性。在第二个小节中，低音更具动态性，上声部音高也高于第一个小节。这是因为影响两个小节的潜在向量是不同的，因为输入的和弦向量经过了时序网络的处理。

当我们更改风格向量（右上）时，两个小节以相似的方式发生变化。整个段落的风格与原始生成的乐谱相比发生了变化，且方式一致（即相同的潜在向量被用来调整所有音轨和小节）。

我们还可以通过旋律和节奏型输入单独更改音轨。在图 11-16 中右中部的乐谱中，我们可以看到仅更改音乐顶线的旋律噪声输入的效果。其他所有部分保持不变，但顶线的音符发生了显著变化。此外，我们可以看到两个之间有节奏变化
