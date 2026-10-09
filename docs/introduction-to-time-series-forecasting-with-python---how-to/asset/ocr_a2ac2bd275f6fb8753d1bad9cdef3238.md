methods model the relationship between the inputs (x) and the outputs (y) that we would like to predict. In this tutorial, we will look at three classes of features that we can create from our time series dataset:

+   - **Date Time Features:** these are components of the time step itself for each observation.

+   - **Lag Features:** these are values at prior time steps.

+   - **Window Features:** these are a summary of values over a fixed window of prior time steps.

Before we dive into methods for creating input features from our time series data, let’s first review the goal of feature engineering.

# ## 5.2  Goal of Feature Engineering

The goal of feature engineering is to provide strong and ideally simple relationships between new input features and the output feature for the supervised learning algorithm to model. In effect, we are moving complexity.

Complexity exists in the relationships between the input and output data. In the case of time series, there is no concept of input and output variables; we must invent these too and frame the supervised learning problem from scratch. We may lean on the capability of sophisticated models to decipher the complexity of the problem. We can make the job for these models easier (and even use simpler models) if we can better expose the inherent relationship between inputs and outputs in the data.

The difficulty is that we do not know the underlying inherent functional relationship between inputs and outputs that we’re trying to expose. If we did know, we probably would not need machine learning. Instead, the only feedback we have is the performance of models developed on the supervised learning datasets or views of the problem we create. In effect, the best default strategy is to use all the knowledge available to create many good datasets from our time series dataset and use model performance (and other project requirements) to help determine what good features and good views of your problem happen to be.

For clarity, we will focus on a univariate (one variable) time series dataset in the examples, but these methods are just as applicable to multivariate time series problems. Next, let’s take a look at the dataset we will use in this tutorial.

# ## 5.3  Minimum Daily Temperatures Dataset

In this lesson, we will use the Minimum Daily Temperatures dataset as an example. This dataset describes the minimum daily temperatures over 10 years (1981-1990) in the city Melbourne, Australia. You can learn more about the dataset in Appendix A.2. Place the dataset in your current working directory with the filename daily-minimum-temperatures.csv.