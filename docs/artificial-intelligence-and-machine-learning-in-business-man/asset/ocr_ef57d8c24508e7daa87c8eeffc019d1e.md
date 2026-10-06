# Artificial Intelligence and Machine Learning in Business Management

```
data.info()
<class 'pandas.core.frame.DataFrame'>
Index: 14999 entries, 0 to 14998
Data columns (total 10 columns):
satisfaction_level  14999 non-null float64
last_evaluation      14999 non-null float64
number_project      14999 non-null int64
average_montly_hours 14999 non-null int64
time_spend_company   14999 non-null int64
work_accident        14999 non-null int64
left                 14999 non-null int64
ppromotion_last_5years 14999 non-null int64
Departments          14999 non-null object
salary               14999 non-null object
types: float64(2), int64(6), object(2)
memory usage: 1.0+ MB
```

**Figure 11.3** Dataset feature description.

**Work accident**: Whether an employee has had a work accident or not and its data type is integer.

**promotion_last_5years**: Whether an employee has had a promotion in the last 5 years or not and its data type is integer.

**Departments**: Employee's working department/division and its data type is String.

**Salary**: Salary level of the employee such as low, medium and high and its data type is string.

**Left**: Whether the employee left the company or not and its data type is integer. Here 0 means employee is currently working there, and 1 means employee has resigned from that company.

**Exploratory data analysis**: To know more about the data set we will do some deeper data analysis, when we use describe() then it will give us some interesting story about the data set.

The employee dataset currently working in organization is shown below in Figure 11.4. Here, in this dataset, we have only two types of employees: those who are currently working in the organization and one who left the company. Hence, if we compare both of these we get more information about the behaviour of employees. The above figure shows employee dataset currently working in organization.

The employee dataset left the company is shown in Figure 11.5. This graph clearly shows out of 14,999 employees, 11,428 employees are currently working and 3,571employees left the company. Thus, total around 23% of employee left the company (Figure 11.4)

Employee left VS Employee present is shown in Figure 11.6.