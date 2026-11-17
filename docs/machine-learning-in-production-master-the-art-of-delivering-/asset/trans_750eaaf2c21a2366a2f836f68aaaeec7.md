

21. if __name__ == '__main__':
22.     run_training()

## setup.py

要从源目录配置和安装软件包，请创建 setup.py 文件。该文件特定于软件包。PIP 将使用 setup.py 文件安装软件包。进入 setup.py 文件所在的目录，使用 pip install .（句号）命令安装软件包。

```python
import io
import os
from pathlib import Path

from setuptools import find_packages, setup

# Package meta-data
NAME = 'prediction_model'
DESCRIPTION = 'Train and deploy prediction model.'
URL = 'https://github.com/suhas-ds/prediction_model'
EMAIL = 'suhasp.ds@gmail.com'
AUTHOR = 'Suhas Pote'
REQUIRES_PYTHON = '3.6'

here = os.path.abspath(os.path.dirname(__file__))

# What packages are required for this module to be executed?
def list_reqs(fname='requirements.txt'):
    with io.open(os.path.join(here, fname), encoding='utf-8') as fd:
        return fd.read().splitlines()
try:
    with io.open(os.path.join(here, 'README.md'),
                 encoding='utf-8') as f:
    long_description = '\n' + f.read()
except FileNotFoundError:
    long_description = DESCRIPTION

# Load the package's __version__.py module as a dictionary.
ROOT_DIR = Path(__file__).resolve().parent
PACKAGE_DIR = ROOT_DIR / NAME
about = {}
with open(PACKAGE_DIR / 'VERSION') as f:
    _version = f.read().strip()
about['__version__'] = _version

setup(
    name=NAME,
    version=about['__version__'],
    description=DESCRIPTION,
    long_description=long_description,
    long_description_content_type='text/markdown',
    author=AUTHOR,
    author_email=EMAIL,
    python_requires=REQUIRES_PYTHON,
    url=URL,
    packages=find_packages(exclude=('tests',)),
    package_data={'prediction_model': ['VERSION']},
    install_requires=list_reqs(),
    extras_require={},
include_package_data=True,
license='MIT',
classifiers=[
    'License :: OSI Approved :: MIT License',
    'Programming Language :: Python',
    'Programming Language :: Python :: 3',
    'Programming Language :: Python :: 3.6',
    'Programming Language :: Python :: Implementation :: CPython',
    'Programming Language :: Python :: Implementation :: PyPy'
]
)
```

## VERSION

此文件保存软件包的版本。此处使用 **主版本号.次版本号.修订版本号** 方案。

```
0.1.0
```

## pytest.ini

要在运行 pytest 时禁用警告，需要配置 pytest.ini 文件。

```
[pytest]
addopts = -p no:warnings
```

## test_predict.py

它从验证数据中获取一条记录，并使用 **断言** 语句验证输出。

它验证以下检查：

- 输出不为空。
- 输出数据类型为 **str**。
- 对于给定数据（固定），输出为 **Y**。

这些检查通过 pytest 运行。

```python
# Import libraries
import pytest
# Import files/modules
from prediction_model.config import config
from prediction_model.processing.data_management import load_dataset
from prediction_model.predict import make_prediction

@pytest.fixture
def single_prediction():
    ''' This function will predict the result for a single record'''
    test_data = load_dataset(file_name=config.TEST_FILE)
    single_test = test_data[0:1]
    result = make_prediction(single_test)
    return result

# Test Prediction
def test_single_prediction_not_none(single_prediction):
    ''' This function will check if the result of prediction is not None'''
    assert single_prediction is not None

def test_single_prediction_dtype(single_prediction):
    ''' This function will check if the data type of the result of the prediction is str i.e. string'''
    assert isinstance(single_prediction.get('prediction')[0], str)

def test_single_prediction_output(single_prediction):
    ''' This function will check if the result of the prediction is Y'''
    assert single_prediction.get('prediction')[0] == 'Y'
```

设置环境变量 PYTHONPATH 并进入软件包目录，然后运行以下命令：

```
pytest -v
```

如果一切正常，应得到如下输出：

