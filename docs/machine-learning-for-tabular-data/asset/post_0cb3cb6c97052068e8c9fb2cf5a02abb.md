
## Exploratory data analysis

The graphical representation of features alone and their relationship with others can tell you how to act on the data. In general, first employing descriptive statistics and plots, you examine every single feature, called univariate approach. Then you examine how features relate to each other, called bivariate approach. Finally, you try to get a glimpse of all features together using multivariate techniques and dimensionality reduction such as t-SNE and UMAP.

In this phase, just after assembling your data into a tabular format, EDA can do the following:

- Inform you about the characteristics of the data such as numeric, ordinal, categorical features.
- Give you an idea of the values of each feature and how they are distributed. This is especially useful when working with neural networks where scales are important.
- Tell you if there are missing values because neural networks and some machine learning algorithms are deemed to fail in their presence.
- Locate outliers and clusters that can be aggregated.

We will show how to achieve such explorations using simple pandas commands since analyst's reasoning is more effective than automated one. However, you can also use automatic exploration tools if the number of features to explore is vast and you need to save time. Later, you can integrate the automatic EDA with specific data. Among the open-source packages for automatic EDA, there are a few notable ones that we like to suggest to you, and all of them are easy to learn and use:

- AutoViz (https://github.com/AutoML/AutoViz)
- Sweetviz (https://github.com/ydata/sweetviz)
- Pandas Profiling (https://github.com/ydata/profiling)

In the following chapters, we will reprise EDA to complete what you may need depending on the techniques (machine learning or deep learning) you want to apply to your data for predictive purposes.

### 2.9.1 Loading the Auto MPG dataset

Now, as an example of how a simple EDA can hint at ideas for further processing your data and taking necessary steps when adapting it to the model you want to use, we go for the Auto MPG Set, a dataset freely available on the UCI Machine Learning repository (https://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/). The dataset, assembled by Ernesto Ribeiro and David Hornik, originates from the StatLib library maintained at Carnegie Mellon University. Previously, it featured in the 1983 American Statistical Association Exposition (https://archive.ics.uci.edu/ml/datasets/autompg) and the works of Ross Quinlan. Ross Quinlan is a major contributor to the development of the decision tree algorithm and the creator of C4.5 and ID3 algorithms. He quotes this dataset in 1993 paper “Combining Instance-Based and Model-Based Learning”(https://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/), a milestone paper on regression problems in machine learning. For our purposes, it is a simple, manageable example because of its set of features and some missing data to be handled in the mpg and horsepower features.

The following is a list of the available features in the dataset:

- mpg: continuous
- cylinders: discrete
- displacement: continuous
- horsepower: continuous
- weight: continuous
- acceleration: continuous
- model year: discrete
- origin: discrete
- car name: string (unique for each example, it can be used as an index in a pandas DataFrame)

In our example, the list is short, but the available features can last dozens of pages in most complex tabular datasets.

To upload our example dataset, we refer to the following list that will connect to the UCI repository, and it will dump the data into a pandas DataFrame.

#### Listing 2.7 Download of Auto MPG Set from UCI repository

| StringIO reads and writes an in-memory buffer. | Requests is an HTTP library that can help you recover data from the web. |
| :--- | :--- |
| from io import StringIO | import pandas as pd |

```python
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/"
data = "auto-mpg.data-original"
columns = ["mpg","cylinders","displacement","horsepower","weight","acceleration","model_year","origin","car_name"]
colcspecs = [(0, 4), (6, 9), (12, 17), (23, 28), (34, 39), (45, 49), (52, 55), (57, 59), (61, 66)]
data_ingestion = StringIO
```

Derived from the documentation on the UCI machine learning repository, fixed-width data requires providing each feature with its start and end position in the input.

#### Exploratory data analysis

```python
requests.get(url + data).text
data = pd.read_fwf(data_ingestion, colspec=colcspecs, names=columns)
```

The dataset is read from the web by `requests.get()` and then turned into a string buffer. `pd.read_fwf` reads a table of fixed-width formatted lines into a DataFrame.

The Auto MPG data is stored in a fixed-width file, where values are on the same line, separated by a certain number of spaces or a tab. The carriage at the end of the rows signals the end of the file. The following is a sample of text file that the request library returns from the UCI Machine Learning repository:

```text
18.0   8.0 307.0      130.0 3504.0  12.0     1  1  chevrolet malibu
15.0   8.0 350.0      165.0 3693.0  11.5     1  1  buick skylark 320
18.0   8.0 318.0      150.0 3436.0  11.0     1  2  plymouth satellite
16.0   8.0 304.0      150.0 3433.0  12.0     1  1  amc rebel sst
17.0   8.0 302.0      140.0 3449.0  10.5     1  1  ford torino
```

This explains why we must use fixed-width reader such as `pandas.read_fwf` where each value starts and ends. More importantly, you can find other datasets as CSV files. If the same data had stored in CSV format, it would look like the following:

```csv
mpg,cylinders,displacement,horsepower,weight,acceleration,model_year,origin,car_name
18.0,8,307.0,130.0,3504.0,12.0,1,1,chevrolet malibu
15.0,8,350.0,165.0,3693.0,11.5,1,1,buick skylark 320
18.0,8,318.0,150.0,3436.0,11.0,1,2,plymouth satellite
16.0,8,304.0,150.0,3433.0,12.0,1,1,amc rebel sst
17.0,8,302.0,140.0,3449.0,10.5,1,1,ford torino
```

In CSV values, the features are not placed in rows; they vary in position but not in order, and you find them separated by a special character as separator. In our example, this is the comma. Please also notice that textual data, such as strings, is often delimited between quotes to avoid confusion if the text contains the separator. In such a case, you have to use the `pandas.read_csv` reader, which can handle CSV files. Depending on the situation, your data may be stored as a JSON file or an XML file, but there are readers for all formats in pandas (see table 2.2).

#### Table 2.2 Common reading methods in pandas

| Function | Description |
| :--- | :--- |
| read_csv | Reads delimited data from a file, URL or file-like object. Uses comma as the default delimiter |
| read_json | Reads data from a JSON string representation |

#### Table 2.2 Common reading methods in pandas (continued)

| Function | Description |
| :--- | :--- |
| read_xml | Imports shallow XML documents as a DataFrame |
| read_html | Reads all tables found in the given HTML document |
| read_excel | Reads tabular data from an Excel XLS or XLSX file |

### 2.9.2 Examining labels, values, distributions

All you have to do is understand what kind of data you are reading from the internet or your local disk and use the appropriate readers among the ones offered by pandas: each will be automatically handled by the proper function.

As we already have a baseline for the dataset (just read "attribute information" at https://archive.ics.uci.edu/datasets/autompg), we can immediately take note in specific variables about what features are numeric, ordinal, and categorical:

```python
numeric_feats = ["mpg", "displacement", "horsepower", "weight", "acceleration"]
ordinal_feats = ["cylinders", "model_year"]
categorical_feats = ["origin", "car_name"]
```

In different cases with datasets, you have to discover information through your data exploration. The variables will be populated by your discoveries. Hence, if we do not know the characteristics of our features, we should discover them through first data exploration which can be quickly accomplished by a few pandas commands followed by some deductions. For instance, we could ask for the first few rows and immediately get an idea of the data we are dealing with. We get just the top five rows using the .head(n) method:

```python
data.head(5)
```

The results are shown in figure 2.5.

| mpg | cylinders | displacement | horsepower | weight | acceleration | model_year | origin | car_name |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 18.0 | 8 | 307.0 | 130.0 | 3504.0 | 12.0 | 1 | 1 | chevrolet malibu |
| 15.0 | 8 | 350.0 | 165.0 | 3693.0 | 11.5 | 1 | 1 | buick skylark 320 |
| 18.0 | 8 | 318.0 | 150.0 | 3436.0 | 11.0 | 1 | 2 | plymouth satellite |
| 16.0 | 8 | 304.0 | 150.0 | 3433.0 | 12.0 | 1 | 1 | amc rebel sst |
| 17.0 | 8 | 302.0 | 140.0 | 3449.0 | 10.5 | 1 | 1 | ford torino |

Figure 2.5 Results from the data.head(5) command
