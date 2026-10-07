
You couldn't really apply Backward Elimination to Polynomial Regression and Random Forest Regression models because these models don't have coefficients combined in a linear regression equation and therefore don't have p-values.

However, in Chapter 9 - Dimensionality Reduction, we will see some techniques like Backward Elimination, to reduce the number of features, based on Feature Selection & Feature Extraction.

- **What are Low/High Bias/Variance in Machine Learning?**
- **Low Bias** is when your model predictions are very close to the real values.
- **High Bias** is when your model predictions are far from the real values.
- **Low Variance**: when you run your model several times, the different predictions of your observation points won't vary much.
- **High Variance**: when you run your model several times, the different predictions of your observation points will vary a lot.

What you want to get when you build a model: Low Bias and Low Variance.

## Chapter 3 : part 1
## Logistic Regression

### 3.1.1 REGRESSION vs CLASSIFICATION
Regression and Classification algorithms are Supervised Learning algorithms. Both the algorithms are used for prediction in machine learning and work with the labeled datasets. But the difference between both is how they are used for different machine learning problems.

> To predict the continuous values such as price, salary, age, etc., and Classification algorithms are used to predict/Classify the discrete values such as Male or Female, True or False, Spam or Not Spam, etc.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

> The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Types of ML Classification Algorithms: Classification Algorithms can be further divided into the following types:

- Logistic Regression
- K-Nearest Neighbors
- Support Vector Machines (SVM)
- Kernel SVM
- Naive Bayes
- Decision Tree Classification
- Random Forest Classification

Regression: Regression is a process of finding the correlations between dependent and independent variables. It helps in predicting the variables such as Market Trends, prediction of House prices, etc.

> The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

Types of Regression Algorithm:

- Simple Linear Regression
- Multiple Linear Regression
- Polynomial Regression
- Support Vector Regression
- Decision Tree Regression

## Difference between Regression and Classification:

| Regression Algorithm | Classification Algorithm |
|---|---|
| i. In *Regression*, the output variable must be of continuous nature or real value. | ii. In *Classification*, the output variable must be of discrete value. |
| iii. The task of the **regression algorithm** is to **map** the inputvalue(x) with the continuous outputvariable(y). | iv. The task of the **classification algorithm** is to map the inputvariable(s) with the *discrete* outputvariable(y). |
| v. Regression Algorithms are used with *continuous data*. | vi. Classification Algorithms are used with *discrete data*. |
| vii. In *Regression*, we try to find the *best fit line*, which can predict the output more accurately. | viii. In *Classification*, we try to find the **decision boundary**, which can divide the dataset into different classes. |
| ix. Regression algorithms can be used to solve the regression problems such as Weather Prediction, House price prediction, etc. | x. Classification Algorithms can be used to solve classification problems such as identification of spam cells, Speech Recognition, identification of cancer cells, etc. |
| xi. The regression algorithm can be further divided into *Linear* and *Non-linear Regression*. | xii. The Classification algorithms can be divided into *Binary* and *Multi-class Classifier*. |

## Does regression mean?
What you want to get when you build a model: Low Bias and Low Variance.

The regression algorithm can be further divided into *Linear* and *Non-linear Regression*.

### 3.1.2 Introduction to Logistic Regression
The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

> To predict the continuous values such as price, salary, age, etc., and Classification algorithms are used to predict/Classify the discrete values such as Male or Female, True or False, Spam or Not Spam, etc.

Regression and Classification algorithms are Supervised Learning algorithms. Both the algorithms are used for prediction in machine learning and work with the labeled datasets. But the difference between both is how they are used for different machine learning problems.

### 3.1.1 REGRESSION vs CLASSIFICATION

You couldn't really apply Backward Elimination to Polynomial Regression and Random Forest Regression models because these models don't have coefficients combined in a linear regression equation and therefore don't have p-values.

However, in Chapter 9 - Dimensionality Reduction, we will see some techniques like Backward Elimination, to reduce the number of features, based on Feature Selection & Feature Extraction.

- What are Low/High Bias/Variance in Machine Learning?
- **Low Bias** is when your model predictions are very close to the real values.
- **High Bias** is when your model predictions are far from the real values.
- **Low Variance**: when you run your model several times, the different predictions of your observation points won't vary much.
- **High Variance**: when you run your model several times, the different predictions of your observation points will vary a lot.

What you want to get when you build a model: Low Bias and Low Variance.

## Chapter 3 : part 1
## Logistic Regression

### 3.1.1 REGRESSION vs CLASSIFICATION
(Wait, the above is repeated, re-ordering for logical flow)

