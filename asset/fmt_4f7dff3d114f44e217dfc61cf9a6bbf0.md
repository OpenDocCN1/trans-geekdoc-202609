
DDPM 论文的作者将预测的 $\mu_{\theta}(x_t,t)$ 设置为与公式 (9.5) 中所示的 $\tilde{\mu}_t(x_t,x_0)$ 具有相同格式，并忽略公式中的所有繁杂项，得到一个重加权版本的 $L_{VLB}$，该版本强调重建质量，其中 $\varepsilon_{\theta}$ 是一个旨在从 $x_t$ 预测 $\varepsilon$ 的函数逼近器：

$$L_{t-1} = E_{x_0,\varepsilon}(\parallel\varepsilon - \varepsilon_{\theta}(x_t,t)\parallel^2) \tag{9.9}$$

我们训练 `U-Net` 模型在时间步 $t$ 预测噪声 $\varepsilon_{\theta}$，然后根据公式 (9.9) 在均方误差 (MSE) 损失函数中计算预测噪声 $\varepsilon_{\theta}$ 与噪声 $\varepsilon$ 之间的差异，其中 $x_t = \sqrt{\bar{\alpha}_t}x_0 + \sqrt{1 - \bar{\alpha}_t}\varepsilon$。

`Cell 06` 中定义的一个函数用于根据上述 DDPM 理论训练 `U-Net`，并做了一点修改。为了节省模型训练时间，我们不在每个批次中对每张图像使用所有时间步。`Cell 07` 第 10 行的代码生成一批从 0 到 $T-1$（包含）的随机整数作为时间步。通过第 12 行的代码，我们通过添加第 11 行代码生成的一批噪声 $\varepsilon$，获得那些时间步下的一批潜在图像 $x_t$。然后 `U-Net` 为我们预测噪声 $\varepsilon_{\theta}$，以便根据公式 (9.9) 计算 MSE 损失。

