
# Row ID Study Hrs Sleep Hrs Quiz Exam

| Row ID | Study Hrs | Sleep Hrs | Quiz | Exam |
|---|---|---|---|---|
| 1 | 12 | 6 | 78% | 93% |
| 2 | 22 | 6 | 24% | 68% |
| 3 | 115 | 4 | 100% | 95% |
| 4 | 31 | 9 | 67% | 75% |
| 5 | 0 | 10 | 58% | 51% |
| 6 | 5 | 8 | 60% | 61% |
| 7 | 92 | 6 | 82% | 89% |
| 8 | 57 | 8 | 91% | 97% |

```
$C = \sum \frac{1}{2}(y-\hat{y})^2$
```

# Adjust $w_1, w_2, w_5$

| Row ID | Study Hrs | Sleep Hrs | Quiz | Exam |
|---|---|---|---|---|
| 1 | 12 | 6 | 78% | 93% |
| 2 | 22 | 6 | 24% | 68% |
| 3 | 115 | 4 | 100% | 95% |
| 4 | 31 | 9 | 67% | 75% |
| 5 | 0 | 10 | 58% | 51% |
| 6 | 5 | 8 | 60% | 61% |
| 7 | 92 | 6 | 82% | 89% |
| 8 | 57 | 8 | 91% | 97% |

```
$C = \sum \frac{1}{2}(y-\hat{y})^2$
```

# Adjust $w_1, w_2, w_5$

| Row ID | Study Hrs | Sleep Hrs | Quiz | Exam |
|---|---|---|---|---|
| 1 | 12 | 6 | 78% | 93% |
| 2 | 22 | 6 | 24% | 68% |
| 3 | 115 | 4 | 100% | 95% |
| 4 | 31 | 9 | 67% | 75% |
| 5 | 0 | 10 | 58% | 51% |
| 6 | 5 | 8 | 60% | 61% |
| 7 | 92 | 6 | 82% | 89% |
| 8 | 57 | 8 | 91% | 97% |

```
$C = \sum \frac{1}{2}(y-\hat{y})^2$
```

# Adjust $w_1, w_2, w_5$

And we're going to just put the two side by side to remember them.

| Row ID | Study Hrs | Sleep Hrs | Quiz | Exam | Row ID | Study Hrs | Sleep Hrs | Quiz | Exam |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 12 | 6 | 78% | 93% | Upd $w_1$ | 12 | 6 | 78% | 93% |
| 2 | 22 | 6 | 24% | 68% | Upd $w_2$ | 22 | 6 | 24% | 68% |
| 3 | 115 | 4 | 100% | 95% | Upd $w_3$ | 115 | 4 | 100% | 95% |
| 4 | 31 | 9 | 67% | 75% | Upd $w_4$ | 31 | 9 | 67% | 75% |
| 5 | 0 | 10 | 58% | 51% | Upd $w_5$ | 0 | 10 | 58% | 51% |
| 6 | 5 | 8 | 60% | 61% | | 5 | 8 | 60% | 61% |
| 7 | 92 | 6 | 82% | 89% | | 92 | 6 | 82% | 89% |
| 8 | 57 | 8 | 91% | 97% | | 57 | 8 | 91% | 97% |

# Batch Gradient Descent Stochastic Gradient Descent

In the Batch Gradient Descent, we are adjusting the weights after you've run all the rows in your NN and adjust the weights and that's the first iteration.

- For the 2nd iteration we repeat while adjusting the weights and then we do everything again for the 3rd iteration.

The Stochastic Gradient Descent method helps you to avoid the problem with local extrema or local minima. It helps to find minima.

And the reason is that SGD (STOCHASTIC GRADIENT DESCENT) method has much higher fluctuations, because it is one iteration at a time and the fluctuations are higher and it is much more likely to find the global minimum rather than just the local.

SGD is faster than SGD: Stochastic Gradient Descent has more advantages over the Batch Gradient descent. At the first impression you might think that Batch Gradient Descent is faster because it's doing all once at a time. In reality, Stochastic Gradient Descent is faster because it doesn't have to load all the data into memory and wait until all of those rows are regulated.

