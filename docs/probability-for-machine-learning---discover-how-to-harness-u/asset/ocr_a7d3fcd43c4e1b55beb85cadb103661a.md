across the final row of the table. This comes out to be about 0.166 or 16.666% as we may intuitively expect.

Importantly, if we sum the probabilities for all cells in the table, it must equal 1.0. Additionally, if we sum the probabilities for each row, then the sum of these sums must equal 1.0. The same if we sum the probabilities in each column, then the sum of these sums too must equal 1.0. This is a requirement for a table of joint probabilities. Because the events are independent, there is nothing special needed to calculate conditional probabilities.

$P(A|B) = P(A)$ (5.7)

For example, the probability of rolling a 2 with dice1 is the same regardless of what was rolled with dice2.

$P(\text{dice1} = 2|\text{dice2} = 6) = P(\text{dice1} = 2)$ (5.8)

In this way, conditional probability does not have a useful meaning for independent random variables. Developing a table of joint probabilities is a helpful tool for better understanding how to calculate and explore the joint and marginal probabilities. In the next section, let’s look at a more complicated example with dependent random variables.

# 5.4 Probabilities of Weather in Two Cities

We can develop an intuition for joint and marginal probabilities using a table of joint probabilities of events for two dependent random variables. Consider the situation where there are two cities, city1 and city2. The cities are close enough that they are generally affected by the same weather, yet they are far enough apart that they do not get identical weather. We can consider discrete weather classifications for these cities on a given day, such as sunny, cloudy, and rainy. When it is sunny in city1, it is usually sunny in city2, but not always. As such, there is a dependency between the weather in the two cities. Now, let’s explore the different types of probability.

# 5.4.1 Data Collection

First, we can record the observed weather in each city over twenty days. For example, on day 1, what was the weather in each, day 2, and so on.

```
Day | City1 | City2
1   | Sunny | Sunny
2   | Sunny | Cloudy
3
...
```

Listing 5.2: Example of collected data for the weather in two cities.

The complete table of results is omitted for brevity, and we will make up totals later. We can then calculate the sum of the total number of paired events that were observed. For example, the total number of times it was sunny in city1 and sunny in city2, the total number of times it was sunny in city1 and cloudy in city2, and so on.

| City 1 | City 2 | Total |
|---|---|---|
| sunny | sunny | 6/20 |