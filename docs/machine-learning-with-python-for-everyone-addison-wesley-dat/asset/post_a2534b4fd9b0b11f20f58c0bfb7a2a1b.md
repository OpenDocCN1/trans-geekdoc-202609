
## Chapter 4 Predicting Numerical Values: Getting Started with Regression

as the weights. We use $\frac{1}{\text{distances}}$ since if you are closer, we want a higher weight; if you are further, but still a nearest neighbor, we want a lower weight. We put the entire sum into the denominator to normalize the values so they sum to one. Compare the mean with the weighted mean for these values:

```
In [7]:

values = np.array([4, 6, 8])
mean = np.mean(values)
wgt_mean = np.dot(values, weights)
print("Mean:", mean)
print("Weighted Mean:", wgt_mean)
```

```
Mean: 6.0
Weighted Mean: 6.4
```

Graphically—see Figure 4.2—our balance diagram now looks a bit different. The examples that are underweighted (contribute less than their fair share) move closer to the pivot because they have less mechanical leverage. Overweighted examples move away from the pivot and gain more influence.

![](img/d94e4cd766940d79abed0bc6ba4e4344_118_0.png)

#### 4.2.2 Building a k-NN Regression Model

Now that we have some mental concepts to back up our understanding of k-NN regression, we can return to our basic sklearn workflow: build, fit, predict, evaluate.

```
In [8]:

knn = neighbors.KNeighborsRegressor(n_neighbors=3)
fit = knn.fit(diabetes_train_ftrs, diabetes_train_tgt)
preds = fit.predict(diabetes_test_ftrs)
# evaluate our predictions against the held-back testing targets
metrics.mean_squared_error(diabetes_test_tgt, preds)
```

```
Out[8]:
3471.41941941942
```

If you flip back to the previous chapter and our k-NN classifier, you'll notice only two differences.

- We built a different model: this time we used `KNeighborsRegressor` instead of `KNeighborsClassifier`.
- We used a different evaluation metric: this time we used `mean_squared_error` instead of `accuracy_score`.

Both of these reflect the difference in the targets we are trying to predict—numerical values, not Boolean categories. I haven't explained mean_squared_error (MSE) yet; it's because it is deeply tied to our next learning method, linear regression, and once we understand linear regression, we'll basically understand MSE for free. So, just press pause on evaluating regressors with MSE for a few minutes. Still, if you need something to make you feel comfortable, take a quick look at Section 4.5.1.

To put the numerical value for MSE into context, let's look at two things. First, the MSE is approximately 3500. Let's take its square root—since we're adding up squares, we need to scale back to nonsquares:

```
In [9]:

np.sqrt(3500)
```

```
Out[9]:
59.16079783099616
```

Now, let's look at the range of values that the target can take:

```
In [10]:

diabetes_df['target'].max() - diabetes_df['target'].min()
```

```
Out[10]:
321.0
```

So, the target values span about 300 units and our predictions are off—in some average sense—by 60 units. That's around 20%. Whether or not that is “good enough” depends on many other factors which we'll see in Chapter 7.

### 4.3 Linear Regression and Errors

We're going to dive into linear regression (LR)—which is just a fancy name for drawing a straight line through a set of data points. I'm really sorry to bring up LR, particularly if you are one of those folks out there who had a bad experience studying LR previously. LR has a long history throughout math and science. You may have been exposed to it before. You may have seen LR in an algebra or statistics class. Here's a very different presentation.

#### 4.3.1 No Flat Earth: Why We Need Slope

Do you like to draw? (If not, please just play along.) Take a pen and draw a bunch of dots on a piece of paper. Now, draw a single straight line through the dots. You might have encountered a problem already. If there were more than two dots, there are many, many different lines you could potentially draw. The idea of drawing a line through the dots gets a general idea across, but it doesn’t give us a reproducible way of specifying or completing the task.

One way of picking a specific line through the dots is to say we want a best line—problem solved. We’re done. Let’s go for five o’clock happy hour. Oh, wait, I have to define what best means. Rats! Alright, let’s try this. I want the line that stays closest to the dots based on the vertical distance from the dots to the line. Now we’re getting somewhere. We have something we can calculate to compare different alternatives.

Which line is best under that criteria? Let me start by simplifying a little bit. Imagine we can only draw lines that are parallel to the bottom of the piece of paper. You can think about moving the line like raising or lowering an Olympic high-jump bar: it stays parallel to the ground. If I start sliding the line up and down, I’m going to start far away from all the points, move close to some points, slide onwards to a great, just-right middle ground, move close to other points, and finally end up far away from everything. Yes, the idea of a happy medium—too hot, too cold, and just right—applies here. We’ll see this example in code and graphics in just a moment. At the risk of becoming too abstract too quickly, we are limited to drawing lines like $y = c$. In English, that means the height of our bar is always equal to some constant, fixed value.