- The main advantage is that BGD is a deterministic algorithm but SGD being a stochastic algorithm (meaning it is random).
- With SGD, as long as you have the same weights for your NN, every time you run, you will get the same iterations to update weights.
- For SGD you won't get that because it is, in a stochastic manner, you're picking rows at random and you are updating your NN in a stochastic manner. SGD even if you have the same at the start, you're going to have different iterations to get them.

# 8.3.6 Mini Batch Gradient Descent

There's a method in-between BGD and SGD, it is the Mini Batch Gradient Descent. Where you are running smaller batches of rows than all at once. From your dataset, all the rows, you set batch size (number of rows), you divide all the rows into groups and you run it through each epoch and update the weight.

And that's the Mini Batch Gradient Descent if you'd like to learn more about:
- There's a great article well-written, very simple terms. You will get some cool tips and hacks.
- It discussed how to apply Gradient, know advantages and disadvantages.
- Additional Reading: A Neural Network in 13 Lines of Python (Part 2) - Andrew Trask (2015).
- There is another article, it's a bit more to read for those of you who are into mathematics who want to get to the bottom of: What is Gradient descent? What are the formulas and so on. Check out the free online book called Neural Networks And Deep Learning by Michael Nielsen (2015).

# 8.3.7propagation

**Forward propagation:** There's a process called forward propagation where information is entered into the input layer and then propagated forward to get our output y. Then compare those to the actual value y in our training set. And then we calculate the errors, then the errors are back-propagated through the network in the opposite direction and allows us to adjust the weights.

**Back propagation adjusts all weights simultaneously:** Back propagation is driven by very interesting and sophisticated mathematics which allows us to adjust the weights. All the weights are adjusted simultaneously. The huge advantage of back propagation and one key thing to remember is that during the process of back propagation, you are able to adjust all the weights at the same time, because that's how the algorithm is structured. It is the fundamental principle of back propagation. So you can track which part of the neural network is responsible for.

**Adjust weights independently:** If we were doing this manually or coming up with a different type of algorithm even if we evaluated the error and then trying to understand what effect each weight has on the error, we'd adjust each weight independently. Neural Networks And Deep Learning is a book by Michael Nielsen. You'll find the mathematics written out and it will help you understand this is possible.

# 8.3.8 Steps On Training Of A Neural Network

Now we're going to wrap everything up with a step-by-step walkthrough of what happens in training of a neural network.

STEP 1: We randomly initialize the weights to small numbers close to 0 but not 0, i.e., they are initialized with random values near zero. And from there the process of back propagation these weights are adjusted until the error function is minimized.

STEP 2: Input the first observation of your dataset in the input layer, each feature in one input node. That is the first row into input layer and each feature in one input node.

STEP 3: Forward-propagation: From left to right, the neurons are activated in a way that the impact of each neuron's activation is limited by the weights (the weights basically determine how important activation is). Propagate the activations until getting the predicted result Y.

STEP 4: Compare the predicted result to the actual result y. Measure the generated error.

STEP 5: Back-propagation: From left to right, the error is back-propagated. Update the weights according to how much they are responsible for error. The learning rate decides by how much you update the weights. The learning rate is a parameter you control in your network.

STEP 6:
- SGD: Repeat Steps 1 to 5 and update the weights after each observation (this is called reinforcement learning and in our case stochastic gradient descent).
- BGD/Mini-BGD: Repeat Steps 1 to 5 update the weights only after a batch of observations (Batch Learning).

STEP 7: When the whole training set passed through the ANN, that makes an epoch. Redo more epochs. Just keep doing that to allow your NN to train better and constantly adjust itself until you minimize the cost function.

Those are the steps you need to take to build your artificial neural networks (ANN) and train it.

STEP 1: Randomly initialize the weights to small numbers close to 0 (but not 0).

STEP 2: Input the first observation of your dataset in the input layer, each feature in one input node.

STEP 3: Forward-propagation: From left to right, the neurons are activated in a way that the impact of each neuron's activation is limited by the weights. Propagate the activations until getting the predicted result y.

STEP 4: Compare the predicted result to the actual result. Measure the generated error.

STEP 5: Back-propagation: From left to right, the error is back propagated. Update the weights according to how much they are responsible for the error. The learning rate decides by how much we update the weights.
