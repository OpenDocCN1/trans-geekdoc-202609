

```text
xlist = np.linspace(-2.0, 2.0, 100)
ylist = np.linspace(-2.0, 2.0, 100)
X1,Y1 = np.meshgrid(xlist, ylist)
F = b1[0]*X1 + b1[1]*Y1+b1[2]*X1**2 + \
    b1[3]*Y1**2 + b1[4]
plt.contour(X1, Y1, F, [0], colors = 'k',
            linestyles = 'solid')
plt.show()
```

- d) Find the number of correct predictions by CELR which ideally should be 331 out of 337 due to the 6 outliers. Explain any discrepancies.

```text
Y_pred = logreg.predict(X)
print("Number of samples predicted correctly is ", \
    format(np.sum(Y_pred == y),'d'))
```

## 8.5 (PROJECT) Adjust the code above to include regularization using the ridge penalty.

- a) Try using the following code in place of their counterparts in the above project. This is the default setting for C.

```text
logreg = LogisticRegression(C=1.0)
logreg.fit(X, y)
```

- b) Next, try different values of C such as 4.0, 1.0, 0.4, and 0.1. You can plot each of the decision boundaries using the plot routine of the previous project. What value of C provides the best results?

## 8.6 (PROJECT) In this project, the goal is to write and execute the code for LCLR. It requires the logistic function, a routine for LCLR, and an iterative loop to implement gradient descent. The partial derivatives of the form given in Eq. (8.4.12) will be needed. Also, the code below assumes that all the previous projects have been executed.

- a) Define the log-cosh function and the LCLR routine.

```text
logcosh = lambda x: np.logaddexp(x, -x) - np.log(2)
def LCLR(b):
    n = X.shape[0]
    p = 1./(1.+np.exp((-np.dot(X.T,b))))
    diff = y-p
    dbi = -p*(1-p)*np.tanh(y-p)/n
    db = np.dot(X,dbi.T)
    cost = np.sum(logcosh(y-p))/n
    return cost,db
```

- b) Define the X and y data and then run the iterative loop for gradient descent to convergence. Plot the results.

```text
Xd = train_df.drop(["flag"],axis=1)
X = np.array(Xd.T)
y1 = train_df["flag"]
y = np.array(y1)
learning_rate = 0.1
b = np.array([ 0.01,0.02,0.03,0.04,0.05] )
T = 30 # 30 iterations of gradient descent
iterations = np.zeros(T)
for t in range(T):
    loss,db = LCLR(b)
    iterations[t] = loss
    b = b - learning_rate * db.T
b2 = b
plt.plot(iterations)
plt.show()
```

- c) Plot the results of both CELR and LCLR. Compare the results noting that no regularization was used on LCLR.

```text
plt.figure() # Create a new figure window
set1 = train_df[train_df['flag']==1]
set0 = train_df[train_df['flag']==0]
plt.scatter(set1['xval'],set1['yval'],color='red')
plt.scatter(set0['xval'],set0['yval'],color='blue')
xlist = np.linspace(-2.0, 2.0, 100)
ylist = np.linspace(-2.0, 2.0, 100)
X1,Y1 = np.meshgrid(xlist, ylist)
F = b1[0]*X1 +b1[1]*Y1+b1[2]*X1**2 + \
    b1[3]*Y1**2 + b1[4]
plt.contour(X1, Y1, F, [0], colors = 'k',
    linestyles = 'solid')
F = b2[0]*X1 +b2[1]*Y1+b2[2]*X1**2 + \
    b2[3]*Y1**2 + b2[4]
plt.contour(X1, Y1, F, [0], colors = 'green',
    linestyles = 'dashed')
plt.title("LCLR = green, CELR = black")
plt.show()
```

- d) Find the number of correct predictions by LCLR which ideally should be 331 out of 337 due to the 6 outliers. Explain any discrepancies.

```text
p = 1./(1.+np.exp((-np.dot(X.T,b2))))
Y_pred = p > 0.5
print("Number of samples predicted correctly is ", \
       format(np.sum(Y_pred == y),'d'))
```

## Reference

James, G., Witten, D., Hastie, T. et al. (2023). *An Introduction to Statistical Learning with Applications in Python*. Springer.

## 9 Neural Networks Using Log-Cosh

### 9.1 Introduction

