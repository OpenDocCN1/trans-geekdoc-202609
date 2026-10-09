
# 第9章
## 提升模型性能的技巧

### 早停（Early Stopping）

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Input, Dense
from tensorflow.keras.callbacks import EarlyStopping

class TSLARegressor:
    """
    TSLA股票价格回归类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
            .appName("TSLA_Regression") \
            .getOrCreate()
        self.input_shape = None
        self.model = None

    def preprocess_data(
        self,
        file_path,
        feature_cols=['Open', 'High', 'Low', 'Volume'],
        train_ratio=0.8,
        seed=42
    ):
        """
        预处理数据。
        
        参数：
            - file_path (str): CSV文件路径。
            - feature_cols (list): 特征列列表。
            - train_ratio (float): 训练数据比例。
            - seed (int): 用于分割数据的随机种子。
        
        返回：
            - tuple: 包含训练集和测试集数据框的元组。
        """
        
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        
        assembler = VectorAssembler(
            inputCols=feature_cols, outputCol='features')
        df = assembler.transform(df)
        scaler = StandardScaler(
                inputCol='features',
                outputCol='scaled_features',
                withMean=True,
                withStd=True
            )
        scaler_model = scaler.fit(df)
        df = scaler_model.transform(df)
        train_df, test_df = df.randomSplit(
                [train_ratio, 1-train_ratio],
                seed=seed
            )
        return train_df, test_df

    def convert_to_numpy(self, train_df, test_df):
        """
        将 Spark 数据框转换为 numpy 数组。

        参数：
            - train_df (DataFrame):
                包含训练数据的 Spark 数据框。
            - test_df (DataFrame):
                包含测试数据的 Spark 数据框。

        返回：
            - tuple:
                包含特征和标签的训练集和测试集
                numpy
                数组的元组。
        """
        train_features = np.array(
            train_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        train_labels = np.array(
            train_df.select('Close')
            .rdd.map(lambda x: x.Close).collect())
        test_features = np.array(
            test_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        test_labels = np.array(
            test_df.select('Close')
            .rdd.map(lambda x: x.Close).collect()
        )
        return (train_features,
                train_labels,
                test_features,
                test_labels
        )

    def create_and_train_model(
            self,
            train_features,
            train_labels,
            epochs=100,
            batch_size=32
    ): 
        """
        创建并训练神经网络模型。

        参数：
            - train_features (ndarray): 训练特征。
            - train_labels (ndarray): 训练标签。
            - epochs (int): 训练轮数。
            - batch_size (int): 训练批次大小。

        返回：
            - History:
                包含每个轮次
                损失值的训练历史。
        """
        self.input_shape = (train_features.shape[1],)
        self.model = Sequential([
            Dense(
                64,
                activation='relu',
                input_shape=self.input_shape
            ),
            Dense(
                32,
                activation='relu'
            ),
            Dense(
                16,
                activation='relu'
            ),
            Dense(1)
        ])
        self.model.compile(optimizer='adam', loss='mse')
        history = self.model.fit(
                train_features,
                train_labels,
                epochs=epochs,
                batch_size=batch_size,
                verbose=0
            )
            return history

    def evaluate_model(self, test_features, test_labels):
        """
        评估训练好的模型。

        参数：
            - test_features (ndarray): 测试特征。
            - test_labels (ndarray): 测试标签。

        返回：
            - float: 测试损失。
        """
        test_loss = self.model.evaluate(
            test_features,
            test_labels
        )
        return test_loss

    def predict_and_evaluate(
        self,
        test_features,
        test_labels
    ):
        """
        预测并评估神经网络模型。

        参数：
            - test_features (ndarray): 测试特征。
            - test_labels (ndarray): 测试标签。

        返回：
            - float: R2 分数。
        """
        test_predictions = self.model.predict(test_features)
        r2_score_value = r2_score(test_labels, test_predictions)
        return r2_score_value

def main(file_path):
    """
    用于编排整个工作流的主函数。
    
    参数：
    - file_path (str): CSV文件路径。
    
    返回：
    - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = tsla_regressor.preprocess_data(file_path)
        train_features, train_labels, test_features, \
        test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        history = tsla_regressor.create_and_train_model(
            train_features,
            train_labels
        )
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value=tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )

        logging.info("测试损失: {}".format(test_loss))
        logging.info("R2 分数: {}".format(r2_score_value))

        plt.plot(history.history['loss'])
        plt.title('模型损失')
        plt.xlabel('轮次')
        plt.ylabel('损失')

        plt.show()
    except Exception as e:
        logging.error(f"发生错误: {e}")

if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

### Dropout（随机丢弃）

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.layers import Dropout

class TSLARegressor:
    """
    TSLA股票价格回归类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
            .appName("TSLA_Regression") \
            .getOrCreate()
        self.input_shape = None
        self.model = None
    def preprocess_data(
        self,
