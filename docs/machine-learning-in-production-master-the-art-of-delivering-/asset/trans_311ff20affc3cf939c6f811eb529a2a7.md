

```
joblib.dump(pipeline_to_save, save_path)
print("Saved Pipeline : ", save_file_name)

def load_pipeline(pipeline_to_load):
    """Importing pickle file of trained Model"""
    save_path = os.path.join(config.SAVED_MODEL_PATH, pipeline_to_load)
    trained_model = joblib.load(save_path)
    return trained_model
```

## preprocessors.py

此模块包含 sklearn 管道所需的所有拟合和转换函数：

```
# Import Libraries
import pandas as pd
import numpy as np
from sklearn.base import BaseEstimator, TransformerMixin
from sklearn.preprocessing import LabelEncoder

# Import other files/modules
from prediction_model.config import config
```

使用特征的均值来填补缺失的数值。但是，你也可以使用其他缺失值填补技术，例如随机回归填补、插值和冷卡填补。

```
# Numerical Imputer
class NumericalImputer(BaseEstimator, TransformerMixin):
    """Numerical Data Missing Value Imputer"""
    def __init__(self, variables=None):
        self.variables = variables

    def fit(self, X, y=None):
        self.imputer_dict_ = {}
        for feature in self.variables:
            self.imputer_dict_[feature] = X[feature].mean()
        return self

    def transform(self, X):
        X = X.copy()
        for feature in self.variables:
            X[feature].fillna(self.imputer_dict_[feature], inplace=True)
        return X
```

使用特征的最频繁值来填补缺失的类别值，但你也可以使用其他缺失值填补技术，例如缺失指示器填补、**多元连锁方程插补 (MICE)** 算法和系统随机抽样填补。

```
# Categorical Imputer
class CategoricalImputer(BaseEstimator, TransformerMixin):
    """Categorical Data Missing Value Imputer"""
    def __init__(self, variables=None):
        self.variables = variables

    def fit(self, X, y=None):
        self.imputer_dict_ = {}
        for feature in self.variables:
            self.imputer_dict_[feature] = X[feature].mode()[0]
        return self

    def transform(self, X):
        X = X.copy()
        for feature in self.variables:
            X[feature].fillna(self.imputer_dict_[feature], inplace=True)
        return X
```

随后，对类别特征进行编码以用于模型训练。

```
# Categorical Encoder
class CategoricalEncoder(BaseEstimator, TransformerMixin):
    """Categorical Data Encoder"""
    def __init__(self, variables=None):
        self.variables = variables

    def fit(self, X, y):
        self.encoder_dict_ = {}
        for var in self.variables:
            t = X[var].value_counts().sort_values(ascending=True).index
            self.encoder_dict_[var] = {k: i for i, k in enumerate(t, 0)}
        return self

    def transform(self, X):
        X = X.copy()
        # This part assumes that the encoder does not introduce a NANs
        # In that case, a check needs to be done and the code should break
        for feature in self.variables:
            X[feature] = X[feature].map(self.encoder_dict_[feature])
        return X
```

以下代码片段用于创建新特征：

```
# Temporal Variables
class TemporalVariableEstimator(BaseEstimator, TransformerMixin):
    """Feature Engineering"""
    def __init__(self, variables=None, reference_variable=None):
        self.variables = variables
        self.reference_variable = reference_variable

    def fit(self, X, y=None):
        # No need to put anything, needed for Sklearn Pipeline
        return self

    def transform(self, X):
        X = X.copy()
        for var in self.variables:
            X[var] = X[var] + X[self.reference_variable]
        return X
```

对变量应用对数变换，使数据中的模式更具可解释性。

```
# Log Transformations
class LogTransformation(BaseEstimator, TransformerMixin):
    """Transforming variables using Log Transformations"""
    def __init__(self, variables=None):
        self.variables = variables

    def fit(self, X, y):
        return self

    # Need to check in advance if the features are <= 0
    # If yes, needs to be transformed properly (E.g., np.log1p(X[var]))
    def transform(self, X):
        X = X.copy()
        for var in self.variables:
            X[var] = np.log(X[var])
        return X
```

