![](bbox=[0.132, 0.067, 0.723, 0.383])

**Figure 15.3 Common graphical representations of square and hexagonal self-organizing maps.** The top two maps show a grid of rectangular nodes that are each connected to four neighbors. The bottom two maps show a grid of hexagonal nodes that are each connected to six neighbors.

> **NOTE**
> 
> SOMs were created by a Finnish computer scientist called Teuvo Kohonen, and so you will sometimes see SOMs described as *Kohonen maps*. The SOM algorithm has been so popular, Professor Kohonen is the most highly cited Finnish computer scientist of all time!

Once the map has been created, the next step is to randomly assign each node a set of *weights*.

# 15.1.2 Randomly assigning weights, and placing cases in nodes

In this section, I’ll explain what I mean by the term "weights", and what they relate to. I’ll show you how these weights are randomly initialized for every node in the map.

Imagine we have a dataset with three variables, and we want to distribute the cases of this dataset across the nodes of our map. Eventually, we hope the algorithm will place the cases in the nodes such that similar cases are in the same node or a nearby node, and that dissimilar cases are placed in nodes far away from each other.

After the creation of the map, the next thing the algorithm does is to randomly assign each node a set of weights, one weight for each variable in the dataset. So for our example, each node has three weights because we have three variables. These weights are just random numbers, and you can think of them as guesses for the value of each of the variables. If this is hard to visualize, take a look at figure 15.2. We have a dataset containing three variables, and we are looking at