`Cell 05` 中定义的第一个函数用于时间戳。`U-Net` 的主干网络与第 9.1 节中的相同，但有许多修改。我们必须通过基本块（`Cell 06` 的 `Basic` 类）中的时间嵌入用时间戳标记潜在图像。我们在第 3.3 节中为条件 GAN 使用了标签信息嵌入。时间嵌入可以通过多种方式完成。`Cell 05` 中定义的 `sinusoidal_embedding` 函数代码受 Brian Pulfer 的 [GitHub](https://medium.com/mlearning-ai/enerating-images-with-ddpms-a-pytorch-implementation-cef5a2ba8cb1) 仓库代码启发。多头自注意力类（`MHSA`，Petit 等人 [2020]）用于桥接部分。该类实例内部有四个自注意力头。该实例的输入 Q、K 和 V 相同：一个经过层归一化和重塑的桥接张量。关于多头自注意力的详细信息将在第 10 章提供。单头交叉注意力类（`Attention`）用于修改 `U-Net` 的跳跃连接。我在观看 DigitalSreeni 的 [YouTube 视频](https://www.youtube.com/watch?v=KOF38xAvo8I) 并阅读 Attention U-Net 论文（Oktay 等人 [2018]）后编写了单头交叉注意力代码。带有注意力机制的 `U-Net` 给图像的相关部分更大的权重。在 `Cell 06` 的 `Basic` 类中，使用快捷连接构建残差网络，并使用了层归一化。花费了很长时间才得到图 9.4(C) 所示的平滑二次曲线。`Cell 09` 中定义的函数基于公式 (9.5)–(9.6) 从纯噪声生成图像。

![图 9.4(A)](img/bk978-0-7503-6244-3ch9uf8_pr.gif)

![图 9.4(B)](img/bk978-0-7503-6244-3ch9uf9_pr.gif)

![图 9.4(C)](img/bk978-0-7503-6244-3ch9uf10_pr.gif)

![图 9.4(D)](img/bk978-0-7503-6244-3ch9uf11_pr.gif)

### 9.3 使用 Hugging Face 的预训练 U-Net 生成图像

上一节中的注意力 `U-Net` 对 MNIST 足够强大，但对 CIFAR10 不够智能。为了为 CelebA 和 STL10 等其他数据集生成高质量假图像，我们需要更强大的 `U-Net`。幸运的是，Hugging Face 为不同数据集提供了预训练的 `U-Net` 模型。我们只需编写几行代码即可生成精美图像。以下项目 9.3.1 中的代码用于演示 Hugging Face 扩散模型的强大功能。运行代码前，请在工作区的 VS Code 终端中使用 DOS 命令 `pip install Hugging Face diffusers`。第 2 行的 `model_id` 是特定数据集预训练参数文件的名称。首次运行代码时，将为 `DDPMPipeline` 下载一个约 500 MB 的 `U-Net` 文件。你可以从 Hugging Face 找到更多带有预训练参数的文件，第 2-3 行列出了几个此类文件的名称。第 5 行 `DDPMPipeline` 实例的输出是一个包含名为 `sample` 的键的字典。该键的值是一个仅包含一个元素的列表，即从纯噪声生成的图像。第 6 行代码提取并显示该图像。图 9.5 显示了由三个预训练 `U-Net` 生成的三张假图像。我相信，仅用六行代码的程序生成的图像质量可以与著名网站 *This Person Does Not Exist* 上的图像质量相媲美。你可以尝试在笔记本电脑或 Google Colab 上运行这段简短的代码。在我的配备 RTX 2060 GPU 的笔记本电脑上，程序运行时间约为 2.5 分钟。

![图 9.5](img/bk978-0-7503-6244-3ch9uf12_pr.gif)

![图 9.5. 由预训练的 Hugging Face U-Net 模型生成的假图像：(A) ‘google/ddpm-celebahq-256’；(B) ‘google/ddpm-ema-church-256’；(C) ‘google/ddpm-ema-cat-256’。](img/bk978-0-7503-6244-3ch9f5_online.jpg)

**图 9.5.** 由预训练的 Hugging Face `U-Net` 模型生成的假图像：(A) ‘google/ddpm-celebahq-256’；(B) ‘google/ddpm-ema-church-256’；(C) ‘google/ddpm-ema-cat-256’。

在我们的 PyTorch 代码中使用 Hugging Face 强大的 `U-Net` 来处理自定义数据集（例如从 Kaggle 下载的花卉数据集）更加灵活。该数据集约为 215 MB，包含五种美丽的花卉：雏菊、蒲公英、玫瑰、向日葵和郁金香。该数据集由 DPhi Data Sprint #25：花卉识别发布，遵循知识共享署名许可证。以下项目 9.3.2 的输出结果如图 9.6 所示。每 25 个 epoch 保存一个训练好的模型，用于接下来的 25 个 epoch。总共 25 × 11 个 epoch 的模型训练耗时约 11 小时。结果已经相当不错，但仍不如原始图像。花卉项目的代码与第 9.2 节中二次曲线项目的代码几乎相同。仅用 `Cell 06` 中的三行代码，我们就可以从 Hugging Face 导入一个预训练的 `U-Net`。每完成 25 个 epoch 的模型训练，`Cell 10` 中的代码就会保存模型。保存的模型将由 `Cell 06` 中的代码加载。

![](img/bk978-0-7503-6244-3ch9uf13_pr.gif)

![](img/bk978-0-7503-6244-3ch9uf14_pr.gif)

![](img/bk978-0-7503-6244-3ch9uf15a_pr.gif)

![](img/bk978-0-7503-6244-3ch9uf15b_pr.gif)

![](img/bk978-0-7503-6244-3ch9uf16_pr.gif)

![图 9.6. (A) 来自 Kaggle 花卉数据集的原始花卉图像，许可证为 CCO 1.0。(B) 由 Hugging Face 的 DDMP U-Net 从纯噪声生成的假花卉图像，模型训练耗时约 11 小时。](img/bk978-0-7503-6244-3ch9f6_online.jpg)

**图 9.6.** (A) 来自 Kaggle [花卉数据集](https://www.kaggle.com/datasets/imsparsh/flowers-dataset) 的原始花卉图像，许可证为 CCO 1.0。(B) 由 Hugging Face 的 DDMP `U-Net` 从纯噪声生成的假花卉图像，模型训练耗时约 11 小时。

### 9.4 通过 Stable Diffusion 根据文本提示生成逼真图像

由预训练的 Hugging Face `U-Net` 模型生成的花卉图像非常美丽。然而，我们无法控制生成哪种花卉。我们可以使用条件 DDMP 模型根据我们的设置生成图像。即使我们拥有上千行代码且运行良好的条件 DDMP 模型，它也只能生成受训练数据集限制的类别图像。要获得逼真图像，模型训练时间可能会非常长。我们如何在不进行模型训练的情况下，仅使用文本提示生成任意高质量图像？

我们现在（自 2022 年起）拥有一种生成模型，可以根据文本提示生成任意图像。它是 Hugging Face 的 Stable Diffusion，一种名为潜在扩散模型的深度学习文生图模型（LDM (Rombach *et al* 2022)）。用于训练 Stable Diffusion 的数据集是 Laion-5B，这是一个开源数据集，提供超过 58.5 亿对经过 CLIP 筛选的图文对。自然语言处理（NLP）是计算机科学的一个分支。第 9.2 节中使用的多头自注意力是一种从编码文本中获取信息的 NLP 方法。Stable Diffusion 是计算机视觉与 NLP 的融合。Hugging Face 有一个 Stable Diffusion 2.1 演示网站，其中包含一个指向 DreamStudio Beta 的链接。第二个网站生成的图像对我们的文本提示具有更高的忠实度。如果你生成人脸图像，你会看到这两个网站之间巨大的差异。我们可以下载 Stable Diffusion 的库并在 VS Code 中练习生成图像。这些库和预训练参数的文件体积巨大（>10 GB）。为了节省计算机硬盘空间，你可以在配有免费 GPU 的 Google Colab 或 Kaggle 中运行以下代码（图 9.7）。2024 年 1 月，微软的 Copilot 和谷歌的 Bard 让人们能够通过文本提示生成逼真图像。

![](img/bk978-0-7503-6244-3ch9uf17_pr.gif)

![图 9.7. 在项目 9.4 中，由预训练的 Stable Diffusion 在 Google Colab 中运行，根据文本提示“a girl in a rose garden”生成的图像。](img/bk978-0-7503-6244-3ch9f7_online.jpg)

**图 9.7.** 在项目 9.4 中，由预训练的 Stable Diffusion 在 Google Colab 中运行，根据文本提示“a girl in a rose garden”生成的图像。

### 参考文献

Ho J, Jain A and Abbeel P 2020 Denoising diffusion probabilistic models *Adv. Neural Inform. Process. Syst.* **33** 6840–51

Ioffe S and Szegedy C 2015 Batch normalization: accelerating deep network training by reducing internal covariate shift *Int. Conf. on Machine Learning* (PMLR) pp 448–56

Oktay O, Schlemper J, Folgoc L L, Lee M, Heinrich M, Misawa K, Mori K, Mcdonagh S, Hammerla N Y and Kainz B 2018 Attention u-net: learning where to look for the pancreas *arXiv preprint* arXiv:[1804.03999](http://arxiv.org/abs/1804.03999)

Petit O, Thome N, Rambour C, Themyr L, Collins T and Soler L 2021 U-net transformer: Self and cross attention for medical image segmentation *Int. Workshop on Machine Learning in Medical Imaging* (Berlin: Springer) pp 267–76

Rombach R, Blattmann A, Lorenz D, Esser P and Ommer B 2022 High-resolution image synthesis with latent diffusion models *Proc. of the IEEE/CVF Conf. on Computer Vision and Pattern Recognition* pp 10684–95

Ronneberger O, Fischer P and Brox T 2015 U-Net: convolutional networks for biomedical image segmentation *Int. Conf. on Medical Image Computing and Computer-Assisted Intervention* (Berlin: Springer) pp 234–41

Staal J, Abramoff M D, Niemeijer M, Viergever M A and Ginneken B V 2004 Ridge-based vessel segmentation in color images of the retina *IEEE Trans. Med. Imaging* [**23** 501–9](http://dx.doi.org/10.1109/TMI.2004.825627)

* * *

# **IOP** Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# 第 10 章

## 视觉 Transformer 的应用

使用基于 Transformer 而非卷积网络的模型，计算机足以理解人类语言。用于计算机视觉任务的 Transformer 称为视觉 Transformer。第一节介绍了基本视觉 Transformer 的架构。随后四节使用预训练的视觉 Transformer 对自定义数据集进行图像分类和目标检测，无需模型训练（零样本）。

# OpenAI 的 ChatGPT（生成式预训练 Transformer）的诞生是计算机科学领域的一次突破

人们可以与计算机聊天，讨论任何主题。ChatGPT 似乎无所不知，能够回答人们提出的许多问题。在 ChatGPT 网站的界面上，我使用了文本提示词“please write Python codes about logistic regression for me”（请为我编写关于逻辑回归的 Python 代码）。随后在几秒钟内，我就能从 ChatGPT 复制代码并粘贴到 VS Code 的一个单元格中运行。计算机已通过图灵测试，这是 AI 领域的一种探究方法，用于判断计算机是否具备像人类一样思考的能力。

ChatGPT 是一种语言模型，它使用 Transformer（Vaswani *et al* 2017）进行自然语言处理（NLP）任务，如语言翻译、文本分类和文本生成。Transformer 中包含一个编码器和一个解码器。用自然语言编写的文本提示词中的单词被数字化为高维向量空间中的 Token。Token 是一个小的信息单元。这些嵌入了文本提示词中单词序列信息的 Token 被用作 Transformer 编码器的输入。Transformer 中使用自注意力机制来捕捉论文中不同 Token 之间的依赖关系。Transformer 的使用给 NLP 任务带来了革命性的改进。

视觉 Transformer（ViT）是经过修改的 NLP Transformer，用于计算机视觉任务，如图像分类和目标检测。视觉 Transformer 由 Dosovitskiy *et al* 在其 2020 年的论文（Dosovitskiy *et al* 2020）中提出，题为“An Image Is Worth 16 × 16 Words: Transformers for Image Recognition at Scale”（“一幅图像胜过 16 × 16 个词：大规模图像识别 Transformer”）。与传统卷积神经网络使用一系列卷积和池化层从图像中提取局部特征不同，基于 NLP Transformer 的 ViT 可以捕捉图像不同部分之间的空间关系。

### 10.1 基础 ViT 模型的架构
