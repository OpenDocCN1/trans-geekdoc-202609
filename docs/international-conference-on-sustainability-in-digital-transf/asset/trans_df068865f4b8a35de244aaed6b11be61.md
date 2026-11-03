
## RepTree
`RepTree`：一种快速决策树学习算法是降低误差剪枝（`REP Tree Classifier`）[[15](#ch30.xhtml#ref30_15)]，它通过最小化来自方差的误差并计算信息增益与熵来工作。

多棵树在不同迭代中使用回归树逻辑生成，该逻辑由 `REP Tree` 应用。随后从已重新生长的树中选择最佳树。考虑到方差和信息增益，该方法构建回归/决策树。该方法还对树进行反向拟合的降低误差剪枝。

### D. 结果评估
按照上述程序，使用以下标准评估结果：`TP`、`TN`、`FP` 和 `FN`。

`TP`（真正例）是正确分类的异常的总计数。

`TP`（真负例）是分类正确时的正常记录的总计数。

`TP`（假正例）是错误标记的异常的总计数。

`TP`（假负例）表示被错误分类的典型记录的数量。准确率是相对于数据集中行总数而言正确标记记录的比例。

(3)

`Accuracy = (TP+TN) / (TP+TN+FP+FN)`

(4)

`False Positive Rate (FPR) = FP / FP+TN`

(5)

`False Negative Rate (FNR) = FN / FN+TP`

“`Precision`”一词指的是分类正确的异常记录的百分比。然而，`Recall` 衡量的是相对于已识别和误识别异常的总数的正确识别的异常数量。

(6)

`Precision = TP / TP + FP`

(7)

`Recall = TP / TP + FN`

## 结果与实现
[图 30.1](#ch30.xhtml#fig30_1) 显示了网络配置文件数据集的属性，即协议、源字节、目标字节、root-shell、hostlogin、guestlogin、服务器错误、主机速率和端口速率。

![图 30.1 网络配置文件数据集属性](images/fig30_1_C.jpg)

[图 30.1 网络配置文件数据集属性](#ch30.xhtml#R_fig30_1)

[图 30.2](#ch30.xhtml#fig30_2) 显示了数据归一化，其中所有值都按比例对齐。

![图 30.2 应用归一化后属性的归一化值](images/fig30_2_C.jpg)

[图 30.2 应用归一化后属性的归一化值](#ch30.xhtml#R_fig30_2)

在 [图 30.3](#ch30.xhtml#fig30_3) 中，为所有属性生成特征值，其中每个属性的第一列表示重复项集，第二列表示唯一项集。例如，对于表示为 `a0` 的协议，我们有 46 个重复项集和 54 个唯一项集。

![图 30.3 特征选择值](images/fig30_3_C.jpg)

[图 30.3 特征选择值](#ch30.xhtml#R_fig30_3)

[图 30.4](#ch30.xhtml#fig30_4) 显示了分类器输出，线性方程形式为 `y = mx + c`，其中 `m` 是斜率，`c` 是相关系数。

![图 30.4 对数据集应用线性回归](images/fig30_4_C.jpg)

[图 30.4 对数据集应用线性回归](#ch30.xhtml#R_fig30_4)

这里我们的方程是 `src_port_rate = -0.0003 * destbytes + 0.5788`

在 [图 30.5](#ch30.xhtml#fig30_5) 中，可以看出信息增益和方差是基于树的大小计算的。这里，第一节点的信息增益和方差分别为 6 和 0.16。同理，第二节点的信息增益和方差分别为 4 和 0.3。

![图 30.5 对数据集应用 REPTree](images/fig30_5_C.jpg)

[图 30.5 对数据集应用 REPTree](#ch30.xhtml#R_fig30_5)

## 结果与分析
[表 30.1](#ch30.xhtml#tab30_1) 显示了基于评估指标的线性回归分类器的详细结果。

[表 30.1 线性回归的详细结果。](#ch30.xhtml#R_tab30_1)

| 类别 || TPR || FPR || 精确率 || 召回率 || F1-Score || ROC |
| --- | --- | --- | --- | --- | --- | --- |
| `Anomaly` || 0.89 || 0.45 || 0.95 || 0.94 || 0.96 || 0.76 |
| --- | --- | --- | --- | --- | --- | --- |
| `Normal` || 0.91 || 0.03 || 0.93 || 0.97 || 0.95 || 0.8 |

[表 30.2](#ch30.xhtml#tab30_2) 显示了基于评估指标的 `REPTree` 分类器的详细结果。

[表 30.2 REPTree 的详细结果。](#ch30.xhtml#R_tab30_2)

| 类别 || TPR || FPR || 精确率 || 召回率 || F1-Score || ROC |
| --- | --- | --- | --- | --- | --- | --- |
| `Anomaly` || 0.93 || 0.66 || 0.98 || 0.96 || 0.96 || 0.71 |
| --- | --- | --- | --- | --- | --- | --- |
| `Normal` || 0.94 || 0.56 || 0.96 || 0.95 || 0.95 || 0.67 |

[表 30.3](#ch30.xhtml#tab30_3) 显示了两种分类器的准确率比较。可以看出，`REPTree` 在网络异常检测中达到了 97% 的更高准确率。

[表 30.3 准确率比较。](#ch30.xhtml#R_tab30_3)

| 分类器 || 准确率 (%) |
| --- | --- |
| `Linear regression` || 94 |
| --- | --- |
| `REPTree` || 97 |

![图 30.6 线性回归性能评估](images/fig30_6_C.jpg)

图 30.6 线性回归性能评估

![图 30.7 REPTree 性能评估](images/fig30_7_C.jpg)

图 30.7 REPTree 性能评估

![图 30.8 准确率比较](images/fig30_8_C.jpg)

图 30.8 准确率比较

## 结论与未来工作
本研究介绍了如何将机器学习应用于网络流量异常检测。我们在网络配置文件数据集上使用了线性回归和 `REPTree` 这两种常用技术。为了进一步提高性能，我们还采用了特征选择技术。我们的分析表明，研究中使用的异常检测算法在准确率、召回率、F1 分数和精确率方面都达到了很高的水平。由于特征选择，算法速度也得到了大幅提升。本研究表明，`REPTree` 可以以 97% 的准确率有效识别网络异常。

未来的研究应侧重于创建能够响应网络威胁而变化的模型。研究人员可以研究深度学习技术在网络异常检测中的应用。

## 参考文献
1. [Zoppi, T., Ceccarelli, A., and Bondavalli, A.](#ch30.xhtml#R_ref30_1) (2020)。Into the unknown: unsupervised machine learning algorithms for anomaly-based intrusion detection. 在第 50 届 IEEE-IFIP 可靠系统与网络国际会议增刊卷（DSN-S）中，瓦伦西亚，西班牙，第 81-81 页，doi：[10.1109/DSN-S50200.2020.00044.](http://dx.doi.org/10.1109/DSN-S50200.2020.00044)

2. [Dwivedi, R. K., Rai, A. K., and Kumar, R.](#ch30.xhtml#R_ref30_2) (2020)。A study on machine learning based anomaly detection approaches in wireless sensor network. 在第 10 届云计算、数据科学与工程国际会议（Confluence）中，诺伊达，印度，第 194-199 页，doi：[10.1109/Confluence47617.2020.9058311.](http://dx.doi.org/10.1109/Confluence47617.2020.9058311)

3. [Singh, R., Srivastava, N., and Kumar, A.](#ch30.xhtml#R_ref30_3) (2021)。Machine learning techniques for anomaly detection in network traffic. 在 2021 年第六届图像信息处理国际会议（ICIIP）中，喜马偕尔，印度，第 261-266 页，doi：[10.1109/ICIIP53038.2021.9702647.](http://dx.doi.org/10.1109/ICIIP53038.2021.9702647)

4. [Limthong, K., and Tawsook, T.](#ch30.xhtml#R_ref30_4) (2012)。Network traffic anomaly detection using machine learning approaches. 在 IEEE 网络运营与管理研讨会中，毛伊岛，HI，美国，第 542-545 页，doi：[10.1109/NOMS.2012.6211951.](http://dx.doi.org/10.1109/NOMS.2012.6211951)

5. [Amangele, P., Reed, M. J., Al-Naday, M., Thomos, N., and Nowak, M.](#ch30.xhtml#R_ref30_5) (2019)。Hierarchical machine learning for IoT anomaly detection in SDN. 在信息技术国际会议（InfoTech）中，瓦尔纳，保加利亚，第 1-4 页，doi：[10.1109/InfoTech.2019.8860878.](http://dx.doi.org/10.1109/InfoTech.2019.8860878)
