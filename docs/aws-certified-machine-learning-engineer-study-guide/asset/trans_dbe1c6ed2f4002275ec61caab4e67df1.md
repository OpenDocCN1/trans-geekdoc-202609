

```python
import os
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
from sklearn.datasets import load_iris
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

# 定义输出目录和文件路径
output_dir = './ch04/images'
output_file = os.path.join(output_dir, 'kmeans_iris_3d_plot.png')

# 如果输出目录不存在则创建
os.makedirs(output_dir, exist_ok=True)

# 加载鸢尾花数据集
iris = load_iris()
data = iris.data[:, [0, 2, 3]]
labels = iris.target
feature_names = ['sepal length (cm)', 'petal length (cm)', 'petal width (cm)']

# 标准化特征
scaler = StandardScaler()
scaled_data = scaler.fit_transform(data)

# 执行 K-Means 聚类
kmeans = KMeans(n_clusters=3, random_state=42)
kmeans.fit(scaled_data)
clusters = kmeans.labels_

# 在 3D 中绘制聚类结果
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection='3d')

# 定义颜色和标记
colors = ['blue', 'orange', 'purple']
markers = ['o', 's', 'D']

# 使用不同的颜色和标记绘制每个簇
for cluster in np.unique(clusters):
    ax.scatter(scaled_data[clusters == cluster, 0],
               scaled_data[clusters == cluster, 1],
               scaled_data[clusters == cluster, 2],
               c=colors[cluster],
               marker=markers[cluster],
               label=f'Cluster {cluster+1}',
               edgecolor='black')

# 使用星形标记绘制质心
centroids = kmeans.cluster_centers_
for i, centroid in enumerate(centroids):
    ax.scatter(centroid[0], centroid[1], centroid[2],
               s=300,
               c='yellow',
               marker='*',
               edgecolor='black',
               linewidths=2,
               label=f'Centroid {i+1}')

ax.set_xlabel('Standardized Sepal Length (cm)')
ax.set_ylabel('Standardized Petal Length (cm)')
ax.set_zlabel('Standardized Petal Width (cm)')
ax.legend()
ax.set_title('K-Means Clustering of Iris Dataset (3D)')

# 将绘图保存到指定文件路径
plt.savefig(output_file)

# 显示确认绘图已保存的消息
print(f"Plot has been saved as '{output_file}'")
```

在提供的代码中，语句`clusters = kmeans.labels_`将计算出的标签赋值给`clusters`变量，随后该变量用于根据数据点的簇成员身份在绘图中对其着色和分组。

属性`kmeans.labels_`返回一个整数标签数组，表示每个数据点所属的簇。这发生在语句`kmeans.fit(scaled_data)`使用 K-means 算法拟合训练数据集之后。本质上，语句`clusters = kmeans.labels_`为数据集中的每个数据点分配一个簇标签，显示该数据点根据聚类算法结果被分入了哪个簇。

回顾一下，方法`kmeans.fit()`在训练数据上训练 K-means 模型，而属性`kmeans.labels_`返回训练数据的簇标签，方法`kmeans.predict()`则预测新的、未见过的数据点的簇标签。

现在你已经理解了代码的工作原理，可以在[图 4.17](#c004.xhtml#c04-fig-17)中看到这三个簇。鸢尾花数据集 K-means 聚类的三维图有效地说明了基于三个标准化特征（萼片长度、花瓣长度和花瓣宽度）的数据点分组。该图使用不同的形状区分三个簇，突出了它们在特征空间中的空间分离。每个簇的质心以较大的黄色星形标记显著显示，使其易于识别。该可视化清晰直观地展示了 K-means 算法如何将鸢尾花数据集分割成三个不同的组，反映了不同鸢尾花种类的自然聚类。

![图 4.17 鸢尾花数据集的 3D K-means 聚类。](images/c04f017.png)

[图 4.17](#c004.xhtml#rc04-fig-17) 鸢尾花数据集的 3D K-means 聚类。

要使用 Amazon SageMaker 中的内置 K-means 算法，可以遵循以下步骤。首先，设置 Amazon SageMaker 会话并指定 K-means 算法容器。然后，创建 K-means 估算器，指定簇的数量，并在数据上拟合模型。最后，将训练好的估算器部署到端点以进行推理。以下代码片段展示了一个简短示例：

```python
import sagemaker
from sagemaker import get_execution_role
from sklearn.preprocessing import StandardScaler

# 设置 SageMaker 会话和角色
sagemaker_session = sagemaker.Session()
role = get_execution_role()

# 指定 K-Means 算法容器
container = sagemaker.image_uris.retrieve(
    'kmeans',
    sagemaker_session.boto_region_name
)

# 创建 KMeans 估算器
kmeans = sagemaker.estimator.Estimator(
    container,
    role,
    instance_count=1,
    instance_type='ml.m4.xlarge',
    output_path='s3://your-bucket/path-to-output',
    sagemaker_session=sagemaker_session
)

# 指定簇的数量
kmeans.set_hyperparameters(k=3)

# 在存储于 S3 中的数据上拟合模型
kmeans.fit({'train': 's3://your-bucket/path-to-train-data'})

# 训练完成后，可将模型部署到端点以进行推理
predictor = kmeans.deploy(
    initial_instance_count=1,
    instance_type='ml.m4.xlarge'
)

# 使用预测器对新数据进行预测
new_data = [[5.1, 3.5, 1.4, 0.2], [6.2, 3.4, 5.4, 2.3]]
scaler = StandardScaler()
scaled_new_data = scaler.transform(new_data)  # 确保新数据已标准化

# 进行预测
predicted_clusters = predictor.predict(scaled_new_data)
print(predicted_clusters)
```

### 使用场景

K-means 最适合你清楚预期在数据集中发现的簇数量的场景。该算法能根据特征相似性高效地将数据集划分为互不重叠的不同组。它在特征空间中簇分离良好且呈球形的场景中表现出色。客户细分、市场篮子分析、图像压缩和异常检测等应用非常适合 K-means，因为该算法能高效处理大型数据集，并随样本数量增加而良好扩展。当输入数据主要为数值型且结构相对良好时，K-means 可以提供有洞察力且可操作的分组。

如果数据不符合球形和等大小簇的假设，或者你要检测的簇形状和密度各异，请避免使用 K-means。K-means 对异常值敏感，因此如果数据包含显著异常，这些异常可能会扭曲结果并导致聚类效果不佳。此外，K-means 需要预定义簇的数量（`k`），如果没有数据结构的先验知识，这可能难以确定。如果数据集包含非数值特征，或者你需要一种能处理任意簇形状和密度的更灵活聚类方法（如带有噪声的基于密度的空间聚类应用 [DBSCAN] 或层次聚类），K-means 可能不是最佳选择。

#### 降维

