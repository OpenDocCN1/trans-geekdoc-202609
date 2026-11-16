# Chapter 31

# Graph learning

# 31.1 Learning tree structures

Since the problem of structure learning for general graphs is NP-hard [Chi96], we start by considering the special case of trees. Trees are special because we can learn their structure efficiently, as we discuss below, and because, once we have learned the tree, we can use them for efficient exact inference, as discussed in **??**.

# 31.1.1 Directed or undirected tree?

Before continuing, we need to discuss the issue of whether we should use directed or undirected trees. A directed tree, with a single root node \(r\), defines a joint distribution as follows:

\(p(\boldsymbol{x}|T) = \prod_{t \in V} p(x_t | x_{\text{pa}(t)})\) (31.1)

where we define \(\text{pa}(r) = \emptyset\). For example, in Figure 31.1(b-c), we have

\(p(x_1, x_2, x_3, x_4 | T) = p(x_1)p(x_2|x_1)p(x_3|x_2)p(x_4|x_2)\) (31.2)

\(= p(x_2)p(x_1|x_2)p(x_3|x_2)p(x_4|x_2)\) (31.3)

We see that the choice of root does not matter: both of these models are equivalent.

To make the model more symmetric, it is preferable to use an undirected tree. This can be represented as follows:

\(p(\boldsymbol{x}|T) = \prod_{t \in V} p(x_t) \prod_{(s,t) \in E} \frac{p(x_s, x_t)}{p(x_s)p(x_t)}\) (31.4)

where \(p(x_s, x_t)\) is an edge marginal and \(p(x_t)\) is a node marginal. For example, in Figure 31.1(a) we have

\(p(x_1, x_2, x_3, x_4 | T) = p(x_1)p(x_2)p(x_3)p(x_4) \frac{p(x_1, x_2)p(x_2, x_3)p(x_2, x_4)}{p(x_1)p(x_2)p(x_2)p(x_3)p(x_2)p(x_4)}\) (31.5)

![](bbox=[0.22, 0.745, 0.79, 0.835])

Figure 31.1: An undirected tree and two equivalent directed trees.