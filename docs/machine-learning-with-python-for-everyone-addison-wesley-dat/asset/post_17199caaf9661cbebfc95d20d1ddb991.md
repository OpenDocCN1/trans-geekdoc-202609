
## 7.3.1 Error Plots

To get started, let’s graph an actual, true target value against a predicted value. The graphical distance between the two represents our error. So, if a particular example was really 27.5 and we predicted 31.5, we’d need to plot the point (x = 27.5, y = 31.5) on axes labeled (Reality, Predicted). One quick note: perfect predictions would be points along the line y = x because for each output, we’d be predicting exactly that value. Since we’re usually not perfect, we can calculate the error between what we predicted and the actual value. Often, we throw out the signs of our errors by squaring or taking absolute value. Here, we’ll keep the directions of our errors for now. If we predict too high, the error will be positive; if we predict too low, the error will be negative. Our second graph will simply swap the predicted-actual axes so our point above will become (x = 31.5, y = 27.5): (Predicted, Reality). It may all sound too easy—stay tuned.

```
In [13]:

 ape_df = pd.DataFrame({'predicted' : [4, 2, 9],
                       'actual'   : [3, 5, 7]})

 ape_df['error'] = ape_df['predicted'] - ape_df['actual']

 ape_df.index.name = 'example'
 display(ape_df)
```

| example | predicted | actual | error |
|---|---|---|---|
| 0 | 4 | 3 | 1 |
| 1 | 2 | 5 | -3 |
| 2 | 9 | 7 | 2 |

```
In [14]:

 def regression_errors(figsize, predicted, actual, errors='all'):
    ''' figsize -> subplots;
        predicted/actual data -> columns in a DataFrame
        errors -> "all" or sequence of indices '''
    fig, axes = plt.subplots(1, 2, figsize=figsize,
                             sharex=True, sharey=True)
    df = pd.DataFrame({'actual':actual,
                       'predicted':predicted})

    for ax, (x,y) in zip(axes, it.permutations(['actual',
                                                'predicted'])):
        # plot the data as '.'; perfect as y=x line
        ax.plot(df[x], df[y], '.', label='data')
```

```
ax.plot(df['actual'], df['actual'], '-',
    label='perfection')
ax.legend()

ax.set_xlabel('{} Value'.format(x.capitalize()))
ax.set_ylabel('{} Value'.format(y.capitalize()))
ax.set_aspect('equal')

axes[1].yaxis.tick_right()
axes[1].yaxis.set_label_position("right")

# show connecting bars from data to perfect
# for all or only those specified?
if errors == 'all':
    errors = range(len(df))
if errors:
    acts  = df.actual.iloc[errors]
    preds = df.predicted.iloc[errors]
    axes[0].vlines(acts, preds, acts, 'r')
    axes[1].hlines(acts, preds, acts, 'r')

regression_errors((6, 3), ape_df.predicted, ape_df.actual)
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_244_0.png)

![](img/d94e4cd766940d79abed0bc6ba4e4344_244_1.png)

In both cases, the orange line (y = x which in this case is predicted = actual) is conceptually an omniscient model where the predicted value is the true actual value. The error on that line is zero. On the left graph, the difference between prediction and reality is vertical. On the right graph, the difference between prediction and reality is horizontal. Flipping the axes results in flipping the datapoints over the line y = x. By the wonderful virtue of reuse, we can apply that to our diabetes dataset.

```
```python
In [15]:
lr = linear_model.LinearRegression()
preds = (lr.fit(diabetes_train_ft, diabetes_train_tgt)
         .predict(diabetes_test_ft))

regression_errors((8, 4), preds, diabetes_test_tgt, errors=[-20])
```
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_245_0.png)

The difference between these graphs is that the left-hand graph is an answer to the question “Compared to reality (*Actual Value*), how did we do?” The right-hand graph is an answer to “For a given prediction (*Predicted Value*), how do we do?” This difference is similar to that between sensitivity (and specificity) being calculated with respect to the *reality of sick*, while precision is calculated with respect to a *prediction of sick*. As an example, when the actual value ranges from 200 to 250, we seem to consistently predict low. When the predicted value is near 200, we have real values ranging from 50 to 300.

### 7.3.2 Residual Plots

Now, we are ready to introduce *residual plots*. Unfortunately, we’re about to run smack into a wall of terminological problems. We talked about the *error* of our predictions: error = predicted − actual. But for *residual plots*, we need the mirror image of these: residuals = actual − predicted. Let’s make this concrete:

```
```python
In [16]:
ape_df = pd.DataFrame({'predicted' : [4, 2, 9],
                       'actual'    : [3, 5, 7]})

ape_df['error'] = ape_df['predicted'] - ape_df['actual']
ape_df['resid'] = ape_df['actual'] - ape_df['predicted']
```
```

```
ape_df.index.name = 'example'
display(ape_df)
```

| example | predicted | actual | error | resid |
|---------|-----------|--------|-------|-------|
| 0 | 4 | 3 | 1 | -1 |
| 1 | 2 | 5 | -3 | 3 |
| 2 | 9 | 7 | 2 | -2 |

When talking about errors, we can interpret the value as how much we over- or undershot by. An error of 2 means our prediction was over by 2. We can think about it as what happened. With residuals, we are thinking about what adjustment we need to do to fix up our prediction. A residual of -2 means that we need to subtract 2 to get to the right answer.

Residual plots are made by graphing the predicted value against the residual for that prediction. So, we need a slight variation of the right graph above (predicted versus actual) but written in terms of residuals, not errors. We’re going to take the residual values—the signed distance from predicted back to actual—and graph them against their predicted value.

For example, we predict 31.5 for an example that is actually 27.5. The residual is –4.0. So, we’ll have a point at (x = predicted = 31.5, y = residual = –4.0). Incidentally, these can be thought of as what’s left over after we make a prediction. What’s left over is sometimes called a residue—think the green slime in Ghostbusters.

Alright, two graphs are coming your way: (1) actual against predicted and (2) predicted against residual.

```
def regression_residuals(ax, predicted, actual,
show_errors=None, right=False):
    ''' figsize -> subplots;
    predicted/actual data -> columns of a DataFrame
    errors -> "all" or sequence of indices '''
    df = pd.DataFrame({'actual':actual,
    'predicted':predicted})
    df['error'] = df.actual - df.predicted
    ax.plot(df.predicted, df.error, '.')
    ax.plot(df.predicted, np.zeros_like(predicted), '-')
    if right:
        ax.yaxis.tick_right()
        ax.yaxis.set_label_position("right")
```

```
ax.set_xlabel('Predicted Value')
ax.set_ylabel('Residual')

if show_errors == 'all':
    show_errors = range(len(df))
if show_errors:
    preds = df.predicted.iloc[show_errors]
    errors = df.error.iloc[show_errors]
    ax.vlines(preds, 0, errors, 'r')

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(8, 4))

ax1.plot(ape_df.predicted, ape_df.actual, 'r.', # pred vs actual
        [0, 10], [0, 10], 'b-')               # perfect line
ax1.set_xlabel('Predicted')
ax1.set_ylabel('Actual')
regression_residuals(ax2, ape_df.predicted, ape_df.actual,
                    'all', right=True)
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_247_0.png)

![](img/d94e4cd766940d79abed0bc6ba4e4344_247_1.png)

Now, we can compare two different learners based on their residual plots. I'm going to shift to using a proper train-test split, so these residuals are called predictive residuals. In a traditional stats class, the plain vanilla residuals are computed from the training set (sometimes called in sample). That's not our normal method for evaluation: we prefer to evaluate against a test set.

```
lr = linear_model.LinearRegression()
knn = neighbors.KNeighborsRegressor()

models = [lr, knn]

fig, axes = plt.subplots(1, 2, figsize=(10, 5),
                        sharex=True, sharey=True)
fig.tight_layout()

for model, ax, on_right in zip(models, axes, [False, True]):
    preds = (model.fit(diabetes_train_ftrs, diabetes_train_tgt)
             .predict(diabetes_test_ftrs))

    regression_residuals(ax, preds, diabetes_test_tgt, [-20], on_right)

axes[0].set_title('Linear Regression Residuals')
axes[1].set_title('k-NN-Regressor Residuals');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_248_0.png)

A few comments are in order. Since the two models predict different values for our point of interest, it shows up at different spots on the horizontal x axis. With the linear regression model, the value is predicted a hint under 250. With the k-NN-R model, the value is predicted to be a bit above 250. In both cases, it is underpredicted (remember, residuals tell us how to fix up the prediction: we need to add a bit to these predictions). The actual value is:

```
print(diabetes_test_tgt[-20])
```

280.0
