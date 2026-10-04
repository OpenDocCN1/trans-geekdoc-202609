

我们使用 `DenseNet-121` 架构作为我们的预测模型。我们将 512 × 512 像素的图像调整为 224 × 224，之后将其传递给卷积层，该层将其大小调整为 112 × 112 像素。然后图像通过池化层传输，池化层将图像大小调整为 56 × 56。该架构具有四个密集块，随后有三个过渡层。为了使模型更紧凑，我们在过渡层中减少了特征图的数目。密集块在每个块中对图像应用不同大小的滤波器进行训练，并且每次将输出图像大小减半。最终的密集块输出一个 7 × 7 像素的图像，该图像由分类层矢量化为 1 × 1 像素的输出。

权重是通过使用 `Glorot` 方法 (`Glorot,X` 和 `Bengio,Y`, Understanding the difficulty of training deep feedforward neural networks, [2010](#bodymatter-011.xhtml#b_9783110648195-011_ref_001)) 和 `batch normalization` 来防止过拟合，`dropout` 技术 (`Srivastava N`, Dropout: A simple way to prevent neural networks from overfitting, 2014) 通过以随机方式丢弃单元，使用 0.8 的 dropout 率来使用。

### 11.7.2.3 Results

我们在包含每个类别 1400 张图像的测试集上评估模型的性能。我们的模型实现了 89.50% 的显著准确率。从表-1 我们可以看到我们的模型在三个类别中实现了接近 1 的 `AUROC` 分数：侵袭性、原位和正常，以及在良性类别中非常高的 .98 值（参见表 11.3 和图 11.15）。

## 11.8 Conclusion and future work for case study 1

在这个项目中，我们初步了解了 HEP-2 细胞的分类，而且通过使用各种其他参数并相应地修改现有算法以满足需求，准确率水平仍有很大的改进空间。我们将致力于另一种算法，即 `RIC-LBP`。在该算法中，`LBP` 首先被制成旋转不变，然后在旋转不变的 LBP 之间找到共现对。此外，现有算法可以被定制以获得更好的结果，例如所选邻居的模式已被制成灵活的，因为我们使用了 `C` 语言。更精确的分类器如 `SVM` 可以被使用以产生更好的结果。从结果可以看出，`RIC-LBP` 直方图给出了最佳结果。使用 `CoALBP` 直方图特征获得的结果与 `RIC-LBP` 一样好，但使用 `LBP` 直方图获得的结果准确率非常低。此外，还对 `KNN` 分类器取了不同的 *K* 值，值 4 和 5 给出了我们最好的结果。由于具有区别性的纹理模式，胞质、中心体和均质模式被预测出良好的准确率，而 CS 和 FS 的预测准确率较低。人们发现时间复杂度非常低，因为使用了低级编程语言 `C`。正如前面提到的，该项目的主要特点是它完全用 `C` 实现，这降低了其复杂性并提高了其灵活性。本报告给出了一个非常系统的描述，呈现了整个项目的简要视图，人们可以根据需要修改项目中的算法。

## 11.9 Conclusion and future work for case study 2

在这里，我们旨在使用 `Macenko` 染色标准化图像通过一种类型的 DNN（`DenseNet`）预测乳腺癌的类别。使用 CNN 进行分类的主要问题是随着层数增加特征丢失。此外，即使是组织病理学图像的最小部分也包含大量信息。因此，对医学成像应用 CNN 变得困难，有时毫无意义。但是，在这里，通过使用 `DenseNet` 我们能够克服这个问题。此外，分块和增强不仅帮助我们增加了训练集的大小，这是如果我们想避免过拟合需要解决的重要问题，而且还让我们专注于图像中的每一个微小细节，因为我们在每个实例中只关注组织成像的非常小的一部分。

我们的结果优于该领域的所有最先进方法，给出了更高的准确率。未来我们旨在将这种方法应用于各种其他类型的医学图像。如果获得期望的结果，它可以改变我们处理医学报告的方式。

## References

`Glorot X.` 和 `Bengio Y.`, 2010, March. Understanding the difficulty of training deep feedforward neural networks. In Proceedings of the thirteenth international conference on artificial intelligence and statistics (pp. 249–256). [http://www.jmlr.org/proceedings/papers/v9/glorot10a/glorot10a.pdf?hc_location=ufi](http://www.jmlr.org/proceedings/papers/v9/glorot10a/glorot10a.pdf?hc_location%3Dufi) [→](#bodymatter-011.xhtml#xref_d69967e43335)

`Huang G.`, `Liu Z.`, `van der Maaten L.`, 和 `Weinberger K.Q`, Densely connected convolutional networks, 2017 IEEE Conference on Computer Vision and Pattern Recognition (CVPR), Honolulu, HI,USA. [https://ieeexplore.ieee.org/xpl/conhome/8097368/proceeding](https://ieeexplore.ieee.org/xpl/conhome/8097368/proceeding) 

`Gurcan M.N.`, `Boucheron L.`, `Can A.`, `Madabhushi A.`, `Rajpoot N`, 和 `Yener B.` Histopathological image analysis: a review. IEEE Reviews in Biomedical Engineering, (2009), 2, 147–171. doi: 10.1109/RBME.2009.2034865. \[NCBI\]. [→](#bodymatter-011.xhtml#xref_d69967e43250)

ICIAR 2015 Grand Challenge on Breast Cancer Histology Images. [https://rdm.inesctec.pt/dataset/nis-2017-003](https://rdm.inesctec.pt/dataset/nis-2017-003) [→](#bodymatter-011.xhtml#xref_d69967e43309)

`Loffe S.` 和 `Szegedy C`, 2015. Batch normalization: accelerating deep network training by reducing internal covariate shift. arXiv preprint arXiv:1502.03167. \[arXiv\].

`Macenko M.` 等, A method for normalizing histology slides for quantitative analysis. 2009 IEEE International Symposium on Biomedical Imaging: From Nano to Macro, Boston, MA, 2009, pp. 1107–1110. doi: 10.1109/ISBI.2009.5193250 URL: [http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5193250&isnumber=5192959](http://ieeexplore.ieee.org/stamp/stamp.jsp?tp%3D%26arnumber%3D5193250%26isnumber%3D5192959) 

`Srivastava N.`, `Hinton G.`, `Krizhevsky A.`, `Sutskever I.`, 和 `Salakhutdinov R.` Dropout: a simple way to prevent neural networks from overfitting. The Journal of Machine Learning Research, (2014), 15(1), 1929–1958. [http://www.jmlr.org/papers/volume15/srivastava14a/srivastava14a.pdf](http://www.jmlr.org/papers/volume15/srivastava14a/srivastava14a.pdf) 

URL:[https://medium.com/@RaghavPrabhu/understanding-of-convolutional-neural-network-cnn-deep-learning-99760835f148](https://medium.com/@RaghavPrabhu/understanding-of-convolutional-neural-network-cnn-deep-learning-99760835f148),Date of Access:6th October 2019 

URL:[https://www.analyticsvidhya.com/blog/2018/03/introduction-k-neighbours-algorithm-clustering/](https://www.analyticsvidhya.com/blog/2018/03/introduction-k-neighbours-algorithm-clustering/), Date of Access: 1st October 2019 

URL:[https://medium.com/machine-learning-101/chapter-2-svm-support-vector-machine-theory-f0812effc72](https://medium.com/machine-learning-101/chapter-2-svm-support-vector-machine-theory-f0812effc72), Date of Access: 3rd October 2019 

# 12 Impact of sentiment analysis tools to improve patients’ life in critical diseases

Dhaval Bhoi U & P U. Patel Department of Computer Engineering, Chandubhai S. Patel Institute of Technology, Charotar University of Science and Technology, Gujarat, India Amit Thakkar Smt. Kundanben Dinsha Patel Department of Information Technology, Chandubhai S. Patel Institute of Technology, Charotar University of Science and Technology, Gujarat, India

### Abstract

