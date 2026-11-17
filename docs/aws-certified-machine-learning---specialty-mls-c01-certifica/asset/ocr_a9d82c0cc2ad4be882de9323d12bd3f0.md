# Exploring other regression metrics

There are many more metrics that are suitable for regression problems, in addition to the ones that you have just learned. You will not learn about most of them here, but you will be introduced to a few more metrics that might be important for you to know.

One of these metrics is known as the Mean Absolute Percentage Error (MAPE). As the name suggests, the MAPE will compute the absolute percentage error of each prediction and then take the average value. Figure 7.11 depicts formula that shows how this metric is computed:

![](bbox=[0.23, 0.29, 0.76, 0.415])

Figure 7.11 – Formula for MAPE

The MAPE is broadly used in forecasting models since it is very simple to interpret, and it provides a very good sense of how far (or close) the predictions are from the actual values (in terms of a percentage).

You have now completed this section on regression metrics. Next, you will learn about model optimization.

# Model optimization

As you know, understanding evaluation metrics is very important in order to measure your model’s performance and document your work. In the same way, when you want to optimize your current models, evaluating metrics also plays a very important role in defining the baseline performance that you want to challenge.

The process of model optimization consists of finding the best configuration (also known as hyperparameters) of the machine learning algorithm for a particular data distribution. You do not want to find hyperparameters that overfit the training data, in the same way that you do not want to find hyperparameters that underfit the training data.

You learned about overfitting and underfitting in Chapter 1, Machine Learning Fundamentals. In the same chapter, you also learned how to avoid these two types of modeling issues.