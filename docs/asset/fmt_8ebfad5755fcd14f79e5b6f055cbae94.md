
在 Azure Machine Learning 中，你可以将计算实例挂载到你的 Jupyter notebook 以运行训练作业。这提供了独立于本地机器的可扩展计算资源。以下代码显示了如何连接到你的 Azure ML 工作区、创建或挂载现有的计算实例（如虚拟机），并对其进行模型配置。

点击此处查看代码图像

```python
from azure.ai.ml import MLClient
from azure.identity import DefaultAzureCredential

## 连接到你的 Azure ML 工作区
credential = DefaultAzureCredential()
ml_client = MLClient.from_config(credential)

## 创建或挂载现有的计算实例
compute_name = "my-compute-instance"
if compute_name not in ml_client.compute.list():

    # 定义计算配置
    compute_config = AmlCompute.provisioning_configuration(vm_size="STANDARD_D2_V2",
max_nodes=4)
     compute = ComputeTarget.create(ml_client.workspace, compute_name, compute_config)
    compute.wait_for_completion(show_output=True)
else:
      compute = ml_client.compute.get(compute_name)
```

### 在 notebook 中准备训练数据

在训练模型之前，你必须加载并预处理你的数据。这通常涉及数据清洗、特征工程以及将数据分为训练集和测试集。以下代码使用 Pandas 将数据分为训练集和测试集，然后对特征进行扩展，展示了准备模型训练数据的简单示例。

点击此处查看代码图像

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

## 加载数据
df = pd.read_csv('path/to/your/data.csv')

## 预处理数据

df.dropna(inplace=True)
df = pd.get_dummies(df, drop_first=True)
## 将数据分为特征和目标
X = df.drop('target_column', axis=1)
y = df['target_column']

## 将数据分为训练集和测试集
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2,
random_state=42)

# 缩特征
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

在准备好数据后，你可以定义并训练你的机器学习模型。在这个示例中，我们将使用来自 scikit-learn 的 `RandomForestClassifier`：

点击此处查看代码图像

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

## 定义模型
model = RandomForestClassifier(n_estimators=100, random_state=42)

## 训练模型
model.fit(X_train, y_train)
```

在这个示例中，我们展示了如何在 Azure Machine Learning 的 Jupyter notebook 中挂载计算实例、准备数据并训练模型。这种设置允许你利用云计算资源在更大规模的数据集上训练更复杂的模型。这是一个非常简单的示例；在本章的最后部分，我们将提供一个更真实的模型训练场景。

#### 使用 MLflow 跟踪模型训练

数据科学家利用 notebook 的功能作为模型实验和训练不可或缺的工具。为了有效管理大量的模型训练结果，将它们组织成实验（experiments）变得至关重要。MLflow 成为这一过程中的关键促进者，提供了强大的日志记录功能，可以在 notebook 环境中无缝跟踪模型指标。MLflow 是什么？MLflow 是一个用于跟踪实验和存储模型等构制品（artifacts）的开源框架。它有一个强大的工具叫做模型注册表（model registry），允许你不仅可以跟踪实验中的指标、参数和模型，还可以在它们符合你的解决方案的需求时查询注册表并共享模型进行部署。

创建一个 MLflow 实验是结构化模型管理的第一步。通过在实验内分组运行（runs），数据科学家可以在工作流中获得更高的清晰度和组织性。MLflow 通过允许为特定项目创建自定义实验，简化了这项任务，确保模型训练结果能够被整齐地分类以便分析。

设置好实验后，使用 MLflow 记录结果是下一个重点。在这里，数据科学家可以使用自动记录，也可以根据项目需求选择手动记录。自动记录是 MLflow 支持的一项功能，可以自动跟踪常用库的指标、参数、构制品和模型。这简化了记录过程。模型训练完成后，数据科学家可以轻松地在 MLflow 环境中查看记录的指标，便于分析和决策。下面的代码显示了如何在 notebook 中使用 MLflow 进行自动记录，图 2-17 显示了输出。

```python
from xgboost import XGBClassifier
with mlflow.start_run():
     mlflow.xgboost.autolog()
     model = XGBClassifier(use_label_encoder=False, eval_metric="logloss")
    model.fit(X_train, y_train, eval_set=[(X_test, y_test)], verbose=False)
