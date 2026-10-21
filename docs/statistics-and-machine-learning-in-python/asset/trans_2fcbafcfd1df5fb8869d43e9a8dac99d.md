
## Python中的统计与机器学习，版本0.2

| | | | | | | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| engineer | 1 | 1 | peter | 1 | NaN | NaN | NaN | NaN | NaN | NaN | NaN | 1.0 | NaN | NaN | ... |
| ... | NaN | NaN | NaN | NaN | 0.0 | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | ... |
| ... | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | ... |
| ... | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | ... |

### 在循环中使用Groupby

```python
for grp, data in df.groupby("job"):
    print(grp, data)
```

输出：

| index | group | name | age | gender | job | height |
|---|---:|---|---:|---|---|---:|
| 4 | engineer | peter | 33 | M | engineer | NaN |
| 3 | manager | paul | 58 | F | manager | NaN |
| 5 | scientist | julie | 44 | F | scientist | 171.0 |
| 0 | student | alice | 19 | F | student | 165.0 |
| 2 | student | eric | 22 | M | student | 175.0 |
| 1 | student | john | 26 | M | student | 180.0 |

## 5.9 质量检查

### 5.9.1 移除重复数据

```python
df = users.append(df.iloc[0], ignore_index=True)
print(df.duplicated())  # Series of booleans
# (True if a row is identical to a previous row)
df.duplicated().sum()  # count of duplicates
df[df.duplicated()]  # only show duplicates
df.age.duplicated()  # check a single column for duplicates
df.duplicated(['age', 'gender']).sum()  # specify columns for finding duplicates
df = df.drop_duplicates()  # drop duplicate rows
```

输出：

| index | duplicated |
|---:|---|
| 0 | False |
| 1 | False |
| 2 | False |
| 3 | False |
| 4 | False |

```python
# assert df.travail.isnull().sum() == 0

df['travail'].str.contains("etu|inge")
```

输出：

```
Index(['name', 'age', 'gender', 'job', 'height'], dtype='object')
```

## 5.11 处理离群值

```python
size = pd.Series(np.random.normal(loc=175, size=20, scale=10))
# Corrupt the first 3 measures
size[:3] += 500
```

### 5.11.1 基于参数统计：使用均值

假设随机变量服从正态分布

排除3个标准差之外的数据：

- 样本落在1个标准差内的概率：68.27%
- 样本落在3个标准差内的概率：99.73% (68.27 + 2 * 15.73)

```python
size_outlr_mean = size.copy()
size_outlr_mean[((size - size.mean()).abs() > 3 * size.std())] = size.mean()
print(size_outlr_mean.mean())
```

输出：

```
248.48963819938044
```

### 5.11.2 基于非参数统计：使用中位数

