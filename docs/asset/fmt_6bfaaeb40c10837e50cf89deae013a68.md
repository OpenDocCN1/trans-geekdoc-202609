
# Docker 与自定义模型训练

Docker 于 2013 年发布，通过允许用户快速构建程序的容器镜像，彻底改变了容器技术。Docker 是一款开源虚拟化软件，旨在帮助开发人员。它是一款 PaaS 软件，可隔离虚拟环境，以部署、创建和测试与当前操作系统不兼容的应用程序。

## Docker 的组件

* **Dockerfile**：`Dockerfile` 是每个容器的起点。此文本文件包含构建 Docker 镜像的说明，包括操作系统、语言、环境变量、文件位置、网络端口和其他组件。
* **Docker image**：Docker 镜像是一种可移植的、只读的可执行文件，提供了构建容器的说明以及将执行哪些软件组件。
* **Docker run**：Docker 中的 `run` 命令运行一个容器。同一镜像的多个实例可以在容器中运行。
* **DockerHub**：Docker Hub 是容器镜像的存储库。它是 Docker 面向容器的 GitHub。

## Dockerfile 的创建

Dockerfile 是一个文本文件，由 Docker 从上到下读取。它包含一系列指令，指示 Docker 如何构建 Docker 镜像。Dockerfile 是创建 Docker 镜像的配方，执行单独的构建命令即可根据该配方生成 Docker 镜像。

在构建 Docker 镜像之前，我们需要启用容器注册表和 Artifact Registry 的 API。请按照以下步骤启用它们。

### 步骤 1：API 和服务

平台的所有 API 都可以通过“API 和服务”启用或停用。可以通过导航菜单打开“API 和服务”，如图 4.8 所示：

![](img/Figure_4.8.png)

**图 4.8**：打开平台的 API 和服务

1. 打开导航菜单并选择 **API 和服务**。
   或者，用户可以在搜索框中搜索 **API 和服务**。
2. 点击 **已启用的 API 和服务**。

### 步骤 2：API 和服务的登录页面

API 和服务的登录页面如图 4.9 所示：

![](img/Figure_4.9.png)

**图 4.9**：GCP 的 API 和服务

1. 在搜索框中搜索 **container registry**（容器注册表）。

### 步骤 3：容器注册表搜索结果

容器注册表的搜索结果如图 4.10 所示：

![](img/Figure_4.10.png)

**图 4.10**：API 的搜索结果

1. 右键点击以启用 **Google Container Registry API**。
2. 右键点击以启用 **Artifact Registry API**。

### 步骤 4：容器注册表 API 启用

容器注册表是一个中心化位置，团队可在其中维护 Docker 镜像、执行漏洞分析并实施细粒度的访问控制。按照图 4.11 中的步骤启用容器注册表 API：

![](img/Figure_4.11.png)

**图 4.11**：容器注册表 API

1. 点击 **启用**。

### 步骤 5：Artifact Registry API 启用

Artifact Registry 支持容器镜像和非容器制品。Artifact Registry 增强并扩展了容器注册表的功能，例如客户管理的加密密钥、VPC-SC 支持、Pub/Sub 通知，提供了重要的安全性、可扩展性和控制方面的进步等。

按照图 4.12 所示操作以启用 Artifact Registry API：

![](img/Figure_4.12.png)

**图 4.12**：Artifact Registry API

1. 为 Artifact Registry API 点击 **启用**。

启用这两个 API 后，返回工作台并启动终端（参考下图，双击 **Terminal**）。

### 步骤 6：目录创建

启动终端（参考图 4.6，第 11 点），并按照图 4.13 中描述的步骤在工作台中创建目录：

![](img/Figure_4.13.png)

**图 4.13**：终端中的目录创建

1. 在终端窗口中依次输入以下命令。

   我们创建一个名为 `price_pred` 的新目录，并在 `price_pred` 目录内创建一个 `Dockerfile`：

   ```bash
   mkdir price_pred
   cd price_pred
   touch Dockerfile
   ```

2. `Dockerfile` 将在 `price_pred` 文件夹内创建（文件将没有内容；双击文件以打开它）。

### 步骤 7：编辑 Dockerfile

在 `Dockerfile` 中输入命令，如图 4.14 所示：

![](img/Figure_4.14.png)

**图 4.14**：编辑 Dockerfile

1. 输入以下命令：

   ```dockerfile
   FROM gcr.io/deeplearning-platform-release/tf2-cpu.2-6
   WORKDIR /
   COPY trainer /trainer
   ENTRYPOINT ["python","-m","trainer.train"]
   ```

命令说明如下：

