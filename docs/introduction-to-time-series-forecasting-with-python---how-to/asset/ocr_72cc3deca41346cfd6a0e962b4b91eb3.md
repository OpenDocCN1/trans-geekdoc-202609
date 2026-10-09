![](bbox=[0.19, 0.14, 0.81, 0.55])

# A.5 Airline Passengers Dataset

This dataset describes the total number of airline passengers over time. The units are a count of the number of airline passengers in thousands. There are 144 monthly observations from 1949 to 1960. The code below loads the Airline Passengers dataset, prints the first 5 rows of data and graphs the data as a line plot.

```
# load the airline passengers dataset
from matplotlib import pyplot
from pandas import read_csv
series = read_csv('airline-passengers.csv', header=0, index_col=0, parse_dates=True,
                   squeeze=True)
print(type(series))
print(series.head())
series.plot()
pyplot.show()
```

Listing A.9: Create a line plot of the Airline Passengers dataset.

Below is a sample of the first 5 rows of the loaded dataset.

Month
1949-01-01 112