```

![图 2-17 在 Jupyter notebook 中跟踪模型训练](img/02fig17.jpg)

**图 2-17** 在 Jupyter notebook 中跟踪模型训练

使用 MLflow 进行自定义记录为数据科学家提供了灵活性，允许他们手动记录自动记录无法捕获的补充或自定义信息。该功能允许对记录过程进行更精细的控制，使数据科学家能够根据特定项目需求定制记录工作。通过利用 `mlflow.log_param`、`mlflow.log_metric`、`mlflow.log_artifact` 和 `mlflow.log_model` 等常用函数，数据科学家可以分别捕捉关键参数、指标、文件和模型，增强分析深度和对模型性能的洞察。

#### 评估模型

我们可以对通过自动机器学习实验生成的模型进行评估。你可以采用一种涵盖多种指标和可视化的全面方法。首先，在完成实验后，通过 Azure Machine Learning Studio 或 Jupyter notebook 访问作业结果关重要。获取结果后，大量的分类指标有助于分析模型性能，包括准确率（accuracy）、精确率（precision）、召回率（recall）和 ROC 曲线下面积（`AUC`）。这些指标为分类效果的各个维度提供了见解，有助于就模型选择做出明智决策。此外，混淆矩阵等视觉辅助工具提供了分类错误的直观表示，而 ROC 和精确率-召回率曲线说明了模型在不同阈值下的区分能力。还可以从累积增益、提升曲线和校准曲线中获得更多见解，它们分别展示了模型识别正样本的能力、相对于随机猜测的性能以及对预测置信度的校准情况。表 2-2 显示了评估模型的常用指标。图 2-18 显示了一个模型的 ROC 曲线。

**表 2-2** 评估模型

| 指标 || 说明 |

| --- | --- |

| `AUC` | `ROC 曲线下面积` |

| --- | --- |

| Accuracy | 预测值与真实标签匹配的比例 |

| Avg. Precision | 每个召回率增加时精确率的加权平均值 |

| Balanced Accuracy | 每个类别的平均召回率 |

| F1 Score | 精确率和召回率的调和平均数 |

| Log Loss | 给定预测下真实标签的负对数似然 |

| Matthews Correlation | 平衡准确率衡量标准 |

| Precision | 避免将负样本标记为正样本 |

| Recall | 检测所有正样本 |

| Weighted Accuracy | 按类别样本量加权的准确率 |

![图 2-18 良好模型的 ROC 曲线](img/02fig18.jpg)

**图 2-18** 良好模型的 ROC 曲线

## 使用 Python SDKv2 训练模型

使用 Python SDKv2 训练模型的方法是类似的，但与使用 notebook 相比有一些不同。主要区别在于作业提交。需要提交作业，而不是在 notebook 中交互式地执行代码单元。你将训练作业提交给 Azure Machine Learning 服务。该作业负责在配置的计算资源上调度训练脚本的执行。通过提交作业，你可以跟踪训练进度，监控资源利用率，并利用分布式训练等功能提高效率和可扩展性。通过理解置信水平，你可以评估模型对其预测正确分配置信度的能力。按照以下高级步骤使用 Python SDKv2 训练模型：

1. **工作空间设置**：不是直接在 notebook 中工作，而是首先建立与你的 Azure Machine Learning 工作空间的连接。这个中心化的工作空间为管理所有机器学习资源（包括数据集、模型和实验）提供了一个结构化环境。与资源往往是分散的 notebook 不同，工作空间确保了跨项目的组织性和协作性。

2. **脚本开发**：不再直接在 notebook 中编写所有所有代码，而是创建一个专门用于训练模型的独立 Python 脚本（`main.py`）。该脚本包含用于数据预处理、模型训练和评估的函数。通过将代码分离到脚本中，你可以维护清晰且模块化的结构，与在 notebook 中工作相比，更容易测试、调试和版本控制。

3. **计算配置**：不再仅仅依赖 notebook 环境提供的计算实例，而是为运行训练作业配置特定的计算资源。这允许你根据负载需求（如 CPU 或 GPU 资源、内存和可扩展性）选择合适的计算实例或集群。通过配置专用计算资源，你可以确保大规模模型训练具有优的性能和资源利用率。

## 使用终端配置计算实例

在 Azure Machine Learning 中工作时，有时需要的不仅仅是 notebook 来完成任务。这时访问计算实例的终端就非常有用了。它就像在工作空间内直接有一个命令提示符或终端窗口。

访问终端后，你可以做几件事：

* **使用 Git 中的文件**：这意味着你可以使用存储在工作空间 Git 中的文件，而不局限于某个计算实例。

* **安装包**：有时你可能需要为工作安装额外的库或包。通过终端访问，你可以安装这些包。

* **创建额外的内核**：内核是运行代码的环境。通过创建额外的内核，你可以设置不同的环境。

要访问终端，只需进入你的机器学习 工作空间，导航到 Notebooks 部分，然后从那里打开终端。如果计算实例处于运行状态，你可以访问其附加的终端。图 2-19 显示了如何从 Notebooks 访问。

![图 2-19 访问终端](img/02fig19.jpg)

**图 2-19** 访问终端

### 技能 2.5：使用 Azure Machine Learning 调优参数

参数调优是机器学习流水线中的关键步骤。它涉及寻找能够提高模型性能的最优参数组合。Azure Machine Learning 提供了一个健壮的框架来自动化此过程。

### 选择采样方法

Azure Machine Learning 提供了多种采样空间的方法，每种方法适用于不同的场景和需求。本教程探索了 Azure ML 支持的三种主要采样方法：随机采样、网格和贝叶斯采样。

#### 随机采样

随机采样具有通用性，支持离散和连续参数。它从定义的搜索空间中随机选择值，允许终止低性能作业。这种方法对于初始的大范围搜索特别有用，随后可以关注这些区域。以下是使用 Azure ML 进行随机采样的示例：

查看代码图像

```python
from azure.ai.ml.sweep import Normal, Uniform, RandomParameterSampling
command_job_for_sweep = command_job(
    learning_rate=Normal(mu=10, sigma=3),
    keep_probability=Uniform(min_value=0.05, max_value=0.1),
    batch_size=Choice(values=[16, 32, 64, 128]),
)

