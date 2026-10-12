

Python 代码由导入所需包的代码组成。函数 `get_args` 包含需要调优的超参数，超参数将作为参数传递。在本练习中，我们考虑五个用于调优的超参数；它们是：

*   `n_estimator`
*   `max_depth`
*   `min_samples_split`
*   `min_samples_leaf`
*   `max_features`

`max_features` 接受字符串值作为输入，而所有其他超参数接受整数值。

函数 `preprocess_data` 读取文件，应用基本转换，并返回拆分后的数据。主函数构建模型，启动模型的超参数调优，并将模型保存到云存储。

[镜像创建](#contents.xhtml#sc2_101a)

现在我们已经完成了用于模型构建的 Dockerfile 和 Python 代码的创建，可以继续进行镜像创建。请按照给定的步骤操作。

### 步骤 1：使用 docker build 创建镜像

在终端中输入以下命令，如 [图 5.9](#ch05.xhtml#fig5-9) 所示，以创建镜像：

```
PROJECT_ID=vertex-ai-gcp-1
IMAGE_URL="gcr.io/$PROJECT_ID/eye:v1"
docker build ./ -t $IMAGE_URL
```

![](images/Figure_5.9.png)

图 5.9：镜像创建过程

从 Dockerfile 构建镜像将需要几分钟。构建完成后，终端中将显示成功消息，如 [图 5.10](#ch05.xhtml#fig5-10) 所示（要点 1）。

### 步骤 2：将 Docker 镜像推送到容器注册表

镜像创建完成后（可以在 [图 5.10](#ch05.xhtml#fig5-10) 中看到镜像创建的成功消息），输入以下命令将镜像推送到容器注册表：

```
docker push $IMAGE_URL
```

请参考下图：

![](images/Figure_5.10.png)

图 5.10：镜像推送到项目容器注册表

该镜像将在项目的容器注册表中可用（要检查，请遵循上一章中描述的步骤）。

[提交自定义模型训练作业](#contents.xhtml#sc2_102a)

带有超参数调优的自定义模型训练步骤与上一章描述的步骤非常相似，不同之处在于我们将启用超参数调优选项。请按照给定的步骤提交训练作业。

### 步骤 1：Vertex AI 的训练模块

打开 Vertex AI 的训练模块，如 [图 5.11](#ch05.xhtml#fig5-11) 所示：

![](images/Figure_5.11.png)

图 5.11：Vertex AI 的训练模块

1.  选择训练模块。
2.  选择 **HYPERPARAMETER TUNING JOBS**（超参数调优作业）。
3.  点击 **CREATE**（创建）。

### 步骤 2：选择训练方法

将出现“训练新模型”页面，如 [图 5.12](#ch05.xhtml#fig5-12) 所示：

![](images/Figure_5.12.png)

图 5.12：自定义模型的训练方法选择

按照相应的要点配置训练方法：

1.  选择训练方法。
2.  在数据集选择下选择 **No managed dataset**（无托管数据集）。
3.  选择 **Custom Training**（自定义训练）。
4.  点击 **Continue**（继续）。

### 步骤 3：模型详情

选择模型详情以训练模型，如 [图 5.13](#ch05.xhtml#fig5-13) 所示：

![](images/Figure_5.13.png)

图 5.13：自定义模型的模型详情

按照相应的要点操作：

1.  选择训练方法后，我们需要输入模型详情。
2.  选择 **Train new model**（训练新模型）。
3.  为模型提供名称。
4.  选择与计算关联的服务账号（用户也可以选择我们在 [第 2 章](#ch02.xhtml)《Vertex AI 和 AutoML 表格简介》中创建的服务账号，但需要添加访问云存储的角色）。
5.  向下滚动并点击 **Continue**（继续）。

### 步骤 4：训练容器详情

按照 [图 5.14](#ch05.xhtml#fig5-14) 中的数字及其相应要点配置训练容器：

![](images/Figure_5.14.png)

图 5.14：自定义模型的容器详情

按照相应的要点操作：

1.  选择模型详情后，我们需要输入训练容器详情。
2.  选择 **Custom container**（自定义容器）。
3.  浏览已推送到容器注册表的容器镜像。
4.  选择用于存储模型工件的云存储存储桶（因为我们已经在代码中选择了存储桶，此处可以留空）。
5.  点击 **Continue**（继续）。

### 步骤 5：超参数调优

下一步是配置超参数。按照相应步骤为模型训练启用并配置超参数调优，如 [图 5.15](#ch05.xhtml#fig5-15) 所示：

![](images/Figure_5.15.png)

图 5.15：配置超参数调优

按照相应的要点操作：

1.  选择训练容器后，可以在超参数中配置可选设置。
2.  选择 **Enable hyperparameter tuning**（启用超参数调优）选项。
3.  提供参数名称（需要将我们在代码中包含的 5 个参数单独添加）。
4.  选择为超参数提供的输入类型。支持的超参数类型有 categorical（分类）、discrete（离散）、double（双精度）和 integer（整数）。为 `n_estimator` 选择 **integer**（整数）。
5.  提供值，如 [图 5.15](#ch05.xhtml#fig5-15) 所示（此选项随类型变化）。
6.  选择 **No scaling**（无缩放）选项（支持 linear、log 和 reverse log 缩放）。
7.  点击 **Done**（完成）（五个超参数中的一个已添加）。
8.  点击 **Add new parameter**（添加新参数）以添加其他参数的详情。

请参考表 5.1 并添加其余四个参数的详情：

| 参数名称 | 类型 | 值 | 缩放 |
| :--- | :--- | :--- | :--- |
| `max_depth` | Discrete（离散） | 5,10,15,20 | No scaling（无缩放） |
| `min_samples_split` | Discrete（离散） | 5,10 | No scaling（无缩放） |
| `min_samples_leaf` | Discrete（离散） | 5,10 | No scaling（无缩放） |
| `max_features` | Categorical（分类） | auto, sqrt | N/A |

表 5.1：超参数列表

如有需要，将 `max_depth`、`min_samples_split` 和 `min_samples_leaf` 的类型更改为 integer（整数）以查看其他选项。请参考 [图 5.16](#ch05.xhtml#fig5-16)：

![](images/Figure_5.16.png)

图 5.16：配置超参数调优的其他参数

请参考相应步骤完成超参数配置：

1.  所有添加的参数将被列出。
2.  在代码中我们优化的是准确率指标（最大化），输入 **accuracy**（准确率）。
3.  目标是最大化准确率。
4.  最大试验次数保持为低至 2 次，因为模型非常简单。
5.  最大并行试验次数保持为 1，原因相同。
6.  在 Algorithm（算法）下，选择 **Default**（默认）（也可以选择 random search 或 grid search）。不同算法的解释如下：
    *   **Random search**（随机搜索）：对可实现区域进行直接的随机搜索。
    *   **Unspecified algorithm**（未指定算法）：不指定算法。Vertex AI 会在高斯过程带状搜索、线性组合搜索或其变体之间进行选择。
    *   **Grid search**（网格搜索）：一种可行的网格搜索。如果用户希望指定的试验次数多于可行点，这一点很重要。如果未指定网格搜索，Vertex AI 可能会创建重复选项。
7.  点击 **CONTINUE**（继续）。

> **注意**：GCP 限制了免费账号的训练 CPU。请尽量将最大试验次数和并行试验次数保持较低。如果遇到配额指标超限等错误，请尝试降低这两个参数的值。

### 步骤 6：计算和定价

下一步是提供计算和定价详情。请参考 [图 5.17](#ch05.xhtml#fig5-17)：

![](images/Figure_5.17.png)

图 5.17：自定义模型的计算和定价

按照相应步骤选择用于训练的机器类型：

1.  选择 **Compute and pricing**（计算和定价）。
2.  选择模型训练发生的 Region（区域）。
3.  选择用于模型训练的 Machine type（机器类型）（根据模型训练的复杂程度选择机器类型）。
4.  Acceleration type（加速器类型）为可选，可用于复杂的模型训练。

