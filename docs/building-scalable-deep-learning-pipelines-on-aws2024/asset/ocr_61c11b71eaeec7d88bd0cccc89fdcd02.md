```
test_loss = tsla_regressor.evaluate_model(
   test_features,
   test_labels
)
r2_score_value = tsla_regressor.predict_and_
evaluate(
   test_features,
   test_labels
)

logging.info("Test Loss: {}".
   format(test_loss))
logging.info("R2 Score: {}".format(r2_
   score_value))

except Exception as e:
   logging.error(f"An error occurred: {e}")
[In]: if __name__ == "__main__":
   logging.basicConfig(level=logging.INFO)
   file_path = "/home/ubuntu/airflow/dags/TSLA_
   stock.csv"
   main(file_path)
```

# L2 Regularization

```
[In]: import logging
[In]: import numpy as np
[In]: import tensorflow as tf
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler,
   StandardScaler
[In]: from sklearn.metrics import r2_score
```