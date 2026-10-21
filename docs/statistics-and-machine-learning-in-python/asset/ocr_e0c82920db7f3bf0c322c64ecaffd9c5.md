+   - Sample the t-statistic distribution under the null hypothesis using random permutations.
+   - Assess the p-value.

# 7.9.7 Univariate associations (developpement)

Write a function univar_stat(df, target, variables) that computes the parametric statistics and p-values between the target variable (provided as as string) and all variables (provided as a list of string) of the pandas DataFrame df. The target is a quantitative variable but variables may be quantitative or qualitative. The function returns a DataFrame with four columns: variable, test, value, p_value.

Apply it to the salary dataset available at https://raw.githubusercontent.com/neurospin/pystatsml/master/datasets/salary_table.csv, with target being S: salaries for IT staff in a corporation.

# 7.9.8 Multiple comparisons

This exercise has 2 goals: apply you knowledge of statistics using vectorized numpy operations. Given the dataset provided for multiple comparisons, compute the two-sample t-test (assuming equal variance) for each (column) feature of the Y array given the two groups defined by grp variable. You should return two vectors of size n_features: one for the t-values and one for the p-values.

# ANOVA

Perform an ANOVA dataset described bellow

+   - Compute between and within variances
+   - Compute F-value: fval
+   - Compare the p-value with the one obtained by stats.f_oneway using assert np.allclose(arr1, arr2)

```
# dataset
mu_k = np.array([1, 2, 3])      # means of 3 samples
sd_k = np.array([1, 1, 1])     # sd of 3 samples
n_k = np.array([10, 20, 30])   # sizes of 3 samples
grp = [0, 1, 2]                # group labels
n = np.sum(n_k)
label = np.hstack([[k] * n_k[k] for k in [0, 1, 2]])

y = np.zeros(n)
for k in grp:
    y[label == k] = np.random.normal(mu_k[k], sd_k[k], n_k[k])

# Compute with scipy
fval, pval = stats.f_oneway(y[label == 0], y[label == 1], y[label == 2])
```