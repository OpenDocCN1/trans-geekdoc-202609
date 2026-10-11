
## Figure 2.17. A Pareto diagram is a combination of the values and a cumulative distribution

It’s easy to see from this diagram that the first 50% of the countries contain slightly less than 80% of the total amount. If this graph represented customer buying power and we sell expensive products, we probably don’t need to spend our marketing budget in every country; we could start with the first 50%.

![](image_rsrc9PM.jpg)

**Fig. 2.17. A Pareto diagram**

[Figure 2.18](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig18) shows another technique: brushing and linking. With brushing and linking you combine and link different graphs and tables (or views) so changes in one graph are automatically transferred to the other graphs. This interactive exploration of data facilitates the discovery of new insights.

## Figure 2.18. Link and brush allows you to select observations in one plot and highlight the same observations in the other plots

![](image_rsrc9PN.jpg)

**Fig. 2.18. Link and brush**

[Figure 2.18](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig18) shows the average score per country for questions. Not only does this indicate a high correlation between the answers, but it’s easy to see that when you select several points on a subplot, the points will correspond to similar points on the other graphs. In this case the selected points on the left graph correspond to points on the middle and right graphs, although they correspond better in the middle and right graphs.

Two other important graphs are the histogram shown in [figure 2.19](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig19) and the boxplot shown in [figure 2.20](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig20).

## Figure 2.19. Example histogram: the number of people in the age-groups of 5-year intervals

![](image_rsrc9PP.jpg)

**Fig. 2.19. histogram**

## Figure 2.20. Example boxplot: each user category has a distribution of the appreciation each has for a certain picture on a photography website

![](image_rsrc9PR.jpg)

**Fig. 2.20. boxplot**

In a histogram a variable is cut into discrete categories and the number of occurrences in each category are summed up and shown in the graph. The boxplot, on the other hand, doesn’t show how many observations are present but does offer an impression of the distribution within categories. It can show the maximum, minimum, median, and other characterizing measures at the same time.

The techniques we described in this phase are mainly visual, but in practice they’re certainly not limited to visualization techniques. Tabulation, clustering, and other modeling techniques can also be a part of exploratory analysis. Even building simple models can be a part of this step.

Now that you’ve finished the data exploration phase and you’ve gained a good grasp of your data, it’s time to move on to the next phase: building models.

## 2.6. Step 5: Build the models

With clean data in place and a good understanding of the content, you’re ready to build models with the goal of making better predictions, classifying objects, or gaining an understanding of the system that you’re modeling. This phase is much more focused than the exploratory analysis step, because you know what you’re looking for and what you want the outcome to be. [Figure 2.2.1](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig21) shows the components of model building.

![](image_rsrc9PS.jpg)

**Fig. 2.21. Step 5: Data modeling**

The techniques you’ll use now are borrowed from the field of machine learning, data mining, and/or statistics. In this chapter we only explore the tip of the iceberg of existing techniques. It’s beyond the scope of this book to give you more than a conceptual introduction, but it’s enough to get you started; 20% of the techniques will help you in 80% of the cases because techniques overlap in what they try to accomplish. They often achieve their goals in similar but slightly different ways.

Building a model is an iterative process. The way you build your model depends on whether you go with classic statistics or the somewhat more recent machine learning school, and the type of technique you want to use. Either way, most models consist of the following main steps:

1. Selection of a modeling technique and variables to enter in the model
2. Execution of the model
3. Diagnosis and model comparison

### 2.6.1. Model and variable selection

You’ll need to select the variables you want to include in your model and a modeling technique. Your findings from the exploratory analysis should already give a fair idea of what variables will help you construct a good model. Many modeling techniques are available, and choosing the right model for a problem requires judgment on your part. You’ll need to consider model performance and whether your project meets all the requirements to use your model, as well as other factors:

* Must the model be moved to a production environment and, if so, would it be easy to implement?
* How difficult is the maintenance on the model: how long will it remain relevant if left untouched?
* Does the model need to be easy to explain?

When the thinking is done, it’s time for action.

### 2.6.2. Model execution

Once you’ve chosen a model you’ll need to implement it in code.

Luckily, most programming languages, such as `Python`, already have libraries such as `Stats Models` or `Scikit-learn`. These packages use several of the most popular techniques. Coding a model is a nontrivial task in most cases, so having these libraries available can speed up the process. As you can see in the following code, it’s fairly easy to use linear regression ([figure 2.22](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig22)) with `Stats Models` or `Scikit-learn`. Doing this yourself would require much more effort even for the simple techniques. The following listing shows the execution of a linear prediction model.

## Figure 2.22. Linear regression tries to fit a line while minimizing the distance to each point

![](image_rsrc9PT.jpg)

**Fig. 2.22. Linear regression**

## Listing 2.1. Executing a linear prediction model on semi-random data

![](image_rsrc9PU.jpg)

For a linear regression, a “linear relation” between each `x` (predictor) and the `y` (target) variable is assumed, as shown in [figure 2.22](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig22).

We, however, created the target variable, based on the predictor by adding a bit of randomness. It shouldn’t come as a surprise that this gives us a well-fitting model. The `results.summary()` outputs the table in [figure 2.23](https://livebook.manning.com/book/introducing-data-science/chapter-2/ch02fig23). Mind you, the exact outcome depends on the random variables you got.

![](image_rsrc9PV.jpg)

**Fig.2.23. Linear regression model information output**

Let’s ignore most of the output we got here and focus on the most important parts:

* **Model fit** —For this the R-squared or adjusted R-squared is used. This measure is an indication of the amount of variation in the data that gets captured by the model. The difference between the adjusted R-squared and the R-squared is minimal here because the adjusted one is the normal one + a penalty for model complexity. A model gets complex when many variables (or features) are introduced. You don’t need a complex model if a simple model is available, so the adjusted R-squared punishes you for overcomplicating. At any rate, `0.893` is high, and it should be because we cheated. Rules of thumb exist, but for models in businesses, models above `0.85` are often considered good. If you want to win a competition you need in the high 90s. For research however, often very low model fits (`<0.2` even) are found. What’s more important there is the influence of the introduced predictor variables.
