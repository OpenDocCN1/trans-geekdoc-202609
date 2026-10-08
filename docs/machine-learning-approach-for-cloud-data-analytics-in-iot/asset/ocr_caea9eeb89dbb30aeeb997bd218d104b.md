+   3. After that we install Git terminal window just like Linux.
4. Further, we install Ethereum Wallet (stores and manages Ethereum accounts and transactions) or Metamask wallet (an extension where to transfer and deposit ethers).

# 18.4.5  Reward Model

The reward model is used to buffer the reward points that are evaluated on the basis of daily healthcare activities. It works on the basis of the push-based flow method to distribute rewards to all the health players accordingly. This method computes rewards per hour spent in performing activities and operating on-chain computational overhead to a significant extent. It can handle more number of health players at a given instant $t$, where active health players are engaged in doing healthcare activities, let us say for doing exercises and taking medicines, create distribute events in a given timeline $T$. For every health player,

```
totalreward$_{j}$ = sum$_{t}$reward$_{jt}$ = activities$_{j}$ * sum$_{t}$ $\frac{reward}{T_{t}}$
```

that is, total reward for every health patient is calculated on the basis of their routine-based healthcare activities in given timeline order and these rewards are stored in a table in chronological order which is further used in the predictive model.

# 18.4.6  Predictive Models

There exist many efficient and affordable predictive models because of the increase in the running capacity of thousands of models on multiple cores. What matters is the suitability of the predictive model for a given input dataset. So, it totally depends on the desirable nature of the predictive target. We have taken different machine learning algorithms to design a model. They are linear regression, logistic regression, support vector machine (SVM), artificial neural networks, etc; the different machine algorithms work on different nature of data. Linear regression is used when we want to predict continuous values. Logistic regression is considered to be a more powerful statistical way of modeling a binomial result with one or more descriptive variables. It estimates the relationship between the categorical dependent variable by the use of the logistic function. Next is the SVM that can be used for binary classification and also for multi-class