* Docker 镜像将使用 `gcr.io` 中可用的容器镜像构建（详情请参阅图示）。
* 设置工作目录。
* 它将把 `trainer` 文件夹复制到工作目录（`trainer` 文件夹尚未在 JupyterLab 中创建；`trainer` 文件夹包含用于模型训练的 `train.py` 文件）。
* `ENTRYPOINT` 指向容器启动时执行的可执行文件。

保存 `Dockerfile`（`Ctrl` + `S`）并关闭文件。

GCP 的容器注册表提供深度学习容器的存储库。深度学习容器是提供数据科学框架、库和工具的 Docker 容器。这些经过性能优化的容器使用户能够快速进行实验和部署流程。它们托管在不同的数据中心。

* `gcr.io` 在美国数据中心托管镜像；不过，位置可能会有所不同。
* `us.gcr.io` 在欧盟地区托管容器镜像。
* `eu.gcr.io` 在美国地区托管容器镜像。
* `asia.gcr.io` 在亚洲地区托管容器镜像。

图 4.15 显示了 `gcr.io` 的存储库：

![](img/Figure_4.15.png)

**图 4.15**：gcr.io 的容器注册表

## 模型构建

创建 `Dockerfile` 后，我们需要着手编写用于模型构建的 Python 代码。任务是构建一个回归模型来预测电价。Python 代码将被复制到容器中并提交为训练作业。

让我们回到工作台的终端，并按照以下步骤创建用于模型构建的 Python 代码：

### 步骤 1：创建 trainer 文件夹

在终端中输入命令，如图 4.16 所示：

![](img/Figure_4.16.png)

**图 4.16**：终端中的 trainer 文件夹创建

```bash
PROJECT_ID=vertex-ai-gcp
mkdir trainer
```

在第一条命令中，一个名为 `PROJECT_ID` 的变量被设置为项目 ID（使用项目 ID，而非项目名称）；我们将在创建 Docker 镜像时使用此命令。在第二行命令中，我们将创建一个名为 `trainer` 的新文件夹。打开 `trainer` 文件夹。

### 步骤 2：创建 Python 文件

按照图 4.17 中提到的步骤创建 Python 文件：

![](img/Figure_4.17.png)

**图 4.17**：工作台上的 Python 文件创建

1. 点击 **新建启动器**。
2. 双击 **Python 文件**。

### 步骤 3：Python 代码

一个 Python 文件将在 `trainer` 文件夹内创建。在 `.py` 文件中编写如下 Python 代码，如图 4.18 所示：

```python
import numpy as np
import pandas as pd
import pathlib
import tensorflow as tf

#### Importing tensorflow 2.6
from tensorflow import keras
from tensorflow.keras import layers

def main():
    # Reading data from the gcs bucket
    dataset = pd.read_csv(r"gs://custom_model_ele_prices/electricity_prices.csv", low_memory=False)
    dataset.tail()
    BUCKET = 'gs://custom_model_ele_prices'
    dataset.isna().sum()
    dataset = dataset.dropna()
    dataset.drop(['DateTime', 'Holiday'], axis=1, inplace=True)
    cols = list(dataset.columns[dataset.dtypes.eq('object')])
    dataset[cols] = dataset[cols].apply(pd.to_numeric, errors='coerce', axis=1)
    train_dataset = dataset.sample(frac=0.8, random_state=0)
    test_dataset = dataset.drop(train_dataset.index)
    train_stats = train_dataset.describe()
    train_stats.pop("SMPEP2")
    train_stats = train_stats.transpose()
    train_labels = train_dataset.pop('SMPEP2')
    test_labels = test_dataset.pop('SMPEP2')
    normed_train_data = (train_dataset - train_dataset.mean()) / train_dataset.std()
    normed_test_data = (test_dataset - train_dataset.mean()) / train_dataset.std()

    def tf_build_model_reg():
        # model building function
        model = keras.Sequential([
            layers.Dense(64, activation='relu', input_shape=[len(train_dataset.keys())]),
            layers.Dense(64, activation='relu'),
            layers.Dense(128, activation='relu'),
            layers.Dense(32, activation='relu'),
            layers.Dense(1)
        ])

        optimizer = tf.keras.optimizers.Adagrad(0.001)

        model.compile(loss='mse', optimizer=optimizer, metrics=['mae', 'mse'])

        return model

    model = tf_build_model_reg()

    epochs = 10

    early_stop = keras.callbacks.EarlyStopping(monitor='val_loss', patience=5)

    early_history = model.fit(normed_train_data, train_labels, epochs=epochs, validation_split=0.2, callbacks=[early_stop])

    model.save(BUCKET + '/model')

if __name__ == "__main__":
    main()
```

![](img/Figure_4.18.png)

**图 4.18**：模型训练的 Python 代码

1. 输入 Python 代码。
2. 右键单击并将 Python 文件名重命名为 `train.py`。
3. 保存 Python 文件 (`Ctrl + S`) 并关闭文件。