Let’s draw a few of these high-jump bars and see what happens.

```
def axis_helper(ax, lims):
    'clean up axes'
    ax.set_xlim(lims); ax.set_xticks([])
    ax.set_ylim(lims); ax.set_yticks([])
    ax.set_aspect('equal')
```

We’re going to use some trivial data to show what’s happening.

```
# our data is very simple:  two (x, y) points
D = np.array([[3, 5],
              [4, 2]])

# we'll take x as our "input" and y as our "output"
x, y = D[:, 0], D[:, 1]
```

Now, let’s graph what happens as we move a horizontal line up through different possible values. We’ll call these values our predicted values. You can imagine each raised bar as being a possible set of predictions for our example data points. Along the way, we’ll also keep track of what our error values are. The errors are the differences between the horizontal line and the data points. We'll also calculate a few values from the errors: the sum of errors, the sum of squares of the errors (abbreviated SSE), and the square root of the sum of squared errors. You might want to look at the output first, before trying to understand the code.

```
In [13]:

horizontal_lines = np.array([1, 2, 3, 3.5, 4, 5])

results = []
fig, axes = plt.subplots(1, 6, figsize=(10, 5))
for h_line, ax in zip(horizontal_lines, axes.flat):
    # styling
    axis_helper(ax, (0, 6))
    ax.set_title(str(h_line))

    # plot the data
    ax.plot(x, y, 'ro')

    # plot the prediction line
    ax.axhline(h_line, color='y') # ax coords; defaults to 100%

    # plot the errors
    # the horizontal line *is* our prediction; renaming for clarity
    predictions = h_line
    ax.vlines(x, predictions, y)

    # calculate the error amounts and their sum of squares
    errors = y - predictions
    sse = np.dot(errors, errors)

    # put together some results in a tuple
    results.append((predictions,
                    errors, errors.sum(),
                    sse, np.sqrt(sse)))
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_121_0.png)

We start very far away from one point and not too far from another. As we slide the bar up, we hit a nice middle ground between the points. Yet we keep sliding the bar; we end up on the top point, fairly far away from the bottom point. Perhaps the ideal tradeoff is somewhere in the middle. Let's look at some numbers.

```
In [14]:

col_labels = "Prediction", "Errors", "Sum", "SSE", "Distance"
display(pd.DataFrame.from_records(results,
    columns=col_labels,
    index="Prediction"))
```

| Prediction | Errors | Sum | SSE | Distance |
|---|---|---|---|---|
| **1.0000** | [4.0, 1.0] | 5.0000 | 17.0000 | 4.1231 |
| **2.0000** | [3.0, 0.0] | 3.0000 | 9.0000 | 3.0000 |
| **3.0000** | [2.0, -1.0] | 1.0000 | 5.0000 | 2.2361 |
| **3.5000** | [1.5, -1.5] | 0.0000 | 4.5000 | 2.1213 |
| **4.0000** | [1.0, -2.0] | -1.0000 | 5.0000 | 2.2361 |
| **5.0000** | [0.0, -3.0] | -3.0000 | 9.0000 | 3.0000 |

Our table includes the raw errors that can be positive or negative—we might over- or underestimate. The sums of those raw errors don't do a great job evaluating the lines. Errors in the opposite directions, such as [2, −1], give us a total of 1. In terms of our overall prediction ability, we don't want these errors to cancel out. One of the best ways to address that is to use a total distance, just like we used distances in the nearest-neighbors method above. That means we want something like $\sqrt{\sum(\text{prediction} - \text{actual})^2}$. The SSE column is the sum of squared errors which gets us most of the way towards calculating distances. All that's left is to take a square root. The line that is best, under the rules so far, is the horizontal line at the mean of the points based on their vertical component: $(5 + 2) / 2 = 3.5$. The mean is the best answer here for the same reason it is the pivot on the balance beams we showed earlier: it perfectly balances out the errors on either side.

#### 4.3.2 Tilting the Field

What happens if we keep the restriction of drawing straight lines but remove the restriction of making them horizontal? My apologies for stating the possibly obvious, but now we can draw lines that aren't flat. We can draw lines that are pointed up or down, as needed. So, if the cluster of dots that you drew had an overall growth or descent, like a plane taking off or landing, a sloped line can do better than a flat, horizontal runway. The form of these sloped lines is a classic equation from algebra: $y = mx + b$. We get to adjust m and b so that when we know a point's left-rightedness—the x value—we can get as close as possible on its up-downness y.

How do we define close? The same way we did above—with distance. Here, however, we have a more interesting line with a slope. What does the distance from a point to our
