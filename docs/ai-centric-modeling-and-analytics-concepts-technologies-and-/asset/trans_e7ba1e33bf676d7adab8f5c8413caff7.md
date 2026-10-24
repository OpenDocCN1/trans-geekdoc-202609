
## 课程 87

早上，老师要求学生打开书本，阅读农民和他儿子们的故事。学生们安静地阅读，而老师在教室里走动，帮助有问题的学生。

读完后，老师解释了文章的主要思想。她指出故事中的教训是关于共同工作和分担责任。学生们认真倾听，并在日记中记下笔记。

课程结束时，老师请几名学生分享他们学到的内容。有些人说这个故事让他们想起了在家帮忙，而其他人提到要有耐心和善良很重要。每个人都同意这堂课很有价值。

## 随机森林分类器

![](img/66ecdb8eb8654ae1c99705e55a45a836_257_0.png)

图 13.4 使用 RF 的分类算法。

有效地。即使缺少大量数据，准确率仍能保持。

随机森林由多个决策树组成，每棵树都无需快速处理即可完全发展。随机森林产生更准确的结果，并且如果算法中包含更多树，则不易过拟合，如代码块 13.2 所示。

总体估计是使用随机森林算法进行的，该算法还具有自动选择特征的好处。因此，必须解决以下列出的主要问题。

代码块 13.2. 算法 1：随机森林。

```
for i ← 1 to B do
Draw a bootstrap sample of size N from the training data;
while node size! = minimum node size do
randomly select a subset of m predictor variables from total p;
for j ← 1 to m do
if jth predictor optimizes splitting criterion then
split the internal node into two child nodes;
break;
end
end
end while
end
return the ensemble tree of all B sub-trees generated in the outer for loop;
Alt-text: Code block 13.2 displays the code of the random forest algorithm.
```

对于少数类，使用有放回技术创建自助采样，然后找到 k 个多数类样本，即最近邻样本。Spark 可用于并行完成此操作。

为每组样本生成一个随机森林分类器。每个分类器仅处理在同一节点上提供的训练数据集。然后使用该模型并发预测测试数据集。

最后，使用 Spark Driver 获取预测结果。随机森林算法的自助采样在代码块 13.3 中显示。

代码块 13.3. 算法 2：自助采样。

```
Dataset T parameters {δ, k}
Sample batch
**Bootstrap** (T, δ, K)
Minor ← broadcast (T.minor)
Dist ← T.major.map (l => dist (l, minor))
Candidate ← dist.filter (l => l.distance< δ)
Batch ← sample (candidate, K)
**Return** batch
Alt-text: Code block 1.3 depicts the bootstrap sampling with the replacement technique, and then finds the k major class samples, which are the nearest-neighbor samples.
```

随机森林系统中使用各种决策树。决策树由存在节点的决策、叶节点和根节点组成。需要多数投票来确定结果。在这种情况下，多数决策树的输出决定了雨林系统的最终输出。

### 13.4 结果与讨论

本节检查当前系统的性能，其中包括准确率 83.65%、敏感性 85.59%、特异性 87.65% 和精确率 87.65%。

所提出的系统采用了新颖的疾病预测方法，比当前系统更有效。此外，该预测程序的准确性也得到了提高。

混淆矩阵：混淆矩阵提供了属于不同类别的正确分类 TN 值示例，以及完美分类的 TP 值、属于一个类别但不属于另一个类别的 FP 值、属于一个类别但不属于另一个类别的 FN 值，以及属于一个类别但不属于另一个类别的 FP 值。

![](img/66ecdb8eb8654ae1c99705e55a45a836_259_0.png)

**图 13.5** 混淆矩阵预测。

*来源：* Khang (2021)

**表 13.1**  
拟议系统和现有系统的准确率值。

| 算法 | 结果 |
|---|---:|
| PSO | 77.21 |
| 支持向量机 (SVM) | 78.36 |
| RF | 80.45 |
| 混合粒子群优化 (HPSO) + RF | 83.65 |

**准确率：** 准确率是通过将正确预测的总数除以数据集中观测值的总数来计算的。

最高准确率为 1.0，最低为 0.0。要计算准确率，请使用公式 13.5：

$$\mathrm{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN} \tag{13.5}$$

各种算法的准确率值列于表 13.1，并在图 13.6 中显示。

准确率图在图 13.6 中描述。

**精确率：** 精确率是通过将真正例除以预测为正类的任何内容（公式 13.6）来确定的。

$$\mathrm{Precision} = \frac{TP}{TP + FP} \tag{13.6}$$

![](img/66ecdb8eb8654ae1c99705e55a45a836_260_0.png)

**图 13.6** 准确率图。

**表 13.2**  
**拟议系统和现有系统的精确率值。**

| 算法 | 结果 |
|---|---:|
| PSO | 76.12 |
| SVM | 78.21 |
| RF | 81.65 |
| HPSO + RF | 87.65 |

