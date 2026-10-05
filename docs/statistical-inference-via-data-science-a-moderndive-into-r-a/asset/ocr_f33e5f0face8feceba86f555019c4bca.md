# 5.1 One numerical explanatory variable

+   (b) Computing summary statistics.
(c) Creating data visualizations.

What can you say about the relationship between obesity rate and fertility rate based
on this exploration?

(LC5.2) What is the main purpose of performing an exploratory data analysis (EDA)
before fitting a regression model?

+   - A. To predict future values.
- B. To understand the relationship between variables and detect potential issues.
- C. To create more variables.
- D. To generate random samples.

(LC5.3) Which of the following is correct about the correlation coefficient?

+   - A. It ranges from -2 to 2.
- B. It only measures the strength of non-linear relationships.
- C. It ranges from -1 to 1 and measures the strength of linear relationships.
- D. It is always zero.

# 5.1.2 Simple linear regression

You may recall from secondary/high school algebra that the equation of a line is $y=a+b\cdot x$. (Note that $\cdot$ is equivalent to the $\times “multiply by” mathematical symbol. We will use the symbol in the rest of this book as it is more succinct.) It is defined by two coefficients $a$ and $b$. The intercept coefficient $a$ is the value of $y$ when $x=0$. The slope coefficient $b$ for $x$ is the increase in $y$ for every increase of one in $x$. This is also called the “rise over run.”

However, when defining a regression line like the regression line in Figure 5.3, we use slightly different notation: the equation of the regression line is $\hat{y}=b_0+b_1x$. The intercept coefficient is $b_0$, so $b_0$ is the value of $\hat{y}$ when $x=0$. The slope coefficient for $x$ is $b_1$; the increase in $\hat{y}$ for every increase of one in $x$. Why we put a “hat” on top of $y$? It’s a form of notation commonly used in regression to indicate that we have a “fitted value, or the value of $y$ on the regression line for a given $x$. We discuss this in the upcoming Subsection 5.1.3.

We know that the regression line in Figure 5.3 has a negative slope $b_1$ corresponding to our explanatory $x$ variable $life\_exp$. Why? Because countries tend to have higher $life\_exp$ values, they tend to have lower fertility rates. What is the numerical value of the slope $b_1$? What about the intercept $b_0$? We do not compute these two values by hand, but rather we use a computer!