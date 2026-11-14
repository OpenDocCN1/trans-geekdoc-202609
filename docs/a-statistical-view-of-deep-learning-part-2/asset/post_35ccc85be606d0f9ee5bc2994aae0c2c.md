
## Regularization vs Dropout

### Dropout

- Randomly set to 0 a proportion of weights in the model
- Prevents overfitting via sparser networks
- Dropout rate = fraction of weights set to 0

## Regularization vs Dropout

```
model <- keras_model_sequential()
model %>%
layer_dense(units = 256, activation = 'relu', input_shape
layer_dropout(rate = 0.4) %>%
layer_dense(units = 128, activation = 'relu') %>%
layer_dropout(rate = 0.3) %>%
layer_dense(units = 10, activation = 'softmax')
```

Rstudio's keras pages

## Regularization vs Dropout

Source: Srivastava et al. Dropout: A Simple Way to Prevent Neural Networks from Overfitting

![](img/357c1568568ec7942f9e3cf49122ebd5_58_0.png)

Figure 4: Test error for different architectures

## Regularization

You can also achieve regularization by adding a LASSO-like penalty to the loss function (Tibshirani, 1996)

### Regularization

Loss + Regularization penalty

### L1 Regularization

$Loss + \lambda \sum_{i=1}^{M} |w_i|$

where

- $w_1, \dots, w_M$ represent all model weights (parameters)
- $\lambda$ is a tuning parameter

## Epochs and Batch Size

To deal with large data sets, deep learning optimization algorithms break up the data into subsets.

### Model fitting options:

- Batch size: # of training samples to work through before updating the model
- Epoch: number of complete passes through the data set
- Validation split: Fraction of the training data to be used as validation data per epoch.

## Epochs and Batch Size

Small example: Use the fit() function to train the model for 30 epochs using batches of 128 images:

```
history <- model %>% fit(
x_train, y_train,
epochs = 30, batch_size = 128,
validation_split = 0.2
)
```

Useful reference: machinelearningmastery.com

## Epoch plot

accuracy
epoch
training accuracy
validation accuracy: little overfitting
validation accuracy: strong overfitting

Image source: towardsdatascience.com

## THIS IS YOUR MACHINE LEARNING SYSTEM?

YUP! YOU POUR THE DATA INTO THIS BIG PILE OF LINEAR ALGEBRA, THEN COLLECT THE ANSWERS ON THE OTHER SIDE.

WHAT IF THE ANSWERS ARE WRONG?

JUST STIR THE PILE UNTIL THEY START LOOKING RIGHT.

![](img/357c1568568ec7942f9e3cf49122ebd5_63_0.png)

## Architecture

Network architecture: the overall structure of the network

### General advice

- Fit the largest network you can afford
- Keep the # nodes per layer the same
- Try different layer sizes
- Use ReLU units for hidden layers
- Choose an appropriate loss function for your data
- Make sure the activation function for your output layer matches the loss function

## Types of Deep Learning Models

## Types of Deep Learning Models

### Architecture families:

- 1. Deep feedforward networks: what we've covered so far
- 2. Convolutional networks
- 3. Recurrent and Recursive Nets
- 4. Generative adversarial network
- 5. Bayesian networks
- 6. Always new methods on the horizon

## Types of Deep Learning Models

### Convolutional networks

- For grid-like data like images
- Data need to be correlated in some way (I think)
- Each layer detects small, meaningful features like edges using kernels instead of the entire image
- Sparse connectivity

## Types of Deep Learning Models

### Edge Detection by Convolution

![](img/357c1568568ec7942f9e3cf49122ebd5_68_0.png)

Input

| 1 | -1 |
|---|---|

Kernel

![](img/357c1568568ec7942f9e3cf49122ebd5_68_1.png)

Output

## Convolution network

Image: Deep Learning, Fig 1.2

![](img/357c1568568ec7942f9e3cf49122ebd5_69_0.png)

Output (object identity)

CAR

PERSON

ANIMAL

3rd hidden layer (object parts)

2nd hidden layer (corners and contours)

1st hidden layer (edges)

Visible layer (input pixels)

## Types of Deep Learning Models

### Recurrent and Recursive Nets

- For processing sequential data
- Examples: time series, financial data, text, speech

### Generative adversarial network

- Two neural networks compete to generate new data to be similar to old data
- Used for image generation, video generation and voice generation

## Types of Deep Learning Models

### Bayesian networks

- Can be any of the above (e.g., Bayesian convolutional network)
- Pros: estimate uncertainty
- Cons: slow to compute
- Variational Bayes is a current approach for inference
- Current approaches are pretty crude

## A Statistical View of Deep Learning in Ecology

### Part 1: Introduction

- Introduction to machine learning
- Introduction to deep learning

### Part 2: Going deeper

- Neural networks from 3 viewpoints
- Mathematics of deep learning
- Model fitting
- Types of deep learning models

### Part 3: Deep learning in practice

- Ethics in deep learning
- Deep learning in ecology

## Some useful references on deep learning

- Deep Learning by I. Goodfellow, Y. Bengio and A. Courville (2016) MIT Press
- Deep Learning with R F. Chollet and J.J. Allaire (2018) Manning Publications
- Chapters 1-3 available online
- Focus is on Keras

## Additional references that I used to develop this presentation

### Books:

- *Computational Statistics*
  by Givens and Hoeting (2nd edition, Wiley)
- *The Elements of Statistical Learning*
  by Hastie, Tibshirani, and Friedman
- *Introduction to Statistical Learning*
  by James, Witten, Hastie, Tibshirani

Course materials by:
Ian Goodfellow, Darren Homrighausen, Ander Wilson, Asa Ben-Hur

## Thank you to

- ISEC2020 organizers especially David Warton and Gordana Popovic
- Course assistants: Tess Hamzeh, Winston Hilton, Rachael Krawczyk
- Alison Ketz and Dan Walsh

## Acknowledgment of funding support

This material is based upon work supported by the National Science Foundation (NSF) under Grant No. AGS-1419558, the US Geological Survey (USGS) (G17AC00409), and Colorado State University (CSU). Any opinions, findings, and conclusions or recommendations expressed in this material are those of the author and do not necessarily reflect the views of the NSF, USGS or CSU.
