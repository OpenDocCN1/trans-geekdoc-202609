To give a practical demonstration, consider the following scene. Two people are sitting at a bar, the camera is a medium shot of both characters who are equally in the frame. One of the actors (a female) is facing the camera. The other (a male, possibly a love interest) is attempting to appease the female, as in a prior scene, the female had seen the male with another woman.

If you have the partial graph as seen in Image 12.1, what would be considered for the next node expansion probability?

![](bbox=[0.112, 0.23, 0.888, 0.5])

IMAGE 12.1 A simple graph representation of a scene where a woman sits at a bar facing the camera and a man approaches to enact dialogue – dashes represent potential node expansions.

From the scene context, we know that there are two characters in the scene, so the probability of expanding the graph with another actor would be high. Imagine that the graph expansion maximum probability is that another actor should be added to the scene, and then the proceeding graph expansion would be related to that actor's properties. In Image 12.1, it can be seen that multiple graph expansions are likely for properties of the second actor. Things like where they are in the scene, what direction they are facing, what age and sex they are, and the like.

Now with a mechanism for constructing probable graphs as a series of graph expansion probabilities, the discussion needs to turn to determining the probabilities in the first place.

A graph neural network (GNN) is used for this. GNNs are a flexible method of learning across graph representations. In this implementation, the Pytorch Geometric API (https://github.com/pyg-team/pytorch_geometric) was used to derive a graph attention network trained to learn the probabilities of graph expansions.

At model training time, you can simply load the OpenTimelineIO timeline for a given movie and parse the information for each shot in the movie. In essence, the GNN learns a matrix of probabilities given a set of input node values (the graph structure to this point) and the set of mask values. The mask allows you to invalidate