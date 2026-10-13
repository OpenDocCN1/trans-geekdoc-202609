

## 5. 练习 19.9

**(e)** 在训练期间，每隔 20 个 epoch，可视化生成器创建的生成图像，并对学习过程的演变进行评论。

**(f)** 尝试调整上述建议的所有各种参数，并观察其对训练的影响。

## 3. 练习 19.10

本练习有助于熟悉 Transformer 架构并探究位置编码的影响。重点在于语言翻译 NLP 任务，更具体地说是德译英任务，遵循 PyTorch 教程：<https://pytorch.org/tutorials/beginner/translation_transformer.html>。

在该教程中，详细描述了数据集的设置、Transformer 以及训练过程。最后通过翻译德语句子“Eine Gruppe von Menschen steht vor einem Iglu,”（英语意为“A group of people stands in front of an igloo.”）提供了一个简单的定性评估。

### 1. (a)

尝试各种 Transformer 超参数，即：

*   **`EMB_SIZE`**（嵌入空间维度，$d_m$）。从 `EMB_SIZE=512` 开始。
*   **`NHEAD`**（注意力头数）。从 `NHEAD=8` 开始。
*   **`FFN_HID_DIM`**（两层 FCN 模块的隐藏层维度）。从 `FFN_HID_DIM=512` 开始。
*   **`NUM_ENCODER_LAYERS`**（编码器块数量）。从 `NUM_ENCODER_LAYERS=3` 开始。
*   **`NUM_DECODER_LAYERS`**（解码器块数量）。从 `NUM_DECODER_LAYERS=3` 开始。

在不牺牲性能的前提下，架构可以压缩到何种程度（即减小上述数值）？

### 2. (b)

调整 `PositionalEncoding` 类以移除位置编码的影响。可以添加一个参数来控制是否将位置编码添加到词元嵌入中。具体而言，可以修改 `PositionalEncoding` 类，使其拥有一个额外的参数 `use_pos_encoding`。

### 3. 注意

请注意，该 `PositionalEncoding` 层的 dropout 可能会影响性能，因此在此实验中将 dropout 值设为零。请注意，该 `Seq2SeqTransformer` 定义有一个 dropout 参数，您可以在其中设置 `dropout=0`。在之前的德语句子上评估不带位置嵌入的 Transformer 的性能。结合位置编码的功能，对获得的结果进行评论。

## 5. 练习 19.11

本练习作为自监督方法的入门，重点在于在 MNIST 数据集上实现 SimCLR（第 19.6.5 节）。SimCLR 在预训练期间应用对比学习，同时涉及各种实现细节和超参数，这些都会影响微调阶段的下游性能。

### 1. (a) 实现细节

*   **增强**：创建一个数据加载器，为每张图像提供两个增强版本。使用以下变换序列：`RandomHorizontalFlip()`、`RandomResizedCrop(size=28, scale=(0.2, 1.))`、`ToTensor()`、`Normalize((0.5,), (0.5,))`。
*   **编码器**：设计一个包含三个卷积层的序列，输出通道数分别为：32、64 和 128。使用 `kernel size` 3、`stride` 1 和 `padding` 1。在每个卷积层后应用批量归一化、ReLU 激活和最大池化。最大池化使用 `kernel size` 2 和 `stride` 2，最后一次操作的 `padding` 为 1。
*   **投影头**：应在编码器的输出上应用一个投影头。使用一个线性层将编码器的输出维度映射到 128 维特征空间。

### 2. (b) 预训练

利用 PyTorch 中的交叉熵损失函数实现 InfoNCE 损失函数。可将 InfoNCE 视为特征相似度上的二元交叉熵损失。以温度 0.07 和批量大小 64 训练编码器及其投影头 100 个 epoch。使用 Adam 优化器，`learning rate` 为 0.003，`weight decay` 为 0.003。

### 3. (c) 下游性能

为了评估网络，使用编码器（而非投影头）为所有训练和测试图像提取相应的特征向量。将这些向量作为新数据集，训练三种不同的分类器：（i）线性层，（ii）逻辑回归，和（iii）$k$-NN，以评估下游性能。

### 4. (d) 批量大小的作用

在预训练阶段尝试不同的批量大小。随着批量大小增大，性能如何变化？对结果进行评论。

### 5. (e) 温度的作用

使用不同的 `temperature values` 进行预训练，即 0.07、0.2、0.5 和 1。温度如何影响下游性能？

### 6. (f) 投影头的作用

应在编码器的输出处应用一个投影头。使用一个线性层将编码器的输出维度映射到 128 维特征空间。输出特征上应应用 $\ell_2$ 归一化。研究以下情况对下游性能的影响：(i) 不使用投影头进行预训练，以及 (ii) 使用带有一个 ReLU 激活的两层 MLP 作为投影头。评估投影头的重要性。

### 7. (g) Epoch 数量的作用

探究延长预训练时长（例如 200、300、400 个 epoch）对下游性能指标的影响。

## 6. 练习 19.12

本练习的重点在于扩散模型，使用基于 `HuggingFace` `Diffusers` 包的 DDPM，该包基于 PyTorch 编写。源代码在此：<https://github.com/huggingface/diffusers>。练习包含以下步骤：

### 1. (a)

从 `HuggingFace` 模型中心加载预训练的 Stable Diffusion 模型，即 `Stable Diffusion v2`。在 PyTorch 中，可以通过使用 `diffusers` 包的 `StableDiffusionPipeline` 模块中的 `stable-diffusion-2` 预训练模型来实现。

### 2. (b)

移除少量自注意力和交叉注意力层，并在每次修改后生成图像，以分析其对图像连贯性和相关性的影响。这可以通过将 U-Net 主干网络中任意注意力层的参数应用函数 `param.fill_(0)` 来完成。

### 3. (c)

改变扩散步数（例如减半、加倍），并观察图像质量和生成时间的变化。使用 DPM-Solver++ 调度器（`diffusers` 包的 `DPMSolverMultistepScheduler` 模块）。

### 4. (d)

在使用无分类器引导时，通过调整模型以增强或减弱提示词条件控制，来检查模型表现。调整模型的 `guidance_scale` 参数；`guidance_scale = 1` 对应无引导。

### 5. (e)

修改扩散过程中使用的噪声调度。评估其对生成图像平滑度和真实感的影响。调整 `DPMSolverMultistepScheduler` 模块的参数 `beta_start` 和 `beta_end`，它们分别是推理的起始和最终 beta 值，并将 `beta_schedule` 定义为 linear 或 `scaled_linear`。

## 参考文献

