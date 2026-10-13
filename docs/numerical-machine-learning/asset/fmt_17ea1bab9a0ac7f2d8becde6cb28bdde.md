
### 3.3.1. Start the First Iteration of Learning

![](Images/9789815136982-C3-E11.jpg)

![](Images/9789815136982-C3-E12.jpg)

### 3.3.2. End the First Iteration of Learning

![](Images/9789815136982-C3-E13.jpg)

So, the latest MSE after the first iteration of learning with L1 regularization is 2.7320. Next, let us continue with the second iteration with the updated bias and weights determined above.

### 3.3.3. Start the Second Iteration of Learning

![](Images/9789815136982-C3-E14.jpg)

![](Images/9789815136982-C3-E15.jpg)

### 3.3.4. End the Second Iteration of Learning

![](Images/9789815136982-C3-E16.jpg)

**Table 3.3** The bias, weights and MSE values for the first and last five iterations for training the L1 regularized linear regression model.

| **Iteration** | ***b*** | ***w[1]*** | ***w[2]*** | ***MSE*** |
| --- | --- | --- | --- | --- |
| 1 | 0.001553 | 0.0009274 | 0.0009933 | 2.7320 |
| 2 | 0.003104 | 0.001853 | 0.001985 | 2.7232 |
| 3 | 0.004652 | 0.002777 | 0.002975 | 2.7143 |
| 4 | 0.006198 | 0.003700 | 0.003963 | 2.7055 |
| 5 | 0.007741 | 0.004621 | 0.004949 | 2.6967 |
| ... | ... | ... | ... | ... |
| 499,996 | 1.1466 | 0.7949 | 0.00004110 | 0.0636 |
| 499,997 | 1.1466 | 0.7949 | 0.00003797 | 0.0636 |
| 499,998 | 1.1466 | 0.7949 | 0.00003485 | 0.0636 |
| 499,999 | 1.1466 | 0.7949 | 0.00003172 | 0.0636 |
| 500,000 | 1.1466 | 0.7949 | 0.00002860 | 0.0636 |

![](Images/9789815136982-C3-F2.jpg)

**Fig. 3.2** Mean squared error (MSE) *vs*. learning iteration for training the L1 regularized linear regression model.

As can be seen from **Table 3.3** and **Fig. 3.2**, MSE finally stabilizes at 0.0636, which suggests that we have trained a good linear regression model under L1 regularization. The final obtained bias and weights are `b=1.1466`, `w1=0.7949` and `w2=0.00002860`. One important highlight of L1 regularization is that it shrinks the weights of the features it deems less important, often to zero, effectively serving as a method for feature selection. However, it is worth noting that these "less important" features are determined by the model and data, and may or may not align with domain-specific knowledge or broader context. The resulting linear regression model can be written as:

`Y = b + ∑(j=1 to 2) wj ⋅ normalized Xj`

Here, `b=1.1466`, `w1=0.7949` and `w2=0.00002860`.

As Max-min normalization was performed during the training process, it needs to be reflected in the final model as well. That is why `normalized Xj` is shown here.

Now, we can use this trained linear regression model to make predictions for previously unseen data (*i.e.*, new data). For instance, there is a new house with 1200 sqft and 3 bedrooms. To predict the price of the house, normalization needs to be applied first using the maximum and minimum values of each respective feature from the training dataset. Recall that the maximum and minimum of `size_sqft` are 1600 and 740; the maximum and minimum of `num_bedrooms` are 5 and 2. So, the `normalized X1` for `size_sqft` and `normalized X2` for `num_bedrooms` will be:

`normalized X1 = (1200 - 740) / (1600 - 740) = 0.5349`

`normalized X2 = (3 - 2) / (5 - 2) = 0.3333`

Next, plug the normalized feature values into the equation of linear regression model:

`Y = b + ∑(j=1 to 2) wj ⋅ normalized Xj = 1.1466 + 0.7949 × 0.5349 + 0.00002860 × 0.3333 = 1.572`

