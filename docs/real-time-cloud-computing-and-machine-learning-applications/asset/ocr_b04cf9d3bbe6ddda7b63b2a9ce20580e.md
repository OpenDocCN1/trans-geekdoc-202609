160 T. P. Fowdar, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoondonman

The fitlm function from MATLAB's Statistics and Machine Learning Toolbox can be used to fit a polynomial regression model [26]. The syntax of the function for polynomial regression is as follows:

```
Mdl= fitlm(X,Y,modelspec)
```

The inputs to the function are described below:

+   - X: Predictors variable.

+   - Y: Response variable.

modelspec: Model specification. Should be set to 'polyijk' for polynomial regression, where i, j and k take the value of the highest degrees of the first, second and third predictors respectively. In a single predictor is used, the value i should be set. For example, 'poly3' is used for regression in a single-predictor scenario having the highest degree of 3.

The same predict function from MATLAB's Statistics and Machine Learning Toolbox for simple linear regression can then be used to predict the response for an untested predictor [30].

A MATLAB simulation for performing the regression given in the short-hand example is given below.

The training dataset is first loaded in the MATLAB workspace and then the fitlm function is used to fit the polynomial regression model of degree using the codes given in Listing 3.20.

# Listing 3.20. Polynomial regression- Define dataset

| X = [1835 1970 2372 3086 3504 4341]; |
 y = [26 31 24 18 15]; |
 mdl = fitlm(X,Y,poly2); % Fit the polynomial regression model |

The regression line can be illustrated using the codes given in Listing 3.21.

# Listing 3.21. Polynomial regression- Visualise regression line

| R=[1800:4500]; % Define array of points to illustrate regression line |
 ypred = predict(mdl,R); %Predict mileages for car weights in C |
 plot(X,y,'',R,ypred,'-') %Plot training dataset alongside regression line |
 xlabel ('Weight') |
 ylabel('Mileage') |
 legend('Data','Regression Line') |