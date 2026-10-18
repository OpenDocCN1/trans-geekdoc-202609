

`from sklearn.ensemble import StackingRegressorfrom sklearn.model_selection import StratifiedKFold gbm = GradientBoostingRegressor(n_estimators=300, subsample=0.9, max_depth=16, learning_rate=0.1, random:state=42) svr = SVR(C=10.0, gamma=0.4, epsilon=0.0001) sfk = StratifiedKFold(n_splits=10, shuffle=True, random:state=42) stacker = StackingRegressor(estimators=[('svm', svr)], final_estimator=gbm, passthrough=True, cv=sfk, n_jobs=-2)stacker.fit(X_train, y_train)preds = stacker.predict(X_test)mae = mean_absolute_error(y_test, preds)print(f"test mean absolute error for stacker: {mae:0.3}")`

![Tip](images/tip.png)堆叠多个模型并堆叠或混合多个堆叠的结果，是赢得机器学习竞赛的最佳实践。在实际应用中，请始终牢记，技术债务——即用不必要的复杂性换取微小的额外性能提升——最终都必须偿还。作为一般建议，只有当与使用更简单的方案相比，其差异确实值得时，才采用混合和堆叠。

Part 5

# 将学习应用于实际问题

处理图像

读取和处理文本

对文本进行评分和分类

使用数据进行推荐

Chapter 17

# 图像分类

本章内容

![Bullet](images/check.png)**使用 Python 处理图像**

![Bullet](images/check.png)**从图像中获取特征**

![Bullet](images/check.png)**使用图像信息检测人脸特征**

![Bullet](images/check.png)**对人脸图像执行图像分类任务**

在五种感官中，视觉无疑是传递来自外部世界的知识和信息最强大的感官。许多人认为，视觉天赋有助于儿童了解周围的不同事物和人物。此外，人类通过图片、视觉艺术和文本文档跨越时间接收和传递知识。本章的第一部分将帮助你了解 Python 如何帮助你的计算机与图像进行交互。

由于视觉非常重要和宝贵，它对机器学习算法来说同样无价，因为视觉为算法开辟了新的能力。当今大部分信息都以数字形式存在（文本、音乐、照片和视频），然而，仅仅能够以二进制格式读取视觉信息并不能帮助你理解它并正确使用它。近年来，视觉在机器学习中更重要的用途之一是出于各种原因对图像进行分类。本章将帮助你发现用于获取图像特征以供机器学习任务使用的技术。

例如，机器人需要知道应该避开哪些对象以及需要与哪些对象协作，然而，如果没有图像分类，这项任务就无法完成。人类也依赖图像分类来执行诸如手写识别和在人群中寻找特定个人等任务。以下是图像分类的其他一些重要任务：进行医疗扫描；检测行人（这是汽车中需要实现的重要功能，可能挽救成千上万条生命）；以及帮助农民确定田地最需要水的地方。请查看图像分类的一些用途：[`http://rodrigob.github.io/are_we_there_yet/build/`](http://rodrigob.github.io/are_we_there_yet/build/) 和 [`https://www.altexsoft.com/blog/image-recognition-neural-networks-use-cases/`](https://www.altexsoft.com/blog/image-recognition-neural-networks-use-cases/)。本章的最后两部分演示了获取图像信息的技术，然后使用该信息执行分类任务。

![Remember](images/remember.png)你不必手动输入本章的源代码。事实上，使用可下载的源代码要容易得多。你可以在 Python 代码可下载源代码的 `ML4D2E` 文件夹和 R 代码可下载源代码的 `ML4D2ER` 文件夹中找到本章的源代码。本章的示例文件将以 `ML4D2E; 17;`（用于 Python）或 `ML4D2E_R; 17;`（用于 R）开头。有关如何找到这些源文件的详细信息，请参阅简介。

## 处理一组图像

乍一看，图像文件似乎是由一系列位组成的非结构化数据。文件并没有以任何方式将位彼此分开。你不能简单地查看文件并看到任何图像结构，因为根本不存在这样的结构。与其他文件格式一样，图像文件依赖于用户知道如何解释数据。例如，图片文件中的每个像素可能由三个 32 位字段组成。知道每个字段是 32 位取决于你。文件开头的标头可能会提供关于解释文件的线索，但即便如此，你也需要知道如何使用正确的包或库与文件进行交互。

你在本章中使用 Scikit-image 进行示例演示。它是一个专门用于处理图像、从文件中获取图像以及使用 NumPy 数组处理图像的 Python 包。通过使用 Scikit-image，你可以获得加载和转换图像以供任何机器学习算法使用所需的所有技能。该包还可以帮助你上传所有必要的图像，调整大小或裁剪它们，并将它们展平为特征向量，以便将其转换为学习用途。

Scikit-image 不是唯一可以帮助你在 Python 中处理图像的包。还有其他包，例如以下包：

*   **`scipy.ndimage` (**[`https://docs.scipy.org/doc/scipy/reference/ndimage.html`](https://docs.scipy.org/doc/scipy/reference/ndimage.html)**):** 允许你对多维图像进行操作

*   **`Mahotas` (**[`https://mahotas.readthedocs.org/en/latest/`](https://mahotas.readthedocs.org/en/latest/)**):** 一个基于快速 C++ 的处理库

*   **`OpenCV` (**[`https://opencv-python-tutroals.readthedocs.org/`](https://opencv-python-tutroals.readthedocs.org/)**):** 一个专门从事计算机视觉的强大包

*   **`ITK` (**[`https://www.itk.org/`](https://www.itk.org/)**):** 专为医疗目的处理 3D 图像而设计

*   **`Pillow` (**[`https://pillow.readthedocs.io/en/stable/`](https://pillow.readthedocs.io/en/stable/)**):** Python 图像库 (PIL) 的友好版本，使点操作、过滤、操作和其他图像处理在 Python 中变得容易。Pillow 支持多种图像格式，可以帮助你克服其他库中发现的图像处理问题。

*   **`Matplotlib` (**[`https://matplotlib.org/`](https://matplotlib.org/)**):** 尽管此库通常与绘图相关联，但你也可以使用它进行图像处理。不幸的是，文件格式的数量有限，但当你需要在单个应用程序中同时进行绘图和图像处理，并且不想依赖太多库时，这可能是一个不错的选择。

本节中的示例展示了如何将图片作为非结构化文件来处理。示例图片来自 [`https://commons.wikimedia.org/wiki/Main_Page`](https://commons.wikimedia.org/wiki/Main_Page) 的公共领域资源。要处理图像，你需要访问 Scikit-image 包 ([`https://scikit-image.org/`](https://scikit-image.org/))，这是一个用于图像处理的算法集合。你可以在 [`https://scipy-lectures.github.io/packages/scikit-image/`](https://scipy-lectures.github.io/packages/scikit-image/) 找到该包的教程。第一项任务是使用以下代码在屏幕上显示图像。（请耐心等待：当 Notebook 选项卡上的忙碌指示器消失时，图像即已准备就绪。）