sweep_job = command_job_for_sweep.sweep(
    compute="cpu-cluster",
    sampling_algorithm="random"
)
```

#### Sobol 扩展

Sobol 是一种拟随机序列，改进了搜索空间的分布并允许使用种子实现可重复性。以下是 Sobol 采样的示例：

查看代码图像

```python
from azure.ai.ml.sweep import RandomParameterSampling

sweep_job = command_job_for_sweep.sweep(
    compute="cpu-cluster",
    sampling_algorithm=RandomParameterSampling(seed=123, rule="sobol")
)
```

##### 网格采样

当能够负担起穷举搜索时，网格采样（Grid sampling）是离散超参数的选择。它对所有可能的值进行简单的网格搜索，同时也支持提前终止低性能运行。以下是使用 Azure ML 进行网格采样的示例：

点击此处查看代码图像

```python
from azure.ai.ml.sweep import Choice

command_job_for_sweep = command_job(

_size=Choice(values=[16, 32]),

number_of_hidden_layers=Choice(values=[1,2,3]),

)

sweep_job = command_job_for_sweep.sweep(

compute="cpu-cluster",
sampling_algorithm="grid"
)
```

### 贝叶斯采样

该方法基于贝叶斯优化，根据以往样本的性能选择样本，以持续改进主要指标。适用于有足够预算充分探索超参数空间的场景。以下是使用 Azure ML 进行贝叶斯采样的示例：

点击此处查看代码图像

```python
from azure.ai.ml.sweep import Uniform, Choice

command_job_for_sweep = command_job(
learning_rate=Uniform(min_value=0.05, max_value=0.1),
batch_size=Choice(values=[16, 32, 64, 128]
)

sweep_job = command_job_for_sweep.sweep(
compute="cpu-cluster",
sampling_algorithm="bayesian"   ...
)
```

选择正确的采样方法取决于项目的特定需求，例如超参数的类型、搜索空间的大小以及计算预算。随机采样提供了广泛的初始搜索，网格采样涵盖了有限集合内的所有可能性，而贝叶斯采样则根据对过去评估的学习进行优化。这些方法都可以在 Azure Machine Learning 中轻松实现，为增强模型性能提供了强大工具。图 2-20 显示了可视化该示例超参数性能的指标图。

![图 2-20 指标图](img/02fig20.jpg)

图 2-20 指标图

#### 定义主要指标

搜索空间定义了每个超参数的值范围。你可以使用 `Choice` 指定离散值，或使用 `Uniform` 或 `Normal` 分布指定连续范围。

点击此处查看代码图像

```python
from azure.ai.ml.sweep import Choice, Uniform

search_space = {
 "learning_rate": Uniform(min_value=0.01, max_value=0.1),
 "batch_size": Choice(values=[16, 32, 64, 128])
}
```

我们在讨论 AutoML 中的算法时提到过主要指标的概念。你可能记得，主要指标是调优过程旨在优化的性能衡量标准。你需要指定指标名称以及是最大化还是最小化它。

```python
primary_metric = {
    "name": "accuracy",
    "goal": "Maximize"
}
```

#### 定义提前终止选项

提前终止策略允许你提前停止低性能的训练运行，从而节省时间和资源。Azure Machine Learning 支持多种策略，例如 `Bandit`、`Median StRopping` 和 `Truncation Selection`。

### 章节总结

*   你可以在使用 Apache Spark 进行交互开发期间访问并处理数据，侧重于通过各种资产和存储器准备和操作数据。
