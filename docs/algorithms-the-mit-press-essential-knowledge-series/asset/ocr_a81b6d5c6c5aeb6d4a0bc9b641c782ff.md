a multiset—that is, a set that allows for multiple instances
of its elements. In the same way, the Königsberg graph is
not really a graph but rather a multigraph.

# From Graphs to Algorithms

The definition of a graph is wide so that it can encompass
everything that can be represented as things connected
to other things. The graph may have some relevance to
the topology of a place, but the nodes and links may have
nothing to do with points in space.

A social network is an example of such a graph. In a
social network, nodes are social actors (these may be indi-
uals or organizations), and the links represent interac-
tions between them. The social actors may be real-world
actors, and the links may be their collaborations in films.
The social actors can be us, and the links may be our con-
nections to other people in a social network application.
We can then use social networks to find communities of
people, starting from the premise that communities are
formed by people who interact with each other. There exist
algorithms that are able to find efficiently communities in
graphs with millions of nodes.

The edges in the Königsberg graph are not directed,
meaning that we can traverse both ways; for exam-
ple, we can go from A to B and B to A. The same goes for