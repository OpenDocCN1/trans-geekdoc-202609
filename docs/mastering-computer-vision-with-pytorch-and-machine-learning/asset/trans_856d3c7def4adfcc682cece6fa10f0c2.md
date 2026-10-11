

![图 9.5. 由预训练的 Hugging Face U-Net 模型生成的假图像：(A) ‘google/ddpm-celebahq-256’；(B) ‘google/ddpm-ema-church-256’；(C) ‘google/ddpm-ema-cat-256’。](images/bk978-0-7503-6244-3ch9f5_online.jpg)

**图 9.5.** 由预训练的 Hugging Face U-Net 模型生成的假图像：(A) ‘google/ddpm-celebahq-256’；(B) ‘google/ddpm-ema-church-256’；(C) ‘google/ddpm-ema-cat-256’。

在我们的 PyTorch 代码中使用 Hugging Face 强大的 U-Net 来处理自定义数据集（例如从 Kaggle 下载的花卉数据集）更加灵活。该数据集约为 215 MB，包含五种美丽的花卉：雏菊、蒲公英、玫瑰、向日葵和郁金香。该数据集由 DPhi Data Sprint #25：花卉识别发布，遵循知识共享署名许可证。以下项目 [9.3.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn17) 的输出结果如图 [9.6](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig6) 所示。每 25 个 epoch 保存一个训练好的模型，用于接下来的 25 个 epoch。总共 25 × 11 个 epoch 的模型训练耗时约 11 小时。结果已经相当不错，但仍不如原始图像。花卉项目的代码与第 [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9s9-2) 节中二次曲线项目的代码几乎相同。仅用 Cell 06 中的三行代码，我们就可以从 Hugging Face 导入一个预训练的 U-Net。每完成 25 个 epoch 的模型训练，Cell 10 中的代码就会保存模型。保存的模型将由 Cell 06 中的代码加载。

![](images/bk978-0-7503-6244-3ch9uf13_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf14_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf15a_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf15b_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf16_pr.gif)

![图 9.6. (A) 来自 Kaggle 花卉数据集的原始花卉图像，许可证为 CCO 1.0。(B) 由 Hugging Face 的 DDMP U-Net 从纯噪声生成的假花卉图像，模型训练耗时约 11 小时。](images/bk978-0-7503-6244-3ch9f6_online.jpg)

**图 9.6.** (A) 来自 Kaggle [花卉数据集](https://www.kaggle.com/datasets/imsparsh/flowers-dataset) 的原始花卉图像，许可证为 CCO 1.0。(B) 由 Hugging Face 的 DDMP U-Net 从纯噪声生成的假花卉图像，模型训练耗时约 11 小时。

### 9.4 通过 Stable Diffusion 根据文本提示生成逼真图像

由预训练的 Hugging Face U-Net 模型生成的花卉图像非常美丽。然而，我们无法控制生成哪种花卉。我们可以使用条件 DDMP 模型根据我们的设置生成图像。即使我们拥有上千行代码且运行良好的条件 DDMP 模型，它也只能生成受训练数据集限制的类别图像。要获得逼真图像，模型训练时间可能会非常长。我们如何在不进行模型训练的情况下，仅使用文本提示生成任意高质量图像？

我们现在（自 2022 年起）拥有一种生成模型，可以根据文本提示生成任意图像。它是 Hugging Face 的 Stable Diffusion，一种名为潜在扩散模型的深度学习文生图模型（LDM (Rombach *et al* [2022](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib5))）。用于训练 Stable Diffusion 的数据集是 Laion-5B，这是一个开源数据集，提供超过 58.5 亿对经过 CLIP 筛选的图文对。自然语言处理（NLP）是计算机科学的一个分支。第 [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9s9-2) 节中使用的多头自注意力是一种从编码文本中获取信息的 NLP 方法。Stable Diffusion 是计算机视觉与 NLP 的融合。Hugging Face 有一个 Stable Diffusion 2.1 演示网站，其中包含一个指向 DreamStudio Beta 的链接。第二个网站生成的图像对我们的文本提示具有更高的忠实度。如果你生成人脸图像，你会看到这两个网站之间巨大的差异。我们可以下载 Stable Diffusion 的库并在 VS Code 中练习生成图像。这些库和预训练参数的文件体积巨大（>10 GB）。为了节省计算机硬盘空间，你可以在配有免费 GPU 的 Google Colab 或 Kaggle 中运行以下代码（图 [9.7](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig7)）。2024 年 1 月，微软的 Copilot 和谷歌的 Bard 让人们能够通过文本提示生成逼真图像。

![](images/bk978-0-7503-6244-3ch9uf17_pr.gif)

![图 9.7. 在项目 9.4 中，由预训练的 Stable Diffusion 在 Google Colab 中运行，根据文本提示“a girl in a rose garden”生成的图像。](images/bk978-0-7503-6244-3ch9f7_online.jpg)

**图 9.7.** 在项目 [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn21) 中，由预训练的 Stable Diffusion 在 Google Colab 中运行，根据文本提示“a girl in a rose garden”生成的图像。

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

