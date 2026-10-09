
## Step 2: TSLARegressor class

The `TSLARegressor` class creates a `SparkSession` object using `SparkSession.builder`, sets the application name to “TSLA_Reğression” using `appName()`, and retrieves an existing SparkSession or creates a new one using `getOrCreate()`. This SparkSession is used for Spark-related operations, such as reading data from CSV files and creating Spark DataFrames.

- `self.input_shape = None`: This line creates an instance attribute named `input_shape` and initializes it to None. This attribute is intended to store the shape of the input data for the neural network model.
- `self.model = None`: This line creates an instance attribute named `model` and initializes it to None. This attribute is intended to store the trained neural network model.

In the next steps, we define a series of methods, within the `TSLARegressor` class, for data loading, preprocessing, model creation, training, evaluation, and prediction.

### Step 3: `preprocess_data` Method Definition

In this step, we define the `preprocess_data()` method within the `TSLARegressor` class. The model’s features undergo transformation as they are assembled from the loaded data using PySpark’s `VectorAssembler`, which consolidates multiple columns into a single feature vector. Subsequently, the features are scaled using `StandardScaler` to standardize each feature’s values, ensuring a mean of 0 and a standard deviation of 1:

```python
[In]: def preprocess_data(
    self,
    file_path,
    feature_cols=['Open', 'High', 'Low', 'Volume'],
    train_ratio=0.8,
    seed=42
):
    """
    Preprocesses the data.

    Parameters:
        - file_path (str): Path to the CSV file.
        - feature_cols (list): List of feature columns.
        - train_ratio (float): Ratio of training data.
        - seed (int): Random seed for splitting data.

    Returns:
        - tuple: Tuple containing train and test DataFrames.
    """
    df = self.spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    assembler = VectorAssembler(
        inputCols=feature_cols,
        outputCol='features'
    )
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
```

This method prepares the data for training the TensorFlow neural network model.

Below is a breakdown of what it does:

- **Reading Data**: The method reads the CSV file located at `file_path` into a Spark DataFrame using PySpark’s `read.csv()` method. The `header=True` argument indicates that the first row contains column names, while `inferSchema=True` enables automatic schema inference.
- **Feature Assembly**: Using PySpark’s `VectorAssembler`, the method combines the specified feature columns (`['Open', 'High', 'Low', 'Volume']`) into a single feature vector column named `'features'`. This consolidation facilitates the processing of features as a single entity.
- **Feature Scaling**: The feature vector column `'features'` is scaled using PySpark’s `StandardScaler` to ensure that each feature has a mean of 0 and a standard deviation of 1. This normalization step helps in preventing features with large values from dominating the training process and ensures that the features contribute equally to the model.
- **Data Splitting**: Finally, the method splits the DataFrame into training and test sets using Spark’s `randomSplit()` method. The `train_ratio` parameter determines the ratio of training data, while the `seed` parameter ensures reproducibility by providing a random seed for data splitting.
- **Return**: The method returns a tuple containing the training and test DataFrames.

### Step 4: `convert_to_numpy` Method Definition

In this step, we define the `convert_to_numpy` method, which is responsible for converting Spark DataFrames, `train_df` and `test_df`, containing training and test data, respectively, into NumPy arrays:

```python
[In]: def convert_to_numpy(self, train_df, test_df):
       """
       Convert Spark DataFrames to numpy arrays.

       Parameters:
       - train_df (DataFrame): Spark DataFrame containing training data.
       - test_df (DataFrame): Spark DataFrame containing test data.

       Returns:
       - tuple: Tuple containing train and test numpy arrays
         for features and labels.
       """
       train_features = np.array(
           train_df.select('scaled_features')
           .rdd.map(lambda x: x.scaled_features.toArray())
           .collect()
       )
       train_labels = np.array(
           train_df.select('Close')
           .rdd.map(lambda x: x.Close).collect())
       test_features = np.array(
           test_df.select('scaled_features')
           .rdd.map(lambda x: x.scaled_features.toArray())
           .collect()
       )
       test_labels = np.array(
           test_df.select('Close')
           .rdd.map(lambda x: x.Close).collect()
       )
       return train_features, train_labels, \
           test_features, test_labels
```

The method `convert_to_numpy` facilitates compatibility with TensorFlow by converting Spark DataFrames into NumPy arrays, as TensorFlow typically operates with NumPy data structures. It takes two parameters: `train_df` and `test_df`, which are Spark DataFrames containing training and test data, respectively.

The method returns a tuple containing four NumPy arrays: `train_features`, `train_labels`, `test_features`, and `test_labels`. The conversion process inside the method is as follows:

- `train_features`: Converts the `'scaled_features'` column of the training DataFrame (`train_df`) into a NumPy array
- `train_labels`: Converts the `'Close'` column of the training DataFrame (`train_df`) into a NumPy array
- `test_features`: Converts the `'scaled_features'` column of the test DataFrame (`test_df`) into a NumPy array
- `test_labels`: Converts the `'Close'` column of the test DataFrame (`test_df`) into a NumPy array

In terms of implementation, the method uses Spark's `select` method to extract specific columns from the DataFrames. It then converts these columns into RDDs (Resilient Distributed Datasets) to enable parallel processing. The `map` function is applied to each row of the RDD to extract the values of the selected columns, which are then converted into NumPy arrays using the `np.array` function. Finally, the NumPy arrays are collected from the RDDs and returned as part of a tuple.

### Step 5: `create_and_train_model` Method Definition

Moving on, we define the `create_and_train_model` method, which is responsible for building and training a neural network model using TensorFlow's Keras API:

```python
[In]: def create_and_train_model(
                self,
                train_features,
                train_labels,
                epochs=100,
                batch_size=32
        ):
            """
            Create and train the neural network model.

            Parameters:
            - train_features (ndarray): Training features.
            - train_labels (ndarray): Training labels.
            - epochs (int): Number of epochs for training.
            - batch_size (int): Batch size for training.

            Returns:
            - None
            """
            self.input_shape = (train_features.shape[1],)
            self.model = Sequential([
                Dense(64, activation='relu',
                        input_shape=self.input_shape),
                Dense(32, activation='relu'),
                Dense(16, activation='relu'),
                Dense(1)
            ])
            self.model.compile(optimizer='adam', loss='mse')
            self.model.fit(
                train_features,
                train_labels,
                epochs=epochs,
                batch_size=batch_size
            )
```

The `create_and_train_model` method is responsible for creating the TensorFlow neural network model with a specified architecture and training it using the provided training features and labels.

Below is a breakdown of the method’s parameters and what it accomplishes:

**Parameters:**

- `train_features` (ndarray): NumPy array containing the training features.
- `train_labels` (ndarray): NumPy array containing the corresponding training labels.