Therefore, for the house with 1200 sqft and 3 bedrooms, the sale price is predicted to be 1.572 million dollars.

## 3.4. SAMPLE CODES AND COMPARISON OF L1 REGULARIZATION FOR LINEAR REGRESSION

Following the mathematics and numerical example discussed in Sections 3.2 and 3.3, we have implemented the L1 regularized linear regression machine learning model with the aforementioned small dataset from scratch in Python. The code is similar to that of the original linear regression discussed in Chapter 2. The difference lies in the function `update_bias_weights()`, because of the addition of the L1 regularization term (*i.e.*, `λW1`) to the loss function. Readers are encouraged to have their Jupyter Notebook (or other Python IDE) ready and try the codes along with reading. The complete code file can be downloaded from our shared folder in Google Drive:

<https://drive.google.com/drive/folders/1FqJvo4ZPazNbEH_GlHFoodqvegnQmHcn?usp=share_link>

Firstly, only the `pandas` and `numpy` libraries are imported.

![](Images/9789815136982-C3-E21.jpg)

Secondly, a `loss_MSE()` function is created for calculating the MSE between the known true output values and predicted output values by the linear regression model. See the docstring of the `loss_MSE()` function to understand its usage.

![](Images/9789815136982-C3-E22.jpg)

Thirdly, an `update_bias_weights()` function is created to update the values of bias and weights based on the gradient descent optimization algorithm. The equations (3.4) to (3.11), which we derived in Section 3.2, are well translated into Python codes in this function. See the docstring of the `update_bias_weights()` function to understand its usage.

![](Images/9789815136982-C3-E23.jpg)

Fourthly, a `train()` function is created to oversee the training process for specific iterations and write the log of loss/MSE history. See the docstring of the `train()` function to understand its usage.

![](Images/9789815136982-C3-E24.jpg)

Fifthly, a `max_min_norm()` function is created to normalize the values of input features (*i.e.*, `X`). See the docstring of the `max_min_norm()` function to understand its usage.

![](Images/9789815136982-C3-E25.jpg)

Sixthly, we store the small dataset as a numpy array, invoke the `max_min_norm()` function for normalization, initialize bias and weights, set learning rate, iterations and penalty coefficient that multiplies the L1 regularization term, then invoke the `train()` function to start building our first L1 regularized linear regression model, after decomposing and fully understanding every single step of the process.

![](Images/9789815136982-C3-E26.jpg)

![](Images/9789815136982-C3-E27.jpg)

Finally, the trained linear regression model is utilized to predict the price of the house (new data) with 1200 sqft and 3 bedrooms:

![](Images/9789815136982-C3-E28.jpg)

We then compare the above results with those from the off-the-shelf L1 regularized linear regression model (*i.e.*, Lasso) offered by the `scikit-learn` library. These include the final bias and weights after training, the final MSE, and the predicted price for the house (new data) with 1200 sqft and 3 bedrooms. The codes are as follows:

![](Images/9789815136982-C3-E29.jpg)

![](Images/9789815136982-C3-E30.jpg)

As can be seen from the results using the `scikit-learn` L1 regularized linear regression model (*i.e.*, Lasso), the final bias, weights, and MSE values are the same as or extremely close to those given by our own L1 regularized linear regression model (*i.e.*, `b=1.1466`, `w1=0.7949`, `w2=0.00002860`, and `MSE=0.0636`). Furthermore, the predicted price for the previously unseen house with 1200 sqft and 3 bedrooms is also the same as that produced by our own model (*i.e.*, 1.572 million).

## 3.5. MATHEMATICS OF L2 REGULARIZATION FOR LINEAR REGRESSION

The L2 regularized linear regression starts again with the general equation of linear regression when having more than one independent variable `X` (*i.e.*, input feature), as follows:

`Y = b + ∑(j=1 to n) wj Xj` (3.13)

Here,

- `Y` is the output
- `b` is the bias
- `n` is the number of input features
- `wj` is the weight of the `j`th feature
- `Xj` is input value of the `j`th feature
