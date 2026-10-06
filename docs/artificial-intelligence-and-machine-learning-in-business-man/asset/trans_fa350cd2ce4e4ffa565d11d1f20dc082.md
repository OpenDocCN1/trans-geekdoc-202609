

# 使用 AI 进行员工流失管理

# 191

![](img/9665bc5b38d724f414bf1c78dda7410a_211_0.png)

图 11.13 随机森林的 ROC 曲线。

```python
auc_score1 = roc_auc_score(y_test, pred_prob1[:,1])
auc_score2 = roc_auc_score(y_test, pred_prob2[:,1])
print(auc_score1, auc_score2)
```

0.9791176023517265 0.9877824238680089

图 11.14 KNN 和随机森林的 ROC 分数。

我们对对 XGBoost 模型进行了 ROC-AUC 分析以了解模型的性能，与两者相比，我们得到了相对较好的得分。
XGBoost 的 ROC 曲线如图 11.15 所示。
XGBoost 的 ROC 分数如图 11.16 所示。
对于 XGBoost，AUC 得分为 0.99403091，这是一个很好的分数。我们还为不同模型下的所有模型绘制了一张单一的 ROC–AUC 图。
KNN、随机森林对比 XGBoost 的 ROC 曲线如图 11.17 所示。

## 11.5 结论

在本章中，我们对员工流失数据集使用了三种不同的机器学习算法，并观察到与随机森林和 KNN 相比，XGBoost 更好的性能。存在其他算法和深度学习技术可以应用于此数据集以检查性能。我们可以使用不同类型的超参数调优方法来获得更好的结果。通过使用这种模型，组织可以跟踪其人力资源，并帮助他们制定更好的策略来留住资产并从员工那里获得更好的表现。在人力资源部门中使用 AI，将提高

# 业务管理中的人工智能与机器学习

![](img/9665bc5b38d724f414bf1c78dda7410a_212_0.png)

图 11.15 XGBoost 的 ROC 曲线。

```python
auc_score1 = roc_auc_score(y_test, pred_prob1[:,1])
print(auc_score1)
0.9940309153384559
```

图 11.16 XGBoost 的 ROC 分数。

![](img/9665bc5b38d724f414bf1c78dda7410a_212_1.png)

图 11.17 KNN vs 随机森林 vs XGBoost 的 ROC 曲线。

# 使用 AI 进行员工流失管理

193

HRM 系统将在管理员工方面为组织带来更好的性能。对于任何组织来说，技能丰富的员工可以提高性能并缩短产品或服务的交付时间。因此，没有任何组织会希望失去这些员工，这就是组织努力寻找员工满意度并减轻员工压力的原因。一些组织根据工作环境创建不同类型的互动娱乐活动，使员工没有工作压力。最后，我们可以说，对于任何组织的任何员工来说，薪水、晋升、工作压力工作环境对于决定留在该组织还是离开至关重要。因此，预测这些员工的行为将产生巨大影响，组织将积极行动改进其工作文化和其他相关活动。

# 参考文献

- 1. Jauhari, A. "How AI and Machine learning will impact HR practices", News corp Vccle partners summit, 2017.
- 2. Matsa, P. and Gummajji, K. "To study the impact of Artificial Intelligence on Human Resource Management" IRIJET(6), 2019.
- 3. Nunn, J. "Emerging impact of AI on HR" Forbes Technology Council, February 6, 2019.
- 4. Milani, L., et. al. "Exploring the Impact of AI on HRM", London School of Economics, 2017.
- 5. Verma, R., Bandi, S. "Artificial Intelligence & human resources management in Indian IT Sector, Proceeding of 10th International Conference on Digital Strategies for Organizational Success, 2019.
- 6. Ahmed, O., (2018) Artificial intelligence in HR, JRAR December 2018, 5(4) pp 971–978.
- 7. Cappilli, P., Tambe, P. and Yakubovich, V. "Artificial Intelligence in Human Resource Management: Challenges and a path forward" SSRN Electronics Journal, 2018 doi:10.2.139/smm.3263878
- 8. Saklani, P. Sometimes small data is enough to create small product" Harvard Business Review, 2019 available at https://hbr.org/2017/07/sometimes-small-data-is-enough-to-create-small-products
- 9. Pfe, J. and Sutton, R. “Evidence-based Management", 2019. Available at https://hbr.org/2006/01/evidence-based-management
- 10. Meskő, B., Hétényi, G., and Györőfi, Z. “Will Artificial Intelligence solve the Human Resource crisis in healthcare?" BMC Health Services Research, 18(1),

