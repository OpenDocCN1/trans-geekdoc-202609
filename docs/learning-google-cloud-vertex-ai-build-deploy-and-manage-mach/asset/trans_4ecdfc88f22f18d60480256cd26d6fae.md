
# 新建特征存储

1. 点击**创建实体类型**以进行创建。

## 步骤 5：创建实体类型

按照[图 9.7](#ch09.xhtml#fig9-7)所示步骤创建实体类型：

![](images/Figure_9.7.png)

**图 9.7：创建实体类型**

1. 选择创建特征存储所在的**区域**。
2. 该区域下的所有特征存储将被列出；选择新建的**特征存储**。
3. 提供**实体类型名称**。
4. 为实体类型编写**描述**。
5. **特征监控**（如果需要监控特征则启用）。
   1. 它启用对特征存储和特征的监控。特征存储监控 CPU 利用率、存储和延迟。特征监控有助于监控特征值分布的变化。
6. 点击**创建**。

## 步骤 6：实体类型创建成功

实体类型已成功创建，如[图 9.8](#ch09.xhtml#fig9-8)所示，显示在所选特征存储下：

![](images/Figure_9.8.png)

**图 9.8：实体类型已创建并列在登陆页面上**

1. 点击新建的**实体类型**。

## 步骤 7：创建特征

实体类型创建完成后，需在导入值之前先创建特征。按照[图 9.9](#ch09.xhtml#fig9-9)所述步骤创建特征：

![](images/Figure_9.9.png)

**图 9.9：创建特征**

1. 点击**添加特征**。
   一个新的侧边标签页将弹出以输入特征，如[图 9.10](#ch09.xhtml#fig9-10)所示；按以下步骤创建特征：

   ![](images/Figure_9.10.png)

   **图 9.10：添加用户输入以创建特征**

2. 输入**特征名称**。
3. 输入该特征存储的**值类型**。
4. 为特征输入**描述**。
5. 点击**添加另一个特征**以添加新特征。
6. 所有特征添加完毕后，点击**保存**。

## 步骤 8：特征创建成功

特征成功创建后，将显示在实体类型页面上，如[图 9.11](#ch09.xhtml#fig9-11)所示：

![](images/Figure_9.11.png)

**图 9.11：实体类型下列出的特征**

1. 新建特征以表格格式显示。
2. 点击**导入值**以添加特征值。

## 步骤 9：导入特征值

按照[图 9.12](#ch09.xhtml#fig9-12)所述步骤启动特征值导入：

![](images/Figure_9.12.png)

**图 9.12：将数据导入特征**

1. 数据可从 Cloud Storage 或 BigQuery 导入。选择 **Cloud Storage CSV 文件**。
2. 点击**浏览**从 Cloud Storage 中选择 CSV 文件。
3. 点击**继续**并按照[图 9.13](#ch09.xhtml#fig9-13)所述步骤操作：

选择数据源后，我们需要将数据源的列映射到特征。按照[图 9.13](#ch09.xhtml#fig9-13)所述步骤映射特征：

![](images/Figure_9.13.png)

**图 9.13：将列映射到特征**

1. 添加**员工 ID**，因为该列包含唯一值。
2. 选择手动输入**时间戳**。如果数据包含时间戳值，可在此使用同一列。
3. 选择日期和时间。
4. 将 CSV 文件中的列名映射到特征。
5. 点击**导入**以启动导入作业。

## 步骤 10：导入作业成功

特征值成功导入后，导入作业状态将更新，如[图 9.14](#ch09.xhtml#fig9-14)所示：

![](images/Figure_9.14.png)

**图 9.14：特征存储的导入作业**

1. 导入作业成功完成。

## 步骤 11：创建后的特征存储登陆页面

特征存储的登陆页面如[图 9.15](#ch09.xhtml#fig9-15)所示；实体类型和特征存储下的所有特征均以表格格式列出并显示：

![](images/Figure_9.15.png)

**图 9.15：创建特征后的特征存储登陆页面**

1. 点击**age**特征。窗口将导航至该特征的属性页面，如[图 9.16](#ch09.xhtml#fig9-16)所示：

![](images/Figure_9.16.png)

**图 9.16：特征的属性**

1. 所有特征均显示包含基本信息和统计数据的**特征属性**。
2. 如果为特征存储和该特定特征启用了监控功能，则会填充指标。

# 使用 Python 操作特征存储

在上一节中，我们通过 GUI 方式在特征存储上进行了创建和上传特征值的操作。在本节中，我们将创建另一个特征存储、导入值，并从特征存储中获取值。

我们将使用 Python 3 笔记本文件输入命令来操作特征存储。请按照以下步骤创建 Python 文件并输入本节提供的 Python 代码。

## 步骤 1：创建 Python 笔记本文件

工作台创建完成后，打开 JupyterLab，按照[图 9.17](#ch09.xhtml#fig9-17)所述步骤创建 Python 笔记本文件：

![](images/Figure_9.17.png)

**图 9.17：笔记本的新启动器窗口**

1. 点击新建启动器。
2. 双击 **Python 3** 笔记本文件以创建一个。

## 步骤 2：安装软件包

运行以下命令安装 Google Cloud AI Platform 软件包。（安装软件包需要几分钟）：

```bash
USER="--user"
!pip install {USER} google-cloud-aiplatform
```

## 步骤 3：重启内核

在下一个单元格中输入以下命令以重启内核（用户也可以通过 GUI 重启内核）：

```python
import os
import IPython

if not os.getenv(""):
    IPython.Application.instance().kernel.do_shutdown(True)
```

## 步骤 4：导入已安装的软件包

在新单元格中运行以下代码以导入所需软件包：

```python
import google.cloud.aiplatform_v1
from google.cloud.aiplatform_v1.types import featurestore_service as fs_s
from google.cloud.aiplatform_v1.types import featurestore as fs
from google.cloud.aiplatform_v1.types import feature
from google.cloud.aiplatform_v1.types import entity_type
from google.cloud.aiplatform_v1.types import io
from google.protobuf.timestamp_pb2 import Timestamp
from google.cloud.aiplatform_v1.types.featurestore_service import ImportFeatureValuesRequest
from google.cloud.aiplatform_v1.types import FeatureSelector, IdMatcher
from google.cloud.aiplatform_v1.types import featurestore_online_service
import datetime
```

## 步骤 5：设置项目和其他变量

在新单元格中运行以下代码行以将项目设置为当前项目，并定义变量以存储用于多种用途的路径：

```python
Project_id = "vertex-ai-gcp-1"
featurestore_name = "employee_fs_pysdk"
Entity_name = "emp_entity_pysdk"
location = "us-central1"
endpoint = "us-central1-aiplatform.googleapis.com"
```

## 步骤 6：连接到特征存储

连接到特征存储是操作特征存储的第一步。我们通过服务客户端创建到特征存储的连接，以使用 `FeaturestoreServiceClient` 创建并导入值。

`FeaturestoreOnlineServingServiceClient` 用于从特征存储获取特征值。运行以下代码行以完成连接：

```python
client_admin = google.cloud.aiplatform_v1.FeaturestoreServiceClient(client_options={"api_endpoint": endpoint})
client_data = google.cloud.aiplatform_v1.FeaturestoreOnlineServingServiceClient(client_options={"api_endpoint": endpoint})
fs_resource_path = client_admin.common_location_path(Project_id, location)
```

## 步骤 7：创建特征存储
