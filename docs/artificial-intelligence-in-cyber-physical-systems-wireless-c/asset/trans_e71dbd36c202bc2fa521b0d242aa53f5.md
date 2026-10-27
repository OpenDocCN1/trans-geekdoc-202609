

![](img/56cfba5af06305175d6488aec4d55ab0_37_0.png)

图 1.3 基于 NLP 的分析流程图 [17]。

### 1.3.1 基于文本的情绪检测

该算法使用 NLP 实现，NLP 是机器学习中广泛使用的应用之一（见图 1.3）。

该过程的步骤已在参考 [14] 的流程图中描述。用于训练该算法的数据集来自 Kaggle，其中有 30,000 行用于训练，10,000 行用于测试。用于测试的数据集取自 Emo Bank，包含 10,000 条标注了效价、唤醒度和优势度的句子。在使用第一个数据集训练了三种算法（即逻辑回归、多项式朴素贝叶斯和支持向量机）之后，将它们用于第二个数据集，以查找其中文本的情绪。

这部分使用的算法参考了 [6,15]。

### 1.3.2 基于特征提取的情绪检测

该算法参考了 [6,8]，其中我们使用了委员会神经网络，这些网络进一步使用了反向传播方法（见图 1.4 和图 1.5）。

![](img/56cfba5af06305175d6488aec4d55ab0_38_0.png)

图 1.4 基于 CNN 的情绪检测流程图 [8] 和 [9]。

![](img/56cfba5af06305175d6488aec4d55ab0_38_1.png)

图 1.5 神经网络 NN [6]。

在该算法中，我们使用了特征提取 [6] 和 CNN 的委员会神经网络变体 [8]。我们采用了 CNN 委员会，即广义 CNN 和专门化 CNN。所使用的数据集是 Cohn-Kanade 数据库 [16]。面部表情图像来自 Cohn-Kanade 数据库 [14]。该数据库包含 97 名年龄在 18 至 30 岁之间的受试者的面部照片。其中 65% 的受试者为女性，15% 的受试者为非裔美国人，3% 为拉丁裔或亚裔。CNN 首先基于实值参数和二值参数进行训练。在测试时，图像首先被输入广义 CNN 委员会，根据参数的归一化值 [8] 判断是否为无法分类或模糊分类；随后，根据决定因素将其输入专门化 CNN 委员会，因此，大多数 CNN 检测到的情绪即为最终情绪。

### 1.3.3 媒体推荐算法

该推荐算法名为 Moodyst 算法。在获取情绪后，我们会对情绪进行编码和标记，例如“快乐”为 1001，“悲伤”为 1002。数据库中提供的媒体存储在不同的表中，表名与相应的情绪表相匹配。在将情绪与表映射后，将在所选表的主键不同值范围内生成一个随机整数。在此基础上，将显示一个随机媒体，其主键将与生成的随机整数匹配。该系统还能够将用户引导至 YouTube、Spotify、Indian Express、Kindle、Audible 等应用程序，在网络连接存在的情况下，用户可以重定向到这些应用。

- Moodyst 算法
- Moodyst（字符串情绪）标记情绪
- 将标签与数据库中的表名匹配
- 在主键值范围内生成随机整数
- 媒体与随机整数的映射
- 播放匹配的媒体

### 1.3.4 结果

该系统已在 Android 设备上运行，以下文本分类算法和基于特征提取的（使用委员会 CNN 的）情绪检测算法的准确率如表 1.1 所示。

下图显示了在第二个数据集中检测到的情绪频率（图 1.6–1.9）。

表 1.1 准确率比较

| 训练算法 | 准确率 |
|---|---|
| 逻辑回归 | 0.7125 |
| 多项式朴素贝叶斯 | 0.7183 |
| SVM | 0.7829 |

```
nb = MultinomialNB()
nb.fit(X_train_count, y_train)
y_pred = nb.predict(X_val_count)
print('naive bayes count vectors accuracy %s' % accuracy_score(y_pred, y_val))
```

naive bayes count vectors accuracy 0.7183828610919143

