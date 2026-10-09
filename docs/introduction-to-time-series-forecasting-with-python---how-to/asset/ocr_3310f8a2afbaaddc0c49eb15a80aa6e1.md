+   - **Problem Framing:** Resampling may be required if your data is not available at the same frequency that you want to make predictions.

+   - **Feature Engineering:** Resampling can also be used to provide additional structure or insight into the learning problem for supervised learning models.

There is a lot of overlap between these two cases. For example, you may have daily data and want to predict a monthly problem. You could use the daily data directly or you could downsample it to monthly data and develop your model. A feature engineering perspective may use observations and summaries of observations from both time scales and more in developing a model. Let’s make resampling more concrete by looking at a real dataset and some examples.

# 7.2  Shampo Sales Dataset

In this lesson, we will use the Shampo Sales dataset as an example. This dataset describes the monthly number of sales of shampoo over a 3 year period. You can learn more about the dataset in Appendix [A.1](https://example.com/A.1). Place the dataset in your current working directory with the filename `shampoo-sales.csv`.

The Shampoo Sales dataset only specifies year number and months (e.g. 1–01). A custom function is used to parse the dates and baseline the year number on an arbitrary year (1900) so that the date-times can be interpreted correctly in the Pandas *Series*.

# 7.3  Upsampling Data

The observations in the Shampoo Sales are monthly. Imagine we wanted daily sales information. We would have to upsample the frequency from monthly to daily and use an interpolation scheme to fill in the new daily frequency. The Pandas library provides a function called `resample()` on the *Series* and *DataFrame* objects<sup>1</sup>. This can be used to group records when downsampling and making spaces for new observations when upsampling.

We can use this function to transform our monthly dataset into a daily dataset by calling resampling and specifying the preferred frequency of calendar day frequency or *D*. Pandas is clever and you could just as easily specify the frequency as *1D* or even something domain specific, such as *5D*. Pandas provides a table of built-in aliases<sup>2</sup>.

```
```python
# upsample to daily intervals
from pandas import read_csv
from pandas import datetime

def parser(x):
    return datetime.strptime('%Y-%m' % x, '%Y-%m')

series = read_csv('shampoo-sales.csv', header=0, index_col=0, parse_dates=True, squeeze=True, date_parser=parser)
upsampled = series.resample('D').mean()
print(upsampled.head(32))
```
```

<sup>1</sup> [https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.resample.html](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.resample.html)

<sup>2</sup> [https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html#timeseries-offset-aliases](https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html#timeseries-offset-aliases)