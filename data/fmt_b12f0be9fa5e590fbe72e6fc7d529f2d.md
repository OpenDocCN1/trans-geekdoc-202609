
```python
from sklearn.cluster import DBSCAN
from sklearn.preprocessing import StandardScaler
import seaborn as sns
import matplotlib.pyplot as plt
# Select and scale features
X = df[['Salary', 'Experience']]
X_scaled = StandardScaler().fit_transform(X)
# Apply DBSCAN
dbscan = DBSCAN(eps=0.5, min_samples=5)
df['Cluster'] = dbscan.fit_predict(X_scaled)
# Visualize the clusters
sns.scatterplot(x='Salary', y='Experience', hue='Cluster', data=df, palette='tab10')
plt.title("DBSCAN Clustering")
plt.show()
```

此代码段缩放了输入特征并使用默认参数应用 `DBSCAN`。随后使用聚类标签绘制结果，异常值通常被标记为 `-1`。

## Copilot 和 ChatGPT 辅助

为了有效地实现和解释 `DBSCAN` 聚类，GitHub Copilot 和 ChatGPT 的结合支持提供了自动化代码辅助和概念清晰度：

### GitHub Copilot
GitHub Copilot 通过预判关键预处理需求、建议合适的参数以及完成核心代码组件简化了 `DBSCAN` 的实现：

- 在聚类之前自动建议特征缩放 `StandardScaler` ——这是 `DBSCAN` 关键的预处理步骤。
- 预测合适的默认值 `eps=0.5, min_samples=5`，同时根据数据集大小和特征分布调整建议。
- 自动补全函数调用、DataFrame 赋值和可视化组件。

### ChatGPT
ChatGPT 通过明确 `DBSCAN` 输出并通过视觉和分析技术引导参数选择，提供了宝贵的解释支持：

- 提供更深层次的解释和指导：
- 解释聚类标签 `-1` 指的是噪声或异常值——即不属于任何稠密区域的点。
- 建议绘制 k-距离图以帮助确定合适的 `eps` 值。

## 在 ChatGPT 指导下绘制 k-距离图

k-距离图有助于识别到第 k 个最近邻居距离的剧烈变化点（肘点），这通常预示着一个良好的 `eps` 阈值。

以下代码绘制了 k-距离图，以帮助为 `DBSCAN` 估计合适的 `eps` 值：

```python
from sklearn.neighbors import NearestNeighbors
import numpy as np
neighbors = NearestNeighbors(n_neighbors=5)
neighbors_fit = neighbors.fit(X_scaled)
distances, indices = neighbors_fit.neighbors(X_scaled)
# Sort and plot the distances to the 5th nearest neighbor
distances = np.sort(distances[:, 4], axis=0)
plt.plot(distances)
plt.title("k-distance Graph")
plt.xlabel("Distance to 5th Nearest Neighbor")
plt.ylabel("Sorted Points")
plt.show()
```

ChatGPT 洞察：寻找曲线急剧上升的点——那通常是 `eps` 值的良好候选点。

通过将 `DBSCAN` 的聚类能力与 AI 引导的工作流相结合，开发者可以从试错调优转向获得定义更好的簇、更少的虚假异常值以及更具操作性的洞察。

## AI 建议的层次聚类

层次聚类提供了一种视觉直观且灵活的数据分组方法，无需预先定义簇的数量。然而，它的成功在很大程度上取决于两个关键决策：连接方法 `linkage method`，如何计算簇之间的距离和距离度量，如何衡量数据点之间的距离。

在 AI 辅助工具的支持下，开发者可以更有信心地实现和解释层次聚类。GitHub Copilot 处理技术实现，而 ChatGPT 提供深层的概念指导，帮助在每一步中做出正确的选择。

### 实现示例

```python
from scipy.cluster.hierarchy import linkage, dendrogram
import matplotlib.pyplot as plt
linked = linkage(X_scaled, method='ward')
plt.title("Hierarchical Clustering Dendrogram")
plt.xlabel("Sample Index")
plt.ylabel("Distance")
plt.show()
```

