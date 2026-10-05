
## Chapter 2: t-SNE

In this lecture we are going to talk about another dimensionality reduction and visualization method called t-SNE. The t means we are going to incorporate the t-distribution and SNE stands for “stochastic neighbor embedding”.

One big advantage of t-SNE is that it's a nonlinear method, so it is more expressive than PCA.

### Why study t-SNE?

2 reasons:

- 1) t-SNE was jointly developed by Geoffrey Hinton, who as you know, is one of the main figures of deep learning.
- 2) by doing t-SNE, we are seeing how the limitations of PCA can be overcome by using a more complex mathematical model.

One key difference between PCA and t-SNE, other than the fact that t-SNE is non-linear, is that there is no transformation model with t-SNE.

Instead, t-SNE just modifies the outputs directly in order to minimize the cost function.

What this means is that, you won’t have any train and test sets, and you can’t transform data after fitting on some other data.

The way that t-SNE works is essentially it tries to preserve the distances between each input vector.

We will start with symmetric SME since it intuitively makes more sense.

On the original data X, we define a joint probability distribution $p(i,j)$ which is equal to:

$p(i,j) = \frac{\exp(-|x_i - x_j|^2 /(2s^2))}{\sum_{k \neq m} \exp(-|x_m - x_k|^2 /(2s^2))}$

Note that i and j are not the index for the dimensions like we did with PCA, but rather the ith and jth data point in the dataset, i.e. i and j are the ith and jth sample.

Notice it kind of looks like a Gaussian distribution. You can think of “s” as a hyperperameter. It’s controlling the “spread” of the distribution.

Next, we have our low-dimensional mapping Y, which we define in the same way, but there is no s term.

$q(i,j) = \frac{\exp(-|y_i - y_j|^2)}{\sum_{k \neq m} \exp(-|y_m - y_k|^2)}$

Note that we just set $p(i,i) = q(i,i) = 0$.

So we’ve defined 2 probability distributions, one between every pair of points in X, and one between every pair of points in Y. We usually just initialize every data point in Y randomly. i.e. If we’re looking for a 2-D representation, we’ll create Y as:

`Y = np.random.randn(N, 2)`

Once we’ve done that, we can try to find a better Y by optimizing some objective function that relates $p(i,j)$ and $q(i,j)$. If you are not familiar with how we compare probability distributions, we usually use Kullback-Leibler divergence for short:

$C = D_{KL}(P || Q) = \sum p(i,j) \log\left(\frac{p(i,j)}{q(i,j)}\right)$

If P and Q are exactly the same, this would be 0. How we solve this problem is the same as we solve all other problems of this type - we take the derivative of the objective and do gradient descent. Notice how with this type of model we don't have weights - so we are taking the gradient with respect to Y, which is the output mapping. i.e.

`Y <- Y - learning_rate * dC/dY`

One problem with symmetric SNE that came before is known as the “crowding problem”, which prevents clusters from forming naturally. t-SNE does use slightly different distributions for Q and P, which helps space out clusters. These are defined as follows:

$p(i,j) = \frac{p(i | j) + p(j | i)}{2}$

Where:

$p(j | i) = \frac{\exp(-|x_i - x_j|^2 /(2s^2))}{\sum_{k} \exp(-|x_i - x_k|^2 /(2s^2))}$

Notice each sample has its own “s”. Even though it is relatively simple given the definitions above, the cost function remains the same. The problem is that it's slow and has huge RAM requirements because we need to calculate $q(i,j)$ and $p(i,j)$ for $i=1..N$ and $j=1..N$, which is naturally $O(N^2)$. There is a variant of it which is called Barnes-Hut that is $O(N \log N)$ run time, but still has huge RAM requirements. This is the default method used in SciKit Learn. One solution is to take a sample of just a few hundred points and do t-SNE on that, or if you are willing to wait and have enough RAM.

### Exercises

- Try t-SNE (from scikit learn) on the MNIST dataset.
- Try writing your own implementation given the definitions above, and take advantage of automatic differentiation.

## Chapter 3: Autoencoders

In this chapter we are going to talk about autoencoders. Autoencoders are actually nothing new, just a small twist on something you already know. A supervised learning model has 2 main functions as its API, fit and predict. Usually when we call a neural network we call `model.fit(X, Y)`, and then to make predictions we call `model.predict(X)`. But what if we just make the neural network try to predict itself? So we call `model.fit(X, X)` instead.

That's exactly what an autoencoder is. In most of my previous courses we did classification, but remember that X can be any real value. So if you are trying to predict real values in general, you can use squared error, and it becomes more like regression. You can alternatively still use cross-entropy error and consider your inputs and outputs to be binary, even for variables that are not exactly binary. You'll see that we do this with both autoencoders and RBMs, and you'll see that both error functions work. You can think of images like MNIST as having pixel intensities: 0 would be no intensity at all, and 1 would be maximum intensity, since we always scale by 255.

To make the outputs go between 0 and 1, we are going to use the sigmoid function at both the hidden layer and output layer. One slight modification we sometimes use for both autoencoders and RBMs is the idea of shared weights. So instead of using another weight at the output layer, we just use the transpose of the first weight.

`Z = sigmoid(XW + b)`
`X_hat = sigmoid(ZW^T + c)`

We first encountered the idea of shared weights when we looked at convolutional neural networks, since it was the same filter passed along each part of the image. Remember that having shared weights is a kind of regularization because we are reducing the number of parameters, thereby reducing the chance of overfitting.

Next, let’s return to the squared error objective. If we write it out in terms of the weights and the inputs (ignoring biases), we get:

$J = \|X - \sigma(XW)W^T\|^2$

Remember back when we were doing PCA, I asked you to remember the objective function?

$J = \|X - XX^T\|^2$

Well consider what would happen if we did NOT use the sigmoid here:

$J = \|X - XWW^T\|^2$

We would in fact just get back PCA! You can in fact think of autoencoders as a sort of nonlinear PCA. This is doing a nonlinear mapping, just like t-SNE. Note that this isn't really the full picture because we are not considering biases, and we don't have any requirement that each column of the weight has length 1, or that each column is orthogonal, or that they are ordered in any particular way. So while the functional form looks “like” PCA, it’s not doing everything PCA is doing.

### Denoising Autoencoders

In this section we are going to talk about yet another method of regularization. Remember that when we’re given a dataset, we don't have to only train on that dataset.
