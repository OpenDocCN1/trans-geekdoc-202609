
# GCP 权限配置与 Vertex AI Pipeline 构建

除了启用 API，我们还需要授予与 GCP Compute Engine 关联的服务账号额外的 Storage Admin 权限，以便从 Cloud Storage 访问源文件（默认情况下 Notebook 具有 Cloud Storage 访问权限，但在 Pipeline 场景下，数据获取和模型训练代码并不在 Notebook 上执行，因此需要额外权限。Notebook 仅用于定义 Pipeline 组件和执行 Pipeline）。请按以下步骤授予权限：

## 步骤 1：打开 IAM 和管理部分

按照 [Figure 6.4](#ch06.xhtml#fig6-4) 所述步骤，为与 GCP Compute Engine 关联的服务账号添加角色：

![](images/Figure_6.4.png)

Figure 6.4: IAM of GCP

1.  点击 **IAM**。
2.  点击 **Edit principal** 按钮。

## 步骤 2：添加额外角色

按照 [Figure 6.5](#ch06.xhtml#fig6-5)、[Figure 6.6](#ch06.xhtml#fig6-6) 和 [Figure 6.7](#ch06.xhtml#fig6-7) 所述步骤，编辑 Compute Engine 服务账号的角色：

![](images/Figure_6.5.png)

Figure 6.5: Edit roles of the service account

1.  点击 **ADD ANOTHER ROLE**：

    ![](images/Figure_6.6.png)

    Figure 6.6: Adding storage object admin role

2.  在 Cloud Storage 筛选器下选择 **Storage Object Admin** 角色。
3.  点击 **Save**。如 [Figure 6.7](#ch06.xhtml#fig6-7) 所示，新角色将添加到服务账号：

    ![](images/Figure_6.7.png)

    Figure 6.7: New role added to service account is visible in the IAM

4.  新角色将显示在与 Compute Engine 关联的服务账号下。

# Pipeline 代码演练

需要创建 Workbench 来运行 Pipeline 代码。请按照 [Chapter 4](#ch04.xhtml) "Vertex AI Workbench and custom model training" 中 "Vertex AI Workbench creation" 部分的步骤创建 Workbench（选择 Python 3 机器）：

## 步骤 1：创建 Python Notebook 文件

Workbench 创建完成后，打开 JupyterLab，按照 [Figure 6.8](#ch06.xhtml#fig6-8) 所述步骤创建 Python Notebook 文件：

![](images/Figure_6.8.png)

Figure 6.8: New launcher window

1.  点击 **New launcher**。
2.  双击 **Python 3 notebook** 文件以创建一个。

## 步骤 2：安装依赖包

在后续步骤中，在独立的单元格中运行给定代码。

运行以下命令安装 Kubeflow、Google Cloud Pipeline 和 Google Cloud AI Platform 包（安装需要几分钟）：

```python
USER_FLAG = "--user"

!pip3 install {USER_FLAG} google-cloud-aiplatform==1.18.0 --upgrade

!pip3 install {USER_FLAG} kfp==1.8.10 google-cloud-pipeline-components==1.0
```

## 步骤 3：重启 Kernel

在下一个单元格中输入以下命令以重启 Kernel（用户也可通过 GUI 重启 Kernel）：

```python
import os

if not os.getenv("IS_TESTING"):
    import IPython
    app = IPython.Application.instance()
    app.kernel.do_shutdown(True)
```

## 步骤 4：导入包

在新单元格中运行以下代码行以导入所需包：

```python
import kfp
from kfp.v2 import compiler, dsl
from kfp.v2.dsl import component, pipeline, Artifact, ClassificationMetrics, Input, Output, Model, Metrics
from typing import NamedTuple
from google_cloud_pipeline_components import aiplatform as gcc_aip
from google.cloud import aiplatform
```

使用 Vertex AI Pipeline，我们将从 Cloud Storage 中的可用数据创建 AutoML Image 数据集，训练 AutoML 图像分类模型，并根据阈值评估模型。如果模型性能高于阈值，则创建 Endpoint 并将训练好的模型部署到该 Endpoint。下图展示了 Pipeline 执行步骤的流程图（Pipeline 的不同组件）。除模型评估组件外，所有其他组件均可在 `google_cloud_pipeline_components` 包中找到：

![](images/Figure_6.9.png)

Figure 6.9: Components of pipeline

## 步骤 5：Pipeline 的 Artifact 存储 Bucket

运行以下代码设置 Artifact 存储位置。Bucket 将在 Pipeline 运行期间创建：

```python
PROJECT_ID = "vertex-ai-gcp-1"
bucket_name_arti = "gs://" + PROJECT_ID + "-pipeline-automl-artifacts"
PATH = %env PATH
%env PATH={PATH}:/home/jupyter/.local/bin
REGION = "us-central1"
pipeline_folder = f"{bucket_name_arti}/pipeline_automl/"
print(pipeline_folder)
```

## 步骤 6：Pipeline 的模型评估组件

运行以下代码定义用于模型评估和阈值比较的自定义组件，该组件将包含在 Pipeline 中。以下代码的重要要点：

*   使用 `@component` 装饰器将此函数定义为 Pipeline 的组件。
*   组件的输入为训练好的模型（及其 Artifacts），将从 `Input[Artifact]` 收集。
*   `fetch_eval_info` 函数从训练好的模型获取评估数据，解析评估数据并传递给 `metrics_log_check` 函数，检查模型性能是否高于阈值，返回 `true`（性能优于阈值）或 `false`（否则）。

```python
@component(
    base_image="gcr.io/deeplearning-platform-release/tf2-cpu.2-5:latest",
    output_component_file="model_eval_component.yaml",
    packages_to_install=["google-cloud-aiplatform"]
)
def image_classification_model_eval_metrics(
    project: str,
    location: str,
    api_endpoint: str,
    thresholds_dict_str: str,
    model: Input[Artifact],
    metrics: Output[Metrics],
    metrics_classification: Output[ClassificationMetrics],
) -> NamedTuple("Outputs", [("dep_decision", str)]):

    import json
    import logging
    from google.cloud import aiplatform as aip

    # fetch_eval_info 函数从训练好的模型获取评估信息。
    def fetch_eval_info(client_name, model_name):
        # Refer the repository for code block of the function
        return (model_eval.name, metrics_list_value, metrics_list_string)

    def metrics_log_check(metrics_list_value, metrics_classification, thresholds_dict_str):
        # Refer the repository for code block of the function
        return True

    logging.getLogger().setLevel(logging.INFO)
    aip.init(project=project)

    # 从输入的 Model Artifact 中提取模型资源名称
    model_resource_path = model.metadata["resourceName"]
    logging.info("model path: %s", model_resource_path)

    client_options = {"api_endpoint": api_endpoint}

    # 初始化用于创建和发送请求的客户端
    client = aip.gapic.ModelServiceClient(client_options=client_options)

    # 获取特定模型的评估信息
    eval_name, metrics_list_value, metrics_str_list = fetch_eval_info(client, model_resource_path)
    logging.info("got evaluation name: %s", eval_name)
    logging.info("got metrics list: %s", metrics_list_value)

    deploy = metrics_log_check(metrics_list_value, metrics_classification, thresholds_dict_str)

    if deploy:
        _decision = "true"
    else:
        _decision = "false"

    logging.info("deployment decision is %s", dep_decision)
    return (dep_decision,)
```

## 步骤 7：Pipeline 构建

运行以下代码定义包含自定义组件和其他 GCP 组件的 Pipeline。以下代码的重要要点：

*   使用 `@kfp.dsl.pipeline` 装饰器将此函数定义为 Pipeline。
*   组件的输入为训练好的模型（及其 Artifacts），将从 `Input[Artifacts]` 收集。
