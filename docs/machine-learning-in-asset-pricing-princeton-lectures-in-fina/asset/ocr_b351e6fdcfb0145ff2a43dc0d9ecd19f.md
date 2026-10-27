# TABLE 1.1
Terminology in ML and Statistics

| ML | Statistics |
|---|---|
| Training, Learning | Estimation |
| Learner, Algorithm | Model, Estimator |
| Features | Covariates, Explanatory Variables, Independent Variables, Predictors |
| Target, Label, Output | Dependent Variable |
| Example, Instance | Data Point, Observation |

work, investors can be modeled as machine learners in a realistic high-dimensional environment.

A recurrent theme throughout this book is that even though ML methods have been impressively successful in a wide variety of applications, using these tools off the shelf in asset pricing is not necessarily going to work well. The properties of data in asset pricing applications are often substantially different from those in technology, medicine, and other scientific fields. Successful application of ML methods in asset pricing therefore will often require some adaptation. To develop appropriate adaptations, we need to bring in some prior economic knowledge about the environment that generates the data. The idea, sometimes associated with ML, that one could make predictions in an entirely data-driven automated fashion is too good to be true. Much of this book is devoted to the question of how we can use economic reasoning to make ML tools effective in asset pricing.

Bayesian statistics offers a framework to incorporate prior knowledge into statistical estimation. The Bayesian framework therefore allows us to build a bridge between economic theories of asset pricing and ML. At various points throughout the book I draw on Bayesian statistics to give an interpretation of ML methods and to suggest economically motivated adaptations of these methods.

# 1.4 TERMINOLOGY

Coming from computer science, the machine learning literature has developed its own terminology. The concepts and methods often overlap with similar ones in the statistics literature, but they are named differently. This can be confusing. Table 1.1 lists some common terms that will appear