
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import load_iris
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA
from sklearn.cluster import KMeans
from mpl_toolkits.mplot3d import Axes3D
import os

######## Create the output directory if it doesn't exist
output_dir = './ch04/images'
os.makedirs(output_dir, exist_ok=True)

######## Load the Iris dataset
iris = load_iris()
data = iris.data

######## Scale the data
scaler = StandardScaler()
scaled_data = scaler.fit_transform(data)

######## Apply PCA to reduce to 3 dimensions
pca_3d = PCA(n_components=3)
pca_data_3d = pca_3d.fit_transform(scaled_data)

######## Apply K-Means clustering
kmeans = KMeans(n_clusters=3, random_state=42)
kmeans.fit(pca_data_3d)
cluster_assignments_3d = kmeans.predict(pca_data_3d)
centroids_3d = kmeans.cluster_centers_

######## Plotting the results in 3D
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection='3d')

######## Define colors and markers
colors = ['blue', 'orange', 'purple']
markers = ['o', 's', 'D']

######## Plot each cluster with different color and marker
for cluster in np.unique(cluster_assignments_3d):
    ax.scatter(pca_data_3d[cluster_assignments_3d == cluster, 0],
               pca_data_3d[cluster_assignments_3d == cluster, 1],
               pca_data_3d[cluster_assignments_3d == cluster, 2],
               c=colors[cluster],
               marker=markers[cluster],
               label=f'Cluster {cluster + 1}',
               edgecolor='black')

######## Plot centroids with yellow stars and enumerate them
for i, centroid in enumerate(centroids_3d):
    ax.scatter(centroid[0], centroid[1], centroid[2],
               s=300, c='yellow', marker='*',
               edgecolor='black', label=f'Centroid {i + 1}')
    ax.text(centroid[0], centroid[1], centroid[2], f'C{i + 1}',
            color='black', fontsize=12, ha='center', va='center')

ax.set_xlabel('Principal Component 1')
ax.set_ylabel('Principal Component 2')
ax.set_zlabel('Principal Component 3')
ax.legend()
ax.set_title('3D K-Means Clustering of Iris Dataset Using PCA')

######## Save the plot to the specified file path
plt.savefig(os.path.join(output_dir, 'pca_kmeans_iris_plot_3d.png'))
plt.close()
print(f"3D plot has been saved in '{output_dir}' as 'pca_kmeans_iris_plot_3d.png'")
```

我在 Amazon SageMaker Studio 中运行了此程序；图 4.18 显示了生成的图像，展示了使用 PCA 降维后的鸢尾花数据集的 3D K-means 聚类结果及高亮显示的质心。

![图 4.18 使用 PCA 的鸢尾花数据集 3D K-means 聚类。](img/c04f018.png)

图 4.18 使用 PCA 的鸢尾花数据集 3D K-means 聚类。

该图显示了三个截然不同的簇，每个簇用不同的形状表示：

*   簇 1：圆圈
*   簇 2：正方形
*   簇 3：菱形

3D 图的坐标轴代表从 `PCA` 算法得出的三个主成分（`PC1`、`PC2` 和 `PC3`）。这些成分捕获了数据集中的最大方差，在保留其基本结构的同时有效降低了维度。

每个簇的质心以星号突出显示，并枚举为 `C1`、`C2` 和 `C3`。这些质心代表每个簇的中心点，为每组内数据点的典型特征提供了参考。

3D 图中簇的空间分离展示了 `PCA` 降维和 K-means 识别数据中不同群组的有效性。簇之间的清晰区分表明，鸢尾花的特征可由所选主成分很好地表示。

Amazon SageMaker 提供了高度可扩展且高效的 `PCA` 实现，可轻松处理大型数据集。要在 Amazon SageMaker 中使用 `PCA`，首先创建一个 `PCA` 估算器对象，指定要保留的成分数量。然后将估算器拟合到您的数据集，这涉及计算主成分并将原始数据转换为新的低维空间。Amazon SageMaker 的 `PCA` 算法支持稀疏和稠密数据格式，使其适用于各种类型的数据预处理任务。

`PCA` 模型训练完成后，您可以将其作为端点部署在 Amazon SageMaker 中以实时转换新数据，或将其用于大型数据集的批量转换。这使其能无缝集成到您的机器学习工作流中，支持实时或大规模预处理数据。此外，Amazon SageMaker 与其他 AWS 服务（如用于数据存储的 Amazon S3 和用于开发的 Amazon SageMaker Studio）的集成，为开发、测试和部署 `PCA` 模型提供了全面的环境。通过利用 Amazon SageMaker 的内置 `PCA` 算法，数据科学家和机器学习工程师可以高效地降低维度、提高模型性能并简化数据处理管道。

以下 Python 代码片段展示了如何将 `PCA` 与 Amazon SageMaker 结合使用的示例：

```python
import pandas as pd
import boto3
import sagemaker
from sagemaker import get_execution_role
import os

