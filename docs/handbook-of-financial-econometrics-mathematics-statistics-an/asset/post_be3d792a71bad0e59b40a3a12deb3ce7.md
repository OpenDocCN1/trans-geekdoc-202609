
Verbraken, T., Bravo, C., Weber, R. and Baesens, B. (2014). Development and Application of Consumer Credit Scoring Models Using Profit-based Classification Measures. European Journal of Operational Research 238(2), 505-513.

Yeh, I.-C. and Lien, C.-H. (2009). The Comparisons of Data Mining Techniques for the Predictive Accuracy of Probability of Default of Credit Card Clients. Expert Systems with Applications 36, 2473-2480.

## Appendix: Python Codes

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

dataset = pd.read_csv('C:\\default of credit card clients.csv')
dataset.shape
dataset.head()
dataset = dataset.iloc[0:29999,:]
colForLog = ["X1",
            "X12","X13","X14","X15","X16","X17",
            "X18", "X19", "X20", "X21", "X22", "X23"]
for col in colForLog:
    dataset.loc[:, col] = ( dataset.loc[:, col]
    - dataset.loc[:,col].min()
    + dataset.loc[:,col].median()).apply(np.log)

dataset = dataset.drop(['Unnamed: 0'], axis = 1)

X = dataset.drop(['Y'],axis=1)
y = dataset['Y']

# Get 70-30 split to get the training-testing data
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y,
test_size=0.30, random_state = 42)

from sklearn import metrics # to get the accuracy
def calc_testing_score(X_train,
y_train, X_test, y_test, clf):
    clf = clf.fit(X_train, y_train)
    y_pred = clf.predict(X_test)
    accuracy = metrics.accuracy_score(y_test, y_pred)
    return accuracy

from sklearn.neighbors import KNeighborsClassifier
param_range = range(1, 100, 20)
# (a) get testing score for distance = uniform
for i in range(1, 100, 20):
    clf = KNeighborsClassifier(n_neighbors = i)
    clf2 = KNeighborsClassifier(n_neighbors = i, weights
        = "distance")
    accuracyTest = calc_testing_score(X_train, y_train, X_test,
        y_test, clf)
    accuracyTest2 = calc_testing_score(X_train, y_train, X_test,
        y_test, clf2)
```

### II. Decision Tree 2/5

```python
from sklearn.tree import DecisionTreeClassifier
param_range = np.arange(.1, .9, .1)
for i in np.arange(.1, .9, .1):
    clf = DecisionTreeClassifier(min_samples_split = i)
    clf2 = DecisionTreeClassifier(criterion = "entropy",
        min_samples_split = i)
    accuracyTest = calc_testing_score(X_train, y_train, X_test,
        y_test, clf)
    accuracyTest2 = calc_testing_score(X_train, y_train,
        X_test, y_test, clf2)
```

### III. Boosting 3/5

```python
from sklearn.ensemble import AdaBoostClassifier
param_range = range(10, 109, 10)
for i in range(10, 109, 10):
    clf = AdaBoostClassifier(
        base_estimator = DecisionTreeClassifier(max_depth = 1),
        n_estimators = i)
    clf2 = AdaBoostClassifier(
        base_estimator = DecisionTreeClassifier(max_depth = 2),
        n_estimators = i)
    accuracyTest = calc_testing_score(X_train, y_train, X_test,
        y_test, clf)
    accuracyTest2 = calc_testing_score(X_train, y_train, X_test,
        y_test, clf2)
```

### IV. Support Vector Machine 4/5

```python
from sklearn.svm import SVC
param_range = range(1000, 5003, 500)
for i in range(1000, 10003, 500):
    clf = SVC(kernel = "poly", max_iter = i)
    clf2 = SVC(kernel = "rbf", max_iter = i)
    accuracyTest = calc_testing_score(X_train, y_train, X_test,
        y_test, clf)
    accuracyTest2 = calc_testing_score(X_train, y_train,
        X_test, y_test, clf2)
```

### 5/5 Neural networks

```python
from sklearn.neural_network import MLPClassifier
# (a) numHiddenLayers
param_range = range(1, 8, 1)
tup = (100,)
for i in range(1, 8, 1):
    tup2 = (i, 10)
    clf = MLPClassifier(activation = 'relu', hidden_layer_sizes
        = tup2)
    accuracyTest = calc_testing_score(X_train, y_train, X_test,
        y_test, clf)

# (b) size of number of neurons in the
param_range = range(1, 36, 5)
for i in range(1, 36, 5):
    clf = MLPClassifier(hidden_layer_sizes = (i, i, i))
    accuracyTest = calc_testing_score(X_train, y_train, X_test,
        y_test, clf)
