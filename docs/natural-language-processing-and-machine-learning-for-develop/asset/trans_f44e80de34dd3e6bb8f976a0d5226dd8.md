
import`numpy` as `np` import`pandas` as `pd` import`matplotlib.pyplot` as `plt` from`sklearn.linear_model` import`LinearRegression` `x` = 10\*`np`.`rand`(100) `y` = 5\*`x` + 5\*`np`.`rand`(100) `print`("=> first 10 x values:") `print`(`x`[0:10]) `print`("=> max x value:",`x`.`max`()) `print`() `print`("=> first 10 y values:") `print`(`y`[0:10]) `print`("=> max y value:",`y`.`max`()) `print`() `model` = `LinearRegression`(`fit_intercept`=`True`) `X` = `x`.`reshape`(-1, 1) `print`("X.shape:",`X`.`shape`) `model`.`fit`(`X`, `y`) `print`("=> slope of line:", `model`.`coef_[0]`) `print`("=> y-intercept:  ", `model`.`intercept_`) `x_fit` = `np`.`linspace`(-1,11) `X_fit` = `x_fit`.`reshape`(-1,1) `y_fit` = `model`.`predict`(`X_fit`) `# "random" points: plt.scatter(x,y) # best-fitting line: plt.plot(x_fit,y_fit) plt.show()` 

import`numpy` as `np` import`pandas` as `pd` import`matplotlib.pyplot` as `plt` from`scipy` import`stats` from`sklearn.metrics` import`r2_score`  \# same data as sklearn_lin_reg.py: `x` = 10\*`np`.`rand`(100) `y` = 5\*`x` + 5\*`np`.`rand`(100)  \# "linefit" uses the values slope and intercept: **slope, intercept, r_value, p_value, std_err** = `stats`.`linregress`(`x`,`y`) `print`("slope:    ", `slope`) `print`("intercept:", `intercept`) `print`("r_value:  ", `r_value`) `print`("p_value:  ", `p_value`) `print`("std_err:  ", `std_err`)  def `linefit`(`b`):  return `intercept` + `slope` \* `b`  `myline` = `linefit`(`x`)  `plt.scatter`(`x`,`y`, color='b') `plt.plot`(`x`,`myline`, color='r') `plt.show()` 

