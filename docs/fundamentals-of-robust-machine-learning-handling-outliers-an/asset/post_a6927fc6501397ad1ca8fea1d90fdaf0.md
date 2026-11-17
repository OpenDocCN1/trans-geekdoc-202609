
![](img/f26d7f591c2a080d86425985301266a4_293_0.png)

and the true negative rate (TNR), sometimes called the *specificity*, is given by

TNR = \frac{tn}{tn + fp}. (9.8.5)

Then, the FPR is given by

FPR = 1 - TNR = 1 - \frac{tn}{tn + fp} = \frac{fp}{tn + fp}. (9.8.6)

In Figure 9.9, we show a few hypothetical plots of TPR against FPR to illustrate the concepts discussed above. The trajectory of the plot starts from (0,0) and traces a path to (1,1). At (0,0), the classifier predicts all 0's, meaning no false positives, while at (1,1), the classifier predicts all 1's, meaning no false negatives. All other cases fall in between these two extremes as the ROC traces a path from one corner to the other. Three such paths are shown. First, the diagonal line represents the case of a random value classifier. That is, a classifier that simply guesses the outcomes would produce a diagonal line which represents a worst-case classifier. Second, the curve labeled A is the plot for classifier A that is clearly better than the random guess classifier since its trajectory lies above the diagonal line. Third, the curve labeled B is the plot for classifier B that is better than A because its curve is above A.

**Example:** Let \( p_T \) be the threshold for deciding whether a probability value from a classifier should be considered a 0 or a 1. Next, select different values of \( p_T \) starting at 0 and ending at 1 in steps of 0.01—a total of 101 points. For each \( p_T \), the TPR and FPR are plotted to produce the ROC curve. The quality of a classifier can be established by finding the area under the ROC curve (AUROC). Three classifiers are compared in Figure 9.9. Specifically, the AUROC of a random guess classifier is 0.5. However, the total AUROC of classifier A is 0.75 whereas the total area under the ROC of classifier B is 0.8. Therefore, B is considered to be better than A. The AUROC can be loosely interpreted as the probability that the classifier has assigned the correct class to the data points. The ideal value under this interpretation is of course AUROC = 1.0.

When AUROC is used with robust methods, the results can be misleading to some extent. For example, the AUROC of LCNN tends to be similar to CENN even though the F1 results are better than CENN. In fact, the AUROC may not be a suitable metric in this type of comparison. Chapter 12 describes an alternative approach which is better suited for such a comparison.

## 9.9 Summary

In this chapter, it has been shown that the log-cosh loss function is effective when used with neural networks. In fact, it is robust to outliers for binary classification problems. The cross-entropy loss commonly used in neural networks is affected by outliers but it can be made more tolerant with the use of the ridge penalty for regularization. However, the log-cosh loss was shown to have an auto-regularization feature such that penalty functions are not required. Chapters 10 and 12 take these concepts to several data science problems to illustrate their use in real-world applications. A number of other capabilities provided by using this robust loss function in neural networks will also be described in those chapters.

To close out this chapter, various metrics used to compare different binary classification tools were presented. Prediction accuracy by itself is not sufficient as an evaluation metric. Instead, metrics such as recall, precision, and F1 score are more appropriate. In addition, the AUROC is also useful when comparing different classifiers. In Chapter 12, the effect of outliers on the AUROC metrics is considered in detail.

## Problems

The following two-layer neural network will be used in all problems to follow. The labels are associated with Python code provided in the projects.

![](img/f26d7f591c2a080d86425985301266a4_294_0.png)

### 9.1 How many total parameters must be learned during training for the above network?

### 9.2 Find the expression for ∂J^LC(b0)/∂b0 for the log-cosh loss function. (Hint: derive Eq. (9.5.17) noting that the bias term is fixed at 1.)

### 9.3 Apply the chain rule to find the partial derivative term ∂J^LC(w)/∂w1 for the log-cosh loss function. (Hint: this is similar to the derivation of Eq. (9.5.18).)

### 9.4 Apply the chain rule as in Eq. (9.5.19) to find the complete expression for ∂J^LC(w)/∂w13 using the log-cosh loss function. (Hint: you will need to use the indicator function since the relu activation function is involved.)

### (Project)

This project involves the creation of a synthetic circular dataset and the implementation of CENN/LCNN algorithms to find a nonlinear decision boundary.

- a) Import the libraries.

```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
```

- b) Build a circular dataset similar to Figure 9.6(a) using Python. Assign six data points to be outliers as shown in the upper region of the figure. The Python code below is suitable for this purpose. Enter this code and check the results in a Jupyter notebook.

