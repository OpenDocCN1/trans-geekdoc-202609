TSLARegressor class. It creates a SparkSession object using SparkSession.builder, sets the application name to “TSLA_Reğression” using appName(), and retrieves an existing SparkSession or creates a new one using getOrCreate(). This SparkSession is used for Spark-related operations, such as reading data from CSV files and creating Spark DataFrames.

+   - self.input\_shape = None: This line creates an instance attribute named input\_shape and initializes it to None. This attribute is intended to store the shape of the input data for the neural network model.

+   - self.model = None: This line creates an instance attribute named model and initializes it to None. This attribute is intended to store the trained neural network model.

In the next steps, we define a series of methods, within the TSLARegressor class, for data loading, preprocessing, model creation, training, evaluation, and prediction.

# Step 3: preprocess\_data Method Definition

In this step, we define the preprocess\_data() method within the TSLARegressor class. The model’s features undergo transformation as they are assembled from the loaded data using PySpark’s VectorAssembler, which consolidates multiple columns into a single feature vector. Subsequently, the features are scaled using StandardScaler to standardize each feature’s values, ensuring a mean of 0 and a standard deviation of 1:

```
[In]: def preprocess\_data(
    self,
    file\_path,
    feature\_cols=['Open', 'High', 'Low', 'Volume'],
    train\_ratio=0.8,
```