# What’s a Point, and What’s a Penalty?

In modularity maximization you give yourself one point every time you cluster two nodes that share an edge in the adjacency matrix. You get zero points every time you cluster those that don’t.

Easy.

What about penalties?

This is where the modularity maximization algorithm really gets creative. Consider again the Friends graph, originally pictured in Figure 5.1.

Modular maximization bases its penalties for putting two nodes together on one question:

If you had this graph and you erased the middle of each edge and “rewired” it a bunch of times at random, what is the expected number of edges you’d get between two nodes?

That expected number of edges is the penalty.

Why is the expected number of edges between two nodes the penalty? Well, you don’t want to reward the model as much for clustering people based on a relationship that was likely to happen anyway because both parties are extremely social.

Instead, we want to know how much of that graph is an intentional relationship and connection and how much of it is just because, “Yeah, well, Chandler is connected to a lot of people, so odds are Phoebe would be one of them.” This means that edges between two highly selective individuals are “less random” and worth more than edges between two socialites.

To understand this more clearly, look at a version of the Friends graph in which I’ve erased the middle of each edge. These half-edges are called stubs. See Figure 5.23.

![](bbox=[0.134, 0.59, 0.38, 0.8])

Figure 5.23: Stubby Friends graph

Now, think about wiring the graph up randomly. In Figure 5.24, I’ve drawn an ugly random rewiring. And yes, in a random rewiring it’s totally possible to connect someone to themselves if they have multiple stubs coming out of them. Trippy.