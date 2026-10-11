
## 3.2.1 Handling Missing Numerical Data

One of the most commonly occurring data types is numeric data, which consists of numbers. To handle missing numerical data, we can use statistical techniques. The use of statistical techniques or algorithms to replace missing values with statistically generated values is called imputation. Complete case analysis (CCA), also known as list wise deletion is the most basic technique for handling missing data. In CCA, you simply move all the rows or records where any column or field contain a missing value. Only those records are processed where an actual value is present for all the columns in the dataset.

### Mean or Median Imputation

In mean or median imputation, missing values in a column are replaced by the mean or median of all the remaining values in that particular column. For instance, if you have a column with the following data:

![](Image00083.jpg)

In the above Age column, the second value is missing. Therefore, with mean and median imputation, you can replace the second value with either the mean or median of all the other values in the column. For instance, the following column contains the mean of all the remaining values, i.e., 25 in the second row. You could also replace this value with median if you want.

![](Image00084.jpg)

Let’s see a practical example of mean and median imputation. We will import the Titanic dataset and find the columns that contain missing values. Then, we will apply mean and median imputation to the columns containing missing values, and, finally, we will see the effect of applying mean and median imputation to the missing values. You do not need to download the Titanic dataset. If you import the Seaborn library, the Titanic data will be downloaded with it. The following script imports the Titanic dataset and displays its first five rows.

**Script 14:**
![](Image00085.jpg)

**Output:**
![](Image00086.jpg)

Let’s filter some of the numeric columns from the dataset and see if they contain any missing values.

**Script 15:**
![](Image00087.jpg)

**Output:**
![](Image00088.jpg)

To find the missing values from the aforementioned columns, you need to first call the `isnull()` method on the `titanic_data` dataframe, and then, you need to call the `mean()` method, as shown below:

**Script 16:**
![](Image00089.jpg)

**Output:**

| survived | | 0.000000 |
| --- | --- | --- |
| pclass | | 0.000000 |
| age | | 0.198653 |
| fare | | 0.000000 |
| dtype: | | float64 |

The output shows that only the `age` column contains missing values. And the ratio of missing values is around 19.86 percent. Let’s now find out the median and mean values for all the non-missing values in the `age` column.

**Script 17:**
![](Image00090.jpg)

**Output:** 28.0 29.69911764705882

The `age` column has a median value of 28 and a mean value of 29.6991. To plot the kernel density plots for the actual age and median and mean age, we will add columns to the Pandas dataframe.

**Script 18:**
![](Image00091.jpg)

The above script adds `Median_Age` and `Mean_Age` columns to the `titanic_data` dataframe and prints the first 20 records. Here is the output of the above script:

**Output:**
![](Image00092.jpg)

The highlighted rows in the above output show that NaN, i.e., null values in the `age` column have been replaced by the median values in the `Median_Age` column and by mean values in the `Mean_Age` columns. The mean and median imputation can affect the data distribution for the columns containing the missing values. Especially, the variance of the column is decreased by mean and median imputation since now more values are added to the center of the distribution. The following script plots the distribution of data for the `age`, `Median_Age`, and `Mean_Age` columns.

**Script 19:**
![](Image00093.jpg)

Here is the output of the script above:
![](Image00094.jpg)

You can clearly see that the default values in the age columns have been distorted by mean and median imputation, and the overall variance of the dataset has also been decreased.

### End of Distribution Imputation

The mean and median imputation and the CCA are not good techniques for missing value imputations in case the data is not randomly missing. For randomly missing data, the most commonly used techniques are end of distribution/end of tail imputation. In the end of tail imputation, a value is chosen from the tail end of the data. This value signifies that the actual data for the record was missing. Hence, data that is not randomly missing can be taken to account while training statistical models on the data. In case the data is normally distributed, the end of the distribution value can be calculated by multiplying the mean with three standard deviations. In the case of skewed data distributions, the Inter Quartile Rule can be used to find the tail values.

```
IQR = 75th Quantile – 25th Quantile
Upper IQR Limit = 75th Quantile + IQR x 1.5
Lower IQR Limit = 25th Quantile – IQR x 1.5
```

Let’s perform the end of tail imputation on the `age` column of the Titanic dataset. The following script imports the Titanic dataset, filters the numeric columns, and then finds the percentage of missing values in each column.

**Script 20:**
![](Image00095.jpg)

**Output:**

| survived | | 0.000000 |
| --- | --- | --- |
| pclass | | 0.000000 |
| age | | 0.198653 |
| fare | | 0.000000 |
| dtype: | | float64 |

The above output shows that only the `age` column has missing values, which are around 20 percent of the whole dataset. The next step is plotting the data distribution for the `age` column. A histogram can reveal the data distribution of a column.

**Script 21:**
![](Image00096.jpg)

**Output:**
![](Image00097.jpg)

The output shows that the `age` column has an almost normal distribution. Hence, the end of distribution value can be calculated by multiplying the mean value of the `age` column by three standard deviations, as shown in the following script:

**Script 22:**
![](Image00098.jpg)

**Output:** 73.278

Finally, the missing values in the `age` column can be replaced by the end of tail value calculated in script 22.

**Script 23:**
![](Image00099.jpg)

**Output:**
![](Image00100.jpg)

The above output shows that the end of distribution value i.e., -73 has replaced the NaN values in the `age` column. Finally, you can plot the kernel density estimation plot for the original `age` column and the `age` column with the end of distribution imputation.

**Script 24:**
![](Image00101.jpg)

**Output:**
![](Image00102.jpg)

## 3.2.2 Handling Missing Categorical Data

### Frequent Category Imputation

One of the most common ways of handling missing values in a categorical column is to replace the missing values with the most frequently occurring values, i.e., the mode of the column. Let’s see a real-world example of the frequent category imputation. We will again use the Titanic dataset. We will first try to find the percentage of missing values in the `age`, `fare`, and `embarked_town` columns.

**Script 25:**
![](Image00103.jpg)

**Output:**

| embark_town | | 0.002245 |
| --- | --- | --- |
| age | | 0.198653 |
| fare | | 0.000000 |
| dtype: | | float64 |

The output shows that `embark_town` and `age` columns have missing values. The ratio of missing values for the `embark_town` column is very less. Let’s plot the bar plot that shows each category in the `embark_town` column against the number of passengers.

**Script 26:**
![](Image00104.jpg)

The output clearly shows that most of the passengers embarked from Southampton.

**Output:**
![](Image00105.jpg)

Let’s make sure if Southampton is actually the mode value for the `embark_town` column.

**Script 27:**
![](Image00106.jpg)

**Output:**

| 0 | | Southampton |
| --- | --- | --- |
| dtype: | | object |
