
## Quantamental Investing Model

The fundamental data dataset we are going to use contains the financial statements of a set of companies listed on the market. This accounting data is supplemented by the stock market performance of each company. Our objective will be to predict the stock market performance that occurs in the period following the publication of the fundamental data as accurately as possible.

This type of analysis is an example of the quantamental approach, which combines quantitative (quant) models with the fundamental (amental) expertise of financial analysts and accountants.

Let us start by presenting the dataset. This dataset can be downloaded from `https://www.kaggle.com`. This is a data science competition site. This dataset contains fundamental data obtained via the FMP API, which we detailed in the previous section. The archive (zip file) contains data from 2014 to 2018. The data for each year is contained in a different dataset (`2014_Financial_Data.csv`, … , `2018_Financial_Data.csv`).

We will work on the first of these files. It contains the data for 2014. You can then carry out the same analysis on the files corresponding to subsequent years.

This dataset contains hundreds of financial indicators that are found in the 10-K filings that each publicly traded company releases yearly. This annual report provides a comprehensive overview of the company's business and financial condition and includes audited financial statements.

Once the csv file has been downloaded to your computer, the following code can be used to read the data:

```python
# specify TICKER as index column
df = pd.read_csv('2014_Financial_Data.csv', index_col=0)
```

The following function `df.info()` gives us the dataset’s identity card, giving its size, the type of data, and column labels:

```python
df.info()
```

```
Index: 3808 entries, PG to WTT
Columns: 224 entries, Revenue to Class
dtypes: float64(222), int64(1), object(1)
memory usage: 6.5+ MB
```

This means that there are 3808 rows and 224 columns. Among these columns, one is a text column (object type), and the rest of the data are numeric columns. For details of the type of each column, we use `df.dtypes`:

```python
df.dtypes
```

```
Revenue                    float64
Revenue Growth             float64
Cost of Revenue            float64
Gross Profit               float64
R&D Expenses               float64
...
R&D Expense Growth         float64
SG&A Expenses Growth       float64
Sector                     object
2015 PRICE VAR [%]         float64
Class                      int64
Length: 224
```

The last two columns are the stock market performance data we hope to predict using the machine learning model.

The second-to-last column, `PRICE VAR [%]`, represents the variation in the share price between 1 January and 31 December 2015 following the publication of the fundamental accounting data.

The `Class` column is a binary indicator derived from the previous column. The value of this indicator is 0 (negative class) or 1 (positive class), depending on whether the variation indicated in the previous column (`PRICE VAR [%]`) is positive or negative.

This column will be used as a target to learn to predict by the classification algorithm, which seeks to predict a class or category.

Each row in the dataset represents a company. These are grouped by sector (`Sector` column) as follows:

```python
print(df[['Sector','2015 PRICE VAR [%]']])
```

| Symbol | Sector | % Change |
| :--- | :--- | :--- |
| PG | Consumer Defensive | -9.323276 |
| VIPS | Consumer Defensive | -25.512193 |
| KR | Consumer Defensive | 33.118297 |
| RAD | Consumer Defensive | 2.752291 |
| GIS | Consumer Defensive | 12.897715 |
| ... | ... | ... |
| TSRI | Technology | 29.362884 |
| TZOO | Technology | -31.167763 |
| USATP | Technology | -23.558900 |
| WSTG | Technology | 7.779579 |
| WTT | Technology | -34.099613 |

[3808 rows x 2 columns]

Here is the distribution of companies in terms of sector:

```python
df['Sector'].value_counts()
```

```
Financial Services       660
Healthcare               582
Technology               576
Industrials              501
Consumer Cyclical        457
Basic Materials          242
Real Estate              224
Energy                   221
Consumer Defensive       165
Utilities                97
Communication Services   83
```

We are now starting the data preparation phase as follows:

This phase will involve the following steps:

1. Removing outliers
2. Imputing missing data
3. Remove column
4. Label encoding
5. Prepare the target column
6. Split dataset

Let us start by removing outliers as follows:

### 1. Removing Outliers

We will identify the extreme values for each column and then replace them with the quantile value (0.95).

Let us start by calculating the quantile as follows:

```python
# Cut outliers (extrem HIGH values)
top_q = df.quantile(numeric_only=True, q=0.95)
top_q
```

```
Revenue                    2.137668e+10
Revenue Growth             8.804800e-01
Cost of Revenue            1.212385e+10
Gross Profit               8.570324e+09
R&D Expenses               1.760486e+08
...
Debt Growth                1.876595e+00
R&D Expense Growth         7.013900e-01
SG&A Expenses Growth       9.633700e-01
2015 PRICE VAR [%]         5.701303e+01
Class                      1.000000e+00
Name: 0.95, Length: 223, dtype: float64
```

The rest of the method is in the following code. We use the missing data (type `np.nan`: not a number) as a marker to identify them unambiguously and then replace (`df.fillna`) them with the accepted value.

```python
# identify outliers -> replace outlier values by Nan -> replace Nan by top_q values
outliers = df > top_q
df[outliers] = np.nan
df.fillna(top_q, inplace=True)
```

We proceed in the same way for the extrem low values:

```python
# Cut outliers (extrem LOW values)
top_q = df.quantile(numeric_only=True, q=0.05)

# identify outliers -> replace values by Nan -> replace Nan by top_q values
outliers = df < top_q
df[outliers] = np.nan
df.fillna(top_q, inplace=True)
```
