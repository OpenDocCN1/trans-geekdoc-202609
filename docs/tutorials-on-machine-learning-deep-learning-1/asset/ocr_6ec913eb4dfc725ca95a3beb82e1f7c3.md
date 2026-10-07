Directed Models: Now, even though the SOM is an unsupervised type of deep learning model, but ANN, CNN, RNN & SOM all these four are actually directed models.

There is a direction in which the model operates. For example in SOM, we've got the input-data and then the information goes through the nodes creates an output map.

![](bbox=[0.106, 0.107, 0.893, 0.193])

ANN, CNN, RNN & SOM all these four are Directed Models

Boltzmann machines (Undirected Models): Boltzmann machines are Unsupervised Deep Learning Model and it is an Undirected Model. All kind of Boltzmann machines are undirected models.

In the diagram, notice that there are no arrows in the connections between nodes, all these connections both ways.

Let's have a bit closer at a Boltzmann machine (BM), and understand what's going on. Following is a Boltzmann machine (BM), we got hidden nodes in red and got visible nodes in blue (Actually there is no difference between hidden nodes and visible nodes. In BM all nodes connected to each other. For learning purpose we used two colors.).

Here, we've got hidden nodes (input nodes) at the bottom, and we've got seven hidden nodes.

![](bbox=[0.259, 0.477, 0.74, 0.655])

# Three things to notice:

+   [1]. This model doesn't have each other. There is an input layer, there's a hidden layer, but no output layer.

+   [2]. All nodes connect to each other. Everything is connected (hyper connected) to everything, there is no specific layering per say.

+   [3]. There is no direction in these connections (Undirected). All connections in BM are bi-directional. The connection has both ways.

The Visible Nodes (input nodes) are connected each other: Notice that the visible nodes are all connected between each other,

What's the point of row of data and you put it to the input and the node and there's no point in these connections between visible nodes. You're not going to be adjusting the weights or training, because that data is fixed, right?

And that's it! Boltzmann machines are fundamentally different to all algorithms.

Boltzmann machines don't just expect data they also generate data. They generate information in all available nodes, regardless of whether there's an input or a hidden node. For a Boltzmann machine all of these nodes are the same.

For a BM this thing is a system, it's generating states of this