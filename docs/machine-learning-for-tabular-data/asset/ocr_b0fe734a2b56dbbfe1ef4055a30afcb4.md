# CHAPTER 9 Deep learning best practices

| Size_type_bin | input: | [(None, 1)] |
| InputLayer | output: | [(None, 1)] |

| embedding_17 | input: | (None, 1) |
| Embedding | output: | (None, 1, 10) |

| batch_normalization_17 | input: | (None, 1, 10) |
| BatchNormalization | output: | (None, 1, 10) |

| flatten_17 | input: | (None, 1, 10) |
| Flatten | output: | (None, 10) |

| dropout_17 | input: | (None, 10) |
| Dropout | output: | (None, 10) |

| concatenate_21 | input: | [(None, 40), (None, 10)] |
| Concatenate | output: | (None, 50) |

| concatenate_22 | input: | [(None, 50), (None, 1)] |
| Concatenate | output: | (None, 51) |

| concatenate_23 | input: | [(None, 51), (None, 11)] |
| Concatenate | output: | (None, 52) |

| dense_3 | input: | (None, 52) |
| Dense | output: | (None, 10) |

> Figure 9.14 Layers for the Size column with custom layers

single concatenation layer that pulls together layers coming in from each input. This difference in the number of intermediate layers between the input of the Size column and the final layer reflects the overall complexity of the Keras model with custom layers compared to the Keras preprocessing layers.

# 9.3.2 Examining the code for model definition using Keras preprocessing layers

In general, the code for defining and training the model using Keras preprocessing is simpler and more streamlined than what you read about in previous chapters that used custom layers and Scikit-learn pipelines. However, a small price is to be paid in exchange for the increased simplicity of a model based on Keras preprocessing layers. To avoid an error when saving the model save() and in the model saving callback, need to ensure that all column names are lowercase and contains no spaces (this can be achieved using the snake_case naming convention instead) for the model using Keras preprocessing layers. The code in the following listing automatically does this.