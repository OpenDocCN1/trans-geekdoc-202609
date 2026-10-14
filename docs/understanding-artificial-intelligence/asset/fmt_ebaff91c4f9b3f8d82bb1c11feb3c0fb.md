
The principle of evolutionary algorithms, then, is the following. We choose two random solutions from our cluster (the “herd” of solutions) and we make new solutions based on these two points. And we do this over and over many times. Our total number of solutions grows large with the initial solutions and all the solutions generated from other solutions.

Now, we eliminate the weakest solutions (this is the hard law of natural selection) to thin out our cluster a little. Theoretically, the solutions of this new population should be of a higher quality than the initial cluster. A few solutions from the first cluster, the best ones, will be kept. The bad ones will be eliminated. Similarly, from among the “children solutions,” only the best are kept. The bad solutions are eliminated.

Then, the evolutionary algorithm gets to work on this new cluster, reproducing and selecting, so it can continue to improve the population. After some time, we should have only the very best solutions!

![image](images/inline7_1.jpg)

## [YOU’VE GOT TO START SOMEWHERE](#contents.xhtml#toc2_69)

To use this type of algorithm, we have to follow three steps:

```
  1. Build an initial set of solutions.
```

```
  2. Choose pairs of solutions to make new solutions.
```

```
  3. Eliminate the weakest solutions and repeat step 2.
```

Each step presents its own difficulties. The first among them is to make a cluster with lots of different solutions. How is this possible? It took us an entire chapter to understand how to make one single solution!

Honestly, this depends on the problem in question. With the traveling salesman problem, it is very easy to build lots of solutions: all we have to do is to randomly choose one city after another. Limoges, Marseille, Bordeaux, Toulouse, Nantes, and there you have it! Done! No need to think. An algorithm that produces a solution at random can be written as follows:

```
  Let L be the cluster of cities.
```

```
  Randomly choose a city in L.
```

```
  Remove this city from L.
```

```
  Repeat.
```

It’s very fast: for a graph with a hundred cities (*N* = 100), we can produce a thousand solutions in under a millisecond on one of today’s computers!

Of course, there is no guarantee the randomly chosen solutions will be of good quality. Just the opposite, it’s very likely they’ll be totally worthless. But that doesn’t matter: the algorithm will see to it that they evolve into something better.

## [TWO BEAUTIFUL CHILDREN!](#contents.xhtml#toc2_70)

Remember the principle: as with the giraffes, the individuals (solutions) are going to reproduce and make babies, and only the best of them will survive under the hard law of natural selection in the traveling salesmen jungle.

You’re probably wondering how “solutions” that are basically just numbers in a computer can reproduce and have children. Why not have an eHarmony for solutions, while we’re at it? You are right. This is just an illustration. We’re going to choose solutions two by two at random and “mix” them, just like when two living beings reproduce and combine their DNA.

Let’s look at an example. Imagine that we have to visit 15 cities, which we will name A, B, C, D, E, F, G, H, I, J, K, L, M, N, and O. Now, let’s choose two solutions at random: Dad-solution, whose route is ABEDCFHGJMNLKIO, and Mom-solution, whose route is DFKNMJOACBEIGLO.

To build a “child” solution, we take the first cities in the order indicated by the first solution (the one we named “Dad”) and the following cities in the one named “Mom.”

We choose, always at random, the initial number of cities. For example, we decide to keep Dad’s first six cities: ABEDCF. Next, we take Mom’s cities in order (except for any we’ve already visited): KNMJOIGLO. This gives us the following solution:

ABEDCF KNMJOIGLO

And that’s it! This operation, called a crossover, is also written as an algorithm: the parents are the clusters from which we take elements to put in the “child” cluster. If the algorithm is well written, it requires very few operations and thus allows us to develop many solutions by choosing couples of parents. If we come back to our example of one thousand solutions with one hundred cities each, by applying the crossover algorithm to the parents chosen at random one thousand times, we get a whole new generation of one thousand “child” solutions in under a millisecond!

![image](images/inline7_2.jpg)

## [A LITTLE MORE RANDOMNESS](#contents.xhtml#toc2_71)

The evolutionary algorithm can also use genetic mutations, just like in real life. From time to time (at random again!), one of the children “mutates,” inverting two cities. This little operation allows the algorithm to find good solutions faster, as long as these mutations remain rare. This generates solutions that are not consistent with the parents: if the result is catastrophic, the mutation will not be kept. But if it is of good quality, the mutation will benefit this piece of solutions in future generations!

An evolutionary algorithm is, thus, simply a method for exploring a solution space in a shrewd way. There is no natural selection because our “individuals” are just numbers in a machine. When you “mix” two solutions to make a new one, you’re just choosing a new point in the solution space that has traits in common with the initial solutions.

If your two initial solutions are good solutions – in other words, relatively short routes for the traveling salesman problem – you have two possibilities. One possibility is that the route proposed by the “child” solution isn’t as good, in which case it will be eliminated at the end of the trip. The other possibility is that the child’s route is better because one of the parent’s routes helped shorten the other one, in which case you keep it. This is how your population progresses.

![image](images/inline7_3.jpg)

The mutation, for its part, behaves like the Tabu search we saw at the end of the previous chapter. It allows us to explore the neighborhood in the solution space and look for new routes for our traveling salesman, without losing everything that has been calculated previously.

Researchers have mathematically shown that this type of algorithm works well. With enough trips, you get a very good solution – provided, of course, you programmed it right!

## [SO, WHAT IS THIS GOOD FOR?](#contents.xhtml#toc2_72)

Like the Tabu search, evolutionary algorithms are what we call *metaheuristics* because they work in the solution space, not in the state space. Like all heuristics, they don’t seek the best solution: they explore just a very small part of the space as best they can to find a “good” solution within the time available. And, when you add it all up, they choose a solution that is nothing more than a heuristic: “If you pass through Nantes, Bordeaux, Toulouse, and, then, Marseille, this shouldn’t be too bad.”

The advantage of these methods is that they can be used for a whole bunch of different problems, no matter how the solution is built. This makes them very powerful! Metaheuristics are widely used in logistics: optimizing the routes of a fleet of trucks, managing air traffic, improving how a nuclear reactor is loaded… this is just a small sample of evolutionary algorithms and metaheuristic search methods.

There are many more examples, such as 3G mobile network optimization (i.e. where to place antennas to ensure the best possible coverage) or even the automated space antenna developed by NASA engineers, which was computed automatically using an evolutionary algorithm. The question we have yet to answer is “How do we maximize the reception?” The computer’s answer is this small, twisted piece of iron wire. Who else could have invented this, if not a computer?

![image](images/inline7_4.jpg)

## [THIS DOESN’T SOLVE EVERYTHING, HOWEVER](#contents.xhtml#toc2_73)