```
m = 354
np.random.seed(42)
setx = np.random.random(m) * 4.0 - 2.0
np.random.seed(30)
sety = np.random.random(m) * 4.0 - 2.0
y = np.zeros(m)
for i in range(m):
    if (setx[i]**2 + sety[i]**2) < 0.9:
        y[i] = 0
    elif (setx[i]**2 + sety[i]**2) > 1.2:
        y[i] = 1
    else:
        y[i] = -1
    counter = 0
outliers = 6 # number of outliers
for i in range(100):
    if sety[i] > 1.6 and counter < outliers:
        y[i] = 0
        counter += 1
setx_df = pd.DataFrame(setx, columns=["xval"])
```

```
sety_df = pd.DataFrame(sety, columns=["yval"])
setr_df = pd.DataFrame(y, columns=['flag'])
setx_df['yval'] = sety_df['yval']
setx_df['flag'] = setr_df['flag']
set10 = setx_df[setx_df['flag'] == 1]
set00 = setx_df[setx_df['flag'] == 0]
plt.scatter(set10['xval'], set10['yval'], \
color='red')
plt.scatter(set00['xval'], set00['yval'], \
color='blue')
plt.show()
```

- c) Create the X and y dataset for the neural network.

```
# Create a DataFrame
df = pd.DataFrame({'X': setx, 'y': sety, \
'flag': y})
# Filter DataFrame to exclude rows where z is -1
X_df = df[df['flag'].isin([0, 1])]
Xd = X_df.drop(["flag"], axis=1)
X = np.array(Xd)
y1 = X_df["flag"]
y = np.array(y1)
```

- d) The code below is for a specific neural network that performs CENN/LCNN using the detailed example provided in this chapter. The architecture of the NN was provided earlier in the figure. The forward propagation uses four steps. The backward propagation uses two steps and requires the partial derivatives to compute gradients for weights and biases, which are then stored in matrices and vectors for ease of use. The learning rate is used to obtain the new estimates. Note: The code below is written in a form that is easy to follow rather than for efficiency or general-purpose use. Enter the code and run it on the circular dataset just created. It will initially run CENN as the default setting.

```
#Define logcosh function
logcosh = lambda x: np.logaddexp(x, -x) - \
np.log(2)
#Define sigmoid function
def sigmoid(z):
    a = 1./(1.+ np.exp(-z))
    return a
#Initialize weights and biases
np.random.seed(9)
W_matrix = np.random.randn(4,2)*0.001
w_vector = np.random.randn(4)*0.001
b_vector = np.random.randn(4,1)*0.001
```

```
pick_random = np.random.randn(5)*0.001
b0 = pick_random[4]
n = X.shape[0]
#IMPORTANT: CE=1 and LC=0, OR CE=0 and LC=1
CE = 1
LC = 0
if (CE):
    print("Cross-entropy")
else:
    alpha = 5.  # hyperparameter a in log-cosh
    print("Log-cosh")
learning_rate = 0.2
maxIter = 7500
epochs = np.zeros(maxIter)
#MAIN LOOP
for t in range(maxIter):
# FWD PROP
    z = np.matmul(W_matrix,X.T)+b_vector     #Step 1
    a = z*(z>0)   # ReLU function          #Step 2
    zout = np.matmul(w_vector,a)+b0        #Step 3
    p = sigmoid(zout)                      #Step 4
#BACK PROP
    delW_matrix = np.zeros([4,2])
    delW_vector = np.zeros([4])
    delb_vector = np.zeros([4,1])
    delb0 = 0.0
    wvec = np.array([w_vector])
    ones_matrix = np.ones((n, 1))
    for i in range(n):
        Indicator = np.array([z[:,i]>0,z[:,i]>0])
        if (CE):
            fullW_matrix = np.matmul(wvec.T, \
            [X[i,:]])*(p[i]-y[i])
            fullb_vector = np.matmul(wvec.T, \
            [ones_matrix[i,:]])*(p[i]-y[i])
            delW_vector += (y[i]-p[i])*(-a[:,i])
            delb0 += (y[i]-p[i])*(-1.)
        else:
            fullW_matrix = -np.matmul(wvec.T, \
            [X[i,:]])*np.tanh(alpha*(y[i]-p[i]))
            fullb_vector = -np.matmul(wvec.T, \
            [ones_matrix[i,:]])* \
            np.tanh(alpha*(y[i]-p[i]))
```
