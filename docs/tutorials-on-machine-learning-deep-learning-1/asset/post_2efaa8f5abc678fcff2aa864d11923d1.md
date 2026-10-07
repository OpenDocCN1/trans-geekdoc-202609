
It's not actually mentioned that it's Auto Encoders from the very start, just Neural Networks, and then in the comments you can read that indeed they were talking about Auto Encoders.

## Additional Reading:

## Neural Networks Are Impressively Good At Compression

By Malte Skarupke (2016)

Link:

https://probablydance.com/2016/04/30/neural-networks-are-impressively-good-at-compression/

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_524_0.png)

## 15.1.3 Biases in Auto Encoder (AE)

We've got our simplified version of Auto Encoders and sometimes you'll see a bit of a different representation as follows. The “+1” on both side with the dashed connection are just biases.

- Biases means that in your activation function you define a constant $b$ in $z = f(Wx + b)$, $W$ = weights, $b$ = bias

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_524_1.png)

- The more correct representation is given in right. This is how it should be represented if people are showing biases.

- Bias is just added there because bias affects the layer ahead, the layer that's in front.

- If you see that just remember it's just basically a bias in it. It's just constant in that equation.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_524_2.png)

## 15.1.4 Training an AE

Here we walk through the steps to train an Auto Encoder. We've got an Auto Encoder, where we've got some inputs: the **ratings** of lots and **lots of users** for these **six movies**, and then we'll get some outputs.

Based on these ratings, **Auto Encoder** will come up with a way to **compress** data and **adjust** the weights so that it sets itself up to be able to **encode the data** and **decode the data** in the future.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_525_0.png)

### Steps for Training an Auto Encoder

- **STEP 1:** We start with an *array* where the *lines/rows* (the observations) correspond to the *users* and the *columns (features)* correspond to *movies*. Each cell **(u, i)** contains the *rating* (from $r_1$, ..., $r_m$) of the **movie i** by the **user u**.
- Every single row in your data set is a unique user who rated movies.

- **STEP 2:** The *first user* (first row) goes into the network. The **input vector x** = $(r_1, r_2, ..., r_m)$ contains all its *ratings* for **all the movies** of that user for all of movies.

- **STEP 3:** The **input vector x** is *encoded into* **vector z of lower dimensions** by a *mapping function* $f$ (e.g., sigmoid function or a hyperbolic tangent):

$z = f(Wx + b)$ where $W$ is the vector of **input weights** and $b$ is the bias

- **STEP 4:** z is then *decoded* into the **output y** of same dimensions as **input-vector x**, aiming to replicate the **input vector x**.

- **STEP 5:** The reconstruction error $d(x, y) = ||x - y||$ (which is **different** is the **output** compared to the **input**) is computed. The goal is to **minimize $d(x, y)$**.

- **STEP 6:** Back-Propagation: *from right to left*, the error is back-propagated. The **weights** are updated according to how much they are responsible for the error so we get a **Gradient Descent** happening thereafter. The **learning rate** decides by how much we **update the weights** (that's a parameter you can tune during decoding and you will see that in the practical example).

- **STEP 7:** Repeat *Steps* to 6 and update the weights after each observation (Reinforcement Learning).
Or
Repeat Steps 1 to 6 update the weight **only after a batch of observations** (Batch Learning).

- **STEP 8:** When the **training set** passed through the **ANN**, it makes an **epoch**. Repeat more epochs.

## Training Auto Encoder

**STEP 1:** We start with an array where the (observations) correspond to the users and the columns (features) correspond to the movies. Each cell (i, j) contains the rating (from 1 to 5, or 0 if no rating) of the movie by the user u

**STEP 2:** the user goes into the network. The input vector x = $(r_1, r_2, ..., r_n)$ contains all its ratings for the movies.

**STEP 3:** the input vector x is encoded into a vector z of lower dimensions by a mapping function $f(x; \theta$ sigmoid(function))

```
z = f(W x + b) where W is the vector of input weights and b the bias
```

**STEP 4:** z is decoded into the output y of same dimensions as x, aiming to replicate the input vector x.

**STEP 5:** the reconstruction error, $dx = |x - x|$, is computed. The goal is to minimize it.

**STEP 6:** Back-Propagation from right to left, the error is updated according to how much they are responsible for the error. The learning rate how much we update the weights.

**STEP 7:** Repeat Steps 1 to 6 and update the weights after each observation (Reinforcement Learning).
Repeat Steps 1 to 6 but update the weights only after a batch of observations (Batch Learning).

**STEP 8:** when the training set is passed through the ANN, an epoch is made. Repeat more epochs.

*Walkthrough:* We have ratings 0 and we can have ratings from 1 to 5 (it will be a recommender system). In this case we've got 1, 0, we can easily change them to "4" for ratings and 0 for empty.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_526_0.png)
- 1. That's our input.
- 2. We take the first row, we put it into our AutoEncoder.
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_526_1.png)
- 3. We calculate the hidden nodes. The start you have some randomly weights. This process is called encoding.
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_526_2.png)
- 4. We're going to calculate output nodes, initially it will be some random weights. This process is called decoding. That's the forward propagation. We've just put the information, the data through our Auto Encoder from left to right.
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_527_0.png)
- 5. We're going to compare the results to the actual ratings for those six movies. And then we'll calculate the error.
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_527_1.png)
- 6. And then we will propagate it back through the network, we'll adjust the weights accordingly.
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_527_2.png)
- 7. We will take the next row in our data set. And we'll do the same thing and so on. We'll continue through all the rows.
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_527_3.png)
- 8. It means we've finished a whole epoch. And then we just repeat these epochs. Hopefully, our training converges to some sort of value.
![](img/0aa092657a6eb1b9f2dd65bbb79055a3_527_4.png)

Additional reading: Here is a blog by Francois Chollet the creator of Keras, it's called Building Autoencoders in Keras, check it out, it's got some actual applications so if you want to get some hands on experience before you start to Practice.

## Additional Reading:

## Building Autoencoders in Keras

By Francois Chollet (2016)

Link:

https://blog.keras.io/building-autoencoders-in-keras.html

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_528_0.png)

## 15.1.5 Overcomplete hidden layers in AE

Overcomplete hidden layers is an underlying concept in most of the variations of Autoencoders. So here we got an autoencoder, four input values, two nodes in the hidden layer and four nodes in the output layer.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_528_1.png)

- What if we wanted to increase the number of nodes in the hidden layer?
- What if we wanted to actually have more nodes in the hidden layer than the input layer?

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_528_2.png)

- Why would we do that? We said that an auto encoder can be used as a feature extraction tool, that if we want more features.
- Number of nodes in hidden layer in ANN doesn't matter: Remember in ANN it was very easy for us to do, we had a certain number of inputs, then we could have a whole layer of hidden nodes that could have more nodes than input layer (It could be six, or 10, it could be 100, dearest). We could add more layers and so on.
- We weren't restricted to how many nodes we would have in the hidden layer. And that allowed us to extract more features in ANN.

Increasing nodes in hidden layer in Auto-Encoder can cause problem: if we increase nodes in hidden layer encoder obviously the auto-encoder can cheat.
