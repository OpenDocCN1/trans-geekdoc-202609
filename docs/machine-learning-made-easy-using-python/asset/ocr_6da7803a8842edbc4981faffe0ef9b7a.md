# 123 DATA VISUALIZATION

In [2]: import pandas
dt = pandas.read_csv('trees.csv',
names=['Index', 'Girth', 'Height', 'Volume'])
dt.drop(0, inplace=True)
ddt['Height'].hist()

Out [2]: <matplotlib.axes._Subplot at 0x261f0daa

![](bbox=[0.318, 0.245, 0.803, 0.483])

Note that we renamed the columns while importing the csv data using the names parameter of the read_csv() function, but the default column names will be stored as the first row, we need to remove that, to do so we use the drop() function and provide the Ø as the index i.e. first row and also True for the inplace parameter which will remove that from the actual data

Next is density plots which are similar to histograms but have smooth lines like the below chart

![](bbox=[0.318, 0.763, 0.603, 0.936])