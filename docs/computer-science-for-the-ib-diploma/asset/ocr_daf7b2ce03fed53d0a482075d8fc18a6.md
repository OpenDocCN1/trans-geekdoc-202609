Two questions to ponder. Is the optimized route perfect? And, does it matter?
To find the absolute most perfect solution would require testing 50! permutations; that is, over 30,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000 permutations. That is a lot of processing! The reality is, in scenarios such as this, rather than labouring for perfect, good enough will do. In the context of travelling between 50 cities, does it make sense to spend exponential time in calculations to save just a few minutes of travel?
This is an example of the type of problem that genetic algorithms can help solve.

# Step 1: Create an initial population

Assign each city a number and use a random number generator to create a randomized route. Do this for an initial population of 500 possible solutions (population size being one of the hyperparameters you may want to tune).

```
Python
def create_random_route():
    route = [n for n in range(0,50)]
    random.shuffle(route)
    return route

def create_initial_population():
    return [create_random_route() for n in range(0, 500)]
```

# Step 2: Create a fitness function to measure the performance of each member of the population

The obvious metric is to use the journey distance of the route; however, given the crossover function will give preference to those with a higher score for reproduction, it is necessary to use a fitness function that gives the highest scores for those routes with lowest distances.
One simple solution might be to calculate the fitness score by setting the distance as a fraction denominator, such as:

$fitness_i = \frac{1}{distance_i}$

An alternative approach used in the example code that follows is to use normalization to convert the data into a [0,1] range, where the 0 represents the highest distance and the 1 represents the smallest distance. The resulting normalized values are then used as an exponent to ensure that small differences in the normalized value, especially at the higher end, caused very large differences in fitness.

$normalized_i = \frac{distance_i - distance_{min}}{distance_{max} - distance_{min}}$

$fitness_i = 2^{100 * normalized(i)}$

The selection function is yet another hyperparameter for you to tune and experiment with for each given problem. The method outlined here was only selected after experimenting with half a dozen different possible approaches to see which produced the quickest results.