Our objective in this chapter is to build on Chapter 8, which addressed logistic regression using the log-cosh loss function, and investigate the feasibility of applying the log-cosh loss to neural networks. The question here becomes: Can log-cosh methods be effectively used in conjunction with neural networks? Since we already know that log-cosh methods are applicable to logistic regression, it naturally follows that they should be immediately applicable to neural networks. Therefore, the issue at hand is to determine the advantages of log-cosh neural networks over cross-entropy neural networks for machine learning and what new capabilities they may provide, if any. This is the main question to be explored in this chapter.

We begin with a brief history of neural networks (see Haykin 2009; James et al. 2023) and then describe the basic units and architecture in the next section, including the activation functions, which are the non-linear part of the units that allow neural networks to learn patterns and characteristics of the input data. Then, details of training neural networks will be described, along with the steps involved in computing gradients needed for training. The chapter concludes with examples of binary classification and a number of metrics typically used to assess accuracy.

### 9.2 A Brief History of Neural Networks

Work on neural networks (NNs) began in earnest in the mid-to-late 1980s and early 1990s by computer scientists in the pursuit of artificial intelligence (AI) systems. Neural networks were initially touted as a way to mimic the behavior and operation of neurons in the brain, although that connection is not fully embraced today. There was much excitement at the time regarding the potential of NNs to solve many unsolvable problems due to breakthroughs such as the use of the sigmoid function for activation in conjunction with the development of efficient methods for back propagation. But there were many technological barriers to its success at that time and it quickly fell out of favor. In particular, computers were relatively slow and the era of big data had not yet arrived. As skepticism grew, NNs were relegated to being a stagnant technology with no future and, as a result, lay dormant for many years. In the intervening years, the speed of computers increased significantly, new and efficient algorithms for neural networks were developed, and the Internet emerged as a way to deliver large datasets and open-source software to users around the world.

By 2010, the neural network had emerged from its dormant state and made an impact in many important applications, most notably speech recognition, image processing, and natural language processing. In medical applications, it was able to quickly and accurately identify cancerous tissue and gained a strong foothold in radiology. Other advances in optimization methods and NN architectures with many layers of neurons were made in the same period. Some of the most difficult problems became tractable and were solved using these advanced techniques. The promise of AI systems of the 1980s was finally being realized. Collectively, these methods were rebranded as “deep learning.” This term caught the attention of academics and practitioners alike and is now used to describe almost all neural networks in use today. The key driver from the early use of NNs to its ubiquitous presence today is the availability of big data. Images, video files, audio files, etc. are well-known forms of data for deep learning, but there are an uncountable number of other datasets that are also being processed using deep NNs. Eventually, NNs led to the development of large language models (LLMs) which are at the heart of recent generative AI systems used by hundreds of millions of people today.

Our purpose in this chapter is rather limited to a comparison of traditional cross-entropy NNs (CENNs) against robust log-cosh NNs (LCNNs). Here, we view NNs as simply multiple layers of logistic regression modified only by the activation functions used in each layer. If we have a single layer (i.e. no hidden layers), it is standard logistic regression. If we have two or three layers it is a shallow NN. If there are many layers of logistic regression, it is called a deep NN, which is used for deep learning. This view may be somewhat oversimplified but it is something to keep in mind as a good starting point to understand neural networks. The meaning of layers and networks will become clear later in this chapter but the basic idea is that complex relationships between the independent variables and the response variable can be realized by increasing the parameter space of the problem. Training of these types of networks is carried out using gradient descent but they are usually accelerated using *momentum* and *rmsprop*, which will be described when the Adam optimization technique is detailed in Chapter 10. However, the method of creating the gradient terms through back propagation will be described in this chapter. Then, a simple circular dataset from Chapter 8 will be used to compare and contrast LCNN and CENN. A more advanced application using the MNIST dataset will be used to compare the two methods in Chapter 10. Finally, in the last section, binary classification metrics such as the $F_1$ score and AUROC will be described.

> Nomenclature: You may have heard the terms **sigmoid function** and **logistic function** and wondered about the difference between them. The logistic function and the sigmoid function are equivalent. Statisticians typically use the term “logistic function,” while those in machine learning prefer “sigmoid function.” Generally, the term “logistic function” is used when referring to equations or computing probabilities. In contrast, “sigmoid function” is used when discussing activation functions in neural networks.

### 9.3 Defining Neural Networks

In this section, we describe the basic building blocks of neural networks. These building blocks will be used to construct a prototypical neural network. As a simple way of thinking about neural networks, one