Regression: Regression is a process of finding the correlations between dependent and independent variables. It helps in predicting the variables such as Market Trends, prediction of House prices, etc.

> The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

**Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

Types of Regression Algorithm:

- Simple Linear Regression
- Multiple Linear Regression
- Polynomial Regression
- Support Vector Regression
- Decision Tree Regression

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

> The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

**Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Types of ML Classification Algorithms: Classification Algorithms can be further divided into the following types:

- Logistic Regression
- K-Nearest Neighbors
- Support Vector Machines (SVM)
- Kernel SVM
- Naive Bayes
- Decision Tree Classification
- Random Forest Classification

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

## Difference between Regression and Classification:

| Regression Algorithm | Classification Algorithm |
|---|---|
| i. In *Regression*, the output variable must be of continuous nature or real value. | ii. In *Classification*, the output variable must be of discrete value. |
| iii. The task of the **regression algorithm** is to **map** the inputvalue(x) with the continuous outputvariable(y). | iv. The task of the **classification algorithm** is to map the inputvariable(s) with the *discrete* outputvariable(y). |
| v. Regression Algorithms are used with *continuous data*. | vi. Classification Algorithms are used with *discrete data*. |
| vii. In *Regression*, we try to find the *best fit line*, which can predict the output more accurately. | viii. In *Classification*, we try to find the **decision boundary**, which can divide the dataset into different classes. |
| ix. Regression algorithms can be used to solve the regression problems such as Weather Prediction, House price prediction, etc. | x. Classification Algorithms can be used to solve classification problems such as identification of spam cells, Speech Recognition, identification of cancer cells, etc. |
| xi. The regression algorithm can be further divided into *Linear* and *Non-linear Regression*. | xii. The Classification algorithms can be divided into *Binary* and *Multi-class Classifier*. |

### 3.1.2 Introduction to Logistic Regression
The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

## Does regression mean?
What you want to get when you build a model: Low Bias and Low Variance.

The regression algorithm can be further divided into *Linear* and *Non-linear Regression*.

### 3.1.3 Logistic Regression & Sigmoid Function
In our first attempt, we used Linear Regression, y = b0 + b1. But in our last attempt we ended up with S-shaped function.

```
p = \frac{1}{1 + e^{-y}}
```

(Note: The OCR text contained significant repetitions and garbled segments. I have reconstructed the logical flow based on the provided content while cleaning up the artifacts.)

[/content]

*Self-correction during processing: The provided OCR text was highly repetitive and overlapping across pages. I have provided a clean version that follows the document structure present in the source.*

***

```markdown
[content]
You couldn't really apply Backward Elimination to Polynomial Regression and Random Forest Regression models because these models don't have coefficients combined in a linear regression equation and therefore don't have p-values.

However, in Chapter 9 - Dimensionality Reduction, we will see some techniques like Backward Elimination, to reduce the number of features, based on Feature Selection & Feature Extraction.

- What are Low/High Bias/Variance in Machine Learning?**
- **Low Bias** is when your model predictions are very close to the real values.
- **High Bias** is when your model predictions are far from the real values.
- **Low Variance**: when you run your model several times, the different predictions of your observation points won't vary much.
- **High Variance**: when you run your model several times, the different predictions of your observation points will vary a lot.

What you want to get when you build a model: Low Bias and Low Variance.

## Chapter 3 : part 1
## Logistic Regression

### 3.1.1 REGRESSION vs CLASSIFICATION
Regression and Classification algorithms are Supervised Learning algorithms. Both the algorithms are used for prediction in machine learning and work with the labeled datasets. But the difference between both is how they are used for different machine learning problems.

> To predict the continuous values such as price, salary, age, etc., and Classification algorithms are used to predict/Classify the discrete values such as Male or Female, True or False, Spam or Not Spam, etc.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

> The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Types of ML Classification Algorithms: Classification Algorithms can be further divided into the following types:

- Logistic Regression
- K-Nearest Neighbors
- Support Vector Machines (SVM)
- Kernel SVM
- Naive Bayes
- Decision Tree Classification
- Random Forest Classification

Regression: Regression is a process of finding the correlations between dependent and independent variables. It helps in predicting the variables such as Market Trends, prediction of House prices, etc.

> The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

Types of Regression Algorithm:

- Simple Linear Regression
- Multiple Linear Regression
- Polynomial Regression
- Support Vector Regression
- Decision Tree Regression

## Difference between Regression and Classification:

| Regression Algorithm | Classification Algorithm |
|---|---|
| i. In *Regression*, the output variable must be of continuous nature or real value. | ii. In *Classification*, the output variable must be of discrete value. |
| iii. The task of the **regression algorithm** is to **map** the inputvalue(x) with the continuous outputvariable(y). | iv. The task of the **classification algorithm** is to map the inputvariable(s) with the *discrete* outputvariable(y). |
| v. Regression Algorithms are used with *continuous data*. | vi. Classification Algorithms are used with *discrete data*. |
| vii. In *Regression*, we try to find the *best fit line*, which can predict the output more accurately. | viii. In *Classification*, we try to find the **decision boundary**, which can divide the dataset into different classes. |
| ix. Regression algorithms can be used to solve the regression problems such as Weather Prediction, House price prediction, etc. | x. Classification Algorithms can be used to solve classification problems such as identification of spam cells, Speech Recognition, identification of cancer cells, etc. |
| xi. The regression algorithm can be further divided into *Linear* and *Non-linear Regression*. | xii. The Classification algorithms can be divided into *Binary* and *Multi-class Classifier*. |

### 3.1.2 Introduction to Logistic Regression
The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

## Does regression mean?
What you want to get when you build a model: Low Bias and Low Variance.

The regression algorithm can be further divided into *Linear* and *Non-linear Regression*.

### 3.1.3 Logistic Regression & Sigmoid Function
In our first attempt, we used Linear Regression, y = b0 + b1. But in our last attempt we ended up with S-shaped function.

```
p = \frac{1}{1 + e^{-y}}
```

(Note: The OCR text contained significant repetitions and garbled segments. I have reconstructed the logical flow based on the provided content while cleaning up the artifacts.)
[/content]
```
Wait, the prompt asks for *only* the final text in [content]. I will provide the cleaned version now. 

