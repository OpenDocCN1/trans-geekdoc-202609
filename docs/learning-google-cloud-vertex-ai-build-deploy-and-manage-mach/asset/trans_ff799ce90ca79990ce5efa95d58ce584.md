

# 图 7.9：API 成功启用

## 步骤 5：导入包

在新单元格中运行以下代码行以导入所需的包：

```
from typing import NamedTuple

from kfp.v2 import dsl

from kfp.v2.dsl import (Artifact, Dataset, Input, Model, Output, Metrics, ClassificationMetrics, component, OutputPath, InputPath)

from kfp.v2 import compiler

from google.cloud import BigQuery

from google.cloud import aiplatform

from google.cloud.aiplatform import pipeline_jobs

from datetime import datetime
```

使用 Vertex AI 流水线，我们将从 BigQuery 中可用的数据创建数据集，应用最少的数据转换，并拆分数据用于训练和测试目的。然后我们使用训练数据集训练模型，并在测试数据集上评估模型性能。我们在流水线的每个阶段将工件（或中间输出）保存到 Cloud Storage。

## 步骤 6：用于存储流水线工件的存储桶

运行以下代码行以设置存储工件的位置。存储桶将在流水线运行期间创建：

```
USER_FLAG = "--user"

REGION = "us-central1"

# 设置环境路径
PATH = %env PATH

%env PATH={PATH}:/home/jupyter/.local/bin

# 获取项目名称
shell_output = !gcloud config get-value project 2> /dev/null

PROJECT_ID = shell_output[0]

# 设置存储桶名称以存储工件
BUCKET_NAME = "gs://" + PROJECT_ID + "-bucket-employee"

PIPELINE_ROOT = f"{BUCKET_NAME}/pipeline_root_employee/"

PIPELINE_ROOT
```

## 步骤 7：流水线的第一个组件（从 BigQuery 获取数据）

运行下述代码以定义将包含在流水线中的模型评估和阈值比较的自定义组件。关于代码的重要要点：

*   `@component` 装饰器用于将此函数定义为流水线的一个组件。
*   组件的输入将是需要从中获取数据的 BigQuery 表的位置：

```
# 流水线中的第一个组件，用于从 big query 获取数据。

@component(
    packages_to_install=["google-cloud-bigquery==2.34.1", "pandas", "pyarrow", "db-dtypes", "scikit-learn"],
    base_image="python:3.7",
    output_component_file="data_fetch_bigquery.yaml"
)
def get_data(bq_table: str, output_data_path: Output[Dataset]):
    from google.cloud import bigquery
    import pandas as pd

    bqclient = bigquery.Client()
    table = bigquery.TableReference.from_string(bq_table)
    rows = bqclient.list_rows(table)
    dataframe = rows.to_dataframe(create_bqstorage_client=True)
    dataframe.to_csv(output_data_path.path + ".csv", index=False, encoding='utf-8-sig')
```

## 步骤 8：流水线的第二个组件（数据转换）

运行以下代码以定义流水线的第二个组件。它将应用数据转换并将数据拆分为训练样本和测试样本。此组件的输入将是来自前一个组件的数据集，输出将是两个单独的数据集。

```
# 流水线中的第二个组件，用于应用数据转换和拆分数据

@component(
    packages_to_install=["scikit-learn", "pandas"],
    base_image="python:3.7",
    output_component_file="data_transformation.yaml",
)
def data_transformation(
    dataset: Input[Dataset],
    dataset_train: Output[Dataset],
    dataset_test: Output[Dataset]
):
    from sklearn.metrics import roc_curve
    from sklearn.model_selection import train_test_split
    from joblib import dump
    from sklearn.metrics import confusion_matrix
    from sklearn.tree import DecisionTreeClassifier
    from sklearn.ensemble import RandomForestClassifier
    import pandas as pd

    data = pd.read_csv(dataset.path + ".csv")
    data = data.copy()
    data = data.drop(['region', 'employee_id'], axis=1)
    data = data.dropna(axis=0)
    data['gender'] = data['gender'].replace({'f': 0, 'm': 1})
    dummies = pd.get_dummies(data['department'])
    data = pd.concat([data, dummies], axis=1)
    data = data.drop('department', axis=1)

    edu_ranking = {"Master's & above": 1, "Bachelor's": 2, "Below Secondary": 3}
    recruit_ranking = {'sourcing': 1, 'other': 2, 'referred': 3}

    data['education'] = data['education'].map(edu_ranking)
    data['recruitment_channel'] = data['recruitment_channel'].map(recruit_ranking)

    train, test = train_test_split(data, test_size=0.3)

    train.to_csv(dataset_train.path + ".csv", index=False, encoding='utf-8-sig')
    test.to_csv(dataset_test.path + ".csv", index=False, encoding='utf-8-sig')
```

