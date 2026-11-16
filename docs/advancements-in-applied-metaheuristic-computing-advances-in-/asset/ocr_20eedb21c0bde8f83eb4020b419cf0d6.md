# Figure 10. Evolution during the GA of mean min max objective function (ch130, JMPX)

![](bbox=[0.14, 0.15, 0.85, 0.41])

For the Moroccan context, Figure 13 shows a simulation of our algorithm, on a real instance with a real data set of the Moroccan road network. The concept of Volunteered Geographic Information has recently emerged with the new Web 2.0 technologies. The OpenStreetMap project is currently the most significant example of a VGI-based system (Girres & Touya, 2010). It aims to produce free geographic databases using the contributions of Internet users.

We cleaned the data and organized it for use, and then transformed it into a road graph in QGIS (Tsou & Smith, 2011).

We choose 128 of the important and largest cities in Morocco, in terms of population, and therefore the most demanding in terms of goods. Then we run a Dijkstra algorithm to find the shortest paths between each of the selected cities on the road graph, and then we have launched the genetic algorithm with that input data to optimize the overall path.

# CONCLUSION

This paper presented a new genetic crossover operator for solving the TSP using GAs. The new method is tested and compared to other conventional crossover operators and methods: Partially matched crossover (PMX), Edge recombination Crossover (ERX) and r-opt Heuristic, To conclude on the overall performance of