此代码使用 Ward 方法（最小簇内方差）执行层次聚类，并以树状图的形式可视化结果，展示了簇是如何形成的。

## AI 工具辅助

GitHub Copilot 和 ChatGPT 等 AI 工具通过简化实现和深化可解释性增强了层次聚类工作流：

### GitHub Copilot
GitHub Copilot 通过生成工作流的核心组件并建议常用的视化连接策略简化了层次聚类过程：

- 自动补全从 `linkage()` 到 `dendrogram()` 的聚类工作流。
- 建议常用的连接方法，例如：
  - `'ward'`：用于紧凑的簇。
  - `'complete'`：通过最大对距离获得分离良好的簇。
  - `'average'`：通过平均距离获得更平衡的聚类。
- 生成轴标签、标题和绘图格式，帮助简化可视化。

### ChatGPT
ChatGPT 通过提供概念洞察以及选择连接方法和有效解读树状图的实践指导来增强层次聚类：

- 提供概念决策的支持。
- 根据数据特征推荐连接方法（例如：连续数值特征使用 `'ward'`，长尾分布使用 `'complete'`）。
- 解释如何解读树状图，包括：
  - 识别簇合并的高度。
  - 视觉上选择水平阈值来定义簇。

> **ChatGPT 提示：** 寻找树状图中水平簇连接线之间巨大的垂直间隙。在这些间隙之前切割通常可以获得自然的分组。

这种方法有助于在不预先 k 的情况下确定层次聚类中的最佳簇数量。以下树状图显示了层次聚类中簇是如何形成的以及在哪里切割树

为了获得自然的分组：

![](img/036cc5d5719121241c605ad59a82949c_466_0.png)

图 7.1：显示聚类形成的树状图

在较大的垂直间隙之前（例如在距离 25-30 处）切割树状图，可以获得有意义的聚类。明显的间隙表明通过切割树可以形成三个聚类。

在树状图中（使用 Ward's 连接方法在合成数据上生成），较大的垂直间隙表明数据可以自然地分为三个聚类。这种视觉化方法有助于根据数据集的内部结构选择有意义的分组。你可以在 Python 中使用以下代码生成类似的图表：

```python
scipy.cluster.hierarchy.dendrogram()
linkage()
```

通过将 Copilot 的实时代码补全与 ChatGPT 的解释能力相结合，开发者可以更有效地实现层次聚类工作流，从选择合适的连接方法到清晰地判释结果。

# 在流水线中自动化聚类任务

当聚类任务实现在模块化、可扩展且可重复的流水线中时，它们在现实世界应用和生产环境中最为有效。通过 scikit-learn 的 `Pipeline` 自动化聚类任务，开发者可以在统一的工作流中标准化预处理、建模和输出生成。

流水线减少了样板代码，并使其更容易跨项目或数据集对聚类模型进行版本控制、部署和重用。

## k-means 流水示例

以下代码定义了一个 scikit-learn 流水线，它可以一步完成特征缩放和 k-means 聚类：

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