Python 代码包含导入所需包的代码。主函数从云存储存储桶读取 `.csv` 文件，应用一些数据转换，并拆分数据用于训练和测试。`tf_build_model_reg` 函数包含 TensorFlow 模型的框架（模型将使用 TensorFlow 2.6 构建）。最后，训练好的模型将被推送到云存储存储桶。

> **注意**：我们将 Epochs 设置为 10。请根据您的需求进行增加。

本练习使用的代码并不十分详细，因为它仅用于说明目的。用户可以使用更复杂的代码进行模型训练。

## 镜像创建

现在我们已经完成了用于模型构建的 Dockerfile 和 Python 代码的创建。我们可以继续进行镜像创建。

### 步骤 1：使用 docker build 创建镜像

按照图 4.19 所示输入以下命令以创建镜像：

```bash
IMAGE_URL="gcr.io/$PROJECT_ID/price:v1"
docker build ./ -t $IMAGE_URL
```

![](img/Figure_4.19.png)

**图 4.19**：镜像创建过程

1. 在终端中输入命令。

从 Dockerfile 构建镜像将需要几分钟时间。构建完成后，终端中将显示成功消息，如图 4.20 所示：

![](img/Figure_4.20.png)

**图 4.20**：镜像创建完成

1. 镜像创建完成后显示的成功消息。

### 步骤 2：检查 Docker 镜像

创建镜像后，让我们检查一下是否可以从创建的镜像运行 Python 代码。按照图 4.21 所示输入以下命令：

```bash
docker run $IMAGE_URL
```

![](img/Figure_4.21.png)

**图 4.21**：容器上 Python 代码的测试运行

1. 输入命令。

Python 代码已成功运行，如下图所示：

![](img/Figure_4.22.png)

**图 4.22**：代码成功运行

## 将镜像推送到容器注册表

现在我们已经创建了镜像，并测试了代码是否能以正确的输出运行，我们现在可以将镜像推送到容器注册表。

### 步骤 1：镜像推送命令

按照图 4.23 所示在终端中输入以下命令：

```bash
docker push $IMAGE_URL
```

![](img/Figure_4.23.png)

**图 4.23**：镜像推送到项目容器注册表

1. 输入命令。
2. 镜像成功推送到容器注册表。

### 步骤 2：检查容器注册表

从平台导航菜单打开容器注册表（它将列在 CI/CD 下）。或者，在平台的搜索框中输入 container registry 以打开它。容器注册表的着陆页如图 4.24 所示：

![](img/Figure_4.24.png)

**图 4.24**：容器注册表中创建的 price 文件夹

1. 容器注册表中将创建一个名为 `price` 的文件夹（请参阅镜像创建部分，我们在那里指定 `price` 为名称，`v1` 为标签）。点击 `price`。

![](img/Figure_4.25.png)

**图 4.25**：推送到容器注册表的创建镜像

1. 镜像将在文件夹内且标签 `v1` 下可用。

## 提交自定义模型训练作业

为了让模型得到训练，它会从上传到云存储存储桶的 `.csv` 文件中获取数据。默认情况下，Workbench 资源将拥有对云存储的读写访问权限。然而，当我们提交训练作业时，训练代码将在一个或多个由 Google Cloud 管理的虚拟机实例上执行。这些虚拟机将无法访问云存储存储桶，因此我们将使用服务账号。请按照以下步骤提交训练作业：

### 步骤 1：Vertex AI 的训练模块

按照图 4.26 所示打开 Vertex AI 的训练模块：

![](img/Figure_4.26.png)

**图 4.26**：训练模块

1. 选择训练模块。
2. 选择自定义作业。
3. 点击创建。

### 步骤 2：选择训练方法

将出现“训练新模型”页面，如图 4.27 所示。按照图中提到的步骤配置训练方法：

![](img/Figure_4.27.png)

**图 4.27**：自定义模型的训练方法选择

1. 选择训练方法。
2. 在数据集选择下选择**非托管数据集**。
3. 选择自定义训练。
4. 点击继续。

### 步骤 3：模型详情

按照图 4.28 所示选择模型详情以训练模型：

![](img/Figure_4.28.png)

**图 4.28**：自定义模型的模型详情

1. 选择训练方法后，我们必须输入模型详情。
2. 选择训练新模型。
3. 为模型提供名称。
4. 提供模型描述。
5. 必须为模型训练选择服务账号。点击浏览。
6. 由于代码将被推送到 Google Cloud 虚拟机实例，因此需要服务账号来从云存储访问数据并将模型存回云存储。
7. 选择与计算关联的服务账号（用户也可以选择我们在第 2 章 中创建的服务账号，但需要添加访问云存储的角色）。
8. 点击选择。
9. 点击继续。

### 步骤 4：训练容器详情
