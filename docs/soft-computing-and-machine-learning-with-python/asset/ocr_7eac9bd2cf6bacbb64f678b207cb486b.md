# Prediction of Solar Irradiation Using Quantum Support Vector ... 123

unit of information is known as a quantum digit (qudit) [16]. Just like a classical computer, which use gates for computation, quantum computers also use quantum gates to perform operations on quits. Essentially, a quantum gate operation on a quantum state |$\psi\rangle$ (which is represented as a column vector) is a linear operation. Therefore, mathematically speaking, quantum information processing makes use of vectors, matrices and tensors, hence it involves linear transformations.

# Quantum Machine Learning

Machine learning generally represents data in vector and matrix form. This is also the case with QIP, hence why QIP concepts find applications in machine learning. This results in the new field of research called quantum machine learning. Quantum machine learning can take two forms: where classical machine learning algorithms are transformed into their quantum counterparts; to be implemented on a quantum information processor, or taking some of the computationally expensive classical machine learning sub-routines and implementing them on the quantum computer.

# Model Evaluation and Validation

Different measures are used to evaluate and validate models. These measures include mean squared error (MSE), Root mean squared error (RMSE), mean absolute error (MAE), and $R^2$ error.

# Mean Squared Error

Mean squared error is one of the measures of the goodness of fit. It measures the closeness of a data line to the data points. For n as the number of predictions, $\widehat{Y}$ as the vector of predicted values, and Y as the vector of observations, MSE is given

```
$MSE = \frac{1}{n}\sum_{i=1}^{n}(\widehat{Y}_i - Y_i)^2 \quad (3)$
```

# Root Mean Squared Error

Root mean squared error, which is also a measure of goodness of fit, is the average Euclidean distance of the line from the data points. It is given as