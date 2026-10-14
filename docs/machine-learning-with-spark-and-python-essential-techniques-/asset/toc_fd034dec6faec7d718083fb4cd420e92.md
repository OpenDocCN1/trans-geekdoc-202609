## Spark 与 Python 机器学习：预测分析核心技术
## 简介
## 本书旨在弥合这一差距
### 本书适合的读者
### 本书内容概览
## 集成方法：强大的预测分析工具
### 首版出版以来的变化
### 本书结构安排
### 使用本书所需环境
### 本书读者支持
#### 源代码
#### 如何联系出版社
# 第 1 章：进行预测的两大核心算法
## 为什么这两种算法如此有用？
### 算法性能对比表
### 什么是惩罚回归方法？
### 模拟数据点减少的影响
### 自由度与数据量的关系
### 什么是集成方法？
### 如何决定使用哪种算法
### 表 1.4：惩罚线性回归与集成算法的高层权衡
### 构建预测模型的流程步骤
### 界定机器学习问题
### 特征提取与特征工程
### 决定用于预测的变量
### 确定训练模型的性能
## 章节内容与依赖关系
### 第 5 章
### 第 6 章
### 第 7 章
## 总结
## 参考文献
# 第 2 章：通过理解数据来理解问题
## 新问题的剖析
## 不同类型的属性和标签驱动建模选择
## 关于新数据集需要注意的事项
## 分类问题：利用声纳探测未爆水雷
### “岩石与水雷”数据集的物理特征
#### 清单 2-1：评估新数据集规模 — rockVmineSummaries.py
#### 清单 2-2：确定属性性质 — rockVmineContents.py
### 岩石与地雷数据集的统计摘要
#### 清单 2-3：数值与分类属性的汇总统计 — rVMSummaryStats.py
#### 使用分位数-分位数图可视化离群值
#### 清单 2-4：岩石与地雷数据第 4 个属性的分位数-分位数图 — qqplotAttribute.py
### 分类属性的统计特征描述
### 如何使用 Python Pandas 对岩石与矿山数据集进行汇总
#### Listing 2-5: 使用 Python pandas 读取和汇总数据 — pandasReadSummarize.py
## 可视化岩石与地雷数据集的属性
### 使用平行坐标图进行可视化
#### 清单 2-6：用于实值属性可视化的平行坐标图 — linePlots.py
### 可视化属性与标签之间的相互关系
#### 清单 2-7：属性成对交叉绘图 — corrPlot.py
#### 清单 2-8：分类目标与实值属性之间的相关性 — targetCorr.py
### 两个属性（或一个属性与目标）之间的相关程度可以使用皮尔逊相关系数来量化
#### 清单 2-9: 属性 2 对 3 和属性 2 对 21 的皮尔逊相关性计算 — corrCalc.py
### 使用热力图可视化属性与标签的相关性
#### 清单 2-10: 直观呈现属性相关性 — sampleCorrHeatMap.py
### 理解岩石与地雷数据集过程的总结
## 含因子变量的实值预测：你的鲍鱼多大了？
#### Listing 2-11：读取并汇总鲍鱼数据集 — abaloneSummary.py
### 回归问题的平行坐标图——可视化鲍鱼问题的变量关系
#### 清单 2-12：鲍鱼数据的平行坐标图 — abaloneParallelPlot.py
### How to Use a Correlation Heat Map for Regression—Visualize Pair-Wise Correlations for the Abalone Problem
#### Listing 2-13: Correlation Calculations for the Abalone Data — abaloneCorrHeat.py
## Real-Valued Predictions Using Real-Valued Attributes: Calculate How Your Wine Tastes
#### Listing 2-14: Wine Data Summary — wineSummary.py
### 代码示例：读取葡萄酒数据并生成统计摘要
#### Listing 2-15: 为葡萄酒数据生成平行坐标图 — wineParallelPlot.py
### 打印输出
### 图 2.19：葡萄酒数据的相关性热力图
## 多类分类问题：那是什么类型的玻璃？
### 图 2.20：玻璃数据的箱线图
#### 清单 2-16：玻璃数据集摘要 — glassSummary.py
#### Listing 2-17: 玻璃数据的平行坐标图 — glassParallelPlot.py
## 使用 PySpark 理解大型数据集
#### Listing 2-18: 使用 PySpark 汇总数据集 — SparkDataFrameProperties.py
#### Listing 2-19: 使用 PySpark 对数据进行采样——SamplingSparkDataFrame.py
## 摘要
## 参考文献
# 第 3 章：预测模型构建：平衡性能、复杂性与大数据
## 基本问题：理解函数逼近
### 处理训练数据
### 评估预测模型的性能
## 驱动算法选择和性能的因素——复杂性与数据
### 简单问题与复杂问题的对比
### 影响性能的因素：问题复杂度与数据规模
### 简单模型与复杂模型的对比
#### 驱动预测算法性能的因素
#### 选择算法：线性还是非线性？
## 预测模型性能度量
### 不同类型问题的性能度量
#### 清单 3.1：MSE、MAE 和 RMSE 的对比——regressionErrorMeasures.py
#### 清单 3.2：在岩石与地雷数据集上训练的分类器性能度量——classifierPerformance:RocksVMines.py
## 岩石与矿石分类：线性回归模型分析
### 代码实现
#### 使用 scikit-learn 包执行线性回归
#### 从 uci.edu 数据仓库读取岩石与矿石数据集
#### 将属性和标签划分为训练集和测试集（2/3 和 1/3）
#### 构建训练和测试数据数组
#### 检查形状以查看其结构
#### 训练线性回归模型
#### 生成样本内误差的预测值
#### 生成训练集预测的混淆矩阵（样本内
#### 选取阈值并生成混淆矩阵条目
#### 生成样本外数据的预测值
#### 根据样本外数据的预测生成混淆矩阵
#### 选取阈值并生成混淆矩阵条目
#### 生成样本内 ROC 曲线
#### 绘制 ROC 曲线
#### 生成样本外 ROC 曲线
#### 绘制 ROC 曲线
### 运行结果
### ROC 曲线与 AUC
#### 模拟已部署模型的性能
### 实现模型与数据的和谐
### 选择模型以平衡问题复杂度、模型复杂度和数据集大小
#### 使用前向逐步回归控制过拟合
##### 代码清单 3.3：前向逐步回归：葡萄酒质量数据——fwdStepwiseWine.py
##### 代码清单 3.4：前向逐步回归输出
#### 评估和理解你的预测模型
#### 通过惩罚回归系数控制过拟合——岭回归
##### 清单 3.5：使用岭回归预测葡萄酒口感——ridgeWine.py
##### 清单 3.6：岭回归输出
##### 清单 3.7：使用岭回归进行岩石与地雷分类——classifierRidgeRocksVMines.py
#### Python 代码示例：岭回归分类岩石与矿山数据
##### read data from uci data repository
##### divide attribute label vector into training and test sets (2/3, 1/3)
##### plot auc values versus alpha values
##### visualize the performance of the best classifier
##### scatter plot of actual vs predicted
#### Listing 3.8：使用岭回归进行岩石与矿山分类模型的输出
#### 在极大数据集上使用 PySpark 训练惩罚回归模型
##### 代码清单 3.9：葡萄酒数据上岭回归的 Spark 实现——`linear_regression_w_spark.py`
## 总结
## 参考文献
# 第 4 章 惩罚线性回归
## 惩罚线性回归：规范线性回归以实现最优性能
### 为什么惩罚线性回归方法如此有用
#### 极快的系数估计
#### 变量重要性信息
#### 部署时评估极快
#### 可靠性能
#### 稀疏解
#### 问题可能要求线性模型
#### 何时使用集成方法
### 惩罚线性回归：规范线性回归以实现最优性能
#### 训练线性模型：最小化误差及其他
##### 在 OLS 表述中添加系数惩罚
#### 为什么这讲得通？
##### 其他有用的系数惩罚——曼哈顿距离和弹性网
##### 为什么 Lasso 惩罚会导致稀疏系数向量
##### ElasticNet 惩罚融合了 Lasso 和 Ridge
### 求解惩罚线性回归问题
#### 理解最小角回归及其与前向逐步回归的关系
##### LARS 算法
###### 代码清单 4.1：用于预测葡萄酒口感的 LARS 算法——larsWine2.py
####### 将葡萄酒数据读入列表
####### 标准化特征
####### 标准化标签
####### 初始化系数向量 beta
####### 初始化每一步的 beta 矩阵
####### 初始化列表以累积已使用的特征
####### 步数和步长
#### LARS 如何生成数百个复杂度各异的模型
#### 从 LARS 生成的数百个模型中选择最佳模型
##### 清单 4.2：用于确定最佳系数集的 10 折交叉验证——larsWineCV.py
##### 用于模型选择的 Python 代码中的交叉验证机制化
##### 在每个交叉验证折上累积误差并评估结果
##### 模型选择和训练序列的实际考量
#### 使用 Glmnet：极快且极通用
##### Glmnet 和 LARS 算法机制的比较
##### 初始化和迭代 Glmnet 算法
###### 清单 4.3：Glmnet 算法——glmnetWine2.py
####### 将葡萄酒数据读入属性行列表和标签列表
####### 归一化 x 
####### 归一化标签
####### 选择 alpha 参数的值
####### 定义迭代参数
####### 遍历数据一次以确定恰好抑制所有系数为零的 lambda 值
####### 初始化系数向量 beta
####### 初始化每一步的 beta 矩阵
####### 开始迭代
####### 打印出有序的 beta 列表
####### plt.savefig('glmnetWine2.png', dpi=500)
### 将线性回归扩展到分类问题
#### 使用惩罚回归求解分类问题
##### 清单 4.4：通过为二元标签分配数值将分类问题转化为普通回归问题——larsRocksVMines.py
#### 处理具有两个以上结果的分类问题
#### 理解基扩展：在非线性问题上使用线性方法
##### 清单 4.5：葡萄酒口味预测的基扩展——wineBasisExpansion.py
#### 将非数值属性纳入线性方法
##### 带分类变量的惩罚线性回归
###### 代码清单 4.6：为惩罚线性回归编码分类变量——鲍鱼数据——larsAbalone.py
####### read abalone data
####### code three-valued sex attribute as numeric
####### Normalize features (w coded 3-valued sex)
####### Normalize labels
####### initialize matrix of betas at each step
####### number of steps to take
## 总结
## Chapter Objectives
## References
# Chapter 5 Building Predictive Models with Penalized Linear Methods
## Python Packages for Penalized Linear Regression
## 多元回归：预测葡萄酒口感
### 构建并测试预测葡萄酒口感的模型
#### 清单 5-1：使用交叉验证估算 Lasso 建模葡萄酒口感的样本外误差——wineLassoCV.py
##### Display results
### 部署前在完整数据集上训练
#### 清单 5-2：在完整数据集上进行 Lasso 训练——wineLassoCoefCurves.py
##### The coefficients on normalized attributes give another slightly 
##### different ordering
### 基展开：通过从旧变量创建新变量来提升性能
#### 清单 5-3：使用样本外误差评估预测葡萄酒质量的新属性——wineExpandedLassoCV.py
##### read data into iterable
##### append two new attributes - square of last term (alcohol) and product
##### of alcohol and volatile acidity
##### check the new dimensions
##### Normalize columns in x and labels
##### Note: be careful about normalization.  Some penalized regression 
##### packages include it
##### and some don't.
##### Normalize labels
##### Display results
## 二分类：使用惩罚线性回归检测未爆地雷
### 使用弹性网络回归构建二分类分类器
#### Listing 5-4：使用弹性网络回归构建二分类（两类）分类器——rocksVMinesENetRegCV.py
### 构建用于部署的岩石与地雷分类器
#### 清单 5-5：在岩石与地雷数据上训练的 ElasticNet 系数轨迹——rocksVMinesCoefCurves.py
#### 清单 5-6：在岩石与地雷数据上训练的惩罚逻辑回归——rvmGlmnet2.py
## 多分类：犯罪现场玻璃样本分类
### 清单 5-7：带惩罚线性回归的多分类：犯罪现场玻璃样本分类——glassENetRegCV.py
##### Display results
## 使用 PySpark 进行线性回归和分类
### 使用 PySpark 预测葡萄酒口感
#### 清单 5-8：使用 PySpark 惩罚回归确定葡萄酒口味预测中的变量重要性——wine_variable_importance:spark.py
##### 导入 sparksession 
##### 将鲍鱼数据作为 pandas 数据框读入并创建 Spark 数据框。
##### 为葡萄酒数据创建 spark 数据框
##### 对特征调用 StandardScaler
##### 将每个特征归一化为单位标准差。
##### scaledData 包含单个原始特征以及
##### 原始特征和缩放特征的向量化版本
##### alpha 列表 从大到小，以及用于存储结果的空列表
##### 根据表现最佳的 alpha (index=2) 的系数幅度对属性排序
##### 绘制样本外误差与 alpha 的曲线
### 使用 PySpark 进行逻辑回归：岩石与地雷
#### 清单 5-9：用于训练岩石与地雷问题 PySpark 模型的代码——rocksVMines_spark.py
##### PySpark 逻辑回归：岩石与矿山分类
###### 代码实现
####### Import sparksession
####### read in abalone data as pandas data frame and create Spark data frame.
####### Create spark dataframe for wine data
###### 运行结果
###### 结果分析
### 在 PySpark 模型中引入分类变量：预测鲍鱼年龄
#### 清单 5.10：独热编码分类特征：鲍鱼数据——`abalone_data_spark.py`
##### 导入 sparksession 
##### 将鲍鱼数据读取为 pandas 数据框并创建 Spark 数据框。
### 使用元参数优化的多类逻辑回归
#### 清单 5.11：构建并优化用于玻璃分类的 PySpark 模型的代码——`glass_log_regress_spark.py`
## Summary
## References
# Chapter 6: Ensemble Methods
## 二叉决策树
#### 清单 6-1：构建决策树预测葡萄酒质量——wineTree.py
##### conda install -c conda-forge pydotplus 
### 二叉决策树如何生成预测
### 如何训练二叉决策树
#### 清单 6-2：为简单回归问题训练决策树——simpleTree.py
##### 树训练等于分裂点选择
##### 构建一个简单的数据集，y = x + 随机噪声
##### 用于绘图的 x 值
##### y（标签）在 x 值基础上添加了随机噪声
##### 设置随机种子
##### 绘制树 -- 此代码块需要在独立的单元格中运行
##### 将树的预测与真实值进行比较
##### 绘制树
##### 分裂点计算 - 尝试每一个可能的分裂点以找到最佳分裂点
### 分裂点选择如何影响预测
### 选择分裂点的算法
### 多变量树训练——选择哪个属性进行分裂？
#### 递归分裂以增加树深度
### 二叉树的过拟合
#### 用二叉树测量过拟合
#### 平衡二叉树复杂度以获得最佳性能
#### Listing 6-3 (#c06.xhtml#R_c06-fea-0003): Cross-Validation at a Range of Tree Depths—simpleTreeCV.py
### 分类和分类特征的修改
## Bootstrap 聚合：“Bagging”
### Bagging 算法如何工作？
#### 清单 6-4：Bootstrap 聚合算法——simpleBagging.py
##### 构建一个简单的数据集，y = x + 随机噪声
##### 用于绘图的 x 值
##### y（标签）在 x 值基础上添加了随机噪声
##### 设置随机种子
##### 取固定测试集，占样本的 30%
##### 定义测试集和训练集的属性与标签
##### 在训练数据的随机子集上训练一系列模型
##### 将模型收集在列表中，并检查随着列表增长组合模型的误差
##### 要生成的最大模型数量
##### 树的深度 - 通常取较高值
##### 初始化一个列表来保存模型
##### 随机装袋法抽取的样本数量
##### 从前 "n" 个模型构建累积预测
#### 装袋性能——偏差与方差
#### 装袋法在多变量问题上的表现
### Listing 6-5：使用装袋法预测葡萄酒质量——wineBagging.py
##### 将数据读入可迭代对象
##### 取固定测试集，占样本的 30%
##### 定义测试集和训练集的属性及标签集
##### 在训练数据的随机子集上训练一系列模型
##### 将模型收集在列表中，并检查随着列表增长组合模型的误差
##### 要生成的最大模型数量
##### 树的深度 - 通常取较高值
##### 初始化一个列表以保存模型
##### 随机装袋法要抽取的样本数量
##### 从前 "n" 个模型构建累积预测
##### 从前 "n" 个模型构建累积预测
### 装袋法需要树的深度来保证性能
### 装袋法总结
## 梯度提升
### 梯度提升算法的基本原理
#### 清单 6-6：简单问题的梯度提升——simpleGBM.py
##### Build a simple data set with y = x + random
##### x values for plotting
##### y (labels) has random noise added to x-value
##### set seed
##### take fixed test set 30% of sample
##### Define test and training attribute and label sets
##### train a series of models on random subsets of the training data
##### collect models in a list and check error of composite as list grows
##### maximum number of models to generate
##### tree depth - typically at the high end
##### initialize a list to hold models
##### initialize residuals to be the labels y
##### build cumulative prediction from first "n" models
### 梯度提升的参数设置
### 梯度提升如何迭代生成预测模型
### 从梯度提升中获得最佳性能
#### 梯度提升模型的预测与属性值关系
#### 多变量问题上的梯度提升
##### 清单 6-7 (#c06.xhtml#R_c06-fea-0007): 用于预测葡萄酒质量的梯度提升——wineGBM.py
### 梯度提升总结
## 随机森林
#### 清单 6-8：带随机属性选择的装袋法——wineRF.py
##### 将数据读入可迭代对象
##### 取固定测试集，占样本的 30%
##### 定义测试集和训练集的属性及标签集
##### 在训练数据的随机子集上训练一系列模型
##### 将模型收集在列表中，并随着列表增长检查组合模型的误差
##### 要生成的最大模型数量
##### 树的深度 - 通常取较高值
##### 选定每个模型将使用多少属性。
##### 作者建议回归问题使用 1/3
##### 初始化一个列表以保存模型
##### 从前 "n" 个模型构建累积预测
### 随机森林：装袋法加随机属性子集
### 随机森林性能驱动因素
### 图 6.25–6.27：随机属性选择下的 MSE 与树的数量关系
### 随机森林总结
## 总结
## 参考文献
# 第 7 章：使用 Python 构建集成模型
## 使用 Python 集成包解决回归问题
### 使用梯度提升预测葡萄酒口感
#### 使用 GradientBoostingRegressor 的类构造函数
#### 使用 GradientBoostingRegressor 实现回归模型
### 清单 7-1：构建梯度提升模型预测葡萄酒质量——wine_gbm.py
#### 评估梯度提升模型的性能
### 构建随机森林模型预测葡萄酒口感
#### Python scikit-learn ensemble 模块包含用于回归问题的随机森林算法
### 构建 RandomForestRegressor 对象
#### `n_estimators`
#### `max_depth`
#### `min_samples_split`
#### `min_samples_leaf`
#### `max_features`
#### `random_state`
#### `feature_importances_`
#### `fit(XTrain, yTrain, sample_weight=None)`
#### `predict(XTest)`
### 使用 RandomForestRegressor 对葡萄酒口味建模
#### 清单 7-2：构建随机森林预测葡萄酒质量——wine_rf.py
##### 从 UCI 网站读取葡萄酒质量数据
##### 取固定留出集，占数据行的 30%
##### 针对不同森林规模训练随机森林 - 观察 mse 如何变化
##### 绘制训练和测试误差随集成中树数量变化的曲线
##### 绘制特征重要性
##### 按最大重要性归一化
#### 可视化随机森林回归模型的性能
## 在 Python 集成模型中融入非数值属性
### 为 Python 梯度提升回归对鲍鱼性别进行编码
#### 清单 7-3: 训练梯度提升模型预测鲍鱼年龄——abalone_gbm.py
##### Train gradient boosting model to minimize mean squared error
### 使用梯度提升评估性能和编码变量的重要性
### 为 Python 随机森林回归输入对鲍鱼性别进行编码
#### 清单 7-4: 训练随机森林模型预测鲍鱼年龄——abalone_rf.py
### 评估性能和编码变量的重要性
## 使用 Python 集成方法解决二分类问题
### 使用 Python 梯度提升检测未爆地雷
#### 二分类的三个目标
#### 清单 7-5：构建梯度提升模型以区分水下地雷与岩石——rocks_v_mines_gbm.py
##### 从 uci 数据仓库读取数据
##### x 矩阵中的行数和列数
##### 将 x 和 y 转换为 numpy 数组并编造列名
##### 训练梯度提升模型以最小化均方误差
### 确定梯度提升分类器的性能
### 使用 Python 随机森林探测未爆地雷
#### 构建用于探测未爆地雷的随机森林模型
##### Listing 7-6：构建随机森林模型以区分水下地雷与岩石——rocks_v_mines_rf.py
### 确定随机森林分类器的性能
## 使用 Python 集成方法解决多类分类问题
### 处理类别不平衡
### 使用梯度提升对玻璃进行分类
#### Listing 7-7：构建梯度提升模型以区分不同类型的玻璃——glass_gbm.py
### 确定梯度提升模型在玻璃分类上的性能
### 使用随机森林进行玻璃分类
#### Listing 7-8：构建随机森林模型以区分不同玻璃类型——glass\_rf.py
##### 读取玻璃数据
##### x 矩阵的行数和列数
##### 标签为 1 到 7 的整数，没有 4 的示例。
##### gb 需要从 0 开始的连续整数
##### 类别分布：
##### 旧标签     新标签     样本数量
##### 1              0               70
##### 2              1               76
##### 3              2               17
##### 5              3               13
##### 6              4               9
##### 7              5               29
##### 抽取 30% 测试样本可能无法保持总体比例
##### 按标签进行分层抽样。
##### 生成混淆矩阵
##### 绘制集成中树的数量与训练和测试错误的关系图
##### 绘制特征重要性
##### 按最大重要性归一化
##### 绘制变量重要性
### 确定随机森林模型在玻璃分类上的性能
## 使用 PySpark 集成包解决回归问题
### 使用 PySpark 集成方法预测葡萄酒口感
#### 清单 7-9：使用 PySpark GBM 预测葡萄酒质量——wine_taste_pred_spark_gbm.py
#### 清单 7-10：使用 PySpark RF 预测葡萄酒质量——wine_taste_prediction_spark_rf.py
### 使用 PySpark 集成方法预测鲍鱼年龄
#### Listing 7-11：使用 PySpark 梯度提升预测鲍鱼年龄——`abalone_gbm_spark.py`
##### 使用 PySpark 集成方法预测鲍鱼年龄
### 梯度提升树模型
#### Import sparksession 
#### read in abalone data as pandas data frame and create Spark data frame. 
#### Create spark dataframe for abalone data
##### 模型输出结果
### 随机森林模型
#### Listing 7-12: 使用 PySpark 随机森林预测鲍鱼年龄——`abalone_rf_spark.py`
##### Use the same data pipeline as for gbt. 
##### use evaluator to assess performance
### 使用 PySpark 集成方法区分矿石与岩石
#### 清单 7-13：使用 PySpark 区分地雷与岩石——rocks_v_mines_gbt_spark.py
##### 导入 sparksession 
##### 将鲍鱼数据读入 pandas 数据帧并创建 Spark 数据帧。 
##### 为葡萄酒数据创建 spark 数据帧
#### 清单 7-14：使用 PySpark 随机森林区分地雷与岩石——rocks_v_mines_rf_spark.py
### 使用 PySpark 集成方法识别玻璃类型
#### 清单 7-15：使用 PySpark 随机森林识别玻璃类型——glass_multiclass_rf_spark.py
### 随机森林多类别预测示例
## 总结
## 参考文献
## 索引
### B
### C
## 索引
### A
### C
### D
### E
### F
### S
### T
### U
## 索引
### U
### V
### W
### X
### Y
# Machine Learning with Spark™ and Python^®: Essential Techniques for Predictive Analytics, Second Edition
# 作者简介
## 关于技术编辑
## 致谢
## WILEY 最终用户许可协议