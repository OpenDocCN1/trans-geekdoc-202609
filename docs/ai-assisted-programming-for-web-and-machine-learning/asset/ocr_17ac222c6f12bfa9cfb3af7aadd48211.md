for deeper analysis and informed preprocessing.

# Comparing features using bivariate visualizations

While univariate analysis helps us understand individual features, exploring relationships between two variables, known as bivariate analysis, is key to uncovering trends, correlations, and potential interactions that can influence model performance. Whether comparing numerical features or examining how a categorical variable impacts a numerical, bivariate visualizations offer critical insights for feature engineering and model design.

# Traditional approach

Let us look at two common examples using Seaborn:

+   **Scatter plot for numeric-numeric relationships:** A scatter plot is ideal when comparing two continuous variables: **Experience** and **Salary**.

The following scatter plot illustrates the relationship between 'Experience' and 'Salary':
ns.scatterplot(x='Experience', y='Salary', data=df)
plt.title("Experience vs Salary")
plt.show()

This visualization reveals whether there is a positive or negative trend between the variables and highlights any clustering or outliers.

+   **Box plot for categorical-numeric comparisons:** To analyze how salaries differ across departments (a categorical variable), a box plot provides a clear visual summary of distributions.

The following box plot compares salary distributions across different departments:
sns.boxplot(x='Department', y='Salary', data=df)