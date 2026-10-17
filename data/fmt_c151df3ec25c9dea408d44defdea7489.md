
此处呈现的结果仅来自 IBU 生物特征数据集中的 40 人的小数据集。每个人有 20 张不同的面部图像。对于人脸识别，我们在 `DroidAuth` 应用程序上执行了 `PCA`。我们计算的准确率如公式 30.1 所描述所示。手机使用的是 Samsung Galaxy S。此处实现的总体准确率为 92.64%。我们确定了测试图像与训练图像之间的欧几里得距离。距离阈值为 10e+16。在表 30.1 中，结果显示男性识别准确率为 100%。问题出现在女性身上，尤其是染发者。我们可以看到，深色头发的女性比浅色/金发女性获得更高的准确率。

Accuracy = Matched Faces / Total Number of Face Images in Database × 100%   (30.1)

准确率 = 匹配人脸数 / 数据库中人脸图像总数 × 100%   (30.1)

图 30.6 显示了根据表 30.2 至 30.4 绘制的结果的图形表示。

**表 30.1** 生物识别系统应用

| 领域 | 应用 |
|---|---|
| 信息安全 | 访问安全（操作系统、数据库） |
| 访问管理 | 安全访问认证（受限访问） |
| 生物识别 | 个人识别（国家身份证） |
| 执法 | 视频监控 |
| 个人安全 | 家用视频监控系统 |
| 娱乐 – 休闲 | 视频摄像机应用 |

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_934_0.png)

图 30.6 结果的图形表示。

### 表 30.2 身份验证的形式

| 因素 | 示例 |
|---|---|
| 我们知道的 | 密码、PIN、密码短语 |
| 我们拥有的 | 令牌、CAC 卡、RSA |
| 我们本身是 | 生物识别：指纹、虹膜、语音模式 |

### 表 30.3 不同组的 结果

| 描述 | 匹配 | 样本 | 精度 |
|---|---|---|---|
| 总样本 | 36 | 40 | 90.00% |
| 仅男性 | 9 | 9 | 100% |
| 浅发女性 | 8 | 9 | 88.88% |
| 深发女性 | 11 | 12 | 91.66% |

### 表 30.4 不同分类器的分类性能

| 分类器 | 精度 (%) | F 测度 | ROC 面积 | Kappa |
|---|---|---|---|---|
| ANN (MLP) | 92.6923 | 0.923 | 0.983 | 0.925 |
| k-NN | 95 | 0.95 | 0.974 | 0.9487 |
| SVM | 92.9487 | 0.929 | 0.995 | 0.9276 |
| Random Forest | 96.7949 | 0.968 | 0.999 | 0.9671 |
| C4.5 | 84.2308 | 0.841 | 0.928 | 0.8382 |
| Random Tree | 86.2821 | 0.862 | 0.93 | 0.8592 |
| REPTree | 73.8462 | 0.738 | 0.932 | 0.7316 |
| LAD Tree | 73.8462 | 0.734 | 0.982 | 0.7316 |
| NB | 90.641 | 0.899 | 0.991 | 0.9039 |
| Rotation Forest | 94.8718 | 0.949 | 0.997 | 0.9474 |
| CART | 83.0769 | 0.831 | 0.93 | 0.8263 |

本文所示结果表明 `Random Forest` 和 `SVM` 具有最高的识别率。这是通过提取特征向量实现的。使用 `Weka` 对 `ANN`、`k-NN`、`SVM`、`Random Forest`、`C4.5`、`LAD Tree` 等进行了测试。通过这些我们可以看到它们各自的不同性能。最高的结果由 `Random Forest` 呈现。`Random Forest` 的性能为 96.79%。在测试时，构建了 30 棵树。交叉验证折数 `k = 10`。`Random Forest` 的 F 测度为 96%，即 0.968。`Random Forest` 的 ROC 为 0.999，高于 `SVM`、`ANN`、`CART`。`ANN` 的性能为 92.69%，即 0.92。`ANN (MLP)` 的 F 测度为 0.923。`ANN (MLP)` 的 ROC 为 0.983，高于 `k-NN` 的 0.974。`k-NN` 的精度为 95%，高于 `SVM`、`C4.5`、`Random Tree`、`REPTree`、`NB`、`LAD Tree`，且低于 `Random Forest`。`k-NN` 的 F 测度为 0.983。`k-NN` 的 ROC 为 0.983。

对人脸图像直方图值在 `SVM` 线性核上进行的处理提供了高精度。对于训练，选择了 `SVM` 和适当的分类器 `C`。`C` 的最佳值使结果表现更好为 `C = 100`。我们可以看到 `Random Forest` 树的表现几乎与 `SVM` 线性核一样好。除上述所有内容外，将此类模型与实时人脸识别结合使用，专家系统可通过增加多样的参数数量而以更高的准确率得到改进。

## 30.8 结论

