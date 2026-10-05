# 5.1 One numerical explanatory variable

+   * The fert_rate column represents the observed outcome variable y. This is the y-position of the 181 black points.
* The life_exp column represents the values of the explanatory variable x. This is the x-position of the 181 black points.
* The fert_rate_hat column represents the fitted values \hat{y}. This is the corresponding value on the regression line for the 181 x values.
* The residual column represents the residuals y-\hat{y}. This is the 181 vertical distances between the 181 black points and the regression line.

Just as we the 21st country in the UN_data_ch5 dataset (in the first row of the table), we repeat the calculations for the 24th country (in the fourth row of Table 5.3). This corresponds to the country of Brunei (BRN):

+   * fert_rate = 1.7 is the observed fert_rate y for this country.
* life_exp = 0.8590 is the value of the explanatory variable life_exp x for Brunei.
* fert_rate_hat = 1.535 = 12.599 + (-0.137) \cdot 0.8590 is the fitted value \hat{y} on the regression line for this country.
* residual = 0.165 = 1.7 - 1.535 is the value of the residual for this country. In other words, the model's fitted value was off 0.165 fertility rate units for Brunei.

At this point, you can skip ahead if you like to Subsection 5.3.2 to learn about the processes behind what makes "best-fitting". As a primer, a "best-fitting" line refers to the line that minimizes the sum of squared residuals out of all possible lines we can draw through the points. In Section 5.2, we'll discuss another common scenario of having a categorical explanatory variable and a numerical outcome variable.

# Learning check

(LC5.8) What is a "wrapper function" in the context of statistical modeling in R?

+   * A. A function that directly fits a regression model without using any other functions.
* B. A function that combines other functions to simplify complex operations and provide a user-friendly interface.
* C. A function that removes missing values from a dataset before analysis.
* D. A function that only handles categorical data in regression models.

(LC5.9) Generate a data frame of the residuals of the Learning check model where you used obes_rate as the explanatory x variable.