######## 初始化 SageMaker 会话
sagemaker_session = sagemaker.Session()

######## 获取执行角色
role = get_execution_role()

######## 加载鸢尾花数据集
from sklearn.datasets import load_iris
iris = load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)

######## 将 DataFrame 保存为 CSV 文件
data_csv = 'iris.csv'
df.to_csv(data_csv, index=False, header=False)

######## 将 CSV 文件上传到 S3
s3_bucket = sagemaker_session.default_bucket()
s3_data_path = f's3://{s3_bucket}/pca/iris.csv'
boto3.Session().resource('s3').Bucket(s3_bucket).Object('pca/iris.csv').upload_file(data_csv)

######## 获取 PCA 容器镜像 URI
pca_image_uri = sagemaker.image_uris.retrieve(
    'pca',
    boto3.Session().region_name
)

######## 创建 PCA 估算器
pca = sagemaker.estimator.Estimator(
    image_uri=pca_image_uri,
    role=role,
    instance_count=1,
    instance_type='ml.m4.xlarge',
    output_path=f's3://{s3_bucket}/pca/output'
)

######## 设置 PCA 超参数
pca.set_hyperparameters(
    feature_dim=4,
    num_components=3,
    subtract_mean=True,
    algorithm_mode='regular'
)

######## 训练 PCA 模型
pca.fit({'train': s3_data_path})

######## 部署 PCA 模型
pca_transformer = pca.transformer(
    instance_count=1,
    instance_type='ml.m4.xlarge',
    strategy='SingleRecord'
)

######## 执行转换
transformed_output = pca_transformer.transform(
    data=s3_data_path,
    content_type='text/csv',
    split_type='Line'
)

transformed_output.wait()