今天未解决的与变化相关的问题是：光照、头部旋转和面部表情。Goldstein、Harmon 和 Lesk 在贝尔实验室对耳大小和眼距等面部特征的测量研究已完成 (Goldstein et al., 1971)。1973 年，Fischer 和 Elschlanger 开始计算距离并自动测量可比较的特征 (Fischler et al., 1973, Marques, 2010)。Eigenface 在图像处理中由 Kirby 和 Sirovich 引入。他们的技术被称为主成分分析 (`PCA`)。主成分分析多年来一直占主导地位。识别问题吸引了新的研究水平，特别是在未来尝试开发将涉及的识别系统。 然而，我们仍然完全没有理解人类大脑的工作方式以及进行何种识别性能；因此，在开发具有更高水平准确性的系统方面还有很多工作要做。

## 30.9 摘要

本章讨论了与移动安全相关的人脸识别和检测方法。本章讨论了机器学习技术。该工作讨论了信息安全、访问管理和个人安全。在移动系统上实施人脸识别认证模型已显示出 96% 的准确率成就。已进行了大量研究。在该主题上仍有足够的空间继续开展研究工作。随着手机的消费，用户认证的老式方法永远改变了。这种变化带来了重要的安全问题。传统的 PIN 技术将逐渐被放弃并最终被取代。增强所需的智能认证水平将不是通过或失败的问题，而是确认用户身份的问题。未来研究的一个重要问题在于视频和语音识别在手机安全中作为认证的一部分。人工智能，无论是机器学习还是模式识别，都将尝试在自我学习人类识别系统的生物识别系统中提供准确的结果。算法及其应用将在数字安全中发挥主要作用。今天未解决的与变化相关的问题包括光照、头部旋转和面部表情。识别问题吸引了高水平的兴趣和研究，特别是在未来该学科的学生寻求开发能够检测情绪的识别系统时。然而，我们仍然不完全理解人类大脑如何运作或需要何种识别技术来解锁其众多奥秘。因此，在开发不仅具有更高准确性的系统而且能够深入到其人类受试者皮肤之下的系统方面还有很多工作要做。毫无疑问，人类识别领域仍有许多问题有待解决。但未来将使我们更接近发现一台计算机，它可以在识别人类时具有、显示和检测情绪。挑战已抛给未来的研究人员。他们必须迎接挑战并继续努力实现一个能够从特征向量构建全面图像的模型。

## 参考文献

Alhussain, T., Drew, S., & Alfarraj, O. (2010). 移动政府安全的生物识别认证。于 Intelligent Computing and Intelligent Systems (ICIS), 2010 IEEE 国际会议发表, IEEE (第 2 卷, 页 114–118)。

Arandjelović, O., & Cipolla, R. (2009). 基于视频的人脸识别的姿势线性光照流形模型。Computer Vision and Image Understanding, 113(1), 113–125。

Arteaga-Falconi, J. S., Al Osman, H., & El Saddik, A. (2016). 移动设备的 ECG 认证。IEEE Transactions on Instrumentation and Measurement, 65(3), 591–600。

Biel, L., Pettersson, O., Philipson, L., & Wide, P. (2001). ECG 分析：人类识别的新方法。IEEE Transactions on Instrumentation and Measurement, 50(3), 808–812。

Bledsoe, W. W. (1966). 人脸识别中的模型方法。Panoramic Research Inc., Palo Alto, CA, Rep. PR1, 15, 47。

Breiman, L., Friedman, J., Stone, C. J., & Olshen, R. A. (1984). 分类与回归树。Boca Raton, FL: CRC Press。

Burnette, E. (2015). 你好，Android：介绍 Google 的移动开发平台。Dallas, TX: Pragmatic Bookshelf。

Campisi, P., & La Rocca, D. (2014). 用于自动生物识别用户识别的脑电波。IEEE Transactions on Information Forensics and Security, 9(5), 782–800。

Chen, Y., Atnafu, A. D., Schlatlner, I., Weldtsadik, W. T., Roh, M.-C., Kim, H. J., ... Fazli, S. (2016). 基于 RSVP 刺激和干电极的高安全性 EEG 登录系统。IEEE Transactions on Information Forensics and Security, 11(12), 2635–2647。

Choi, H.-S., Lee, B., & Yoon, S. (2016). 使用移动传感器获取的噪声心电图进行生物识别认证。IEEE Access, 4, 1266–1273。

Choi, J. Y., Ro, Y. M., & Plataniotis, K. N. (2011a). 基于彩色图像的人脸识别中预处理不匹配效应的比较研究。Pattern Recognition, 44(2), 412–430。

Choi, K., Toh, K.-A., & Byun, H. (2011b). 面部识别应用的移动设备实时训练。Pattern Recognition, 44(2), 386–400。

Clarke, N. L., & Furnell, S. (2007). 移动设备的先进用户认证。Computers & Security, 26(2), 109–119。

