
Not all variables are important for some; Now we previously saw that all of the neurons from the input layer they have synapses connecting each of them to the top neuron in the hidden layer.

But those synapses have WEIGHTS. Now some weights will have a non-zero value and some weights will have zero value, because not all inputs will be valid for all single neuron. Some inputs will not be important and neglected by some neurons.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_228_0.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_228_1.png)

We can see two variables $x_1$ and $x_2$ the area and the distance to the city are important for first neuron bedrooms and are not.

We can explain: The further away you go from the city the real estate becomes, in square feet of properties becomes larger. For the same price you can get a larger property the further away you go from the city.

And probably this neuron is dealing: it is looking for area variable which are not far from the city but have a large area. For their distance from the city they have an unfair area.

So that neuron might be picking out those specific properties and it will activate the activation function only when the certain criteria is met. It performs on calculations inside itself and combines those two variables area and the distance to the city and contributes to the price in output.

And therefore this first neuron doesn't really care about the variables bedrooms and age because it's focused on that specific thing.

Now let's not draw these lines for the synapses that are neglected

That's where the Power of the Neural Network comes from because you have many of these Neurons focusing on specific criteria.

Let's take one in the middle neuron. We've got three parameters feeding Area. Bedrooms and Age. So what exactly does that neuron is doing? Why this neuron through all of the thousands of examples has found out that the Area Bedrooms and Age, combination of those parameters is important?

The reason could be: in the area/city model this is true (i.e. low). People can get Larger properties with lots of bedrooms and the age of the property. People could be New couples with new jobs and better income or be larger families with old parents and grandchild. The common thing with those people, they don't care about the distance from the city.

Hence this specific neuron is looking for these three parameters (variables), as soon as that criteria is met the neuron fires up and the combination of these three parameters occurs.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_228_2.png)

So this is the Power of the Neural Network, it combines these parameters into a brand new parameter that helps with the evaluation of the property.

Let's look at another, at the very bottom one, for instance neuron can be picked up just one property: Age criteria can be built as some properties are more valuable than it is to. For example: a hundred old property can be a historic place and some Elite/Rich family want to buy for 'show of theirs'. Hence this neuron only aims to the Age property.

This can be part of rectify Rectify Activation function, because after some age limit, the value of the property gets higher.

And also a neuron can consider only one of bedrooms and distance. Another neuron can consider all of the variables. And so on. Since there can be so many options for the neurons. That's the power of the NNs.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_229_0.png)

So you can see these neurons and this hidden layer situation allows you to increase the flexibility of your neural network and allows you to look for very specific things and then in combination they predict the price.

That's the power of NNs. Like an ant, itself cannot build anything. But when you have 100000 ants they can build an Anthill together. And that's the situation here.

Each of these neurons by itself cannot predict the price. But together they have powers and predict the price and they can do out accurate job if trained properly, set up properly.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_229_1.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_229_2.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_229_3.png)

# 8.2.2 How an NN Learner

There are fundamentally different approaches to getting a program to what you want to do it.

- a) Hard coded source-code: where actually you tell the program's specific rules and what outcomes you want. Guide the program throughout the whole world and define all the possible options that the program has to deal with.

- b) Neural Networks: On the other hand you have neural networks where you automate the program to be able to understand what it needs to do on its. In this NN you provided, it tells what you want as outputs and lets it figure everything out its own.

Our goal is to create this which learns on its own. By avoiding trying to put in the rules.

```python
def create_nn(input_size, output_size):
    weights = np.random.randn(input_size, output_size)
    biases = np.random.randn(output_size)
    return weights, biases

weights, biases = create_nn(3, 1)
print(weights)
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_229_4.png)

For example: Distinguish between Dog and Cat.

- Option 1: You would use hard-coded program using different characters like the cat's ears, look out for type of nose, look out for type of color or etc.

- Option 2: On the other hand for a neural network you just code the neural networks architecture and then you point the neural network at a folder with images of all the cats and dogs, which are already categorized. From those images of cats and NN going to learn by itself what a cat or dog looks like.

- Once NN is trained up you give it a new image of a cat or dog it will be able to understand what it is.

# 8.2.3 PERCEPTRON

Here we have a very neural network with one layer. It is called a perception.

- y stands for the actual value
- Output value, it is predicted by the neural network.

And the perception was first invented in 1957 by Frank Rosenblatt and his whole idea was to create something can actually learn.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_230_0.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_230_1.png)

Let's see how our perception learns: Say we have some input values that have been supplied to the PERCEPTION(basic NN).

- Then the activation function is applied and we get an output.
- Now we are going to plot the output value and actual value on a chart.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_230_2.png)

To make our NN to be able to learn we need to compare the output value to the actual value. So we use a function called the cost function and is calculated as:

```
C = \frac{1}{2}(\hat{y} - y)^2
```

Now there are many ways of calculating cost function. There are many different cost functions that you can use. We used the simplest form here.

The cost function is telling us about the error that we have in our prediction. Our goal is to minimize the cost function because the lower the cost the closer output value and actual value.

# Additional Reading:

A list of cost functions used in neural networks, alongside applications

CrossValidated (2015)

Link:

http://stats.stackexchange.com/questions/1548739/a-list-of-cost-functions-used-in-neural-networks-alongside-applications

Next step once we've compared and calculated the cost function, now we're going to feed this information back into the Neural Network. The information going back into the NN and the weights get updated.

# 8.2.4 How an nn learns: Single Row of a Dataset

Example: Let's consider following screenshot of the data. From a dataset, of a row where we have: these independent variables- how long you study, how long you sleep and your quiz score. We are predicting the result you're going to get on an exam.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_231_1.png)
