
Assume, however, a slightly different set of circumstances:

• `E` advertises `F` to `B` with a path of `[E]` and a metric of 100.

• `B` advertises `F` to `A` with a path of `[E,B]` and a metric of 100.

• `E` advertises `F` to `D` with a path of `[E]` and a metric of 50.

• `D` advertises `F` to `C` with a path of `[E,D]` and a metric of 50.

• `C` advertises `F` to `A` with a path of `[E,D,C]` and a metric of 50.

`A` has two paths, one with a metric of 100, and another with a metric of 50. Therefore:

• `A` will choose the higher of the two metrics, the path through `[E,B]`, and advertise this route to `C`.

• `C` will choose the higher of the two metrics, the path through `[E,B,A]`, and advertise this route to `D`.

• `D` will choose the higher of the two metrics, the path through `[E,B,A,C]`, and advertise this route to `E`.

• `E` will discard this route, as `E` itself is already in the path.

Hence, even if the metric overrides the path length at (almost) every node, no loop will form.

## The Multiple Metric Problem

Every algorithm discussed to this point has used a single metric to compute loop-free paths except path-vector, and path-vector uses two metrics in a very constrained way, with one always preferred over the other. The path, in fact, can be seen as a “tie breaker” that comes into play only when the primary metric, which does not relate to the path in any way (because it is not summed hop by hop in the network) fails to prevent a loop. Some protocols can use multiple metrics, but they will always combine these metrics in some way so only a single combined metric is used to find loop-free paths. Why?

In mathematical terms, all methods used to find a set of loop-free (or shortest) paths through a network are solvable in polynomial, or nonexponential, time—or rather, they are considered problems of the class `P`. There is a broader class of problems, containing `P`, that contains any problem solvable using a (theoretical) nondeterministic Turing machine. Among the NP problems, there is a set of problems considered NP-complete, which means there is no known efficient way to solve the problem; in other words, to solve the problem, every possible combination must be listed, and the best possible solution chosen from among this set.

The multiple metric problem is classified as NP-complete, and hence— while solvable—it is not solvable in any way lending itself to use in near- real-time communication networks.

## Disjoint Path Algorithms

Consider the problem of a medical procedure executed by a robot following the hands of a live surgeon halfway across the world. It is possible that making such a system work requires packets to be delivered from the sensors on the surgeon’s hands to the robot in near real time, in order, with little or no jitter, and absolutely no packets can be dropped. This example, of course, can be expanded to many different situations, including financial systems and other mechanical control systems where near-real-time packet delivery with no failures is required.

What is often needed in these situations is to transmit two copies of each packet and then allow the receiver to choose the packet best fitting the Quality of Service (`QoS`) and packet loss characteristics needed to support the application. All of the systems discussed so far, however, can find only one loop-free path, and potentially an alternate path (an LFA and/or an rLFA). The problem being solved, then, by disjoint path algorithms, is this:

How can paths be built through a network in such a way as to make certain they use the smallest number of overlapping resources (devices and links) as possible (hence are maximally disjoint, or maximally redundant)?

This section will begin by describing the concept of a two-connected network, and then consider two different (but seemingly related) ways of calculating disjoint topologies on two-connected networks.

### Two-Connected Networks

A two-connected network is any network in which there are at least two paths between a source and destination that do not use the same devices (nodes) or links (edges). There are points to pay attention to here:

• A network is two-connected in relation to a specific set of sources and destinations; most networks are not two-connected for every source and every destination.

• Small blocks of any given network may be two-connected for some sources and destinations, and these blocks may be interconnected by narrow one- or two-connected *choke points.*

**Note**

Choke points will play a major role in many different areas of network design, a topic considered in [Part III](#part3.xhtml#part3), “[Network Design](#part3.xhtml#part3).”

It is often easiest to understand two-connectedness through an actual example; [Figure 13-13](#ch13.xhtml#ch13fig13) shows a network marked out in blocks.

![Image](graphics/13fig13.jpg)

**Figure 13-13** *Two-Way Connected Network Example*

In *block A*, there are at least two different disjoint paths between `X` and `F`:

• `[X,A,B,E,F]` and `[X,C,F]`

• `[X,A,B,F]` and `[X,C,F]`

In *block B*, there is one pair of disjoint paths from `G` to `L`: `[G,K,L]` and `[G,H,L]`. There are no disjoint paths to `Z`, as this node is *single connected*. There are also no disjoint paths between `F` and `G`, as these two are single connected. The `[F,G]` link can be considered a choke point between these two topology blocks. It is not possible, in the network illustrated in [Figure 13-13](#ch13.xhtml#ch13fig13), to compute two disjoint paths between `X` and `Z`.

#### Suurballe’s Disjoint Path Algorithm

In 1974, J. W. Suurballe published a paper describing how to use multiple runs of `Dijkstra`’s `SPF` algorithm to find multiple disjoint topologies in a network.^[2](#ch13.xhtml#ch13fn-2) The algorithm essentially computes `SPF` once, removes a subset of the links in use on the `SPT`, and then computes a second `SPF` across the remaining links. Suurballe’s algorithm is harder to explain than to illustrate in an example because of its reliance on the directional nature of the links computed through `SPT`; [Figure 13-14](#ch13.xhtml#ch13fig14) through [Figure 13-18](#ch13.xhtml#ch13fig18) are used as examples.

![Image](graphics/13fig14.jpg)

**Figure 13-14** *Using Suurballe’s Algorithm for Finding Disjoint Paths, Step 1*

![Image](graphics/13fig15.jpg)

**Figure 13-15** *Using Suurballe’s Algorithm for Finding Disjoint Paths, Step 2*

![Image](graphics/13fig16.jpg)

**Figure 13-16** *Using Suurballe’s Algorithm for Finding Disjoint Paths, Step 3*

![Image](graphics/13fig17.jpg)

**Figure 13-17** *Using Suurballe’s Algorithm for Finding Disjoint Paths, Step 4*

![Image](graphics/13fig18.jpg)

**Figure 13-18** *A Depth First Search Tree Example*

[Figure 13-14](#ch13.xhtml#ch13fig14) shows the state of the operations after the first `SPF` run has completed and the initial `SPT` is computed. Note the directional arrows on the links; it is not common to think about an `SPT` as being directional, but in reality it is, with each link oriented away from the source, or the root of the tree. When `F` computes a tree back toward `X`, it would also produce a directional tree with the arrows pointing in the opposite direction.

Edges (or links) on the `SPT` are called tree edges, and edges (or links) not on the resulting `SPT` are called nontree edges. In [Figure 13-14](#ch13.xhtml#ch13fig14), the tree edges are marked in solid black with directional arrows, and the nontree edges are lighter gray dashed lines.

The second step is shown in [Figure 13-15](#ch13.xhtml#ch13fig15).
