
21. if __name__ == '__main__':
22.     run_training()

## setup.py

To configure and install packages from the source directory, create a setup.py file. It is specific to the package. PIP will use the setup.py file to install packages. Go to the directory where the setup.py file is located and install the packages using the pip install . (period) command.

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

This file holds the version of the package. Here, a **major.minor.micro** scheme is used.

```
0.1.0
```

## pytest.ini

To disable warnings while running pytest, you have to configure the pytest.ini file.

```
[pytest]
addopts = -p no:warnings
```

## test_predict.py

It fetches a single record from the validation data and verifies the output using **assert** statements.

It validates the following checks:

- The output is not null.
- The output data type is **str**.
- The output is **Y** for given data (fixed).

These checks are run using pytest.

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

Set the environment variable PYTHONPATH and go to the package directory, and then run the following command:

```
pytest -v
```

If everything goes well, you should get an output as follows:

![](img/cc4299656808e62a294f1843a1e18e72_94_0.png)

Figure 4.3: pytest output

## sdist

Python’s sdists are compressed archives (.tar.gz files) containing one or more packages or modules.

This creates a dist directory containing a compressed archive of the package (for example, <PACKAGE_NAME>-<VERSION>.tar.gz in Linux).

## wheel

This is the binary distribution or bdist, and it supports Windows, Mac, and Linux.

Wheels will speed up the installation if you have compiled code extensions, as the build step is not required. A wheel distribution is a built distribution for the current platform. The installable wheel will be created under the dist directory, and a build directory will also be created with the built code.

## Set up environment variables and paths

You may need to add the path to the environment variables. It allows you to import modules and functions:

Open the .bashrc file using terminal

```
sudo nano ~/.bashrc
```

Add the path to the package directory. Here’s an example:

```
PYTHONPATH=/home/suhas/code/packages/prediction_model:$PYTHONPATH
```

```
export PYTHONPATH
```

Then run source ~/.bashrc.
Reopen the terminal and test using the following:
echo $PYTHONPATH

## Build the package

- 1. Go to the project directory and install dependencies:
  pip install -r requirements.txt
- 2. Create a pickle file:
  python prediction_model/train_pipeline.py
- 3. Creating a source distribution and wheel:
  python setup.py sdist bdist_wheel

## Install the package

Go to the project directory where the setup.py file is located and install this project with the pip command:

To install the package in editable or developer mode:

```
pip install -e .
```

- . refers to the current directory.
- -e refers to --editable mode.

Normal installation of the package:

```
pip install .
```

- . refers to the current directory.

You can push the entire package to the GitHub repository.

To install it from the GitHub repository.

With git:

```
pip install git+https://github.com/suhas-ds/prediction_model.git
```

Without git:

```
pip install https://github.com/suhas-ds/prediction_model/tarball/master
```

Or:

```
pip install https://github.com/suhas-ds/prediction_model/zipball/master
```

Or:

```
pip install https://github.com/suhas-ds/prediction_model/archive/master.zip
```

After building the package, your directory structure should look like this:

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

## Package usage with example

Start a Python console (in a virtual environment):

```
(venv_package) suhas@ds:~/code/packages$ python
```

```
Python 3.6.9

[GCC 8.4.0] on linux

Type "help", "copyright", "credits" or "license" for more information.
```

Import the prediction_model package and make the predictions:

```python
import prediction_model

from prediction_model import train_pipeline

from prediction_model.predict import make_prediction

import pandas as pd

train_pipeline.run_training() # Save the pickle object of the trained model
```
