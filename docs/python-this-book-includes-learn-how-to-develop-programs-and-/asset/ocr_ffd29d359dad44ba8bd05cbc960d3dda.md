Multiple linear regression occurs when more than a single independent variable is used to forecast a dependent variable.
$Y=a+b_1x_1+b_2x_2+\dots+b_nx_n$

In the above formula, y denotes a dependent variable, a denotes an intercept, b1 and b2 represent the coefficients, x1 and x2 represent independent variables.
to create the multiple linear regression model, you will need to make use of the NBA’s basketball data to forecast the average points attained per game. Below are the data column descriptions:

+   - Height: Describes the height in feet.
- Weight: Describes the weight in pounds.
- Success_field_goals: Describes the rate of successful field goals.
- Success_free_throws: Describes the rate of successful free throws.
- Avg_points_scored: Describes the average points attained per game.

The code below ingests the above data, and then you apply the desc() method of the DataFrame to acquire the univariate metrics in every field.

```
>>> b_data = pd.read_csv('Data/basketball.csv')
>>> b_data.describe()
```

Below is the output of the code:

| | weight | success_field_goals | success_free_throws | avg_points_scored |
|---|---|---|---|--|
| count | 54.000000 | 54.000000 | 54.000000 | 54.000000 |
| mean | 6.588727 | 200.907407 | 0.449111 | 0.741852 | 11.700741 |
| std | 0.458894 | 30.265026 | 0.100146 | 6.800267 |
| min | 5.700000 | 105.000000 | 0.291000 | 0.244000 | 2.800000 |
| 25% | 6.225000 | 188.000000 | 0.415260 | 0.713000 | 8.190000 |
| 50% | 6.650000 | 212.500000 | 0.443900 | 0.753500 | 10.750000 |
| 75% | 6.900000 | 235.000000 | 0.483500 | 0.796250 | 13.800000 |
| max | 7.000000 | 253.000000 | 0.599000 | 0.900000 | 27.400000 |