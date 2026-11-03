
下标 (`t`) 表示当年财务报表中的数值，下标 (`t` − 1) 表示上年财务报表中的数值。

![](images/page332-01.png)![](images/page333-01.png)

### 1. 数据集中操纵者与非操纵者的案例各有多少？绘制条形图来展示。

### 2. 创建 80:20 的划分，并找出测试数据中正例的数量。

### 3. 操纵者的案例数相比非操纵者非常少。使用 `caret` 包并使用过采样技术构建模型。
- 随机森林
- 梯度提升机
使用 ROC AUC 分数作为性能指标比较模型的准确率。

### 4. 操纵者的案例数相比非操纵者非常少。使用下采样技术创建平衡数据集。使用 `caret` 包构建以下模型：
- 随机森林
- 梯度提升机
使用 ROC AUC 分数作为性能指标比较模型的准确率。

### 5. 操纵者的案例数相比非操纵者非常少。使用 `SMOTE` 采样技术创建平衡数据集。使用 `caret` 包构建以下模型：
- 随机森林
- 梯度提升机
使用 ROC AUC 分数作为性能指标比较模型的准确率。

### 6. 操纵者的案例数相比非操纵者非常少。使用 `rose` 采样技术创建平衡数据集。使用 `caret` 包构建以下模型：
- 随机森林
- 梯度提升机
使用 ROC AUC 分数作为性能指标比较模型的准确率。

### 7. 比较使用过采样、下采样、`SMOTE` 和 `rose` 技术的结果。报告所有模型中最好的模型。哪种采样技术在此数据集上给出最佳结果。

### 8. 使用随机森林和梯度提升机报告最佳模型的特征重要性。解释结果。

### 参考文献

**1.** Anon (2016), *“mtries 描述”*, 网页地址：[http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/al-go-params/mtries.html](http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/al-go-params/mtries.html), 访问于 01 February 2021.

