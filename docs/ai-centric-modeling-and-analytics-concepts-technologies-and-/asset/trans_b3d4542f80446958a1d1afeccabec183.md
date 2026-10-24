

## 5.3.4.2 变换

离散小波变换（DWT）是一种信号处理技术，已被广泛应用于各种领域，包括图像和信号处理、模式识别和机器学习。

近年来，DWT 已被应用于植物病害检测与分类领域。使用 DWT 进行植物病害检测的基本思想是植物纹理和颜色中变化模式的显现，这些变化模式可以通过小波系数进行捕获和分析。

离散小波变换将图像分解为不同的频带，每个频带的小波系数表示该特定频率尺度下的图像信息。通过分析小波系数，可以识别与特定植物病害相关的纹理和颜色模式。

要使用 DWT 进行植物病害检测，第一步是获取植物的高分辨率图像。这些图像可以通过各种成像技术获取，例如数码相机或高光谱成像。

获取图像后，对其进行预处理，然后即可使用模型进行预测。使用小波基函数将图像分解为不同的频带，并计算每个频带的小波系数，如图 5.3 所示。

## 5.3.4.3 分类器

使用卷积神经网络（CNN）进行植物病害预测是一种很有前途的方法，可以准确识别和分类植物病害。卷积神经网络是一种深度学习算法，特别擅长处理和分析图像，因此非常适合基于视觉症状识别植物病害，如图 5.4 所示。

要使用 CNN 构建植物病害预测模型，需要包含健康植物和患病植物图像的数据集。这些图像被分为训练集、验证集和测试集。

- CNN 使用反向传播在训练集上进行训练，这涉及调整网络的权重以最小化真实标签与预期标签之间的差异。验证集用于评估模型在训练期间的性能，而测试集用于评估模型的整体准确率。
- CNN 模型通常由多个卷积层组成，通过从输入图像中提取特征将图像分类为多个病害组，并包含多个全连接层。数据增强技术（如旋转、翻转和裁剪）可用于增强模型并增加训练集的大小。

总体而言，使用 CNN 进行植物病害预测的结果令人鼓舞，并有望显著提高农业中病害识别与防控的有效性和精确性，如图 5.5 所示。

![](img/66ecdb8eb8654ae1c99705e55a45a836_114_0.png)

**图 5.3** DWT 变换后的图像。

![](img/66ecdb8eb8654ae1c99705e55a45a836_114_1.png)

**图 5.4** CNN 算法。

*来源：* Khang (2021)

```
training started...Wait for 200 seconds...
training started...
Elapsed time is 2.033151 seconds.
Elapsed time is 2.239313 seconds.
...training finished.
testing started....
test error is
Elapsed time is 1.085832 seconds.
CNN Accuracy = 99.0909
CNN Precision = 0.9913
CNN Sensitivity = 0.99091
CNN Specificity = 0.99773
```

```
confmatrix =
```

| 22 | 1 | 0 | 0 | 0 |
| 0 | 21 | 0 | 0 | 0 |
| 0 | 0 | 22 | 0 | 0 |
| 0 | 0 | 0 | 22 | 0 |
| 0 | 0 | 0 | 0 | 22 |

图 5.5 CNN 精度结果。

## 5.3.5 灌溉系统

传统农业是全球发展的基石。尽管如此，由于人口的指数增长和消费的不断增加，农民需要水来灌溉土地。

由于这种资源的稀缺性，农民需要一种能够改变他们耕作方式的解决方案。为了跟上并满足需求，新技术得以实施，催生了“农业 4.0”的概念。

本研究中提出的灌溉方法巧妙、适应性强，且成本和使用费用低。这种智慧农业策略基于机器学习算法。为了实现这一目标，我们使用了一组传感器（土壤、湿度、温度和降雨），并将其放置在有利于植物更好地生长的环境中数月。

然后，我们使用 Node-RED 平台和 MongoDB，根据这些传感器的采集映射来收集数据。基于我们的数据，我们使用了多种模型，包括 k 近邻（KNN）、逻辑回归、神经网络、支持向量机和朴素贝叶斯（Khang 等，2022b）。

与其他模型相比，结果表明 KNN 表现更好，识别率达 98.3%，RMSE 为 0.12。

最后，为了更好地可视化和监控我们周围的环境，我们提供了一个 Web 应用程序，将传感器产生的各种数据与我们的模型预测相结合。

![](img/66ecdb8eb8654ae1c99705e55a45a836_117_0.png)

**图 5.6** 灌溉模型。

## 5.5 建议

未来的研究可以在整个训练集上采用集成机器学习，将结果与基于特征选择的研究进行对比（Rana 等，2021）。