各种算法的精确率值列于表 13.2。  
精确率图在图 13.7 中显示。

**特异性：** 计算特异性涉及将负数总数除以准确负预测数 (TN) (*N*)，如公式 13.7 所示：

Specificity = TN/(TN + FP)　　　　　　　　　　　　　　　　　　 (13.7)

各种算法的特异性值列于表 13.3。  
特异性图在图 13.8 中描述。

**敏感性：** TP 率是所有真正阳性事件中阳性值的比例 (TPR)，如公式 13.8 所示：

Sensitivity = TP/(TP + FN)　　　　　　　　　　　　　　　　　　 (13.8)

**表 13.4**  
拟议系统和现有系统的敏感性值。

| 算法 | 结果 |
|---|---|
| PSO | 71.69 |
| SVM | 72.55 |
| RF | 78.20 |
| HPSO + RF | 85.59 |

![](img/66ecdb8eb8654ae1c99705e55a45a836_262_0.png)

**图 13.9** 敏感性图。

各种算法的敏感性值列于表 13.4。敏感性图在图 13.9 中描述。上述敏感性图解释了所提出的 PSO + RF 机器学习技术在员工任务调度方面实现了更好的性能，而与任何其他现有系统相比 (Khang et al., 2023a)。

### 13.5 结论

我们提出并测试了一种使用 SVM 对选定数据集进行入侵检测的方法。它提供高数据准确性并表现出兼容的性能水平。

物联网 (IoT) 中的所有事物都发送数据包，随着连接设备数量呈指数增长，这种通信需要可靠的连接、存储和安全 (Khang et al., 2022b)。

健康的民主社会需要隐私，这不仅仅是个体个人数据的关注。随着技术进步，个人护理和医疗保健也在发展。

我们研究了新提出的隐私保护 SVM 分类系统，发现其主要协议是一种安全技术，用于确定加密数字的符号是否存在健全性问题或安全泄漏。然后，我们提出了一种新技术，可用于帮助隐私保护 SVM 分类，并且安全且准确地找到加密整数的符号 (Khang et al., 2023b)。

实验表明，MR-SVM 模型可以有效解决 SVM 成本随数据量增加而快速增加的问题。然而，实验使用了两个节点，数据传输速度有限。未来研究中可建立多个节点用于网络安全。

## 参考文献

- Abdel-Basset M., Gunasekaran M., Mohamed M., Smarandache F., (2019). “一种求解完全中性线性规划问题的新方法，” Neural Computing and Applications, 31, 1595–1605. https://link.springer.com/article/10.1007/s00521-018-3404-6
- Anna et al. (2018). World Health Organization, Regional Office for Europe, European Observatory on Health Systems and Policies. 欧洲公共卫生服务组织与融资：国家报告。 World Health Organization. Regional Office for Europe. https://apps.who.int/iris/handle/10665/326190
- Balyan A. K., Ahuja S., Lilhore U. K., Sharma S. K., Manoharan P., Algarni A. D., Raahemifar K., (2022). “一种使用 EGA-PSO 和改进随机森林方法的混合入侵检测模型，” Sensors, 22(16), 5986. www.mdpi.com/1424-8220/22/16/5986
- Bhambri P., Rani S., Gupta G., Khang A., (2022). 物联网的云和雾计算平台。 CRC Press. https://doi.org/ 10.1201/9781003213888
- Borner K., Bueckle A., Ginda M., (2019). “数据可视化素养：定义、概念框架、练习和评估，” Proceedings of the National Academy of Sciences, 116(6), 1857–1864. www.pnas.org/doi/abs/10.1073/pnas.1807180116
- Chan W., Saharia C., Hinton G., Norouzi M., Jaitly N., (Nov 2020). “Imputer：通过插补和动态规划进行序列建模，” In International Conference on Machine Learning, pp. 1403–1413. PMLR. http://proceedings.mlr.press/v119/chan20b.html
- Choi T. M., Wallace S. W., Wang Y., (2018). “运营管理中的大数据分析，” Production and Operations Management, 27(10), 1868–1883. https://onlinelibrary.wiley.com/doi/abs/10.1111/poms.12838
- Dai M., Tang D., Giret A., Salido M. A., (2019). “考虑运输约束的节能柔性作业车间调度问题的多目标优化，” Robotics and Computer-Integrated Manufacturing, 59, 143–157. www.sciencedirect.com/science/article/pii/S0736584518305222
- Dash S., Shakyawar S. K., Sharma M., Kaushik S., (2019). “医疗保健中的大数据：管理、分析与未来展望，” Journal of Big Data, 6(1), 1–25. https://link.springer.com/article/10.1186/s40537-019-0217-0
- Deng W., Xu J., Zhao H., (2019). “一种基于混合策略的调度问题改进蚁群优化算法，” IEEE Access, 7, 20281–20292. https://ieeexplore.ieee.org/abstract/document/8635465/
