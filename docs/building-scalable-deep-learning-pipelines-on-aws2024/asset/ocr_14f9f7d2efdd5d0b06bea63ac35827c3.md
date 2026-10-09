```
) 
history = tsla_regressor.create_and_
train_model(
train_features,
train_labels
)
test_loss = tsla_regressor.evaluate_model(
test_features,
test_labels
)
r2_score_value = tsla_regressor.predict_and_
evaluate(
test_features,
test_labels
)

logging.info("Test Loss: {}".format(test_loss))
logging.info("R2 Score: {}".format(r2_
score_value))

except Exception as e:
logging.error(f"An error occurred: {e}")

[In]: if __name__ == "__main__":
logging.basicConfig(level=logging.INFO)
file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
main(file_path)
```

# # L1 Regularization

```
[In]: import logging
[In]: import numpy as np
[In]: import tensorflow as tf
```