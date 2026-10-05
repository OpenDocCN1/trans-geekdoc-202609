# 9.4.2 The Hopfield model

Steven Grossberg pioneered much of the field of recurrent neural networks and their relation to cognitive neuroscience in the early 1970s. We will discuss a specific example that has been popularized by John Hopfield. In the Hopfield model, each node receives an input and can communicate its activity to all other neurons. Hence, this is a special form of a conditional random field where all the output neurons interact. Such a network is illustrated on the left-side in Fig. 9.10. All the neurons in the network receive input and communicate the output. Thus, all the neurons in this network are visible nodes. In the next section we discuss the more general case with hidden nodes.

![](bbox=[0.196, 0.303, 0.782, 0.467])

Fig. 9.10 A recurrent network with only visible nodes and symmetric lateral connections.

This type of networks has received a great deal of attention in neuroscience. It has been known for some time that an area of the archicortex the hippocampus in humans is important for some form of memory, in particular episodic memory, the memory of specific events. This area has interesting structures, including an area called CA3 which has a lot of connections. In 1971, David Marr proposed an explanation for such networks, suggesting that they could facilitate associative memory, the memory of recall that could be triggered by partial cubes. The Hopfield model is a good abstraction of this kind of memory.

To demonstrate associative memory, we run a small experiment with binary neurons. We choose to represent these states as -1 and 1. We can easily transform the network to other state representations, but it turns out that this representation helps with the compactness of the program. We use hard threshold units in this example with the “update rule"

```
$s(t + 1) = sign(ws(t - 1)).
```

The sign function returns -1 if the element is less than or otherwise 1. This is just another version of a threshold perceptron. We now want to store some patterns $x^k$ in this network. The new part is how we train this network. We use here the

```
Hebb rule: $w = \sum_{\mu} xx'$
```

This rule has a long history. It was verbally suggested by Donald O. Hebb in the 1940s and formalized by Eduardo R. Cianello in 1961. This rule basically specifies that