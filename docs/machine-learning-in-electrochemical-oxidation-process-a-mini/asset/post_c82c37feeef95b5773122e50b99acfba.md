
![](img/3aa35d4c40b6a535721ef39907027cd0_2_0.png)

Fig. 1. An overview of application in ML in electrochemical oxidation.

2021. And these keywords are hotly researched until 2023. Thus, ML research predicting applications related to electrochemical oxidation may be the focus of future research.

In general, the interdisciplinary research at the intersection of electrochemistry and ML exhibits a noticeable growth trend, signifying widespread attention to this field. Keywords such as degradation, model, performance, oxidation, lithium-ion battery, and CO2 reduction reveal the thematic framework of the cross-disciplinary exploration between electrochemistry and ML. Therefore, ML has proven to be an effective technology applied in electrochemistry. As shown in Fig. 1, based on the results of bibliometric analysis, this review article provided a systematic overview of recent advances in environmental applications of ML for electrochemical pollutant treatment, battery repair and degradation, electrochemical generation and synthesis, and surface mechanism analysis of materials.

## 3. Mainly machine learning algorithms in electrochemical oxidation

This section analyzed and summarized the basic theory of common ML algorithms, including MLR and typical nonlinear regression (NR) algorithms such as SVM, XGBoost, ANN and RF.

The MLR model determines the optimal parameter estimates by minimizing the discrepancy between the actual observed values and the predicted values of model (usually the sum of squared differences). This model is capable of assessing and interpreting the weight of each independent variable with respect to the dependent variable [27]. Within the context of electrochemical oxidation, MLR can be utilized to understand how various process parameters such as current density, pH value, electrode material, and treatment time influence the efficiency of electrochemical oxidation. By analyzing data collected from experimental processes, MLR aids in predicting the outcomes of electrochemical treatment under varying conditions and in optimizing process parameters to achieve maximum efficiency [28]. The multiple linear regression equation is a mathematical model used to describe the linear relationship between a dependent variable (Y) and multiple independent variables (X1, X2, ..., Xn). The equation is typically represented as follows (Eq. 1):

```
Y = \beta_1 X_1 + \beta_2 X_2 + \beta_3 X_3 + \cdots + \beta_n X_n + \varepsilon
```

where \beta_j (j = 1, 2, 3, ..., k) represents the regression coefficient, while \varepsilon denotes the error component.

NR is a form of regression analysis where observed data is modelled by a function that is a nonlinear combination of the model parameters and depends on one or more independent variables. NR is particularly useful in environmental applications, as the relationships between variables are often not linear. This type of regression allows for more accurate modeling and prediction of complex processes [29]. Nonlinear models can be generally expressed in the form (Eq. 2):

```
Y = f(x, \theta) + \varepsilon
```

where Y represents the response variable, while f denotes the function employed. The x indicates inputs, \theta symbolizes the parameters that require estimation, and \varepsilon refers to the error component. If the second derivative of the function with respect to any parameter is non-zero, then that parameter is categorized as a nonlinear parameter [30]. Based on that principle, numerous models with superior performance for addressing nonlinear problems have been developed, such as SVM, ANN, RF, and XGBoost, as shown in Fig. 2.

![](img/3aa35d4c40b6a535721ef39907027cd0_2_1.png)

Fig. 2. Schematic diagram of SVM, ANN, RF, and XGBoost algorithms.

As a general ML algorithm, the SVM idea was originally proposed by Vapnik and Chervonenkis in 1963 [31]. With constant improvement, SVM have emerged as a standard algorithm for ML, pattern recognition, and data fitting, and they are now applied to a wide range of real-world issues. SVM is based on finding a dividing hyperplane in the sample space based on the training set, thus differentiating different samples. The hyperplane in the sample space and the distance from any point to the hyperplane are denoted as Eqs. 3 and 4, respectively [4]:

```
\omega^T x + b = 0
```

```
r = \frac{|\omega^T x + b|}{\|\omega\|}
```

where \omega is the normal vector, which determines the direction of the hyperplane and b is the displacement term, which determines the distance between the hyperplane and the origin. If a hyperplane can correctly classify the training set, then the margin of the support vectors can be represented as Eq. 5. To find the hyperplane with the maximum margin, it is necessary to maximize Eq. 5. Consequently, this forms the fundamental expression of SVM, as represented by Eq. 6, which is the minimization of 1/\gamma. In practical scenarios, the original dataset may not always be linear. Therefore, when there is no hyperplane that can correctly classify the dataset in the original space, kernel functions are employed to map the samples from the original space to a higher-dimensional feature space. Thus, the equation is further derived as Eq. 7 [4].

```
Y = \frac{1}{\|\omega\|} \tag{5}
```

```
\min_{w,b} \frac{1}{2} \|\omega\|^2 \tag{6}
```

```
\min_{w,b} \frac{1}{2} \|\omega\|^2 + C \sum_{i=1}^m l_e(f(x_i) - y_i) \tag{7}
```

where \(\omega\) represents the regularization function, and \(l_e\) is the epsilon-insensitive loss function.

In summary, the SVM model employs a learning strategy based on maximizing the margin to map original samples into a higher-dimensional space, thereby finding the optimal hyperplane to solve nonlinear scientific problems.

