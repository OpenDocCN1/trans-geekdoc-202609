

![](img/cc4299656808e62a294f1843a1e18e72_75_0.png)

图 4.2: Python 包结构

## 导入模块语法

```
import <module_name>
import <module_name> as <alt_name>
```

## 导入 f4 模块

- 1. from My_Package import f4
- 2. from My_Package import f4 as load

## 导入 f1 模块以使用 x()

- 1. from My_Package.Sub_PackageA import f1
- 2. f1.func()

或者您可以使用以下方法导入模块：

- 1. from My_Package.Sub_PackageA.f1 import func
- 2. func()

## 开发、构建和部署 ML 包

在本节中，您将研究一个用例，该用例将从定义业务问题开始，最终以安装和使用 ML 包结束。您将学习为 ML 模型开发和构建自定义 Python 包。自定义包具有可移植性，可用于给定项目。您将能够像安装其他 Python 包一样安装自定义包，并对新数据进行预测。

### 业务问题

一家公司希望根据客户通过在线申请表格提供的详细信息来自动化贷款资格流程。这是一个分类问题，您需要预测贷款是否会被批准。

### 数据

数据对应与个人相关的一组财务交易。数据已标准化、去趋势化并匿名化。有关数据列的详细信息，请参阅以下表格：

| Variable | Description |
|---|---|
| Loan_ID | 唯一贷款 ID |
| Gender | 男性 / 女性 |
| Married | 申请人的婚姻状态 (Y / N) |
| Dependents | 受赡养人数量 |
| Education | 申请人的教育程度 (Graduate/Under Graduate) |
| Self_Employed | 自雇 (Y / N) |
| ApplicantIncome | 申请人的收入 |
| CoapplicantIncome | 联合申请人的收入 |
| LoanAmount | 贷款金额（以千为单位） |
| Loan_Amount_Term | 贷款期限（以月为单位） |
| Credit_History | 信用记录是否符合指南 (Y / N) |
| Property_Area | 城市 / 半城市 / 农村 |
| Loan_Status | 贷款是否批准 (Y / N) |

*表 4.1: 数据描述*

## 构建 ML 模型

此时，您可以使用 Jupyter 笔记本构建和比较不同的 ML 算法。

识别表现优于其他模型的模型，并为模型确定最佳参数（和超参数）。在此实验阶段，您应准备好所需的信息，例如需要转换的变量、缺失值填充、数值变量列表以及数据路径。

当您完成实验阶段后，可以开始构建包。打包的目的是可重用性、可移植性、减少错误以及机器学习流程的自动化。

首先，为构建包创建一个单独的目录。为不同阶段和操作维护单独的模块（Python 文件），例如，为数据预处理维护单独的模块。这将模块化代码并使代码调试变得容易。

构建测试用例，这些测试用例将运行代码文件并验证文件和预期输出的完整性。

本章不专注于优化 ML 模型，因此您可以通过微调来进一步提高模型性能。此包仅限于当前项目，即您不应在不同项目中使用同一个包。

## 开发包

以下是包的目录结构：

```
prediction_model
|— MANIFEST.in
|— prediction_model
|   |— config
|   |   |— config.py
|   |   |— __init__.py
|   |— datasets
|   |   |— __init__.py
|   |   |— test.csv
|   |   |— train.csv
|   |— __init__.py
|   |— pipeline.py
|   |— predict.py
|   |__ processing
|   |   |__ data_management.py
|   |   |__ __init__.py
|   |   |__ preprocessors.py
|   |__ trained_models
|   |   |__ classification_v1.pkl
|   |   |__ __init__.py
|   |__ train_pipeline.py
|   |__ VERSION
|__ README.md
|__ requirements.txt
|__ setup.py
|__ tests
|   |__ pytest.ini
|   |__ test_predict.py
```

### __init__.py

__init__.py 模块通常为空。但是，它有助于导入其他 Python 模块。

此文件指示该目录应被视为一个包。

### MANIFEST.in

MANIFEST.in 文件由命令组成，每行一个，指示 setuptools 将一组文件添加到或从 sdist（源发行版）中删除。在 Python 中，发行版是指允许打包、构建和分发模块的一组文件。sdist 包含文件存档，例如源文件、数据文件和 setup.py 文件，存储在 Unix 上的压缩 tar 文件 (.tar.gz) 中。

以下表格列出了命令及其描述。但是，本章将仅介绍其中几个命令。