```
[63] lsvm = SGDClassifier(alpha=0.001, random_state=5, max_iter=65, tol=None)
lsvm.fit(X_train_count, y_train)
y_pred = lsvm.predict(X_val_count)
print('lsvm using count vectors accuracy %s' % accuracy_score(y_pred, y_val))
```

lsvm using count vectors accuracy 0.7829993089149966

```
[64] logreg = LogisticRegression(C=1, max_iter=5000)
logreg.fit(X_train_count, y_train)
y_pred = logreg.predict(X_val_count)
print('log reg count vectors accuracy %s' % accuracy_score(y_pred, y_val))
```

log reg count vectors accuracy 0.7125086385625432

图 1.6 不同向量的准确率。

![](img/56cfba5af06305175d6488aec4d55ab0_40_0.png)

图 1.7 SVM 检测到的情绪。

### 朴素贝叶斯检测到的情绪

![](img/56cfba5af06305175d6488aec4d55ab0_41_0.png)

图 1.8 朴素贝叶斯检测到的情绪。

### 逻辑回归检测到的情绪

![](img/56cfba5af06305175d6488aec4d55ab0_41_1.png)

图 1.9 逻辑回归检测到的情绪。

因此，本系统以基于 Android 的应用程序形式实现。该系统已在多台联网的 Android 设备上成功运行，并支持多种 Android 版本。用户界面的设备架构使用 Adobe Illustrator 设计。框架通过 Android 应用工具包（ADT）开发为 Android 应用。下面附上了运行 Android 6.0.1 版本的三星 F41 型号智能手机的几张设备截图。

## 参考文献

- [1] Wang, S, Q Ji, “视频情感内容分析：最新方法综述”，*IEEE 情感计算汇刊*，6，410–430，2015年10月至12月。
- [2] Liu, D, L Lu, H J Zhang, “基于声学音乐数据的自动情绪检测1”，*IEEE*，8712006，2005年12月19日。
- [3] Erion C, Riccardo Coppola Eleonora G, Marco M, Maurizio M, “基于情绪的车载音乐推荐”，*国际工业网络与智能系统会议*，154–163，2016年。
- [4] Vijayakumar, C, V Adaickalam, “使用智能情感分析的智能减压音乐播放器”，*国际工业电子与电气工程杂志*，ISSN：2347-6982 4, 6, 2016年。
- [5] Iyer, A V, V Pasad, S R Sankhe, K Prajapati, “基于情绪的情绪增强音乐推荐”，*IEEE*，17504486，2018年1月5日。
- [6] Kobayashi, H, F Hara, “基于神经网络的基本面部表情识别”，*国际神经网络联合会议*，460–466，1991年。
- [7] Pratama, B Y, R Sarno, “基于朴素贝叶斯、KNN 和 SVM 的 Twitter 文本个性分类”，*2015年数据与软件工程国际会议（ICoDSE）*，170–174，2015年，印度尼西亚日惹：IEEE。DOI：10.1109/ICODSE.2015.7436992。
- [8] Kulkarni, S S, N P Reddy, S I Hariharan, “基于委员会神经网络的面部表情（情绪）识别”，*生物医学工程在线*，16，2009年。
- [9] Kobayashi, H, F Hara, “基于神经网络的混合面部表情识别”，*国际机器人与人类通信研讨会论文集*，387–391，1992年。
- [10] Mariappan, M B, M Suk, B Prabhakaran, “FaceFetch：基于面部表情识别的用户驱动多媒体内容推荐系统”，*2012年IEEE国际多媒体研讨会*，1，84–87。
- [11] Tripathi, A, T S Ashwin, R M R Guddeti, “WmoWare：使用情感视频序列的个性化视频推荐上下文感知框架”，*IEEE Access*，7，51185–51200，2019年。
- [12] Zhao, J, G Kearney, “基于模糊输入的反向传播神经网络面部情绪分类”，*神经信息处理会议论文集*，1，454–457，1996年。
- [13] Kim, S-M, E Hovy, 确定意见的情感。*COLING 会议论文集*，2004年。
- [14] Fasel, B, J Luettin, “自动面部分析综述”，*模式识别*，36，259–275，2003年。

