
## 15.6.2 A PGM View of Linear Regression

Let’s apply the idea of PGMs to linear regression.

### 15.6.2.1 The Long Way

Here’s how this works for our good old-fashioned (GOF) linear regression. We start by drawing a model (Figure 15.6) of how the features and weights interact. This drawing looks an awful lot like the model we drew for the neural network form of linear regression, with the addition of placeholder distributions for the learned weights.

![](img/d94e4cd766940d79abed0bc6ba4e4344_547_0.png)

Figure 15.6 A probabilistic graphical model for linear regression.

Our major tool for exploring PGMs is going to be pymc3. The mc stands for Monte Carlo, a famous casino. When you see that name, you can simply mentally substitute randomness.

```
In [29]:
import pymc3 as pm

# getting really hard to convince toolkits to be less verbose
```

```
import logging
pymc3_log = logging.getLogger('pymc3')
pymc3_log.setLevel(2**20)
```

For most of the book, we’ve swept this detail under the carpet—but when we predict a value with a linear regression, we have really been predicting a single output target value that is a mean of the possible outcomes at that spot. In reality, if our data isn’t perfect, we have some wiggle room above and below that value. This possible wiggle room—which GOF linear regression treats as the same for each prediction—is a normal distribution. Yes, it really does show up everywhere. This normal distribution is centered at the predicted value with a standard deviation around that center, so it shows up as a band above and below our linear regression line. Our predictions still fall on the linear regression line. The new component is simply something like a tolerance band around the line. When we look at linear regression as PGM, we make this hidden detail explicit by specifying a standard deviation.

Let’s turn our diagram from Figure 15.6 into code:

In [30]:

```
with pm.Model() as model:
    # boilerplate-ish setup of the distributions of our
    # guesses for things we don't know
    sd          = pm.HalfNormal('sd', sd=1)
    intercept   = pm.Normal('Intercept', 0, sd=20)
    ftr_1_wgt   = pm.Normal('ftr_1_wgt', 0, sd=20)

    # outcomes made from initial guess and input data
    # this is y = m x + b in an alternate form
    preds = ftr_1_wgt * linreg_table['ftr_1'] + intercept

    # relationship between guesses, input data, and actual outputs
    # target = preds + noise(sd)  (noise == tolerance around the line)
    target = pm.Normal('tgt',
                       mu=preds, sd=sd,
                       observed=linreg_table['tgt'])

    linreg_trace = pm.sample(1000, verbose=-1, progressbar=False)
```

After all that, not seeing any output is a bit disappointing. Never fear.

In [31]:

```
pm.summary(linreg_trace)[['mean']]
```

|  | mean |
|---|---|
| **Intercept** | 2.0000 |
| **ftr_1_wgt** | 3.0000 |
| **sd** | 0.0000 |

Now *that* is comforting. While we took a quite different path to get here, we see that our weight estimates are 3 and 2—precisely the values we used to generate the data in `linreg_table`. It's also comforting that our estimate as to the noisiness of our data, `sd`, is zero. We generated the data in `linreg_table` without any noise. We are as perfect as we can be.

### 15.6.2.2 The Short Way

There are a lot of details laid out in that code example. Fortunately, we don't have to specify each of those details every time. Instead, we can write a simple formula that tells `pymc3` that the target depends on `ftr_1` and a constant for the +1 trick. Then, `pymc3` will do all the hard work of filling in the pieces we wrote out above. The `family=` argument serves the same role as our `target=` assignment did in our long-hand version. Both tell us that we are building a normal distribution centered around our predictions with some tolerance band.

```
In [32]:

with pm.Model() as model:
    pm.glm.GLM.from_formula('tgt ~ ftr_1', linreg_table,
                            family=pm.glm.families.Normal())
    linreg_trace = pm.sample(5000, verbose=-1, progressbar=False)
pm.summary(linreg_trace)[['mean']]
```

|  | mean |
|---|---|
| **Intercept** | 2.0000 |
| **ftr_1** | 3.0000 |
| **sd** | 0.0000 |

The names here are the names of the features. I'd be happier if it was clear that they are the values of the *weights* on those features. Still, consider my point made. It's reassuring that we get the same answers for the weights. Now, I brought up a benefit of PGMs: we can see a *range* of possible answers instead of just a single answer. What does that look like?

In [33]:

```
%%capture

# workaround for a problem: writing to a tmp file.
%matplotlib qt

fig, axes = plt.subplots(3,2,figsize=(12,6))
axes = pm.traceplot(linreg_trace, ax=axes)
for ax in axes[:,-1]:
    ax.set_visible(False)

plt.gcf().savefig('outputs/work-around.png')
```

In [34]:

```
Image('outputs/work-around.png', width=800, height=2400)
```

Out[34]:

![](img/d94e4cd766940d79abed0bc6ba4e4344_550_0.png)

We can spin up almost the exact same model as linear regression except with a slightly different family: now we need to use Binomial as our target. Whenever you see binomial, you can immediately use a mental model of coin flipping. Since our logistic regression example has two classes, we can think of them as heads and tails. Then, we are simply trying to find the chances of flipping a head. Making that substitution—of the binomial distribution for the normal distribution—gives us the following code:

```
In [35]:

with pm.Model() as model:
    pm.glm.GLM.from_formula('tgt ~ ftr_1', logreg_table,
                            family=pm.glm.families.Binomial())
    logreg_trace = pm.sample(10000, verbose=-1, progressbar=False)
pm.summary(logreg_trace)['mean']
```

Out[35]:

|  | mean |
|---|---|
| Intercept | 22.6166 |
| ftr_1 | -2.2497 |

Our results here are not exact: the true, original values were 20 and −2. But remember, our logreg_table was a bit more realistic than our linear regression data. It included noise in the middle where examples were not perfectly sorted into heads and tails—our original zeros and ones.

For linear regression, we looked at the univariate—stand-alone—distributions of the weights. We can also look at the bivariate—working together—distributions of the weights. For the logistic regression example, let’s see where the most likely pairs of values are for the two weights.

```
In [36]:

%matplotlib inline

df_trace = pm.trace_to_dataframe(logreg_trace)
sns.jointplot('ftr_1', 'Intercept', data=df_trace,
              kind='kde', stat_func=None, height=4);
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_553_0.png)

The darker area represents the most likely combinations of weights. We see that the two are not independent of each other. If the weight on ftr_1 goes up a bit—that is, becomes a little less negative—the weight on the intercept has to go down a bit.

You can think of this like planning for a long drive. If you have a target arrival time, you can leave at a certain time and drive at a certain speed. If you leave earlier, you can afford to drive a bit more slowly. If you leave later—holiday craziness, I'm looking at you—you have to drive more quickly to arrive at the same time. For our logistic regression model, arriving at the same time—the dark parts of the graph—means that the data we see is likely to have come from some tradeoff between the start time and the driving speed.

## 15.7 EOC

### 15.7.1 Summary

We’ve covered three main topics here: (1) how several different learning algorithms can be solved using generic optimization, (2) how linear and logistic regression can be expressed using neural networks, and (3) how linear and logistic regression can be expressed using probabilistic graphical models. A key point is that these two models are very close cousins.

A second point is that *all* learning methods are fundamentally doing similar things. Here’s one last point to consider: neural networks and PGMs can express very *complicated* models—but they are built from very *simple* components.

### 15.7.2 Notes

If you are interested in learning more about optimization, take a glance at zero-finding and derivatives in a calculus class or dig up some Youtube videos. You can get entire degrees in finding-the-best. There are people studying optimization in mathematics, business, and engineering programs.

## Logistic Regression and Loss

With $z = \beta x$, probability in a logistic regression model is $p_{y=1} = \frac{1}{1+e^{-z}}$. That also gives us $p = \text{logistic}(z) = \text{logistic}(\beta x)$. Minimizing the cross-entropy loss gives us these expressions:

- For 0/1: $-y z + \log(1 + e^{z})$
- For $\pm1$: $\log(1 + e^{-y z})$

When we go beyond a binary classification problem in NN, we use a one-hot encoding for the target and solve several single-class problems in parallel. Then, instead of using the logistic function, we use a function called *softmax*. Then, we take the class that results in the highest probability among the possible targets.

## Neural Networks

It’s really hard to summarize the history of neural networks in four sentences. It started in the mid-1940s and had a series of boom-bust cycles around 1960 and then in the 1980s. Between the mid-1990s and early 2010s, the main theoretical and practical hardware problems got workable solutions. For a *slightly* longer review, see “Learning Machine Learning” by Lewis and Denning in the December 2018 issue of the *Communications of the ACM.*

I mentioned briefly that we can extend neural networks to work with more than binary target classification problems. Here’s a super quick example of those techniques applied to a binary problem. You can adjust the number of classes to work with larger problems simply by increasing n_classes.

In [37]:

```python
from keras.utils import to_categorical as k_to_categorical
def Keras_MultiLogisticRegression(n_ftrs, n_classes):
    model = km.Sequential()
    model.add(kl.Dense(n_classes,
                    activation='softmax',
                    input_dim=n_ftrs))
    model.compile(optimizer=ko.SGD(), loss='categorical_crossentropy')
    return model

logreg_nn2 = Keras_MultiLogisticRegression(1, 2)
```