######## 下载并查看转换后的数据
transformed_output_path = transformed_output.output_path
transformed_data = pd.read_csv(transformed_output_path + '/train.csv.out', header=None)
print(transformed_data.head())
```

您将分别在第 5 章、第 6 章和第 7 章中了解更多关于超参数调优、模型部署和模型监控的内容。

## 用例

PCA 在需要降低数据维度以提高分析和建模效率的场景中非常有用。它在处理特征间存在多重共线性（高相关性）这一问题的高维数据集时尤为有效。通过将数据转换为一组新的正交成分，PCA 有助于在减少变量数量的同时保留最显著的方差。常见用例包括图像压缩，PCA 可在不显著损失质量的情况下减少表示图像所需的像素数量；以及探索性数据分析，它通过将复杂数据集投影到低维空间来帮助可视化。此外，PCA 还用于为 ML 模型预处理数据，通过减少噪声和过拟合风险来提升性能。

然而，PCA 不应被随意使用。一个局限性是它假设变量间存在线性关系，这可能无法捕捉具有非线性交互的数据中的复杂性。它也不适用于方差不是重要性适当度量的数据集，因为 PCA 优先考虑方差较大的特征，可能会丢弃较小但至关重要的方差。此外，主成分的可解释性可能具有挑战性，因为它们是原始特征的组合，可能没有清晰、直观的含义。因此，尽管 PCA 是降维的强大工具，但在应用它之前，必须考虑数据的性质和分析的具体要求。

## 主题建模

主题建模被认为是一种无监督 ML 技术，因为它不需要标记数据即可识别文档集合中的模式或主题。与在输入-输出对上训练模型以预测特定结果的监督学习不同，LDA 和 NTM 等主题建模算法探索数据的内在结构。它们旨在发现能最好地代表文档语义的潜在主题，纯粹基于词共现模式，无需任何先验知识或标注。这使得主题建模对于探索和理解大型非结构化文本数据集极具价值，使用户能够在无需预标记训练数据的情况下发掘隐藏的主题和洞见。

打个比方，可以将主题建模想象为类似于聚类。正如聚类算法根据相似性对数据点进行分组，主题建模算法根据文档的潜在主题对文档进行分组。通过识别文本中的模式和关系，这些算法可以将文档归类为不同的主题，从而更容易管理和理解大量文本数据。

Amazon SageMaker 开箱即提供 LDA 和 NTM，使用户无需具备深度学习方面的专业知识，即可轻松实现和扩展其主题建模解决方案。

### 隐含狄利克雷分布

LDA 是一种用于识别大型文本语料库中主题的生成概率模型。它假设每个文档都是主题的混合体，而每个主题都是词的混合体。“Dirichlet”（狄利克雷）这个名字源于狄利克雷分布，这是一种在 LDA 中至关重要的概率分布。狄利克雷分布用于建模文档中不同主题概率的不确定性。它本质上提供了一种为文档中的各个主题分配概率的方法，确保这些概率之和为一。该分布有助于确定每个文档中不同主题的比例，使 LDA 能够发掘文本的潜在主题结构。狄利克雷分布的形状由一组参数（称为 `concentration parameters`）控制，这些参数可以调整以影响概率质量在不同主题间的分布。通过迭代更新文档上的主题分布和主题上的词分布，LDA 可以识别出最能代表文本语义的有意义主题。

在 AWS 中，可以通过 Amazon SageMaker 高效地使用 LDA，后者提供了用于主题建模的内置 LDA 算法。要在 Amazon SageMaker 中使用 LDA，首先需要准备文本数据并将其上传到 Amazon S3 存储桶（或 Amazon EFS 或 Amazon FSx for Lustre）。接下来，通过指定主题数量和其他超参数来创建 LDA 估算器。Amazon SageMaker 会负责训练过程，利用其可扩展的基础设施来处理大型数据集和计算密集型任务。模型训练完成后，您可以使用它来转换新文档，从而深入了解其主题分布。这种能力对于文档聚类、内容推荐和信息检索等应用特别有用，在这些应用中，理解文本的主题结构至关重要。通过将 LDA 集成到您的 AWS 工作流中，您可以利用主题建模的力量来增强数据分析和 ML 解决方案。

#### 用例

LDA 在理解大型文本语料库的主题结构至关重要的场景中非常有效。它在文档聚类、内容推荐和信息检索等应用中表现出色。例如，在新闻聚合服务中，LDA 可以帮助按政治、体育或技术等主题对文章进行分组，通过支持基于主题的浏览来改善用户体验。同样，在学术研究中，LDA 可用于分析大量研究论文，以发现随时间变化的普遍主题和趋势。通过识别每个文档内的主题分布，LDA 使企业和研究人员能够高效地从非结构化文本数据中提取洞见。

然而，由于 LDA 假设主题服从狄利克雷分布，因此存在一些局限性，可能无法捕捉词与主题之间更复杂的依赖关系。在这种情况下，NTM 便可大显身手。NTM 利用神经网络学习主题表示，从而提供更大的灵活性，并能捕捉数据中的复杂模式。这使得 NTM 对于具有强时间或序列依赖性的数据集，或词与主题之间的关系无法用狄利克雷分布良好建模的情况特别有效。通过将 NTM 纳入您的 AWS 工作流，您可以解决 LDA 的一些不足，并增强分析和理解复杂文本数据的能力，确保获得更准确、更有意义的主题表示。

### 神经主题模型

NTM 是一种先进的主题建模方法，它利用神经网络学习主题表示，相比 LDA 等传统方法，能获得更灵活、更细致的主题表示。通过利用深度学习的强大功能，NTM 可以捕捉文本数据中的复杂模式和依赖关系，使其能从海量文本中高效提取有意义的主题。与依赖狄利克雷分布来建模文档中主题概率的 LDA 不同，NTM 使用神经网络自动学习这些分布，从而为各类文本数据提供更强的适应性。这产生了更准确、更可解释的主题，对于文档聚类、内容推荐和情感分析等应用极具价值。

NTM 可使用 Amazon SageMaker 无缝实现，后者提供了 NTM 的内置算法。要在 Amazon SageMaker 中使用 NTM，您首先需要准备文本数据并将其上传到 Amazon S3 存储桶（或 Amazon EFS 或 Amazon FSx for Lustre）。接下来，通过指定必要的超参数和训练配置，在 Amazon SageMaker 中创建 NTM 估算器。Amazon SageMaker 可扩展的基础设施可处理训练 NTM 算法的计算需求，使其适用于大型数据集。模型训练完成后，可用于转换新文档并生成主题分布，从而为文本数据的主题结构提供有价值的见解。此功能使企业能够高效分析和理解其文本数据，从而做出数据驱动的决策并增强其 ML 工作流。通过将 NTM 集成到您的 AWS 环境中，您可以利用神经网络的优势，从复杂的文本数据中发掘更深层的见解。

### 使用案例