# 定义流水线
pipeline = Pipeline(
    ('scaler', StandardScaler()),
    ('kmeans', KMeans(n_clusters=3, random_state=42))
)
```

```python
# 拟合并预测聚类
df['Cluster'] = pipeline.fit_predict(df[['Salary', 'Experience']])
```

这个紧凑的流水线按顺序处理缩放和聚类。它确保数据在聚类之前始终以相同的方式进行预处理，增强了可重复性并消除了手动步骤。

## AI 工具辅助

GitHub Copilot 和 ChatGPT 等 AI 工具通过简化实现、推广最佳实践以及支持部署就绪方案，加强了聚类工作流：

### GitHub Copilot
GitHub Copilot 通过推荐最佳实践、选择相关数据子集以及最小化编码错误，提高了 k-means 聚类工作流的可靠性和效率：

- 建议最佳的步骤顺序，例如在 k-means 之前应用 `StandardScaler`（因为 k-means 对特征尺度敏感）。
- 识别何时选择特定的 DataFrame 列，并在正确的子集上自动补全 `.fit_predict()`。
- 帮助类型转换和形状验证，减少常见错误的概率。

### ChatGPT
ChatGPT 通过建议增强方案并引导预处理和模型持久化的最佳实践，支持流水线的优化和部署的就绪性：

- 鼓励扩展流水线，包括：
  - 在聚类之前加入如 PCA 之类的降维步骤。
  - 用于编码或特征工程的自定义预处理转换器 `Transformers`。

- 提供用于部署的模型持久化指导。

以下代码将聚类流水线保存到文件中，以便日后在部署场景中运行：

```python
import joblib
joblib.dump(pipeline, 'clustering_pipeline.pkl')
```

这使得流水线可以被保存并在以后重用，无论是在批处理作业、Web 应用还是已部署的机器学习服务中。

> **ChatGPT 提示：** 使用 joblib 对调优后的流水线进行序列化。对于 Web 部署，在 API 初始化期间加载流水线，以保持跨环境聚类逻辑的一致性。

通过将聚类嵌入流水线中并使用 AI 工具来简化、扩展和部署它们，开发者可以从一次性的实验转向稳健、可维护且可扩展的生产级聚类解决方案。

# 将聚类与下游应用结合

聚类不仅仅是一项孤立的任务；它通常是广泛现实世界应用的策略性推动因素。一旦识别出有意义的聚类，它们就可以作为更有针对性的系统的输入，提供远超初始分析的价值。

一些常见的下游应用包括：

- **推荐系统**：根据偏好、行为或人口统计数据对用户进行分组，可以在电子商务、流媒体和社交媒体中实现个性化的推荐。
- **异常检测**：通过识别正常行为的密集聚类，标记出异常（例如在 `DBSCAN` 中），这对欺诈检测、网络安全或故障监控至关重要。
- **精准营销**：根据消费行为、位置或参与度进行聚类，可以帮助设计转化率更高的营销活动。

## 聚类的 AI 工具支持

GitHub Copilot 和 ChatGPT 等 AI 助手通过以下方式弥合聚类结果与决策决策之间的差距：

- **聚类解释与标记**：为了使聚类结果更具操作性，ChatGPT 通过分析底层模式来协助分配有意义的标签：
  - ChatGPT 可以建议使用以下策略标记聚类：
    - 中心分析（例如，根据收入和支出将聚类标记为高价值客户）。
    - 用于解释标签的特征分布。

- **沟通与可视化**：为了有效地展示聚类结果，Copilot 和 ChatGPT 都支持创建清晰的可视化结果和摘要：
  - Copilot 帮助为非技术利益相关者生成图表。
  - ChatGPT 推荐易读的可视化方案，如标注点图、摘要表或通过 Streamlit 或 Plotly 的交互式仪表板。

- **伦理考量**：为了促进负责任且公平地使用聚类，ChatGPT 就数据细分和标记中的伦理问题提供了重要的指导：
  - ChatGPT 提供了负责任聚类的指导，包括：
    - 避免自动分割中的偏差（例如排除性别或种族等敏感属性）。
    - 确保定义和使用分组的透明度。
    - 谨慎处理自动标记以防止刻板印象或不公平的目标。

> **ChatGPT Insight**：始终与领域专家验证聚类结果，特别是当聚类用于驱动影响人们获取、定价或体验的现实决策时。

通过将聚类见解与下游场景相结合，并使用 AI 工具进行解释、可视化和伦理对齐，数据团队可以确保他们的模型是准确、有效、透明且符合用户需求的。

# ML 项目数据预处理与聚类的案例

掌握数据预处理和聚类背后的理论和工具是重要的，但这些技术的真正价值在于它们在现实中的应用。在本章的最后部分，我们将通过实际案例将这些概念具体化，突出预处理和聚类如何应用于各个领域的机器学习项目。

这些示例不仅展示了有效的技术执行，还展示了 GitHub Copilot 和 ChatGPT 等 AI 辅助编程工具如何增强工作流的每个阶段，从清理混乱的数据集到使结果具有操作性。

## 零售连锁客户聚类

为了演示 AI 辅助工具在 ML 工作流中的实际影响，让我们探索一个真实的案例，在该案例中 GitHub Copilot 和 ChatGPT 协作简化并增强了客户聚类任务。该项目重点关注理解客户行为，以实现更个性化的营销策略。

- **目标**: 根据购买行为对客户进行细分，以支持有针对性的营销策略并提高活动有效性。
- **数据集**: 为了支持客户细分，本次分析使用了商场客户数据集 `Mall Customer Dataset`，这是一个包含零售客户关键人口统计数据和行为细节的公共数据集：
  - **特征**: 该数据集包含以下用于聚类的几类关键属性：
    - 年龄
    - 年收入
    - 消费评分
  - **来源**: 商场客户数据集（公开可用）
- **预处理步骤**: 为了为有效的聚类准备数据，应用了以下预处理步骤：
  - **缺失值填补**: ChatGPT 建议按年龄段分组，使用基于中数的策略填充“年收入”列中的缺失值，以保持人口统计数据的完整性。
  - **特征缩放**: GitHub Copilot 建议在流水中集成 `StandardScaler()`，以确保 k-means 聚类不会受到特征尺度差异的偏。
- **聚类方法**: 聚类过程由算法技术和 AI 驱动工具的组合指导，概述如下：
  - **算法**: K-means 聚类
  - **工具支持**: 利用了以下 AI 工具来简化聚类工作流并增强模型的可解释性：
    GitHub Copilot 协助编写了完整的流水线，包括特征缩放、模型拟合以及使用 Seaborn 进行可视化。
    ChatGPT 被用于策略调优和解释。
- **AI 提示词**: 如何确定客户聚类的最佳 k 值？
- **ChatGPT 响应**: 使用肘部法 `Elbow Method` 可视化不同聚类数量下的惯性量 `inertia`，并使用轮廓系数 `Silhouette Scores` 验证选择，以评估分离质量。
- **结果**: 该分析成功识别了四个不同的客户群体：
  - 高消费群体：高收入和高消费评分。
  - 预算敏感型：低收入、中低水平消费者。
  - 偶尔购买者：中等收入，消费行为不一致。
  - 低频率购物者：活跃度低，有偶发性购买。

这些细分群体被用于开发定制化的营销活动，从而实现了更好的参与度和更有效的客户触达预算分配。

--------------------------------

## 员工流失风险分析

为了展示 AI 工具在揭示员工相关洞察方面的强大能力，本案例研究重点介绍了如何在无监督学习场景下利用 GitHub Copilot 和 ChatGPT 来识别组织内部潜在的员工流失风险。其目标是通过数据驱动的聚类，主动支持 HR 团队提高员工留存率。让我们来看这个案例研究：

**目标**: 通过将员工分为行为和薪酬类簇来识别潜在的流失风险，使 HR 团队能够采取主动的留存措施。

**数据集**: 为了执行无监督聚类，分析使用了一个包含关键员工相关属性的数据集：

**特征**: 数据集包含以下作为聚类基础的特征：

- 经验
- 薪资
- 培训小时数

**输出**: 无标签（应用了无监督聚类）。

**预处理**: 为了确保数据集适用于聚类，实施了以下预处理步骤：

**标准化**: GitHub Copilot 建议使用 **StandardScaler** 进行列级归一化，在聚类之前将数值特征转换到共同尺度。

**类别编码**: ChatGPT 建议使用 `pd.get_dummies()` 并设置 `drop_first=True` 对“部门” `Department` 列进行编码，在减少冗余的同时为 `DBSCAN` 准备数据。

**聚类**: 聚类算法和原理是根据数据性质和分析特定目标选择的：

**算法**: `DBSCAN`

**理由**: 考虑到员工队伍中非均匀的行为模式，选择 `DBSCAN` 是因为其能够：

- 处理具有不同形状和密度的类簇。
- 检测离群值：这对于识别高风险个体至关重要。
- **AI 提示词**: 如何在 `DBSCAN` 中设置 `eps` 和 `min_samples`？
- **ChatGPT 洞察**: 使用 k-距离图 `k-distance graph` 视觉上识别“肘部点”，这暗示了 `eps` 的合适值。
- **结果**: 聚类发现了一小部分离群值，主要是具有以下特征的员工：
