# Feedforward neural networks on massively parallel architectures 65

![](bbox=[0.076, 0.075, 0.923, 0.396])

# 3.6 Folded ClosNN

In multilayer NNs, one ClosNN is placed between any two subsequent layers. As an instance, for a three-layer NN, we need two ClosNN networks; one ClosNN to connect the input layer to the hidden layer and another one to connect the hidden layer to the output layer. In this way, for an NN with $n$ layers, we need $n-1$ ClosNN networks. In order to make ClosNN scalable, we propose to employ the bidirectional folded Clos architecture.

In a folded Clos, the entire network is folded along the middle stage. In other words, folded Clos is a hierarchical topology in which the first-stage and third-stage switches are combined and the unidirectional switches are replaced with bidirectional ones. This architecture benefits from the symmetry of Clos topology, while it further reduces the hop count.

After folding, as depicted in Figure 3.7, ClosNN’s switches are arranged in two layers: leaf and spine. The leaf layer integrates the input-stage and output-stage switches that are connected to both input and output of the network. In the PE side, leaf switches are directly connected to the PE (neurons) using bidirectional ports ($n$ inputs and $n$ outputs). In the network side, leaf switches are connected to m spine switches (the network has $m$ middle-stage switches) using $m$ bidirectional ports. Each switch has $r$ bidirectional ports, that is, equivalent to the middle-stage switches of the baseline Clos with $r$ unidirectional input and $r$ unidirectional output ports (Figure 3.7).

Several prior works have shown the advantages of the bidirectional folded Clos in terms of floor plan efficiency and circuit-level optimizations [34–36,40]. There is no