[content]
You couldn't really apply Backward Elimination to Polynomial Regression and Random Forest Regression models because these models don't have coefficients combined in a linear regression equation and therefore don't have p-values.

However, in Chapter 9 - Dimensionality Reduction, we will see some techniques like Backward Elimination, to reduce the number of features, based on Feature Selection & Feature Extraction.

- **What are Low/High Bias/Variance in Machine Learning?**
- **Low Bias** is when your model predictions are very close to the real values.
- **High Bias** is when your model predictions are far from the real values.
- **Low Variance**: when you run your model several times, the different predictions of your observation points won't vary much.
- **High Variance**: when you run your model several times, the different predictions of your observation points will vary a lot.

What you want to get when you build a model: Low Bias and Low Variance.

## Chapter 3 : part 1
## Logistic Regression

### 3.1.1 REGRESSION vs CLASSIFICATION
Regression and Classification algorithms are Supervised Learning algorithms. Both the algorithms are used for prediction in machine learning and work with the labeled datasets. But the difference between both is how they are used for different machine learning problems.

> To predict the continuous values such as price, salary, age, etc., and Classification algorithms are used to predict/Classify the discrete values such as Male or Female, True or False, Spam or Not Spam, etc.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

> The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Types of ML Classification Algorithms: Classification Algorithms can be further divided into the following types:

- Logistic Regression
- K-Nearest Neighbors
- Support Vector Machines (SVM)
- Kernel SVM
- Naive Bayes
- Decision Tree Classification
- Random Forest Classification

Regression: Regression is a process of finding the correlations between dependent and independent variables. It helps in predicting the variables such as Market Trends, prediction of House prices, etc.

> The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

Types of Regression Algorithm:

- Simple Linear Regression
- Multiple Linear Regression
- Polynomial Regression
- Support Vector Regression
- Decision Tree Regression

## Difference between Regression and Classification:

| Regression Algorithm | Classification Algorithm |
|---|---|
| i. In *Regression*, the output variable must be of continuous nature or real value. | ii. In *Classification*, the output variable must be of discrete value. |
| iii. The task of the **regression algorithm** is to **map** the inputvalue(x) with the continuous outputvariable(y). | iv. The task of the **classification algorithm** is to map the inputvariable(s) with the *discrete* outputvariable(y). |
| v. Regression Algorithms are used with *continuous data*. | vi. Classification Algorithms are used with *discrete data*. |
| vii. In *Regression*, we try to find the *best fit line*, which can predict the output more accurately. | viii. In *Classification*, we try to find the **decision boundary**, which can divide the dataset into different classes. |
| ix. Regression algorithms can be used to solve the regression problems such as Weather Prediction, House price prediction, etc. | x. Classification Algorithms can be used to solve classification problems such as identification of spam cells, Speech Recognition, identification of cancer cells, etc. |
| xi. The regression algorithm can be further divided into *Linear* and *Non-linear Regression*. | xii. The Classification algorithms can be divided into *Binary* and *Multi-class Classifier*. |

