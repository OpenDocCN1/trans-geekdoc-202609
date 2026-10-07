variable(s) or feature(s) from the existing independent variable(s) is called Feature Engineering (Refer to Table 1.3).

| Date | Month | Day of the Year | CLOUDY | Temperature (in Celsius) |
|---|---|---|---|--|
| 01-Jan-2001 | 1 | 1 | YES | 14.3 |
| 02-Jan-2001 | 1 | 2 | NO | 13.7 |
| 03-Jan-2001 | 1 | 3 | NO | 13.6 |
| 04-Jan-2001 | 1 | 4 | YES | 14.2 |
| 05-Jan-2001 | 1 | 5 | NO | 12.8 |

Table 1.3: Feature Engineered dataset of temperatures in a city

The temperature is the dependent variable or target variable. Given this data, we want the machine to learn the patterns and create a rule. Then, given any date in the future and it is cloudy, the machine should predict the temperature on that day. So, this is Supervised Learning.

A regression implementation on the example data provided in Table 1.2 is as follows: import pandas as pd

```
df = pd.DataFrame([['01-01-2001', 'YES', 14.3],
                   ['01-02-2001', 'NO', 13.7],
                   ['01-03-2001', 'NO', 13.6],
                   ['01-04-2001', 'YES', 14.3],
                   ['01-05-2001', 'NO', 14.2],
                   ['01-06-2001', 'YES', 12.8],
                   ['01-07-2001', 'NO', 14.7],
                   ['01-08-2001', 'NO', 11.3],
                   ['01-09-2001', 'NO', 11.7],
                   ['01-10-2001', 'NO', 12.1]],

columns = ['Date', 'Cloudy', 'Temperature'])
```

```
df Date Cloudy Temperature
0 01-01-2001 YES 14.3
1 01-02-2001 NO 13.7
```