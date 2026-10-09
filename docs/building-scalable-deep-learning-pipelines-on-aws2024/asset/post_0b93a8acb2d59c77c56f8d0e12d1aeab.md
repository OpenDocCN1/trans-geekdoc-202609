
## 代码实现

```python
y_train,
epochs=100,
lr=0.01
):
    """Trains the TensorFlow (Keras) model."""
    try:
        model = Sequential([
            Dense(64, input_dim=X_train.shape[1]),
            ReLU(),
            Dense(32),
            ReLU(),
            Dense(16),
            ReLU(),
            Dense(1, activation='sigmoid')
        ])
        optimizer = SGD(learning_rate=lr)
        model.compile(loss='binary_crossentropy',
                      optimizer=optimizer,
                      metrics=['accuracy'])
        custom_callback = CustomCallback()
        model.fit(
            X_train,
            y_train,
            epochs=epochs,
            verbose=0,
            callbacks=[custom_callback]
        )
        logger.info("Model training completed.")
        return model
    except Exception as e:
        logger.error(
            f"Error occured during "
            f"model training: {str(e)}"
        )
```

In this code:

- The docstring `"""Class for training the TensorFlow (Keras) model."""` provides a brief description of the purpose of this class.
- Inside the class, there’s a static method `train_tensorflow_model(X_train, y_train, epochs=100, lr=0.01)`, which is responsible for training the TensorFlow (Keras) model. This method takes four arguments: `X_train` (the input features for training), `y_train` (the target labels for training), `epochs` (the number of epochs for training, with a default value of 100), and `lr` (the learning rate for the optimizer, with a default value of 0.01). The `@staticmethod` decorator is used to declare this method as a static method, indicating that it does not require access to the instance or its attributes and can be called directly on the class without needing to create an instance of `DiabetesModelTrainer`.
- Within the method, a neural network model is defined using Keras’s Sequential API. This model consists of several fully connected (Dense) layers with rectified linear unit (ReLU) activation functions, ending with an output layer with a sigmoid activation function.
- An optimizer (stochastic gradient descent with a specified learning rate) is configured, and the model is compiled with a binary cross-entropy loss function and accuracy as the evaluation metric.
- A custom callback (`CustomCallback`) is instantiated to log information during model training.
- The fit method is called on the model object with the input features (`X_train`) and target labels (`y_train`) to train the model for the specified number of epochs. The `custom_callback` is passed to the `callbacks` argument to enable logging of epoch information during training.
- Upon successful completion of model training, a log message is generated indicating that the model training has been completed, and the trained model is returned.
- Error handling is implemented using a try-except block to catch any exceptions that may occur during the model training process. If an exception occurs, an error message is logged using `logger.error()`. This ensures that any issues encountered during model training are appropriately handled and logged for debugging purposes.

## Step 6: Model Evaluation

In this step, we define the `DiabetesModelEvaluator` class, which is responsible for evaluating the TensorFlow (Keras) model trained for diabetes prediction. It includes methods for assessing the performance of the model using various evaluation metrics such as accuracy, precision, recall, and F1 score:

```python
class DiabetesModelEvaluator:
    """Class for evaluating the TensorFlow (Keras)
    model."""
    @staticmethod
    def evaluate_model(model, X_test, y_test):
        """Evaluates the TensorFlow (Keras) model."""
        try:
            y_pred = (model.predict(X_test) > 0.5).astype(int)
            accuracy = accuracy_score(y_test, y_pred)
            precision = precision_score(y_test, y_pred)
            recall = recall_score(y_test, y_pred)
            f1 = f1_score(y_test, y_pred)
            logger.info(f"Accuracy: {accuracy:.4f}")
            logger.info(f"Precision: {precision:.4f}")
            logger.info(f"Recall: {recall:.4f}")
            logger.info(f"F1 Score: {f1:.4f}")
        except Exception as e:
            logger.error(
                f"Error occurred during model "
                f"evaluation: {str(e)}"
            )
```

Let's take a closer look at the code:

- The docstring `"""Class for evaluating the TensorFlow (Keras) model."""` provides a brief description of the purpose of this class.
- Inside the class, there's a static method `evaluate_model(model, X_test, y_test)`, which evaluates the performance of the TensorFlow (Keras) model. This method takes three arguments: `model` (the trained Keras model), `X_test` (the input features for testing), and `y_test` (the true labels for testing). The `@staticmethod` decorator is used to declare this method as a static method, indicating that it does not require access to the instance or its attributes and can be called directly on the class without needing to create an instance of `DiabetesModelEvaluator`.
- Within the method, predictions are generated using the trained model (`model.predict(X_test)`) and thresholded to obtain binary predictions. Several evaluation metrics, including accuracy, precision, recall, and F1 score, are computed using Scikit-Learn’s metric functions (`accuracy_score`, `precision_score`, `recall_score`, and `f1_score`, respectively).
- Evaluation results, including accuracy, precision, recall, and F1 score, are logged using the `logger` at an information level to provide insights into the model’s performance.
- Error handling is implemented using a try–except block to catch any exceptions that may occur during the evaluation process. If an exception occurs, an error message is logged using `logger.error()`. This ensures that any issues encountered during model evaluation are appropriately handled and logged for debugging purposes.

## Step 7: Main

In this final step, we define the main function, which ensures that the following code is only executed when the script is run directly, not when it’s imported as a module into another script:

```python
if __name__ == "__main__":

    try:
        spark = (SparkSession.builder
                 .appName("DiabetesClassification")
                 .config("spark.executor.instances", "4")
                 .config("spark.executor.memory", "4g")
                 .config("spark.executor.cores", "2")
                 .config("spark.driver.memory", "2g")
                 .getOrCreate())
        
        data_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
        
        train_parquet_path = \
            "/home/ubuntu/airflow/dags/diabetes_train.parquet"
        
        test_parquet_path = \
            "/home/ubuntu/airflow/dags/diabetes_test.parquet"
        
        DiabetesProcessor.preprocess_data(
            spark,
            data_file_path,
            train_parquet_path,
            test_parquet_path
        )
        
        train_diabetes_df = spark.read.parquet(train_parquet_path)
        
        X_train = np.array(train_diabetes_df.select("scaled_features").rdd.flatMap(lambda x: x).collect())
        y_train = np.array(train_diabetes_df.select("Outcome").rdd.flatMap(lambda x: x).collect())

        trained_model = DiabetesModelTrainer.train_tensorflow_model(X_train, y_train)

        test_diabetes_df = spark.read.parquet(test_parquet_path)
        X_test = np.array(test_diabetes_df.select("scaled_features").rdd.flatMap(lambda x: x).collect())
        y_test = np.array(test_diabetes_df.select("Outcome").rdd.flatMap(lambda x: x).collect())

        DiabetesModelEvaluator.evaluate_model(trained_model, X_test, y_test)

    except Exception as e:
        logger.error(f"An error occurred: {str(e)}")
```

Below is an explanation of this code:

- The `if __name__ == "__main__":` block is the entry point of the Python script. It ensures that the following code is only executed when the script is run directly, not when it’s imported as a module into another script.
- Inside the try block, several steps are executed to preprocess diabetes data, train a TensorFlow (Keras) model, and evaluate its performance. These steps are enclosed in a try–except block to handle any potential exceptions.
- First, a SparkSession is created using the `SparkSession.builder` API. The SparkSession serves as the entry point to Spark functionality, allowing the script to interact with Spark and perform distributed data processing.
- The SparkSession is configured with various properties such as the application name (`appName`), number of executor instances (`spark.executor.instances`), executor memory (`spark.executor.memory`), executor cores (`spark.executor.cores`), and driver memory (`spark.driver.memory`). These configurations optimize resource allocation for data processing tasks.
- Paths to the input diabetes data file (`data_file_path`), preprocessed training data Parquet file (`train_parquet_path`), and preprocessed test data Parquet file (`test_parquet_path`) are defined.
- The `DiabetesProcessor.preprocess_data()` method is called to preprocess the diabetes data using PySpark. This method reads the raw diabetes data from the CSV file, applies data cleaning and feature engineering
