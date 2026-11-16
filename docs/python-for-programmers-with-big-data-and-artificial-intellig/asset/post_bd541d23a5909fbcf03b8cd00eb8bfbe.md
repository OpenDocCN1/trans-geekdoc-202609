
![](img/34b7fc2f1ee27beb73bca14927d42340_655_0.png)

Iris virginica: https://commons.wikimedia.org/wiki/File:IMG_7911-Iris_virginica.jpg.

Credit: Christer T Johansson.

## 14.7.1 Loading the Iris Dataset

Launch IPython with ipython --matplotlib, then use the sklearn.datasets module's load_iris function to get a Bunch containing the dataset:

Click here to view code image

```python
In [1]: from sklearn.datasets import load_iris
In [2]: iris = load_iris()
```

The Bunch's DESCR attribute indicates that there are 150 samples (Number of Instances), each with four features (Number of Attributes). There are no missing values in this dataset. The dataset classifies the samples by labeling them with the integers 0, 1 and 2, representing Iris setosa, Iris versicolor and Iris virginica, respectively. We'll ignore the labels and let the k-means clustering algorithm try to determine the samples' classes. We show some key DESCR information in bold.:

Click here to view code image

```python
In [3]: print(iris.DESCR)
.. _iris_dataset:

Iris plants dataset
--------------------------------

**Data Set Characteristics:**

:Number of Instances: 150 (50 in each  of three classes)
:Number of Attributes: 4  numeric, predictive attributes and the class
:Attribute Information:
    - sepal length in cm
    - sepal width in cm
    - petal length in cm
    - petal width in cm
    - class:
        - Iris-Setosa
        - Iris-Versicolour
        - Iris-Virginica

:Summary Statistics:

| | Min | Max | Mean | SD | Class Correlation |
|---|---|---|---|---|---|
| sepal length: | 4.3 | 7.9 | 5.84 | 0.83 | 0.7826 |
| sepal width: | 2.0 | 4.4 | 3.05 | 0.43 | -0.4194 |
| petal length: | 1.0 | 6.9 | 3.76 | 1.76 | 0.9490 (high!) |
| petal width: | 0.1 | 2.5 | 1.20 | 0.76 | 0.9565 (high!) |

:Missing Attribute Values: None
:Class Distribution: 33.3% for each of 3 classes.
:Creator: R.A. Fisher
:Donor: Michael Marshall   (MARSHALL%PLU@io.arc.nasa.gov)
:Date: July, 1988
```

The famous Iris database, first used by Sir R.A. Fisher.  The dataset is ... the UCI Machine Learning Repository, which has two wrong ... data points.

This is perhaps the best known database to be found in the pattern recognition literature.  Fisher's paper is a classic in the field and is referenced frequently to this day.  (See Duda & Hart, for example.) refers to a type of iris plant. One class is linearly separable from the other 2; the latter are NOT linearly separable from each other.

### References

- Fisher, R.A. "The use of multiple measurements in taxonomic problems" Annual Eugenics, 7, Part II, 179–188 (1936); also in "Contributions to Mathematical Statistics" (John Wiley, NY, 1950).
- Duda, R.O., & Hart, P.E. (1973) Pattern Classification and Scene Analysis. (Q327.D83) John Wiley & Sons. ISBN 0-471-22361-1. See page 218.
- Dasarathy, B.V. (1980) "Nosing Around the Neighborhood: A New System Structure and Classification Rule for Recognition in Partially Exposed Environments". IEEE Transactions on Pattern Analysis and Machine Intelligence, Vol. PAMI-2, No. 1, 67–71.
- Gates, G.W. (1972) "The Reduced Nearest Neighbor Rule". IEEE Transactions on Information Theory, May 1972, 431–433.
- See also: 1988 MLC Proceedings, 54–64. Cheeseman et al's AUTOCLASS II conceptual clustering system finds 3 classes in the data.
- Many, many more ...

## Checking the Numbers of Samples, Features and Targets

You can confirm the number of samples and features per sample via the data array's shape, and you can confirm the number of targets via the target array's shape:

Click here to view code image

```python
In [4]: iris.data.shape
Out[4]: (150, 4)

In [5]: iris.target.shape
Out[5]: (150,)
```