以下代码片段用于删除对模型不重要的特征：

```
# Drop Features
class DropFeatures(BaseEstimator, TransformerMixin):
    """Dropping Features Which Are Less Significant"""
    def __init__(self, variables_to_drop=None):
        self.variables_to_drop = variables_to_drop

    def fit(self, X, y=None):
        return self

    def transform(self, X):
        X = X.copy()
        X = X.drop(self.variables_to_drop, axis=1)
        return X
```

## _pipeline.py_

本模块中使用了 sklearn 管道。模型可以在没有 sklearn 管道的情况下部署，但建议构建 sklearn 管道。管道的目的是组装多个步骤，以便在设置不同参数的同时一起进行交叉验证。

```
# Import Libraries
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import MinMaxScaler
from sklearn.linear_model import LogisticRegression

# Import other files/modules
from prediction_model.config import config
import prediction_model.processing.preprocessors as pp

loan_pipe = Pipeline([
    ('Numerical Imputer', pp.NumericalImputer(variables=config.NUMERICAL_FEATURES)),
    ('Categorical Imputer', pp.CategoricalImputer(variables=config.CATEGORICAL_FEATURES)),
    ('Temporal Features',
     pp.TemporalVariableEstimator(variables=config.TEMPORAL_FEATURES,
                                  reference_variable=config.TEMPORAL_ADDITION)),
    ('Categorical Encoder',
     pp.CategoricalEncoder(variables=config.FEATURES_TO_ENCODE)),
    ('Log Transform', pp.LogTransformation(variables=config.LOG_FEATURES)),
    ('Drop Features', pp.DropFeatures(variables_to_drop=config.DROP_FEATURES)),
    ('Scaler Transform', MinMaxScaler())),
    ('Linear Model', LogisticRegression(random_state=1))
])
```

## predict.py

一个 `predict.py` 模块加载保存的 ML 模型 (`.pkl`) 并对新数据进行预测。

```
# Import Libraries
import pandas as pd
import numpy as np
import joblib

# Import other files/modules
from prediction_model.config import config
from prediction_model.processing.data_management import load_pipeline

pipeline_file_name = 'classification_v1.pkl'

_loan_pipe = load_pipeline(pipeline_file_name)


def make_prediction(input_data):
    """Predicting the output"""

    # Read Data
    data = pd.DataFrame(input_data)

    # prediction
    prediction = _loan_pipe.predict(data[config.FEATURES])
    output = np.where(prediction == 1, 'Y', 'N').tolist()
    results = {'prediction': output}
    return results
```

## requirements.txt

本文件包含以下库：

```
# Model Building Requirements
joblib==0.16.0
numpy==1.19.0
pandas==1.0.5
scikit-learn==0.23.1
scipy==1.5.1
sklearn==0.0

# testing requirements
pytest<5.0.0,>=4.6.6

# packaging
setuptools==40.6.3
wheel==0.32.3
```

## classification_v1.pkl

这是来自训练模型的 pickle 文件。

## train_pipeline.py

此模块加载训练数据并将其传递给管道，然后将模型的 pickle 文件保存到本地目录。

```
# Import Libraries
import pandas as pd
import numpy as np

# Import other files/modules
from prediction_model.config import config
from prediction_model.processing.data_management import load_dataset, save_pipeline
import prediction_model.processing.preprocessors as pp
import prediction_model.pipeline as pl
from prediction_model.predict import make_prediction


def run_training():
    """Train the model"""
    # Read Data
    train = load_dataset(config.TRAIN_FILE)

    # separating Loan_status in y
    y = train[config.TARGET].map({'N': 0, 'Y': 1})
    pl.loan_pipe.fit(train[config.FEATURES], y)
    save_pipeline(pipeline_to_save=pl.loan_pipe)
```