（注：原文中存在大量重复内容和乱码，此处已按要求进行逻辑翻译）

![](img/9665bc5b38d724f414bf1c78dda7410a_214_0.png)

（注：原文中存在大量重复内容和学码，此处已按要求进行逻辑翻译）

# 机器学习开启新时代

机器学习 Machine Learning
开启的111201/9781003125
Science Direct, Elsevier

（注：原文中存在大量重复内容和学码，此处已按要求进行逻辑翻译）

# 机器学习开启新时代

维杰·尚卡·潘迪（Vijay Shankar）
助理教授
北方大学管理学院， 印度

# 目录

- 12.1 引言...........................................................................195
- 12.2 分析主要研究..................................................................196
- 12.3 使用机器学习技术进行时间序列预测..................................199
- 12.4 结论...........................................................................203
- 参考文献.........................................................................203

## 12.1 引言

通过机器学习算法，人工智能在预测领域开启了新纪元。人工智能的神经网络带来了预测结果。在这些几年中，基于机器学习的研究论文预测了未来。机器学习的股票预测预测了趋势。股票价格的预测分为两个分支：一类是基本分析，另一类是技术分析。基本分析基于公司的财务报表，而技术分析整合了历史数据。预测的准确性取决于适当的模型。在 12

## 12.2 分析主要研究

Hansen 等 [5] 利用指数平滑、自回归移动平均 (ARIMA)、部分 ARIMA 模型和机器学习模型分析了趋势、周期、季节性成分。结果显示支持向量机主于其他模型并取得了最佳结果。

Carbonneau 等 [6] 使用包括循环神经网络和支持向量机在内的先进机器学习技术处理需求效应的影响。他们将结果与传统模型如原生预测法和移动平均进行了比较。他们的发现表明机器学习技术优于传统方法，但差异在统计上是显著的。

Choudhary 和 Garg [7] 使用基于遗传算法 (GA) 和支持向量机 (SVM) 的混合机器学习来预测股市数据。他们的发现显示 GA-SVM 优于独立的 SVM 系统。技术分析师从市场中获利的持续成功对有效市场假设 (EMH) 提出了质疑。在当前十年，使用 AI 技术预测成功结果的趋势日益增加。由于这些后果，在目前的情况下，研究人员将 EMH 作为零假设。

Tsai 和 Wang [8] 尝试使用混合机器学习技术预测台湾交易所上市公司的股票价格。决策树 (DT) 和人工神经网络 (ANN) 的具有更好的预测能力。混合模型 (DT+ANN) 提供了 77% 的预测准确率。他们的发现表明基于生物神经系统的人脑具有良好的预测能力，但缺乏解释性输出。

Ahmed 等 [9] 尝试预测由 3003 个每日、季度和每月时间序列组成的 M3 数据。该数据集是为了由国际预测期刊 [10] 组织的竞赛而生成的。用于比较的模型有多层感知器、贝叶斯神经网络、径基函数、广义回归网络（也称为内核回归）、分类回归树 (CART) 回归树、支持向量回归和高斯过程。这些方法与机器学习预测模型结合使用。发现表明多层感知器 (MLP) 和高斯过程 (GP) 两个模型优于其他。

Cheangga [11] 尝试利用神经网络改进风力预测。该技术的特征是能够将随机输入向量映射到相应的输出，而无需假设任何固定关系。

