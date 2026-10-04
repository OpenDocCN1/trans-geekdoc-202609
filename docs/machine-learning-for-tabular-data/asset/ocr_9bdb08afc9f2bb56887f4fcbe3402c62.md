# Exercising the deep learning model 353

| Bathrooms | input: | Car_Parks | input: | |
| --- | --- | --- | --- | --- |
| InputLayer | output: | (None,1) | InputLayer | output: | (None,1) |

| normalization_1 | input: | (None,1) | normalization_2 | input: | (None,1) |
| Normalization | output: | (None,1) | Normalization | output: | (None,1) |

| Rooms | input: | (None,1) | Size | input: | (None,1) |
| InputLayer | output: | (None,1) | InputLayer | output: | (None,1) |

| normalization_3 | input: | (None,1) | normalization_4 | input: | (None,1) |
| Normalization | output: | (None,1) | Normalization | output: | (None,1) |

![](bbox=[0.118, 0.357, 0.503, 0.375])

The normalization layers adjust the values in the continuous columns into a distribution centered around 0 with a standard deviation of 1 (https://mng.bz/0QKP).
In this section, we have reviewed the code for training the Lumpur real estate price prediction model, along with a set of best practices demonstrated in the model: regularization avoid overfitting, and normalization to bring the values of continuous columns into consistent ranges. In the next section, we will put all our work together by exercising the deep learning model with brand-new data points.

# 9.5 Exercising the deep learning model

So far in this chapter, we have prepared the Lumpur real estate dataset, using a deep learning model with Keras preprocessing layers, and trained the model. In this section, we'll exercise the trained model.

The code in this section is available at https://mng.bz/gaBe and the config file at https://mng.bz/ey19.

# 9.5.1 Rationale for exercising the trained model on some new data points

The process of deploying a model is complex, and we will examine it in more depth in chapters 10 and 11. It can be a big investment to complete the initial deployment, so we want to ensure that deployment goes smoothly and we don't have to backtrack to earlier points in the process if we don't have to. If we exercise the trained model on real-world data points as soon as possible, we can save more problems from appearing later in the process. There are two key benefits to exercising the trained model on new data points as soon as:

+   - It's an easy way of detecting data leakage (see https://mng.bz/zZXw). It can take months between the start of a data science project and the deployment of the