**2.** Anon (2016), *“性能与预测”*, 网页地址：[https://docs.h2o.ai/h2o/latest-stable/h2o-docs/perfor-mance-and-prediction.html](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/perfor-mance-and-prediction.html), 访问于 01 January 2021.

**3.** Anon (2016), *“性能与预测”*, 网页地址：[http://h2o-release.s3.amazonaws.com/h2o/rel-yau/6/docs-website/h2o-docs/performance-and-prediction.html](http://h2o-release.s3.amazonaws.com/h2o/rel-yau/6/docs-website/h2o-docs/performance-and-prediction.html), 访问于 01 January 2021.

**4.** Anon (2016), *“分布”*, 网页地址：[https://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/algo-params/distribution.html](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/algo-params/distribution.html), 访问于 01 February 2021.

**5.** Anon (2016),*”GBM”*, 网页地址：[https://h2o-release.s3.amazonaws.com/h2o/rel-turing/1/docs-website/h2o-docs/welcome.html](https://h2o-release.s3.amazonaws.com/h2o/rel-turing/1/docs-website/h2o-docs/welcome.html), 访问于 01 February 2021.

**6.** Anon (2019), *“分布”*, 网页地址 [https://h2o-re-lease.s3.amazonaws.com/h2o/rel-yau/3/index.html](https://h2o-re-lease.s3.amazonaws.com/h2o/rel-yau/3/index.html), 访问于 01 February 2021.

**7.** Anon (2018), *“SMOTE – 用于不平衡分类问题的 SMOTE 算法”*, 网页地址：[https://www.rdocumentation.org/packages/DMwR/versions/0.4.1/top-ics/SMOTE](https://www.rdocumentation.org/packages/DMwR/versions/0.4.1/top-ics/SMOTE), 访问于 01 February 2021.

**8.** Anon (2020), *“在 R 中使用 SMOTE 创建 1:1 平衡数据集而不修改多数类的观测值”*, 网页地址：[https://stackoverflow.com/questions/62871492/create-balanced-dataset-11-us-ing-smote-without-modifying-the-observations-of-th](https://stackoverflow.com/questions/62871492/create-balanced-dataset-11-us-ing-smote-without-modifying-the-observations-of-th), 访问于 01 February 2021.

**9.** Anon (2021), *“将数据集拆分为训练/测试/验证”*, 查看日期 2021, 网页地址：[https://h2o-re-lease.s3.amazonaws.com/h2o/rel-vajda/1/docs-website/h2o-docs/data-munging/splitting-datasets.html](https://h2o-re-lease.s3.amazonaws.com/h2o/rel-vajda/1/docs-website/h2o-docs/data-munging/splitting-datasets.html), 访问于 01 February 2021.

**10.** Anon (2020), *“隔离森林”*, 网页地址：[http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/if.html](http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/if.html), 访问于 01 February 2021.

**11.** Anon (2020), *“性能与预测”*, 网页地址：[https://docs.h2o.ai/h2o/latest-stable/h2o-docs/performance-and-prediction.html](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/performance-and-prediction.html),, 访问于 01 February 2021.

**12.** Anon (2021), We are improving the predictions of training data but is the procedure also | Course Hero, 网页地址：[https://www.coursehero.com/file/puj8l6/What-is-the-process-of-dividing-each-feature-by-its-range-called-fea-ture](https://www.coursehero.com/file/puj8l6/What-is-the-process-of-dividing-each-feature-by-its-range-called-fea-ture)/, 访问于 01 February 2021.

**13.** Beneish M D (1999), “盈余操纵的检测”, *Financial Analyst Journal*, **55**(5), 24–36.

**14.** Bernard S, Heutte L, Adam S (2010), “随机森林中强度与相关性的研究”, *International Conference on Intelligent Computing*, Aug 2010, Changsha, China. pp.186–191, ff10.1007/978-3-642-14831-6\_25ff.ffhal-00598466f.

**15.** Breiman L (1996), “Bagging predictors,” *Machine Learning*, 24 (2), 123–140.

**16.** Breiman L (2001), “随机森林”, *Machine Learning*, **45** (1), 5–32.

**17.** Chawla N V, Bower K W, Hall L O and Kegelmeyer W P (2002), “SMOTE：合成少数类过采样技术”, *Journal of Artificial Intelligence Research*, **16**, 321–357.

**18.** Kumar U D, Syed T A I and Ganeshan (2016), “使用机器学习算法预测印度公司的盈余操纵”, *Harvard Business Publishing*, 可获取于 [https://hbsp.harvard.edu/product/IMB577-PDF-ENG?Ntt=Earnings%20manipulation](https://hbsp.harvard.edu/product/IMB577-PDF-ENG?Ntt=Earnings%20manipulation), 访问于 04 August 2021.

**19.** Friedman J H (2001), *“贪婪函数逼近：梯度提升机”*, Stanford University Report, 网页地址：[https://statweb.stanford.edu/~jhf/ftp/trebst.pdf](https://statweb.stanford.edu/~jhf/ftp/trebst.pdf), 访问于 01 February 2021.

**20.** Friedman J H (2002), “随机梯度提升”, *Computational Statistics and Data Analysis*, **38**(4), 367–378.

**21.** Kullback S and Leibler R A (1951), “关于信息与充分性”, *Annals of Mathematical Statistics*, **22** (1), 79–86.

**22.** LeDell L (2020), *“`h2o.splitFrame`”*, 网页地址：[https://www.rdocumentation.org/packages/h2o/ver-sions/3.32.0.1/topics/h2o.splitFrame](https://www.rdocumentation.org/packages/h2o/ver-sions/3.32.0.1/topics/h2o.splitFrame), 访问于 01 February 2021.

**23.** Li C (2018), *“梯度提升的温和介绍”*, 网页地址：[https://www.ccs.neu.edu/home/vip/teach/MLcourse/4\_boosting/slides/gradient\_boosting.pdf](https://www.ccs.neu.edu/home/vip/teach/MLcourse/4_boosting/slides/gradient_boosting.pdf), 访问于 01 February 2021.

**24.** D Li, W Li, X Wang, C T Nguyen and S Lu (2020), “基于深度神经网络的加密互联网流量中的应用轨迹识别”, *Computer Networks*, **179**, 网页地址：[https://doi.org/10.1016/jxomnet.2020.107372](https://doi.org/10.1016/jxomnet.2020.107372), 访问于 01 February 2021.