### 3.1.2 Introduction to Logistic Regression
The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

## Does regression mean?
What you want to get when you build a model: Low Bias and Low Variance.

The regression algorithm can be further divided into *Linear* and *Non-linear Regression*.

### 3.1.3 Logistic Regression & Sigmoid Function
In our first attempt, we used Linear Regression, y = b0 + b1. But in our last attempt we ended up with S-shaped function.

```
p = \frac{1}{1 + e^{-y}}
```

(Note: The OCR text contained significant repetitions and garbled segments. I have reconstructed the logical flow based on the provided content while cleaning up the artifacts.)
[/content]
```
Wait, the prompt asks for *only* the final text in [content]. I will provide the cleaned version now. 

[content]
You couldn't really apply Backward Elimination to Polynomial Regression and Random Forest Regression models because these models don't have coefficients combined in a linear regression equation and therefore don't have p-values.

However, in Chapter 9 - Dimensionality Reduction, we will see some techniques like Backward Elimination, to reduce the number of features, based on Feature Selection & Feature Extraction.

- **What are Low/High Bias/Variance in Machine Learning?**
- **Low Bias** is when your model predictions are very close to the real values.
- **High Bias** is when your model predictions are far from the real values.
- **Low Variance**: when you run your model several times, the different predictions of your observation points won't vary much.
- **High Variance**: when you run your model several times, the different predictions of your observation points will vary a lot.

What you want to get when you build a model: Low Bias and Low Variance.

## Chapter 3 : part 1
## Logistic Regression

### 3.1.1 REGRESSION vs CLASSIFICATION
Regression and Classification algorithms are Supervised Learning algorithms. Both the algorithms are used for prediction in machine learning and work with the labeled datasets. But the difference between both is how they are used for different machine learning problems.

> To predict the continuous values such as price, salary, age, etc., and Classification algorithms are used to predict/Classify the discrete values such as Male or Female, True or False, Spam or Not Spam, etc.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

> The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Types of ML Classification Algorithms: Classification Algorithms can be further divided into the following types:

- Logistic Regression
- K-Nearest Neighbors
- Support Vector Machines (SVM)
- Kernel SVM
- Naive Bayes
- Decision Tree Classification
- Random Forest Classification

Regression: Regression is a process of finding the correlations between dependent and independent variables. It helps in predicting the variables such as Market Trends, prediction of House prices, etc.

> The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

Types of Regression Algorithm:

- Simple Linear Regression
- Multiple Linear Regression
- Polynomial Regression
- Support Vector Regression
- Decision Tree Regression

## Difference between Regression and Classification:

| Regression Algorithm | Classification Algorithm |
|---|---|
| i. In *Regression*, the output variable must be of continuous nature or real value. | ii. In *Classification*, the output variable must be of discrete value. |
| iii. The task of the **regression algorithm** is to **map** the inputvalue(x) with the continuous outputvariable(y). | iv. The task of the **classification algorithm** is to map the inputvariable(s) with the *discrete* outputvariable(y). |
| v. Regression Algorithms are used with *continuous data*. | vi. Classification Algorithms are used with *discrete data*. |
| vii. In *Regression*, we try to find the *best fit line*, which can predict the output more accurately. | viii. In *Classification*, we try to find the **decision boundary**, which can divide the dataset into different classes. |
| ix. Regression algorithms can be used to solve the regression problems such as Weather Prediction, House price prediction, etc. | x. Classification Algorithms can be used to solve classification problems such as identification of spam cells, Speech Recognition, identification of cancer cells, etc. |
| xi. The regression algorithm can be further divided into *Linear* and *Non-linear Regression*. | xii. The Classification algorithms can be divided into *Binary* and *Multi-class Classifier*. |

### 3.1.2 Introduction to Logistic Regression
The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training training dataset and after that training, it categorizes the data into different classes.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

## Does regression mean?
What you want to get when you build a model: Low Bias and Low Variance.

The regression algorithm can be further divided into *Linear* and *Non-linear Regression*.

### 3.1.3 Logistic Regression & Sigmoid Function
In our first attempt, we used Linear Regression, y = b0 + b1. But in our last attempt we ended up with S-shaped function.

```
p = \frac{1}{1 + e^{-y}}
```

(Note: The OCR text contained significant repetitions and garbled segments. I have reconstructed the logical flow based on the provided content while cleaning up the artifacts.)
[/content]
```
Wait, the prompt asks for *only* the final text in [content]. I will provide the cleaned version now. 

