
# Nonrepresentative Training Data

In order to generalize well, it is crucial that your training data be representative of the new cases you want to generalize to. This is true whether you use instance-based learning or model-based learning.

For example, the set of countries we used earlier for training the linear model was not perfectly representative; a few countries were missing. Figure 1-21 shows that the data looks like when you add the missing countries.

![](img/0684d2da98e09085c0a622d4fd69aaad_51_0.png)

Figure 1-21. A more representative training sample

If you train a linear model on this data, you get the solid line, while the old model is represented by the dotted line. As you can see, not only does adding a few missing countries significantly alter the model, but it makes it clear that a simple linear model is probably never going to work well. It seems that very rich countries are not happier than moderately countries (in fact they seem unhappy), and conversely some poor countries seem happier than many rich countries.

By using a nonrepresentative training set, we trained a model that is unlikely to make accurate predictions, especially for very poor and very rich countries.

It is crucial to use a training set that is representative of the cases you want to generalize. This is often harder than it sounds: if the sample is too small, you will have sampling noise (i.e., nonrepresentative data as a result of change), but even very large samples can be nonrepresentative if the sampling method is flawed. This is called sampling bias.

# A famous Example of Sampling Bias

Perhaps the most famous example of sampling bias happened during the US presidential election in 1936, which pitted Landon against Roosevelt: the Literary Digest conducted a very large poll, sending mail to about 10 million people. It got 2.4 million answers, and predicted with high confidence that Landon would get 57 of the votes.

Instead, Roosevelt won with 62% of the votes. The flaw was in the Literary Digest’s sampling method:

- First, to obtain the addresses to send the polls to, the Literary Digest used directories, lists of magazine subscribers, club membership lists, and the like. All of these lists tend to favor wealthier people, who are more likely to vote Republican (hence Landon).
- Second, less than 25% of the people who received the poll answered. Again, this introduces a bias, by ruling out people who don't care about politics, people who don't use the Literary Digest, and other groups. This is a special type of sampling biased by nonresponse bias.

Here is another example: say you want to build a system to recognize funk music videos. One way to build your training set is to search “funk music” on YouTube and use the resulting videos. But this assumes YouTube’s search engine returns a set of videos that are representative of all the funk music videos on YouTube. In reality, the search results are likely to be biased towards popular artists (and if you live in Brazil you get a lot of “funk carioca” videos, which sound nothing like James Brown). On the other hand, how else can you get a large training set?

# Poor-Quality Data

Obviously, if your training data is full of errors, outliers, and noise (e.g., due to quality measurements), it will make it harder for the system to detect the underlying patterns, or your system is less likely to perform well. It is often worth the effort to spend time cleaning your training data. The truth is, data scientists spend a significant part of their time doing just that. For example:

- If instances are clearly outliers, it may help to simply discard them or try to fix the errors manually.
- If instances are missing a features (e.g., 5% of your customers did not specify their age), you must decide whether you want to ignore this attribute, ignore these instances, fill in the missing values (e.g., with the median age), or train one model with the feature and one model without it, and so on.

# Irrelevant Features

As the saying goes: garbage in, garbage out. Your system will only be capable of learning if your training data contains relevant features and not too many irrelevant ones. A critical part of the success of a Machine Learning project is coming up with a good set of features to train on. This process, called feature engineering, involves:

- Feature selection: selecting the most useful features to train among existing features.
- Feature extraction: combining existing features to produce a more useful one (as we saw earlier, dimensionality reduction algorithms can help).
- Creating new features by gathering new data.

Now that we have looked at many examples of bad data, let's look at a couple of examples of bad algorithms.

# Overfitting the Training Data

Say you are visiting a foreign country and the taxi driver rips you off. You might be tempted to say that all taxi drivers in that country are thieves. Overgeneralizing something that we do too often, and unfortunately machines can fall into the same trap if we are not careful. In Machine Learning this is called overfitting it means that the model performs well on the training data, but it does not generalize well.

Figure 1-22 shows an example of a high-degree polynomial life satisfaction model that strongly overfits the training data. Even though it performs much better on the training data than the simple linear model, would you really trust its predictions?

![](img/0684d2da98e09085c0a622d4fd69aaad_53_0.png)

Figure 1-22. Overfitting the training data

Complex models like deep neural networks can detect subtle patterns in the data, but if the training data is noisy, or if it is too small (which introduces sampling noise), then the model is likely to detect patterns in the noise itself. Obviously these patterns will not generalize to new instances. For example, if you feed your life satisfaction model many more attributes, including uninformative ones such as the country's name. In that case, a complex model may detect patterns the fact that all countries in the training data with a w in their name have a life satisfaction greater than 7: New Zealand (7.3), Norway (7.4), Sweden (7.2), and Switzerland (7.5). How confident are you the W-satisfaction rule generalizes to Rwanda or Zimbabwe? Obviously this pattern occurred in the training data by pure chance, but the model has no way to tell whether a pattern is real or simply the result of noise in the data.

Overfitting happens when the model is too complex relative to the amount and noisiness of the training data. The possible solutions are:

![](img/0684d2da98e09085c0a622d4fd69aaad_54_0.png)

- To simplify the model by selecting one with fewer parameters (e.g., a linear model rather than a high-degree model), by reducing the number of attributes in the training data or by constraining the model
- To gather more training data
- To reduce the noise in the training data (e.g., fix data errors and remove outliers)

Constraining a model to make it simpler and reduce the risk of overfitting is called regularization. For example, the linear model we defined has two parameters, $\theta_0$ and $\theta_1$. This learning algorithm two degrees of freedom to adapt the model to the training data: it can tweak both the height $(\theta_0)$ and the slope $(\theta_1)$ of the line. If we forced $\theta_0 = 0$, the algorithm would only have one degree of freedom and would have a much harder time fitting the data properly: all it could do is make the line up or to down as close as possible to the training instances, so it would end around the mean. A very simple model ideal. If we allow the algorithm to modify where between one and two degrees of freedom. It will produce a simpler model than two degrees of freedom, but more complex than just one. You want to find the right balance between fitting the training data perfectly and keeping the model simple enough to ensure that it will generalize.

Figure 1-23 shows three models: the dotted line represents the original model that was trained with a few countries, the dashed line is our second model trained with all countries, and the solid line is a linear model trained with the same data as the first model but with a regularization constraint. You can see that regularization forced the model to have a smaller slope, which fits a bit less the training data that the model was trained on, but actually it to generalize better to new examples.