```

- 102.6 Using Stochastic Calculus to Derive Black-Scholes Model . . 3603
- 102.7 Summary and Concluding Remarks . . . . . . . . . . 3610
- Bibliography . . . . . . . . . . . . . . . . . . . . . . . 3610
- Appendix 102A The Relationship Between Binomial Distribution and Normal Distribution . . . . . . . . . . . 3613

## Abstract

The main purposes of this paper are: (i) to review three alternative methods for deriving option pricing models (OPM), (ii) to discuss the relationship between binomial OPM and Black-Scholes OPM, (iii) to compare the Cox et al. method and the Rendleman and Bartter method for deriving Black-Scholes OPM, (iv) to discuss lognormal distribution method to derive the Black-Scholes OPM, and (v) to show how the Black-Scholes model can be derived by stochastic calculus. This paper shows that the main methodologies used to derive the Black-Scholes model are: binomial distribution, lognormal distribution, and differential and integral calculus. If we assume risk neutrality, then we do not need stochastic calculus to derive the Black-Scholes model. However, the stochastic calculus approach for deriving the Black-Scholes model is still presented in Section 102.6. In sum, this paper can help statisticians and mathematicians understand how alternative methods can be used to derive the Black-Scholes option model.

**Keywords**
Black-Scholes option pricing model • Binomial option pricing model • Lognormal distribution method • Stochastic calculus.

## 102.1 Introduction

The use of stock options for risk reduction and return enhancement has expanded at a considerable rate over the last several decades. In 1973, the Chicago Board Option Exchange was established, and brought about liquidity for successful option trading through public listing and option contract standardization. In the same year, the most famous option pricing model — Black-Scholes model — was proposed and became the industry standard (Lee et al., 2013a).

Black and Scholes (1973) and Merton (1973) used stochastic calculus to derive option pricing models. Rendleman and Bartter (1979) and Cox, Ross, and Rubinstein (1979) used binomial distribution to derive the Black-Scholes model. In the next several decades, a group of new models that relax some restrictive assumptions of Black-Scholes model have been proposed.

The first group of researches developed models that allowed important parameters such as interest rate or (and) volatility, to be stochastic. Scott (1987), Wiggins (1987), Hull and White (1987a), Melino and Turnbull (1990, 1995), Stein and Stein (1991), and Heston (1993) generalized the Black-Scholes model in terms of stochastic variance. While Amin and Jarrow (1992) developed the Black-Scholes model allowing stochastic interest rate. Furthermore, there are some literatures proposed generalization method to allow interest rate and volatility to be stochastic at the same time. Examples can be found in Amin and Ng (1993), Bakshi and Chen (1997a,b), and Bailey and Stulz (1989). Similarly, Lee et al. (1991) extended the binomial option pricing model to the case where the up and down percentage changes of stock prices are stochastic. They have proved that assuming stochastic parameters in the discrete-time binomial option pricing is analogous to assuming stochastic volatility in the continuous-time option pricing.

The second group of studies introduced jump-diffusion process into the Black-Scholes model, and made extensions to the original model. Several jump-diffusion models are proposed by Bates (1991), Kou (2002), Kou and Wang (2004), respectively. Psychoyios et al. (2010) well approximated the time series behavior of VIX index by a mean reverting logarithmic diffusion process with jumps. Based on the empirical results, they derived closed-form valuation models for European options written on the spot and forward VIX, respectively. For more complicated cases, Bates (1996) introduced jump-diffusion process into the stochastic-volatility model, and Scott (1997) attempted to price options in a jump-diffusion model with stochastic volatility and interest rates.

Besides the mentioned two large categories of models, an explosion of other option pricing models have also been proposed and well validated using real world data. Examples include: (i) the constant elasticity of variance (CEV) models (Cox and Ross, 1976; Beckers, 1980; Davydov and Linetsky, 2001; Lee et al., 2004; Chen et al., 2009); (ii) the Markovian models (Rubinstein, 1994; Aït-Sahalia and Lo, 1996); (iii) the GARCH models (Duan, 1995; Heston, 2000; Wu, 2006); and (iv) the models based on Lévy processes (Geman, 2001; Carr and Wu, 2004).

In more recent years, much more complex cases are considered to develop new models. And these models were proved to describe the reality more precisely. Chen and Palmon (2005) proposed an empirically-based, non-parametric option pricing model and used it to evaluate S&P 500 index options. As their model is derived under the real measure, an equilibrium asset pricing model, rather than no-arbitrage model is assumed. Costabile et al. (2014) proposed a binomial approach for option pricing assuming the parameters governing the underlying asset process follow a regime-switching model. Lin et al. (2014) developed a currency option pricing model with regimes of high-variance or low-variance states as well as the jump nature of exchange rates. And they have proved that their model performed better than both traditional regime-switching model and the Black-Scholes model.