The array target_names contains the names for the target array's numeric labels —dtype='<U10' indicates that the elements are strings with a maximum of 10 characters:

Click here to view code image

```python
In [6]: iris.target_names
Out[6]: array(['setosa', 'versicolor', 'virginica'],  dtype='<U10')
```

The array feature_names contains a list of string names for each column in the data array:

Click here to view code image

```python
In [7]: iris.feature_names
Out[7]:
['sepal length (cm)',
 'sepal width (cm)',
 'petal length (cm)',
 'petal width (cm)']
```

## 14.7.2 Exploring the Iris Dataset: Descriptive Statistics with Pandas

Let's use a DataFrame to explore the Iris dataset. As we did in the California Housing case study, let's set the pandas options for formatting the column-based outputs:

Click here to view code image

```python
In [8]: import pandas as pd

In [9]: pd.set_option('max_columns', 5)

In [10]: pd.set_option('display.width', None)
```

Create a DataFrame containing the data array's contents, using the contents of the feature_names array as the column names:

Click here to view code image

```python
In [11]: iris_df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

Next, add a column containing each sample's species name. The list comprehension in the following snippet uses each value in the target array to look up the corresponding species name in the target_names array:

Click here to view code image

```python
In [12]: iris_df['species'] = [iris.target_names[i] for i in iris.target]
```

Let's use pandas' to look at a few samples. Once again notice that pandas displays a \ to the right of the column heads to indicate that there are more columns displayed below:

Click here to view code image

```python
In [13]: iris_df.head()
Out[13]:
     sepal length (cm)  sepal width (cm)  petal length (cm)  \
0              5.1              3.5              1.4
1              4.9              3.0              1.4
2              4.7              3.2              1.3
3              4.6              3.1              1.5
4              5.0              3.6              1.4

     petal width (cm) species  
0             0.2  setosa  
1             0.2  setosa  
2             0.2  setosa  
3             0.2  setosa  
4             0.2  setosa 
```

### Let's calculate some descriptive statistics for the numerical columns:

Click here to view code image

```python
In [14]: pd.set_option('precision', 2)

In [15]: iris_df.describe()
Out[15]:
     sepal length (cm)  sepal width (cm)  petal length  (cm)  \
count           150.00          150.00          150.00
mean              5.84            3.06            3.76
std               0.83            0.44            1.77
min               4.30            2.00            1.00
25%               5.10            2.80            1.60
50%               5.80            3.00            4.35
75%               6.40            3.30            5.10
max               7.90            4.40            6.90

     petal width (cm)
count          150.00
mean             1.20
std              0.76
min              0.10
25%              0.30
50%              1.30
75%              1.80
max              2.50
```

Calling the describe method on the 'species' column confirms that it contains three unique values. Here, we know in advance of working with this data that there are three classes to which the samples belong, though this is not always the case in unsupervised machine learning.

Click here to view code image

```python
In [16]: iris_df['species'].describe()
Out[16]:
count    150
unique     3
top     setosa
freq      50
Name: species, dtype: object
```

## 14.7.3 Visualizing the Dataset with a Seaborn pairplot

Let's visualize the features in this dataset. One way to learn more about your data is to see how the features relate to one another. The dataset has four features. We cannot graph one against the other three in a single graph. However, we can plot pairs of features against one another. Snippet [20] uses Seaborn function pairplot to create a grid of graphs plotting each feature against itself and the other specified features:

Click here to view code image

```python
In [17]: import seaborn as sns
In [18]: sns.set(font_scale=1.1)
In [19]: sns.set_style('whitegrid')
In [20]: grid = sns.pairplot(data=iris_df,   vars=iris_df.columns[0:4],
        ...:                 hue='species')
        ...:
```

The keyword arguments are:

- data—The DataFrame ³ containing the data to plot.

³This also may be a two-dimensional array or list.

- vars—A sequence containing the names of the variables to plot. For a DataFrame, these are the names of the columns to plot. Here, we use the first four DataFrame columns, representing the sepal length, sepal width, petal length and petal width, respectively.

- hue—The DataFrame column that's used to determine colors of the plotted data. In this case, we'll color the data by Iris species.