XGBoost represents an advanced implementation of gradient boosting algorithms, popular for its excellent performance in various predictive modelling tasks [32,33]. Designed for efficiency, flexibility, and portability, XGBoost operates by sequentially constructing a series of decision trees, each correcting the errors of the previous one, thereby enhancing the predictive accuracy of the model. The algorithm includes regularization parameters, which help prevent overfitting and make it robust to noise in the data [34]. The XGBoost model is defined by a regularized learning objective that combines a loss function with a term that penalizes complexity, as follows (Eq. 8):

```
Z(x_t) = \sum_{i=1}^n l(y_i, \hat{y}_i^{t-1} + f_t(x_i)) + \Omega(f_t) \tag{8}
```

where, \(\hat{y}_i\) is the prediction for the i-th instance, \(y_i\) is the corresponding target, l represents a differentiable convex loss function that measures the discrepancy between the prediction \(\hat{y}_i\) and target \(y_i\), \(\hat{y}_i^{t-1}\) is the prediction from t - 1 tree, and \(\Omega\) presents the regression tree function used for regularization of the model. The inclusion of additional regularization terms helps to smooth the learned weights, thereby avoiding overfitting. The regularization term \(\Omega(f_t)\) is defined as follows (Eq. 9):

```
\Omega(f_t) = \gamma T + \frac{1}{2} \lambda \|\omega\|^2 \tag{9}
```

where, \(\gamma\) is a parameter that controls the complexity of the tree, T is the number of leaves in the tree, \(\lambda\) is a parameter for regularization on the leaf weights, and \(\omega\) are the leaf weights.

In XGBoost, the model is trained additively, where each tree \(f_t\) is added to minimize the loss function l(t). The process involves using first and second-order gradient statistics on the loss function to find the best tree structure at each iteration. The optimization of the objective function is performed using a second-order approximation, which allows for a quick and effective optimization. When an instance lacks the feature required for splitting in XGBoost, the model classifies it in a default direction, which is determined during the learning process. This approach enables the model to effectively handle missing values and enhances its robustness.

ANNs have emerged as a powerful tool in the field of electrochemical oxidation. Their ability to learn complex patterns and predict outcomes makes them ideal for optimizing and understanding various electrochemical processes. ANNs are computational models inspired by the human brain, consisting of interconnected nodes or neurons that process information [35,36]. ANNs typically consist of an input layer, one or more hidden layers, and an output layer. Each layer contains a number of neurons, and the neurons are interconnected with weights that are adjusted during the training phase. The basic formula for the output of a neuron is given by (Eq. 10):

```
y = f(\sum (w_i \cdot x_i) + b) \tag{10}
```

where \(x_i\) and \(y\) are input and output, \(w_i\) is weight, b is bias term and f is activation function. ANNs are trained using a dataset that contains input-output pairs. During training, the network adjusts its weights and biases to minimize the error between the predicted and actual outputs. The backpropagation algorithm is commonly used for training, which involves propagating the error back through the network to update the weights [37].

RF is a bagging ensemble learning method developed from decision tree algorithms. In this technology, each tree in the forest is trained on a random subset of data and replaced, increasing the diversity between trees and improving the accuracy and robustness of the model. This ensemble learning method operates by constructing multiple decision trees during the training period and outputs the mode of the classes (for classification) or the mean prediction (for regression) of the individual trees. RF demonstrates convergence properties to achieve a lower generalization error, as expressed in Eqs. 11–13 [38].

```
mg = (X, Y) = \alpha v_k l(h_k(X) = Y) - \max_{j \neq Y} \alpha v_k (h_k(X) = j) \tag{11}
```

```
PE^* = P_{X,Y} (mg(X, Y) < 0) \tag{12}
```

```
P_{X,Y} \left( P_\Theta(h(X, \Theta) = Y) - \max_{j \neq Y} h(X, \Theta) = j \right) < 0 \tag{13}
```

Eq. 11 defines the margin function for RF. It considers a set of classifiers \(h_1(x), h_2(x), ..., h_k(x)\), trained on a dataset randomly drawn from the distribution of random vectors X and Y. \(l(\cdot)\) represents an indicator function. The margin "mg" measures the extent to which the average vote for the correct class in X, Y surpasses the average vote for any other class. A larger margin indicates a higher confidence in classification. The generalization error is given by Eq. 12, which represents the probability of a random input X being misclassified in a RF (\(PE^* < 0\)). Ideally, this probability should be as low as possible. In RF, \(h_k(X) = h(X, \Theta_k)\), where for a large number of trees, as the quantity of trees increases, nearly all sequences \(\Theta_1, ..., PE^*\) converge to Eq. 13. This implies that with an increasing number of trees, the generalization error rate \(PE^*\) of the RF will converge to a fixed value, leading to more accurate model predictions. The flowchart of the application of these five common ML algorithms is shown in Fig. S6 (Supporting information).

## 4. Application of electrochemical oxidation combined with machine learning

The integration of ML algorithms in the field of electrochemical oxidation is increasingly receiving attention. In line with the previously mentioned bibliometric analysis, a comprehensive review of the application mechanisms of common ML algorithms in areas such as pollutant treatment, battery restoration, electrochemical synthesis, and material characterization analysis has been conducted. These algorithms play a crucial role in enhancing the understanding of electrochemical processes and improving the overall efficiency and effectiveness of electrochemical applications.

### 4.1. Electrochemical treatment of pollutants

ML has been widely used in the field of electrochemical pollutant treatment. These algorithms have shown promising results in a variety of applications, including predicting pollutant concentrations, optimizing treatment processes and analyzing the complex interactions between various factors in electrochemical systems [18].

Sun et al. evaluated the performance of models trained with pollutant characteristics and reaction conditions as input features,