## 步骤 9：流水线的第三个组件（模型训练）

运行以下代码以定义流水线的第三个组件。它将在训练数据集上训练模型（随机森林分类器）。此组件的输入将是来自第二个组件的训练数据集，输出将是训练好的模型：

```
# 第三个组件 模型训练

@component(
    packages_to_install=[
        "pandas",
        "scikit-learn",
    ],
    base_image="python:3.9",
)
def emp_promotion_training(
    dataset: Input[Dataset],
    model: Output[Model],
):
    from sklearn.ensemble import RandomForestClassifier
    import pandas as pd
    import pickle

    data = pd.read_csv(dataset.path + ".csv")
    model_rf = RandomForestClassifier(n_estimators=10)
    model_rf.fit(
        data.drop(columns=["is_promoted"]),
        data.is_promoted,
    )
    model.metadata["framework"] = "random forest"
    file_name = model.path + ".pkl"
    with open(file_name, 'wb') as file:
        pickle.dump(model_rf, file)
```

## 步骤 10：流水线的第四个组件（模型评估）

运行以下代码以定义流水线的第四个组件。它将从第三个组件导入训练好的模型，并从第二个组件导入测试数据集。它在测试数据集上检查模型性能并记录模型指标：

```
# 第四个组件 模型评估

@component(
    packages_to_install=[
        "pandas",
        "scikit-learn"
    ],
    base_image="python:3.9",
)
def model_evaluation(
    test_set: Input[Dataset],
    trained_model: Input[Model],
    metrics: Output[ClassificationMetrics],
    kpi: Output[Metrics]
):
    from sklearn.ensemble import RandomForestClassifier
    import pandas as pd
    import logging
    import pickle
    from sklearn.metrics import roc_curve, confusion_matrix, accuracy_score, recall_score, precision_score
    import json
    import typing

    data = pd.read_csv(test_set.path + ".csv")
    model = RandomForestClassifier()
    file_name = trained_model.path + ".pkl"
    with open(file_name, 'rb') as file:
        model = pickle.load(file)

    y_test = data.drop(columns=["is_promoted"])
    y_target = data.is_promoted
    y_pred = model.predict(y_test)
    y_scores = model.predict_proba(data.drop(columns=["is_promoted"]))[:, 1]

    fpr, tpr, thresholds = roc_curve(
        y_true=data.is_promoted.to_numpy(), y_score=y_scores, pos_label=True
    )

    metrics.log_roc_curve(fpr.tolist(), tpr.tolist(), thresholds.tolist())

    metrics.log_confusion_matrix(
        ["False", "True"],
        confusion_matrix(
            data.is_promoted, y_pred
        ).tolist(),
    )

    accuracy = accuracy_score(data.is_promoted, y_pred.round())
    recall = recall_score(data.is_promoted, y_pred.round(), pos_label=1)
    precision = precision_score(data.is_promoted, y_pred.round(), pos_label=1)

    trained_model.metadata["accuracy"] = float(accuracy)
    trained_model.metadata["recall"] = float(recall)
    trained_model.metadata["precision"] = float(precision)

    kpi.log_metric("accuracy", float(accuracy))
    kpi.log_metric("recall", float(recall))
    kpi.log_metric("precision", float(precision))
```

## 步骤 11：流水线构建

运行以下代码以使用自定义组件定义流水线：

*   `@kfp.dsl.pipeline` 装饰器用于将此函数定义为流水线。
*   组件的输入将是训练好的模型（和工件），这些将从 `Input[Artifacts]` 收集。