基于中位数计算的中位数绝对偏差（MAD）是一种稳健的非参数统计量。
[中位数绝对偏差](https://en.wikipedia.org/wiki/Median_absolute_deviation)

```python
mad = 1.4826 * np.median(np.abs(size - size.median()))
size_outlr_mad = size.copy()

size_outlr_mad[((size - size.median()).abs() > 3 * mad)] = size.median()
print(size_outlr_mad.mean(), size_outlr_mad.median())
```

输出：

```
173.80000467192673 178.7023568870694
```

## 5.12 文件I/O

### 5.12.1 csv

```python
import tempfile, os.path
tmpdir = tempfile.gettempdir()
csv_filename = os.path.join(tmpdir, "users.csv")
users.to_csv(csv_filename, index=False)
other = pd.read_csv(csv_filename)
```

### 5.12.2 从URL读取csv

```python
url = 'https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/salary_table.csv'
salary = pd.read_csv(url)
```

### 5.12.3 Excel

```python
xls_filename = os.path.join(tmpdir, "users.xlsx")
users.to_excel(xls_filename, sheet_name='users', index=False)

pd.read_excel(xls_filename, sheetname='users')

# Multiple sheets
with pd.ExcelWriter(xls_filename) as writer:
    users.to_excel(writer, sheet_name='users', index=False)
    df.to_excel(writer, sheet_name='salary', index=False)

pd.read_excel(xls_filename, sheetname='users')
pd.read_excel(xls_filename, sheetname='salary')
```

### 5.12.4 SQL（SQLite）

```python
import pandas as pd
import sqlite3

db_filename = os.path.join(tmpdir, "users.db")
```

```python
# Connect

conn = sqlite3.connect(db_filename)
```

```python
# Creating tables with pandas

url = 'https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/salary_table.csv'
salary = pd.read_csv(url)

salary.to_sql("salary", conn, if_exists="replace")
```

```python
# Push modifications

cur = conn.cursor()
values = (100, 14000, 5, 'Bachelor', 'N')
cur.execute("insert into salary values (?, ?, ?, ?, ?)", values)
conn.commit()
```

### 将结果读入pandas DataFrame

```python
salary_sql = pd.read_sql_query("select * from salary;", conn)
print(salary_sql.head())

pd.read_sql_query("select * from salary;", conn).tail()
pd.read_sql_query('select * from salary where salary>25000;', conn)
pd.read_sql_query('select * from salary where experience=16;', conn)
pd.read_sql_query('select * from salary where education="Master";', conn)
```

输出：

| # | index | salary | experience | education | management |
|---|---:|---:|---:|---|---|
| 0 | 0 | 13876 | 1 | Bachelor | Y |
| 1 | 1 | 11608 | 1 | Ph.D | N |
| 2 | 2 | 18701 | 1 | Ph.D | Y |
| 3 | 3 | 11283 | 1 | Master | N |
| 4 | 4 | 11767 | 1 | Ph.D | N |

## 5.13 练习

### 5.13.1 数据框

1. 在'https://github.com/neurospin/pystatsml/tree/master/datasets/iris.csv'读取iris数据集
2. 打印列名
3. 获取数值列
4. 对每个物种计算数值列的均值，并将其存储在如下统计表中：

| # | species | sepal_length | sepal_width | petal_length | petal_width |
|---|---:|---:|---:|---:|---:|
| 0 | setosa | 5.006 | 3.428 | 1.462 | 0.246 |
| 1 | versicolor | 5.936 | 2.770 | 4.260 | 1.326 |
| 2 | virginica | 6.588 | 2.974 | 5.552 | 2.026 |

### 5.13.2 缺失数据

向之前的users表添加一些缺失数据：

```python
df = users.copy()
df.ix[[0, 2], "age"] = None
df.ix[[1, 3], "gender"] = None
```

1. 编写一个函数 `fillmissing_with_mean(df)`，用当前列的均值填充数值列的所有缺失值。
2. 将原始users表和“插补”后的数据框保存到同一个Excel文件“users.xlsx”中，包含两个工作表：original（原始）和imputed（插补）。

**脚本总运行时间：**（0分钟1.485秒）

## MATPLOTLIB：数据可视化

来源

- Nicolas P. Rougier：http://www.labri.fr/perso/nrougier/teaching/matplotlib
- https://www.kaggle.com/benhamner/d/uciml/iris/python-data-visualizations

## 6.1 基本绘图

```python
import numpy as np
import matplotlib.pyplot as plt

# inline plot (for jupyter)
%matplotlib inline

x = np.linspace(0, 10, 50)
sinus = np.sin(x)

plt.plot(x, sinus)
plt.show()
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_62_0.png)

```python
plt.plot(x, sinus, "o")
plt.show()
# use plt.plot to get color / marker abbreviations
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_63_0.png)

```python
# Rapid multiplot
cosinus = np.cos(x)
plt.plot(x, sinus, "b-", x, sinus, "ob", x, cosinus, "-r", x, cosinus, "or")
plt.xlabel('this is x!')
plt.ylabel('this is y!')
plt.title('My First Plot')
plt.show()
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_63_1.png)

```python
# Step by step
plt.plot(x, sinus, label='sinus', color='blue', linestyle='--', linewidth=2)
plt.plot(x, cosinus, label='cosinus', color='red', linestyle='-', linewidth=2)
plt.legend()
plt.show()
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_64_0.png)

## 6.2 散点图（2D）

加载数据集

```python
import pandas as pd
try:
    salary = pd.read_csv("../datasets/salary_table.csv")
except:
    url = 'https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/salary_table.csv'
    salary = pd.read_csv(url)

df = salary
```

### 6.2.1 带颜色的简单散点图

```python
colors = colors_edu = {'Bachelor':'r', 'Master':'g', 'Ph.D':'blue'}
plt.scatter(df['experience'], df['salary'], c=df['education'].apply(lambda x: colors[x]), s=100)
```

输出：

```
<matplotlib.collections.PathCollection at 0x7f0f58dc2358>
```

![](img/c2ad4b400bf63af9804b2d44510f76a6_65_0.png)

### 6.2.2 带颜色和符号的散点图

```python
# Figure size
plt.figure(figsize=(6,5))

# Define colors / symbols manually
symbols_manag = dict(Y='*', N='.')
colors_edu = {'Bachelor':'r', 'Master':'g', 'Ph.D':'blue'}

# group by education x management => 6 groups
for values, d in salary.groupby(['education','management']):
    edu, manager = values
    plt.scatter(d['experience'], d['salary'], marker=symbols_manag[manager], color=colors_edu[edu], s=150, label=manager+"/"+edu)

# Set labels
plt.xlabel('Experience')
plt.ylabel('Salary')
plt.legend(loc=4)  # lower right
plt.show()
```

