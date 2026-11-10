
![Figure 6.3 Google trends for the search query “World Cup” (day-wise and region-wise analysis results).](images/fig6.3.jpg)

[**Figure 6.3**](#c6.xhtml#re_f6.3) Google trends for the search query “World Cup” (day-wise and region-wise analysis results).

### 6.3.2 Time Series Prediction
A time series is a collection of values or observations of data gathered over a period of time through repeated measurements. Time series prediction or forecasting use regression analysis widely for predicting future values. Economic and sales forecasting, budgetary analysis, stock market analysis, yield projections, process and quality control, inventory studies, temperature predictions, etc., are all examples of time series predictions that could be done by using regression analysis ([Figure 6.4](#c6.xhtml#f6.4)).

![Figure 6.4 Time series graph showing the trend of stock.](images/fig6.4.jpg)

[**Figure 6.4**](#c6.xhtml#re_f6.4) Time series graph showing the trend of stock.

### 6.3.3 Biomedical Imaging
Regression techniques are commonly useful in the medical imaging and radiology fields of research. They allow identification of the relationship between the various independent parameters for determining the target variable. Multiple regression analysis is basically used to predict disease progression from the data available in electronic format. Normally the regression analysis is widely used for evaluating the results gathered from visual grading experiments like medical images from radiological studies ([Figure 6.5](#c6.xhtml#f6.5)).

![Figure 6.5 Medical imaging using regression analysis.](images/fig6.5.jpg)

[**Figure 6.5**](#c6.xhtml#re_f6.5) Medical imaging using regression analysis.

## 6.4 Types of Regression
Now that we know about regression and its most common applications, the major job left is to understand the various steps involved in the regression process. Yes, this is a good start. However, it is important to know that there are different types of regression too. Oh my God, are you kidding me?! Not at all. The big brains who found the regression analysis have come up with various types of regression. Let’s have a quick look into the types now. Don’t worry, we’ll keep things simple and easily understandable.

*   *Linear regression* (a predictive technique, but not classification; classification is used for categorical variables, whereas linear regression uses numerical variables which are of the continuous type).
*   *Logistic regression* (a classification technique, because it is used for categorical variables, which are of a discrete, discontinuous type).
*   Oh, that was quite simple! Right?
*   OK, anyway, let’s deep dive into the steps involved in linear regression.

### 6.4.1 Linear Regression and the Steps Involved
Simple linear regression is a simple technique used to find the relationship between one dependent variable and one or more independent variables. That is, simply stated, regression analysis tries to establish a clear relationship between the input and output.

![](images/inline6.14.jpg)![](images/inline6.15.jpg)

Linear regression is the technique used to find the best-fitting line through the data points. The best-fitting line is the line which minimizes the errors. To make clear, an error in this situation is the difference between the actual and predicted data, so that the distance between the actual data and the data predicted by the regression is as small as possible.

Having said that, representing the situation in a more mathematical way, the formula is `Y = a X + b`, which is a simple linear equation. In this equation, `Y` is the dependent variable and `X` is the independent variable with a single predictor. Here, `a` is the slope of the line or the regression coefficient and `b` is the intercept. Regression is a statistical tool to predict the dependent variable with the help of one or more independent variables (multiple predictors).

`b = ȳ − a x̄`, where `b` is the intercept

|   a \=   ∑ (  x i  −  x ¯  )(  y i  −  y ¯  )   ∑   (  x i  −  x ¯  )  2    ,   w h e r e   a   i s   t h e   s l o p e   ||  |
| --- | --- |

Let’s take a very familiar example to understand this. We all might have experienced the scenario of studying the day before a test/exam and passing the test the very next day. If you haven’t experienced this in your student life, we could say you have missed the training for some major employability skills in your life ![](images/inline4.1.jpg).

The problem is simple: predict whether the student will pass the exam or not, depending on the numbers of hours spent studying.

Here, the linear regression line draws a relationship between the independent variable and the dependent variable ([Figure 6.6](#c6.xhtml#f6.6)).

![Figure 6.6 Linear regression line.](images/fig6.6.jpg)

[**Figure 6.6**](#c6.xhtml#re_f6.6) Linear regression line.

#### Case 1 – Positive Relationship
What will be the situation as the independent variable changes? When the independent variable increases, if the dependent variable also increases, we call the relationship (and, hence, the regression) positive ([Figure 6.7](#c6.xhtml#f6.7) and [Figure 6.8](#c6.xhtml#f6.8)).

![Figure 6.7 A Positive correlation.](images/fig6.7.jpg)

[**Figure 6.7**](#c6.xhtml#re_f6.7) A Positive correlation.

![Figure 6.8 A positive linear regression.](images/fig6.8.jpg)

[**Figure 6.8**](#c6.xhtml#re_f6.8) A positive linear regression.

See the picture below:

Here, there is a positive relationship.

*   `x` = number of hours spent studying
*   `y` = passed the test.

If `y` increases positively as `x` increases, it is called positive relationship. In this case, the number of hours studied increases, which increases the probability of passing the test.

The next regression to learn is the negative relationship. One could look at [Figure 6.9](#c6.xhtml#f6.9) to understand what the negative relationship is all about.

![Figure 6.9 A negative linear regression.](images/fig6.9.jpg)

[**Figure 6.9**](#c6.xhtml#re_f6.9) A negative linear regression.

#### Case 2 – Negative Relationship
When the independent variable increases and the dependent variable decreases, we call that a negative relationship.

`x` = number of hours spent watching TV.

`y` = decrease in `CGPA`(Cumulative Grade Point Average - for schools and colleges, `CGPA` is used to measure the overall academic achievement of a student by awarding relevant grades)

If `y` decreases as `x` increases, it is called a negative relationship. In this case, the `CGPA` decreases as the number of hours of TV watched increases. One could also look at [Figure 6.10](#c6.xhtml#f6.10).

![Figure 6.10 A negative linear relationship.](images/fig6.10.jpg)

[**Figure 6.10**](#c6.xhtml#re_f6.10) A negative linear relationship.

With the simple linear regression, one would aim to drawing a straight line through the `x`, `y` data points. (Regressions can be used to analyze non-linear relationships can still, though that will not be covered in this book.) We plot each of the `x`, `y` pair of observations as dots. Then a straight line has to be drawn that fits all the different points as closely as possible (i.e., with minimal error) and it is called the Regression line. This is drawn using the Least Squares method. The core aim is to minimize the error by means of drawing the regression line. A regression line is presented in [Figure 6.11](#c6.xhtml#f6.11) and one can understand the purpose of this clearly now.

![Figure 6.11 Regression line.](images/fig6.11.jpg)

[**Figure 6.11**](#c6.xhtml#re_f6.11) Regression line.

One can also follow the video lecture presented at the YouTube link which talks about the Linear Regression: `https://youtu.be/MdHe7Sn6Qt4`

To understand what the errors are all about, one can have a look at [Figure 6.12](#c6.xhtml#f6.12).

![Figure 6.12 Errors.](images/fig6.12.jpg)

[**Figure 6.12**](#c6.xhtml#re_f6.12) Errors.