![](img/cc4299656808e62a294f1843a1e18e72_94_0.png)

图 4.3：pytest 输出

## sdist

Python 的 sdist 是压缩归档文件（.tar.gz 文件），包含一个或多个软件包或模块。

这会创建一个 dist 目录，其中包含软件包的压缩归档文件（例如，Linux 中的 <PACKAGE_NAME>-<VERSION>.tar.gz）。

## wheel

这是二进制分发版（bdist），支持 Windows、Mac 和 Linux。

如果你有已编译的代码扩展，Wheels 将加快安装速度，因为不需要构建步骤。wheel 分发版是当前平台的已构建分发版。可安装的 wheel 将在 dist 目录下创建，同时也会创建包含已构建代码的 build 目录。

## 设置环境变量和路径

你可能需要将路径添加到环境变量中。这允许你导入模块和函数：

使用终端打开 .bashrc 文件

```
sudo nano ~/.bashrc
```

将软件包目录的路径添加到环境变量。示例如下：

```
PYTHONPATH=/home/suhas/code/packages/prediction_model:$PYTHONPATH
```

```
export PYTHONPATH
```

然后运行 source ~/.bashrc。
重新打开终端并使用以下命令进行测试：
echo $PYTHONPATH

## 构建包

- 1. 进入项目目录并安装依赖项：
  pip install -r requirements.txt
- 2. 创建 pickle 文件：
  python prediction_model/train_pipeline.py
- 3. 创建源分发版和 wheel：
  python setup.py sdist bdist_wheel

## 安装包

进入 setup.py 文件所在的项目目录，并使用 pip 命令安装此项目：

要以可编辑或开发者模式安装软件包：

```
pip install -e .
```

- . 指的是当前目录。
- -e 指的是 --editable 模式。

软件包的普通安装：

```
pip install .
```

- . 指的是当前目录。

你可以将整个软件包推送到 GitHub 仓库。

要从 GitHub 仓库安装。

使用 git：

```
pip install git+https://github.com/suhas-ds/prediction_model.git
```

不使用 git：

```
pip install https://github.com/suhas-ds/prediction_model/tarball/master
```

或：

```
pip install https://github.com/suhas-ds/prediction_model/zipball/master
```

或：

```
pip install https://github.com/suhas-ds/prediction_model/archive/master.zip
```

构建软件包后，目录结构应如下所示：

```
prediction_model
|-- build
|   |-- bdist.linux-x86_64
|   |-- lib
|       |-- prediction_model
|-- dist
|   |-- prediction_model-0.1.0-py3-none-any.whl
|   |-- prediction_model-0.1.0.tar.gz
|-- MANIFEST.in
|-- prediction_model
|   |-- config
|   |   |-- config.py
|   |   |-- __init__.py
|   |-- datasets
|   |   |-- __init__.py
|   |   |-- test.csv
|   |   |-- train.csv
|   |-- __init__.py
|   |-- pipeline.py
|   |-- predict.py
|   |-- processing
|   |   |-- data_management.py
|   |   |-- __init__.py
|   |   |-- preprocessors.py
|   |-- trained_models
|       |-- classification_v1.pkl
|   |-- __init__.py
|   |-- train_pipeline.py
|   |-- VERSION
|   |-- prediction_model.egg-info
|   |   |-- dependency_links.txt
|   |   |-- PKG-INFO
|   |   |-- requires.txt
|   |   |-- SOURCES.txt
|   |   |-- top_level.txt
|-- README.md
|-- requirements.txt
|-- setup.py
|-- tests
|   |-- pytest.ini
|   |-- test_predict.py
```

## 包使用示例

启动 Python 控制台（在虚拟环境中）：

```
(venv_package) suhas@ds:~/code/packages$ python
```

```
Python 3.6.9

[GCC 8.4.0] on linux

Type "help", "copyright", "credits" or "license" for more information.
```

导入 prediction_model 软件包并进行预测：

```python
import prediction_model

from prediction_model import train_pipeline

from prediction_model.predict import make_prediction

import pandas as pd

train_pipeline.run_training() # Save the pickle object of the trained model
```

