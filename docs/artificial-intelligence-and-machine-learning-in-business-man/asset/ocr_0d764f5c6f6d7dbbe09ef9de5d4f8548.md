# Employee Churn Management Using AI

# TABLE 11.1
The Data Set Will Show Top 5 Rows Having These Columns

| Satisfaction Level | Last Evaluation | Number Project | Average Hrs | Time Company | Spent Work | Accident | Promo_Last_5years | Departments | Salary |
|---|---|---|---|---|---|---|---|---|---|n| 0.38 | 0.053 | 2 | 157 | 3 | 0 | 1 | | Sales | Low |
| 0.80 | 0.086 | 5 | 262 | 6 | 0 | 1 | | Sales | Medium |
| 0.11 | 0.088 | 7 | 272 | 4 | 0 | 1 | | Sales | Medium |
| 0.72 | 0.087 | 5 | 223 | 5 | 0 | 1 | | Sales | Low |
| 0.37 | 0.052 | 2 | 159 | 3 | 0 | 4 | | Sales | Low |

```
data = pd.read_csv("HR_comma_sep.csv")
data.head()
```

# FIGURE 11.2 Shows the function result_csv()

We are using Python as the programming language for analyzing the dataset as it is open source, freely available and has huge libraries enabling analyses of the datasets. We are also using Jupyter notebook as the editor for this kind of work, which is open source and has support for data analysis. Python has a library Pandas which is mostly used to load and read the dataset and it also has many functionalities which helps in further analysis. To load and read the CSV file we will use the panda’s-built function read_csv() and to see the first 5 rows (Table 11.1) of the data we need to use head(). Figure 11.2 shows the function result_csv().
The function result_csv() is shown in Figure 11.2.
The data consists of 14,999 employee records, and each record consist of 10 attributes, including the target features. To know more about the dataset and its attributes, we can use info() of Pandas library.
The Dataset feature description is shown in Figure 11.3.
The data set consist of the following features like:

**satisfaction level:** It is employee satisfaction point, which ranges from 0 to 1 and its data type is Float.
**last evaluation:** It is evaluated performance by the employer, which also ranges from 0 to 1 and its data type is Float.
**number project:** How many numbers of projects assigned to an employee and its data type is integer.
**average_monthly_hours:** How many average numbers of hours worked by an employee in a month and its data type is integer.
**Time_spent_company:** Time_spent_company means employee experience. The number of years spent by an employee in the company and its data type is integer.