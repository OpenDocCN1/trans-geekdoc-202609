# 15.1.4 Training an AE

Here we walk through the steps to train an Auto Encoder. We've got an Auto Encoder, where we've got some inputs: the **ratings** of lots and **lots of users** for these **six movies**, and then we'll get some outputs.

Based on these ratings, **Auto Encoder** will come up with a way to **compress** data and **adjust** the weights so that it sets itself up to be able to **encode the data** and **decode the data** in the future.

![](bbox=[0.139, 0.142, 0.861, 0.423])

# Steps for Training an Auto Encoder

+   **STEP 1:** We start with an *array* where the *lines/rows* (the observations) correspond to the *users* and the *columns (features)* correspond to *movies*. Each cell **(u, i)** contains the *rating* (from $r_1$, ..., $r_m$) of the **movie i** by the **user u**.
* Every single row in your data set is a unique user who rated movies.

+   **STEP 2:** The *first user* (first row) goes into the network. The **input vector x** = $(r_1, r_2, ..., r_m)$ contains all its *ratings* for **all the movies** of that user for all of movies.

+   **STEP 3:** The **input vector x** is *encoded into* **vector z of lower dimensions** by a *mapping function* $f$ (e.g., sigmoid function or a hyperbolic tangent):

z = f(Wx + b)$ where $W$ is the vector of **input weights** and $b$ is the bias

+   **STEP 4:** z is then *decoded* into the **output y** of same dimensions as **input-vector x**, aiming to replicate the **input vector x**.

+   **STEP 5:** The reconstruction error $d(x, y) = ||x - y||$ (which is **different** is the **output** compared to the **input**) is computed. The goal is to **minimize $d(x, y)$**.

+   **STEP 6:** Back-Propagation: *from right to left*, the error is back-propagated. The **weights** are updated according to how much they are responsible for the error** so we get a **Gradient Descent** happening thereafter. The **learning rate** decides by how much we **update the weights** (that's a parameter you can tune during decoding and you will see that in the practical example).

+   **STEP 7:** Repeat *Steps* to 6 and update the weights after each observation (Reinforcement Learning).
Or
Repeat Steps 1 to 6 update the weight**only after a batch of observations** (Batch Learning).

+   **STEP 8:** When the **training set** passed through the **ANN**, it makes an **epoch**. Repeat more epochs.