[Listing 8.10](#ch08.xhtml#list8.10) starts with some import statements and then initializes the variable `x` as a vector of 100 random floating point numbers between 0 and 10. The variable `y` is initialized as vector of 100 random floating point numbers, where each number is five times the corresponding value in the vector `x`, plus another random floating point number between 0 and 5.

The next portion of [Listing 8.10](#ch08.xhtml#list8.10) initializes the variable `model` as an instance of the `LinearRegression` class in Sklearn. Then the variable `X` is initialized as a 100×1 vector of values from the vector `x`.

The next code snippet invokes the `fit()` method of the variable `model`, after which the slope and y-intercept of the best fitting line are available. Now we can perform some predictions. Initialize the variable `x_fit` with a set of random numbers between -1 and 11, and initialize `X_fit` as a one-column vector whose values are from `x_fit`. Now we can get the predicted values from `X_fit` by invoking the `predict()` method of the variable `model`, as shown here:

`y_fit` = `model`.`predict`(`X_fit`) 

Launch the code in [Listing 8.10](#ch08.xhtml#list8.10) and you will see the following output, along with a graph that displays the best fitting line for the set of random points:

`=> first 10 x values:` [9.50318249 1.92716624 4.73429059 5.81910031 2.53858169 1.26370769 4.08290837 3.71162985 8.26798678 1.42404685] `=> max x value:` 9.995419932716011 `=> first 10 y values:` [49.94582654 11.9098716  25.61829038 32.7364018  17.18778012  7.14293639 22.574198   20.62959673 42.65198716  7.71367233] `=> max y value:` 54.255842476093875 `X.shape:` (100, 1) `=> slope of line:` 5.070423937652158 `=> y-intercept:`  2.016428692525192 

[Listing 8.11](#ch08.xhtml#list8.11) starts with some familiar import statements, and then initializes the variable `x` as a vector of 100 random floating point numbers between 0 and 10. The variable `y` is initialized as vector of 100 random floating point numbers, where each number is 5 times the corresponding value in the vector `x`, plus another random floating point number between 0 and 5.

The key code snippet in [Listing 8.11](#ch08.xhtml#list8.11) is shown in bold, which calculates the slope, y-intercept, r-value, p-value, and standard error for the best fitting line. If you need access to these quantities, then this type of code is more useful than the code in [Listing 8.10](#ch08.xhtml#list8.10).

Launch the code in [Listing 8.11](#ch08.xhtml#list8.11) and you will see the following output, along with a graph that displays the best fitting line for the set of random points:

`slope:`  5.008309175824397 `intercept:` 2.4242119308236134 `r_value:`  0.9960065560231295 `p_value:`  1.2047321054027177e-104 `std_err:`  0.04534930921236101 

[Figure 8.4](#ch08.xhtml#fig8.4) displays a scatter plot of points and the best-fitting line for those points.

![Figure 8.4 ¶ A Scatter Plot and a Best-Fitting Line.](images/fig8.4.jpg)

Figure 8.4 ¶ A Scatter Plot and a Best-Fitting Line.

## **Keras and Linear Regression**

The code sample in this section contains primarily Keras code in order to perform linear regression. If you have read the previous examples in this chapter, this section will be easier for you to understand because the steps for linear regression are the same.

[Listing 8.12](#ch08.xhtml#list8.12) displays the contents of `keras_linear_regression.py` that illustrates how to perform linear regression in Keras.

***LISTING 8.12: keras_linear_regression.py***

############################################################## #Keep in mind the following important points: #1) Always standardize both input features and target variable: #doing so only on input feature produces incorrect predictions #2) Data might not be normally distributed: check the data and #based on the distribution apply StandardScaler, MinMaxScaler, #Normalizer or RobustScaler ##############################################################   import`tensorflow` as `tf` import`numpy` as `np` import`pandas` as `pd` import`seaborn` as `sns` import`matplotlib.pyplot` as `plt` from`sklearn.preprocessing` import`MinMaxScaler` from`sklearn.model_selection` import`train_test_split`  `df` = `pd`.`read_csv`('housing.csv') `X`  = `df`.`iloc`[:,0:13] `y`  = `df`.`iloc`[:,13].`values`  `mmsc` = `MinMaxScaler`() `X`  = `mmsc`.`fit_transform`(`X`) `y`  = `y`.`reshape`(-1,1) `y`  = `mmsc`.`fit_transform`(`y`)  `X_train`, `X_test`, `y_train`, `y_test` = `train_test_split`(`X`, `y`, test_size=0.3)  \# this Python method creates a Keras model def `build_keras_model`:  model = `tf`.`keras`.`models`.`Sequential`()  model.add(`tf.keras`.`layers`.`Dense`(units=13, input_dim=13))  model.add(`tf.keras`.`layers`.`Dense`(units=1))  model.compile(optimizer='adam',loss='mean_squared_error',                 metrics=['mae','accuracy'])  return model  batch_size=32 epochs = 40  \# specify the Python method 'build_keras_model' to create a \# Keras model \# using the implementation of the scikit-learn regressor API \# for Keras model = `tf.keras.wrappers.scikit_learn`.`KerasRegressor`(`build_fn`=`build_keras_model`, batch_size=batch_size,epochs=epochs)  \# train ('fit') the model and then make predictions: model.fit(`X_train`, `y_train`) `y_pred` = model.predict(`X_test`) #print("y_test:",`y_test`) #print("y_pred:",`y_pred`)  \# scatter plot of test values-vs-predictions fig, ax = `plt`.`subplots`() `ax`.`scatter`(`y_test`, `y_pred`) `ax`.`plot`([`y_test`.`min()`, `y_test`.`max()`], [`y_test`.`min()`, `y_test`.`max()`], 'r\*'--') `ax`.`set_xlabel`('Calculated') `ax`.`set_ylabel`('Predictions') `plt`.`show()` 

