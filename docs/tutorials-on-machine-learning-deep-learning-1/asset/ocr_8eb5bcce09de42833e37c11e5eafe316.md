# Max Pooling

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 2 | 1 |
| 1 | 4 | 2 | 0 |
| 0 | 0 | 2 | 1 |

| 1 | 1 | 0 |
| 4 |

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 2 | 1 |
| 1 | 4 | 2 | 0 |
| 0 | 0 | 2 | 1 |

# Max Pooling

| 1 | 1 | 0 |
| 4 | 2 |

Pooled Feature Map

Feature Map

Pooled Feature Map

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 4 | 1 | 0 |
| 0 | 0 | 2 | 1 |

# Max Pooling

| 1 | 1 | 0 |
| 4 | 2 | 1 |

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 4 | 1 | 0 |
| 0 | 0 | 2 | 1 |

# Max Pooling

| 1 | 1 | 0 |
| 4 | 2 | 1 |

```
0
```

Pooled Feature Map

Feature Map

Pooled Feature Map

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 2 | 1 |
| 1 | 4 | 2 | 0 |
| 0 | 0 | 1 | 1 |

# Max Pooling

| 1 | 1 | 0 |
| 4 | 2 | 1 |
| 0 | 2 |

| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 4 | 1 | 0 |
| 0 | 0 | 1 | 1 |

# Max Pooling

| 1 | 1 | 0 |
| 4 | 2 | 1 |
| 0 | 2 | 1 |

Feature Map

Pooled Feature Map

Feature Map

Pooled Feature Map

> Here're selecting a stride of two and this size is commonly used. After repeating the process we record that maxim values shown in above pictures.

Following things happened:

+   i. Preserving the features: First of all we were still able to preserve the features, the maximum numbers they represents the features. These large numbers in you-feature map represent where you found the closest similarity to a feature.

+   ii. We're introducing spatial invariants: Because we are taking the maximum of the pixels we are gaining spatial invariance. For example: Cheetah's Tearmark in different version of the image (rotated and squashed) or other positioncan-end-up with Pooled-Feature-Map

+   iii. Reducing the size of the data: We're reducing the size by 75% which is really going to help us in terms of Processing By pooling these features we are getting rid of 75% of the information that is not the feature (not related to the feature) by using max pooling of 2x2 pixels

+   iv. Preventing overfitting: Another benefit of pooling is that we are reducing the number of parameters. We're reducing 75% of overfitting as we go into the Final Layers of the neural network and we are preventing overfitting (i.e. model doesn't get dependent on train images).

It is a very important benefit of pooling that we are removing information because way our model might be able to Overfit that information. It's important to see the exact features that all other noise that is still keeping in our eyes. This sense needs for neural networks by eliminating the unnecessary information we are helping with preventing of overfitting.

That's the point of that we're still able to preserve the features for their possible spatial or texture or other kind

+   Max pooling (Additional Readings): There's lots of types of pooling and which size of 2 x 2 pixels box size. On that note I'd like to introduce to this lovely research paper 'Evaluation Of Pooling Operations in Convolutional Architectures For Recognition' by Denise Scherer from University of Bonn.

They talk about about subsampling which is basically average pooling.

In average pooling, instead of taking the max value we make the average.