您可以根据项目要求更新 MANIFEST.in。有关清单文件中常用命令，请参阅以下表格。

| Command | Description |
|---|---|
| include pat1 pat2 ... | 添加匹配任何列出模式的所有文件。 |
| exclude pat1 pat2 ... | 移除匹配任何列出模式的所有文件。 |
| recursive-include dir-pattern pat1 pat2 ... | 添加与 dir-pattern 匹配且符合任何列出模式的目录下的所有文件。 |
| recursive-exclude dir-pattern pat1 pat2 ... | 移除与 dir-pattern 匹配且符合任何列出模式的目录下的所有文件。 |
| global-include pat1 pat2 ... | 添加源树中任何位置匹配任何列出模式的所有文件。 |
| global-exclude pat1 pat2 ... | 移除源树中任何位置匹配任何列出模式的所有文件。 |
| graft dir-pattern | 添加与 dir-pattern 匹配的目录下的所有文件。 |
| prune dir-pattern | 移除与 dir-pattern 匹配的目录下的所有文件。 |

表 4.2: 清单文件的命令

让我们将命令添加到清单文件中以包含或排除文件：

- 1. include *.txt
- 2. include *.md
- 3. include *.cfg
- 4. include *.pkl
- 5. recursive-include ./prediction_model/*
- 6.
- 7. include prediction_model/datasets/train.csv
- 8. include prediction_model/datasets/test.csv
- 9. include prediction_model/trained_models/*.pkl
- 10. include prediction_model/VERSION
- 11. include ./requirements.txt
- 12. exclude *.log
- 13. recursive-exclude * __pycache__
- 14. recursive-exclude * *.py[co]

### config.py

配置模块包含常量变量、目录路径和初始设置。可以通过将此模块导入到其他模块中来访问变量和函数。例如，TARGET 变量存储因变量列名 Loan_Status。

在此，指定包的根目录、数据目录、训练文件名、测试文件名、特征以及其他文件和目录的路径。

```
1. #Import Libraries
2. import pathlib
3. import os
4. import prediction_model
5.
6. PACKAGE_ROOT = pathlib.Path(prediction_model.__file__).resolve().parent
7.
8. DATAPATH=os.path.join(PACKAGE_ROOT, 'datasets')
9. SAVED_MODEL_PATH=os.path.join(PACKAGE_ROOT, 'trained_models')
10.
11. TRAIN_FILE='train.csv'
12. TEST_FILE='test.csv'
13.
14. TARGET='Loan_Status'
15.
16. #Features to keep
17. FEATURES=['Gender', 'Married', 'Dependents',
18.     'Education', 'Self_Employed', 'ApplicantIncome',
19.     'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
20.     'Credit_History','Property_Area'] # Final feature to keep in data
21.
22. NUMERICAL_FEATURES=['ApplicantIncome', 'LoanAmount', 'Loan_Amount_Term']
23.
24. CATEGORICAL_FEATURES=['Gender', 'Married', 'Dependents',
25.     'Education', 'Self_Employed', 'Credit_History',
26.     'Property_Area'] #Categorical
27.
28. FEATURES_TO_ENCODE=['Gender', 'Married', 'Dependents',
29.     'Education', 'Self_Employed','Credit_History',
30.     'Property_Area'] #Features to Encode
31.
32. TEMPORAL_FEATURES=['ApplicantIncome']
33. TEMPORAL_ADDITION='CoapplicantIncome'
34. LOG_FEATURES=['ApplicantIncome', 'LoanAmount'] #Features for Log Transformation
35. DROP_FEATURES=['CoapplicantIncome'] #Features to Drop
```

### data_management.py

此模块包含加载数据、使用 joblib 保存序列化的 ML 模型以及加载反序列化的 ML 模型所需的函数。

```
1. #Import Libraries
2. import os
3. import pandas as pd
4. import joblib
5.
6. #Import other files/modules
7. from prediction_model.config import config
8.
9. def load_dataset(file_name):
10. """Read Data"""
11. file_path = os.path.join(config.DATAPATH,file_name)
12. _data = pd.read_csv(file_path)
13. return _data
15. def save_pipeline(pipeline_to_save):
16. """Store Output Of Pipeline
17. Exporting pickle file of trained Model """
18. save_file_name = 'classification_v1.pkl'
19. save_path = os.path.join(config.SAVED_MODEL_PATH, save_file_name)
```