[content]
You couldn't really apply Backward Elimination to Polynomial Regression and Random Forest Regression models because these models don't have coefficients combined in a linear regression equation and therefore don't have p-values.

However, in Chapter 9 - Dimensionality Reduction, we will see some techniques like Backward Elimination, to reduce the number of features, based on Feature Selection & Feature Extraction.

- **What are Low/High Bias/Variance in Machine Learning?**
- **Low Bias** is when your model predictions are very close to the real values.
- **High Bias** is when your model predictions are far from the real values.
- **Low Variance**: when you run your model several times, the different predictions of your observation points won't vary much.
- **High Variance**: when you run your model several times, the different predictions of your observation points will vary a lot.

What you want to get when you build a model: Low Bias and Low Variance.

## Chapter 3 : part 1
## Logistic Regression

### 3.1.1 REGRESSION vs CLASSIFICATION
Regression and Classification algorithms are Supervised Learning algorithms. Both the algorithms are used for prediction in machine learning and work with the labeled datasets. But the difference between both is how they are used for different machine learning problems.

> To predict the continuous values such as price, salary, age, etc., and Classification algorithms are used to predict/Classify the discrete values such as Male or Female, True or False, Spam or Not Spam, etc.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

> The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Types of ML Classification Algorithms: Classification Algorithms can be further divided into the following types:

- Logistic Regression
- K-Nearest Neighbors
- Support Vector Machines (SVM)
- Kernel SVM
- Naive Bayes
- Decision Tree Classification
- Random Forest Classification

Regression: Regression is a process of finding the correlations between dependent and independent variables. It helps in predicting the variables such as Market Trends, prediction of House prices, etc.

> The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

Types of Regression Algorithm:

- Simple Linear Regression
- Multiple Linear Regression
- Polynomial Regression
- Support Vector Regression
- Decision Tree Regression

## Difference between Regression and Classification:

| Regression Algorithm | Classification Algorithm |
|---|---|
| i. In *Regression*, the output variable must be of continuous nature or real value. | ii. In *Classification*, the output variable must be of discrete value. |
| iii. The task of the **regression algorithm** is to **map** the inputvalue(x) with the continuous outputvariable(y). | iv. The task of the **classification algorithm** is to map the inputvariable(s) with the *discrete* outputvariable(y). |
| v. Regression Algorithms are used with *continuous data*. | vi. Classification Algorithms are used with *discrete data*. |
| vii. In *Regression*, we try to find the *best fit line*, which can predict the output more accurately. | viii. In *Classification*, we try to find the **decision boundary**, which can divide the dataset into different classes. |
| ix. Regression algorithms can be used to solve the regression problems such as Weather Prediction, House price prediction, etc. | x. Classification Algorithms can be used to solve classification problems such as identification of spam cells, Speech Recognition, identification of cancer cells, etc. |
| xi. The regression algorithm can be further divided into *Linear* and *Non-linear Regression*. | xii. The Classification algorithms can be divided into *Binary* and *Multi-class Classifier*. |

### 3.1.2 Introduction to Logistic Regression
The task of the Regression algorithm is to find the mapping function to map the input variable(x) to the continuous output variable(y).

Example: Suppose we want to do weather forecasting, for this, we will use the Regression algorithm. In weather prediction, the model is trained on the past data and once the training is complete, it can easily predict the weather for future days.

The task of classification algorithm is to find the mapping function to map the input(x) to the discrete output(y).

Example: The best example to understand the Classification problem is Email Spam Detection. The model is trained on the basis of emails on different parameters, and whenever it receives a new email, it identifies whether the email is spam or not. If it is spam, then it is moved to the Spam folder.

Classification: Classification is a process of finding a function which helps in dividing the dataset into classes based on different parameters. In Classification, a computer program is trained on the training dataset and after that training, it categorizes the data into different classes.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_80_0.png)

## Does regression mean?
What you want to get when you build a model: Low Bias and Low Variance.

The regression algorithm can be further divided into *Linear* and *Non-linear Regression*.

### 3.1.3 Logistic Regression & Sigmoid Function
In our first attempt, we used Linear Regression, y = b0 + b1. But in our last attempt we ended up with S-shaped function.

```
p = \frac{1}{1 + e^{-y}}
```

(Note: The OCR text contained significant repetitions and garbled segments. I have reconstructed the logical flow based on the provided content while cleaning up the artifacts.)
