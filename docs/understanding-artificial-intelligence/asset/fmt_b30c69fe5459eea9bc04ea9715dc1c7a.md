
The algorithm doesn’t stop there. On the next trip, the agents go out on the road again, but this time, instead of choosing their route completely at random like the first time, they’re going to take notice of the pheromones, like the ants! When they have to choose the next point in their route, they look at the values shown on the connections between the current city and the other cities. They choose the next destination at random by giving a higher probability to the cities that have connections with the lowest values. For example, an agent who is in Marseille and still has to visit Toulouse and Nantes is going to look at the weights for the Marseille-Toulouse connection and Marseille-Nantes. If the weight for Marseille-Toulouse is smaller than Marseille-Nantes, it’s more likely the agent will choose Toulouse.

![image](images/inline8_3.jpg)

## [THE MORE THE MERRIER!](#contents.xhtml#toc2_79)

It’s easy to make these random selections on a computer. All we have to do is compare numbers, do some addition, and find some averages. All this goes really fast, and our agents are going to travel across the graph in no time at all. Then we do it again: each agent records its distance in the cells, the program calculates the averages, and then everyone does it again.

For the algorithm to work well, as with the ants, the pheromones need to evaporate a little, but not right away. For this, the program stores the previous trip’s average in the cell, along with the values provided by the agents for this trip. This way, if all the ants have gone every which way during a trip, there will still be some traces left on the right path.

After a few trips, the connections corresponding to the best paths will have better (pheromone) values than the others, and the agents will almost exclusively take these paths, except a few adventurous agents whose random selections lead them down the wrong path. This is just like a column of ants. There are always one or two who take a long detour to make sure a piece of sugar hasn’t accidentally fallen off to the side somewhere.

## [THE SOLUTION EMERGES](#contents.xhtml#toc2_80)

In a multi-agent system, the solution gets built even though the algorithm does not explicitly describe how it’s supposed to be built: no one has told the agents they had to find the shortest path. We’re simply asking them to flip a coin when they move about and to write some numbers down.

For computer scientists, this phenomenon is known as the `emergence` of the solution. The programmer has given the agents some rather basic behaviors (here, choose a solution more or less at random by looking at what your buddies did on the previous trip), and a solution gradually emerges based on the calculations and interactions among the system’s agents.

![image](images/inline8_4.jpg)

By contrast, with the Tabu method or the evolutionary algorithms we saw in the previous chapters, there is an evaluation and selection function that guides the program’s choice. And even in the greedy algorithm, the heuristic is clearly described. Here, everything happens as if there were no heuristic at all and the agents found the solution all by themselves.

Obviously, that isn’t the case at all. The heuristic is well hidden, but it’s there: the agents have to inform each other about the length of their respective routes. It is, indeed, the humans who figured out which information the bits of program needed to exchange to build the solution.

## [THE SOLUTION TO ALL OUR PROBLEMS?](#contents.xhtml#toc2_81)

Just like evolutionary algorithms, greedy algorithms, or graph paths, multi-agent systems have numerous applications. The main advantage of this method is that there is no need to describe all connections between the different parts of the algorithm. The solution can be developed little bit by little bit, with each agent only focusing on its part of the problem. This method is called `distributed artificial intelligence` because the task of calculating the solution is spread out among many different agents.

Today, we use multi-agent systems in factories to control the inflow of raw materials in production chains; in telecommunications systems to coordinate network communications operations without using a central controller; and even in electric network management systems to balance supply and demand. These have become much more widespread with the advent of alternative energies (for example, wind and solar) that are not “stable” and require the network to adapt continuously. Agents that resolve the problem locally and then coordinate with other network nodes are particularly well suited for this task.

However, agents are not well suited for every type of problem: this AI technique works well only for certain types of problems in which the bits of program can make their own separate calculations, as with the traveling salesman problem.

There is no AI technique to do the cooking, wash the dishes, and go shopping. To solve each problem, we have to choose the right technique… and also provide the right heuristics!

| [A Bit of Tidying Up](#contents.xhtml#toc1_82)[*Understanding How a Machine Learns to Classify*](#contents.xhtml#toc1_82) || [9](#contents.xhtml#toc1_82) |

| --- | --- |

Evolutionary algorithms and multi-agent systems are two examples of artificial intelligence algorithms for which computer scientists drew inspiration from natural phenomena. There are others. Neural networks have been a big success since 2010, and they are also inspired by nature. However, before we learn how they work, we first need to get through another chapter.

## [FIND THE ODD ONE OUT!](#contents.xhtml#toc2_83)

Among the skills that make use of human intelligence, there is one that machines and data processing cannot do without. It is the ability to classify objects – that is, to group or separate elements based on their features.

Human beings do not have much difficulty distinguishing between birds and mammals. We learn early on how to group things that look alike: ducks, geese, and waterfowl all look like each other more than like a cat or a lion. This skill allows us to describe the personality of our friends (shy, exuberant, etc.) without needing to resort to complex reasoning.

However, classification is not as easy as it might seem.

Let’s consider the five animals below: A dog, a cat, a duck, a cow, and a lion.

![image](images/inline9_1.jpg)

If you had to divide them into two clusters of similar animals, how would you group them? Naturally the cat and the lion… perhaps with the dog? And the cow and the duck together? Or would you leave the duck out, since it’s not a mammal? But you could also think of the lion as the odd one out: it’s the only wild animal. Or perhaps the cow: it’s the only animal humans get milk from.

As you can see, grouping objects based on their similarities isn’t always easy.

## [FROM ANIMALS TO GENES](#contents.xhtml#toc2_84)

Since the 1980s, computer scientists have taken an interest in algorithms capable of doing this same type of categorization. As an example of a concrete application of this research, biologists use computers to analyze DNA sequences and find genes shared by different species. This allows them to understand how several different DNA sequences contribute to the way a certain genetic character is expressed in a given species.

Each DNA sequence contains billions of A, C, G, and T elements. It is impossible to analyze them by hand. To accomplish this work, researchers use machines capable of grouping similar genetic data. This problem isn’t that much different from the animals, except the amount of data is enormous.