此外，可以进一步使用样本外数据采样方法来评估预测模型的性能，并与本章提出的样本内方法进行比较。

## 参考文献

Bharath S., Yeshwanth S., Yashas B. L., Vidyaranya R. J., “Comparative analysis of machine learning algorithms in the study of crop and crop yield prediction,” IJERTCONV8IS14008, NCETESFT – 2020 (Volume 8 – Issue 14). www.academia.edu/download/64341632/comparative-analysis-of-machine-IJERTCONV8IS14008.pdf

Khang A., (2021). “Material4Studies,” Material of Computer Science, Artificial Intelligence, Data Science, IoT, Blockchain, Cloud, Metaverse, Cybersecurity for Studies. www.researchgate.net/publication/370156102_Material4Studies

Khang A., Gupta S. K., Rani S., Karras D. A., (Eds.). (2023a). Smart Cities: IoT Technologies, Big Data Solutions, Cloud Platforms, and Cybersecurity Techniques. CRC Press. https://doi.org/10.1201/9781003376064

Khanh H. H., Khang A., (2021). "The role of artificial intelligence in blockchain applications," Reinventing Manufacturing and Business Processes through Artificial Intelligence, 2(20-40) (CRC Press). https://doi.org/10.1201/9781003145011-2

Konstantinos P. F., (2018). "Deep learning models for plant disease detection and diagnosis," Computers and Electronics in Agriculture, 145, 311-318. www.sciencedirect.com/science/article/pii/S0168169917311742

Liu J., Wang X., (2021). "Plant diseases and pests detection based on deep learning: A review," Plant Methods, 17, 22. https://doi.org/10.1186/s13007-021-00722-9.

Majji V. A., Kumaravelan G., (2021). "A review of machine learning approaches in plant leaf disease detection and classification," Third International Conference on Intelligent Communication Technologies and Virtual Mobile Networks (ICICV). https://ieeexplore.ieee.org/abstract/document/9388488/

Meriç Ç., Selami B., (2022). "Smart irrigation systems using machine learning and control theory," The Digital Agricultural Revolution: Innovations and Challenges in Agriculture through Technology Disruptions, Chapter 3. https://doi.org/10.1002/9781119823469

Niketa G., Owaiz P., (2016). "Rice crop yield prediction using artificial neural networks," IEEE Technological Innovations in ICT for Agriculture and Rural Development (TIAR). https://doi.org/10.1109/TIAR.2016.7801222.

Ramesh K., Rudra K., (2021). "Crop yield prediction using machine learning algorithm," 5th International Conference on Intelligent Computing and Control Systems (ICICCS). https://doi.org/10.1109/ICICCS51141.2021.9432236.

Rana G., Khang A., Sharma R., Goel A. K., Dubey A. K., (Eds.). (2021). Reinventing Manufacturing and Business Processes through Artificial Intelligence. CRC Press. https://doi.org/10.1201/9781003145011

Rani S., Bhambri P., Kataria A., Khang A., (Dec 30, 2022). "Smart city ecosystem: Concept, sustainability, design principles and technologies," In AI-Centric Smart City Ecosystems: Technologies, Design and Implementation, Vol. 1, No. 20 (1st ed.). CRC Press. https://doi.org/10.1201/9781003252542-1

Saeed K., Lizhi W., (2019). "Crop yield prediction using deep neural networks," Original Research Article, Frontiers in Plant Science. www.frontiersin.org/articles/10.3389/fpls.2019.00621/full

Sandeep K., Arpit J., Anand Prakash S., Satyendr S., et al., "A comparative analysis of machine learning algorithms for detection of organic and nonorganic cotton diseases," Mathematical Problems in Engineering, 2021, Article ID 1790171. https://doi.org/10.1155/2021/1790171

Shruthi U., Nagaveni V., Raghavendra B. K., (2019). "A review on machine learning classification techniques for plant disease detection," 5th International Conference on Advanced Computing & Communication Systems (ICACCS). https://ieeexplore.ieee.org/abstract/document/8728415/

Tace Y., Tabaa M., Elfilali S., Leghris C., Bensag Hassna B., Renault E., (2022). "Smart irrigation system based on IoT and machine learning," Energy Reports, 8(Suppl. 9), 1025-036. www.sciencedirect.com/science/article/pii/S2352484722013543

Vallejo-Gómez D., Marisol O., Hincapié C., (2023). "Smart irrigation systems in agriculture: A systematic review," Special Issue Proposal Application, 13(2), 342. https://doi.org/10.3390/agronomy1302034225

Van Klompenburg T., Kassahun A., Catal C., (2020). "Crop yield prediction using machine learning: A systematic literature review," Computers and Electronics in Agriculture, 177, 105709. www.sciencedirect.com/science/article/pii/S0168169920302301

