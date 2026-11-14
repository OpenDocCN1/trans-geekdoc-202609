
实际上，使用标准库可以轻松生成等高线图。这里我将在 `Python` 中对比 `Matplotlib` 与 `Plotly`。由于 `Plotly` [[维基](https://en.wikipedia.org/wiki/Plotly)] 是一个用于不同编程语言的通用库，此处讨论的代码可以轻松适配到 `R` 或 `Julia`。本节中的等高线图还表明，高斯类分布的**混合**通常是非高斯类的，且可能是单峰的，也可能不是。然后，关联的**数据视频**通过各种旋转，能让你更好地查看数据。它也非常适合展示随时间演变的系统：一个时间序列，其中每个观测值都是一幅图像。你可以在此观看视频 [here](https://www.youtube.com/watch?v=Jpjw8wtoZrM)。[图 14.2](#Chp014_259-276_B9780443218576000187.xhtml#f0025) 中所示的最后一帧由 `Plotly` 生成，对应第 [18.3.6](#Chp018_361-386_B9780443218576000229.xhtml) 节中 [图 18.6](#Chp018_361-386_B9780443218576000229.xhtml) 所展示的相同分布混合，只不过那次是用 `Mathematica` 生成的。

![图 14.2 等高线图，3D 混合模型，由 Plotly 生成。](images/B9780443218576000187/gr009.jpg)

*图 14.2 等高线图，3D 混合模型，由 Plotly 生成。*

用于生成视频的数据集包含 300 张图像（视频帧），代表随时间演变的某些分布混合。它基于合成数据：大约有 20 个参数驱动演变并控制这些山脉的行为，包括一座正在升起的火山。其中一个参数控制火山增长的衰减率。简而言之，整个视频可以用 20 个数字来概括，在机器学习中称为特征。用于生成数据的模型称为生成模型。

正如图像（例如手写数字图片）可以用 10 个参数概括以执行文本识别一样，这里 20 个参数允许你执行地形分类。不仅是静态地形，还有随时间变化的地形，假设你有代表不同地形的 ![Image](images/B9780443218576000187/fx002.jpg) 视频。你可以使用第 [14.4.2](#Chp014_259-276_B9780443218576000187.xhtml#s0070) 节中的代码生成监督分类所需的视频。下一步是使用来自现实世界的数据（视频），并利用在合成数据上训练的模型进行分类。

### 14.4.1 使用 Matplotlib 的 Python 代码

源代码也可在我的 GitHub 仓库中获取，[点击此处](https://github.com/VincentGranville/Visualizations/blob/main/Source-Code/contourvideoplotly.py)。查找以 `contour` 开头的文件名。该文件夹还包含视频和动画 GIF 版本。尽管我有**颜色不透明度**和透明度方面的经验，但我无法修复 `Matplotlib` 版本中 [图 14.3](#Chp014_259-276_B9780443218576000187.xhtml#f0030) 可见的问题。这个故障产生了一个不错的视觉错觉：如果你盯着 [图 14.3](#Chp014_259-276_B9780443218576000187.xhtml#f0030) 看足够长的时间，它会在从上方看到的山脉和从地下看到的山脉（显示山脉内部）之间来回切换。

![图 14.3 同图 14.2，由 Matplotlib 生成。](images/B9780443218576000187/gr010.jpg)

*图 14.3 同 [图 14.2](#Chp014_259-276_B9780443218576000187.xhtml#f0025)，由 Matplotlib 生成。*

此问题在 `Plotly` 版本中得到了解决。该库更全面且更难掌握，但提供了更多可能性。本节中的代码对应 `Plotly` 版本，包括视频生成。颜色的选择由参数 `colorscale` 决定，此处设置为 `Peach`。可用调色板列表发布在[此处](https://plotly.com/python/builtin-colorscales/)。你可以轻松添加坐标轴和标签、更改字体大小等。处理这些的参数存在于源代码中，但在当前版本中已关闭。

![](images/B9780443218576000187/gr011.jpg)

### 14.4.2 使用 Plotly 的 Python 代码

下面是 `Matplotlib` 版本。它也在 GitHub 上提供，[点击此处](https://github.com/VincentGranville/Visualizations/blob/main/Source-Code/contourMatplotlib.py)。我未在 `Matplotlib` 版本中包含视频生成的代码。

![](images/B9780443218576000187/gr013.jpg)

### 14.4.3 快速解决新问题的技巧

假设你被要求在 `Python` 中生成高质量的 3D 等高线图——而不是曲面图——但你完全不知道如何开始。不过，你熟悉 `Matplotlib`，但对 `Python` 还比较陌生。你有 48 小时完成这个项目（两天的工作时间，减去每天耗费时间的日常杂务）。你会如何着手？这里我解释我是如何做到的，因为我当时处于同样的境地（是我自己强加给自己的）。我只专注于 3D 等高线图，因为我预先知道如何快速将其转化为视频，只要我能生成一张像样的单张图。我的策略分解为以下步骤：

- 我很快意识到生成 2D 等高线图或曲面图非常容易，但 3D 等高线图却不容易。我搜索了 "`contour map 3d matplotib`"。对结果不满意，我搜索了图片而非网页。这引导我找到了一个 `Stackoverflow` 论坛问题 [here](https://stackoverflow.com/questions/35445424/surface-and-3d-contour-in-matplotlib)，进而找到了 `Matplotlib` 网站上的某个页面 [here](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.contour.xhtml)。

- 调整一些参数后，我生成了 [图 14.3](#Chp014_259-276_B9780443218576000187.xhtml#f0030)。对结果不满意且花费大量时间试图修复故障后，我在 `Stackoverflow` 上寻求修复方法。你可以在此查看我的问题及发布的回答 [here](https://stackoverflow.com/questions/74166875/problem-with-3d-contour-plots-in-matplotlib)。一位参与者建议使用颜色透明度，但这没用，因为我之前试过不成功。第二个回答附带了一段代码，作者建议我使用 `Plotly` 而不是 `Matplotlib`。我采纳了他的建议，安装 `Plotly` 后让他的代码跑通了（我收到一条错误消息要求安装 `Kaleido`，但这很容易解决）。相当兴奋，但这远未结束。

- 我搜索了 "`Matplotlib vs Plotly`"，以确保使用 `Plotly` 是合理的。我被说服了，特别是考虑到我对科学计算的兴趣。但很快我发现我的图被任意截断了。我搜索了 "`plotly 3d contour map`" 和 "`plotly truncated 3d contour`"，这引导我访问了多个网站，包括对布局和场景参数的详细描述。这个 [网页](https://stackoverflow.com/questions/73187799/truncated-figure-with-plotly) 特别有用，因为它提供了解决我问题的方案。

- 我花了一些时间弄清楚如何移除坐标轴和标签，因为我担心它们会在视频中造成问题，根据过往经验，它们会从一帧到下一帧发生变化。我用了 30 分钟通过试错找到解决方案。但随后我意识到还剩一个问题：在 `PNG` 输出图像中，图表只占一小部分，尽管在 `Python` 环境中看起来很好。搜索 "`plotly write_image`" 没帮助。我试图在 `Stackoverflow` 上提问，但 24 小时内不允许再提问。我转而在 `Reddit` `Python` 论坛提问。

- 最终，通过缩小 `Z` 轴、修改图表方向、边距和图像尺寸，我获得了显著改进。等我去查看 `Reddit` 问题的潜在回答时，我的帖子已被管理员删除。但我最终解决了它。嗯，几乎解决了。