Da Silva, H. P., Fred, A., Lourenço, A., & Jain, A. K. (2013). 用于用户认证的指尖 ECG 信号：可用性和性能。于 Biometrics: Theory, Applications and Systems (BTAS), 2013 IEEE 第六届国际会议发表, IEEE (页 1–8)。

De Carrera, P. F., & Marques, I. (2010). 人脸识别算法。计算机科学硕士论文, Universidad Euskal Herriko。

Derawi, M. O., Nickel, C., Bours, P., & Busch, C. (2010). 使用生物识别步态识别的移动电话无干扰用户认证。于 Intelligent Information Hiding and Multimedia Signal Processing (IIH-MSP), 2010 第六届国际会议发表, IEEE (页 306–311)。

Fischler, M. A., & Elschlager, R. A. (1973). 图像结构的表示与匹配。IEEE Transactions on Computers, 100(1), 67–92。

Fraschini, M., Hillebrand, A., Demuru, M., Didaci, L., & Marcialis, G. L. (2015). 基于静息态脑网络特征向量中心性的 EEG 生物识别系统。IEEE Signal Processing Letters, 22(6), 666–670。

Goldstein, A. J., Harmon, L. D., & Lesk, A. B. (1971). 人脸识别。Proceedings of the IEEE, 59(5), 748–760。

Hall, M., Holmes, G., & Frank, E. (1999). 从模型树生成规则集。载于 Proceedings of the Twelfth Australian Joint Conference on Artificial Intelligence (页 1–12), Sydney, Australia。Berlin, Germany: Springer-Verlag。

Han, J., Pei, J., & Kamber, M. (2011). 数据挖掘：概念与技术。Burlington, MA: Elsevier。

Hull, J. J., Liu, X., Erol, B., Graham, J., & Moraleda, J. (2010). 移动图像识别：架构与权衡。于 Proceedings of the Eleventh Workshop on Mobile Computing Systems & Applications 会议发表, ACM (页 84–88)。

Islam, M. S., Alajlan, N., Bazi, Y., & Hichri, H. S. (2012). HBS：一种基于心跳形态的新型生物识别特征。IEEE Transactions on Information Technology in Biomedicine, 16(3), 445–453。

Jain, A., Bolle, R., & Pankanti, S. (2006). 生物识别：网络社会中的个人识别 (第 479 卷)。New York: Springer Science & Business Media。

Jain, A. K., & Li, S. Z. (2011). 人脸识别手册。New York: Springer。

Jain, A. K., Nandakumar, K., & Ross, A. (2016). 生物识别研究的 50 年：成就、挑战与机遇。Pattern Recognition Letters, 79, 80–105。

Jain, A., Ross, A. A., & Nandakumar, K. (2011). 生物识别导论。New York: Springer Science & Business Media。

Kang, S. J., Lee, S. Y., Cho, H. I., & Park, H. (2016). 基于移动和可穿戴设备信号分析的心电图认证系统设计。IEEE Signal Processing Letters, 23(6), 805–808.

Klonovs, J., Petersen, C. K., Olesen, H., & Hammershoj, A. (2013). 移动中的身份证明：基于移动脑电图（EEG）的生物识别认证系统的开发。IEEE Vehicular Technology Magazine, 8(1), 81–89.

Kremić, E. (2011). 人脸识别：手机的高级安全模型。硕士论文，国际伯奇大学，萨拉热窝，波斯尼亚和黑塞哥维那。

Kremić, E., & Subasi, A. (2011). 手机认证中人脸安全的实现。International Arab Journal of Information Technology, 414–419.

Kremić, E., & Subasi, A. (2016). 随机森林与SVM在人脸识别中的性能。International Arab Journal of Information Technology, 13(2), 287–293.

Kremić, E., Subasi, A., & Hajdarevic, K. (2012). 使用PCA的客户端-服务器移动应用人脸识别实现。发表于IEEE第34届信息技术接口国际会议（ITI 2012）论文集，IEEE（第435–440页）。

Kresimir, D., Grgic, M., & Marian, S. B. (2008). 人脸识别的最新进展。克罗地亚：I-Tech.

Kumar, S., Singh, P., & Kumar, V. (2010). 基于移动的人脸检测/识别架构。International Journal on Computer Sciences and Engineering, 2(3), 889–894.

Kumari, P., & Vaish, A. (2015). 使用脑电传感器进行个体识别的固有模态函数信息论度量。IEEE Sensors Journal, 15(9), 4950–4960.

Kurkowsky, S., Carpenter, T., & MacDonald, C. (2010). 面向手机的简易虹膜识别实验。发表于2010年第七届信息技术：新一代国际会议（ITNG），IEEE（第1293–1294页）。

Kwapisz, J. R., Weiss, G. M., & Moore, S. A. (2010). 基于手机的生物识别。发表于2010年第四届IEEE生物识别：理论与应用系统国际会议（BTAS），IEEE（第1–7页）。

Marques, I. (2010). 人脸识别算法。
