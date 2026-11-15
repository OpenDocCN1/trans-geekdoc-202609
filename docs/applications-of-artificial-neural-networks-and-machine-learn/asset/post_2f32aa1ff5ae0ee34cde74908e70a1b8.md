
## 17.3 Hybrid Method for Subdomain

A finite element domain D can be divided into two subdomains D1 and D2 employing an expansion process for which their interface is shown by S-S, Fig. 17.2a.

Two subdomains R2 and R3 with equal number of nodes (|R2| = |R3|) are separated from subdomains D1 and D2, respectively, using a graph theoretical method as illustrated in Fig. 17.2b. Let n be the total number of nodes of the model, and i be the total number of nodes in each subdomain R2 and R3, respectively. Then the nodes of elements in subdomain R1 will be m = n - 2i.

In the first stage, two subdomains R2 and R3 with equal number of nodes are departed from the overall domain. In the second stage a neural network method is applied to the clique graph of R1, and the corresponding domain is bisected and each half is added to the adjacent R2 and R3 subdomains, resulting in the partitioning of the whole domain.

For the purpose of initial partitioning of the whole domain, the Greedy algorithm [2] can be employed. In this algorithm first the pseudo peripheral nodes r2 and r3 of the partial clique graph of the FEM is obtained. The shortest route trees (SRT) are routed from these two nodes and the nodes are added to form R2 and R3 contour by contour (level). The generation of trees is halted as soon as a suitable number of nodes are assigned to R2 and R3.

It should be noted that if the simple SRT method is used for initial partitioning of the domain, then the unrestricted growth of the trees yields the suboptimal solution, as shown in Fig. 17.3.

A number of examples studied using a graph theoretical algorithm for initial partitioning have shown that if the following restriction is imposed, then the same results will be obtained for the present and the pure neural networks method:

$$DS_2 + DS_3 \le (depth - width) \quad (17.1)$$

Fig. 17.2 Graph based domain decomposition. a) A domain divided into two subdomains. b) A domain divided into three subdomains

![](img/4048998719320644ee88964326fd7995_339_0.png)

Fig. 17.3 Initial decomposition of a rectangular domain by an expansion method

![](img/4048998719320644ee88964326fd7995_340_0.png)

where DS2 and DS3 are the number of contours of the trees generated from roots r2 and r3, respectively, and the ‘depth’ and ‘width’ are the same as the height and width of the trees, respectively, as defined in Ref. [2].

The algorithm for the present hybrid method can be summarized as follows:

- 1. Construct the partial clique graph of the finite element model using a suitable topological transformation [2].
- 2. Find two pseudo peripheral nodes of the partial clique graph.
- 3. Generate two SRTs routed from these two nodes and form two subdomains R2 and R3 with equal number of nodes. The remaining subdomain is called R1.
- 4. Use the neural networks method of the next section and decompose R1 into two subdomains.
- 5. Add each part of the bisected R1 to the adjacent R2 and R3 subdomains, resulting in the partitioning of the whole domain.

Neural networks for the bisection of FEMs. Combinatorial optimization problems arise in many areas of science and engineering. Unfortunately, due to the NP (non-polynomial) nature of these problems, the computational effort required increases with the size of the problem. Most computational methods that have so far been developed which generally yield good solutions to these problems rely on some form of heuristics. Artificial neural networks (ANNs) make use of highly interconnected networks of simple neurons or processing units which may be programmed to find approximate solutions to these problems. They are also highly parallel systems and have significant potential for parallel hardware implementation.

### 17.3.1 Mean Field Annealing Networks

The roots of mean field annealing (MFA) networks are in the field of statistical physics which combines the features of Hopfield neural network and simulated annealing. MFA is a deterministic approach which essentially replaces the discrete degrees of freedom in a simulated annealing problem with their average values as computed by the mean field approximation.

### 17.3.2 Mapping the Bisection Problem onto the Neural Network

The problem of bisecting meshes may be mapped onto a feedback type neural network and may be defined by an objective function in the form of the Liapunov function given as:

$$E(S) = -\frac{1}{2} \sum_{i=1}^N \sum_{j=1}^N T_{ij} s_i s_j + \sum_{i=1}^N I_i s_i$$

where \( T_{ij} \) is the connecting weights matrix, \( s_i \) is the state of the \( i \)th neuron, \( s_j \) is the state of the \( j \)th neuron, and \( I_i \) is the bias. It may be assumed that the \( T_{ij} \) matrix is symmetric and does not allow self-interaction.

A binary unit of \( s_i = +1 \) or \( s_i = -1 \) is assigned to each node of the mesh defining which partition the node is to be assigned.

The connectivity of the nodes is encoded in the \( T_{ij} \) matrix in the form of

$$T_{ij} = \begin{cases} 1 \text{ if a pair of nodes are connected by an edge} \\ 0 \text{ otherwise} \end{cases}$$

With this terminology, the minimization of the first term of Eq. (17.2) will maximize the connectivity within a bisection while minimizing the connectivity between the bisections. This has the effect of maximizing the boundary. However, using this term alone as the cost function forces all the nodes to move into one bisection, thus a penalty term is applied which measures the violation of the equal sized bisection constraint [7–9]. Therefore the neural network objective function for the mesh bisection is of the form of

$$E(S) = -\frac{1}{2} \sum_{i=1}^N \sum_{j=1}^N T_{ij} s_i s_j + \frac{\alpha}{2} \left( \sum_j s_j \right)^2$$

where \( \alpha \) is the imbalance parameter which controls the bisection ratio.

The mean field equation for bisection is given by:

$$v_i = \tanh \left( \sum_{j=1}^N (t_{ij} - \alpha) \frac{v_j}{T} \right).$$ (17.4)

where $T$ is the temperature. This equation is used to compute a new value of u\(_i\) asynchronously. Initial values for the elements in vector V are assigned using small continuous random values. The temperature is lowered using a cooling factor (0.90) after one complete iteration of Eq. (17.4).

At the beginning of the optimization process, the spins (state of neurons) average stay at or near zero indicating that the bisection is maximally disordered. As the temperature is decreased, the system reaches a critical temperature where the spins begin to converge, causing each element of the mesh to move into one or another of the two bisections. At sufficiently low temperatures, the state of each neuron reaches a value close to +1 or -1, indicating the stable state of the system being reached. This state indicates the fulfillment of the bisection criteria.

For different sets of initial parameters, different bisections may be obtained. However, if the sets are close to each other, then the number of interface nodes and the number of elements in each bisection will not differ much.

## 17.4 Examples

### 17.4.1 Example 1

A finite element model shown in Fig. 17.4a with 7800 triangular elements and 4131 nodes is considered. The graph theoretical approach resulted in dividing the model into three subdomains; two subdomains each with 3800 elements and 2005 nodes and a single subdomain with 200 elements and 121 nodes, Fig. 17.4b. The small subdomain shown in Fig. 17.4c was subjected to bisection using the mean field annealing neural network model. The overall bisection result of the hybrid method is shown in Fig. 17.4d, in which the number of interface nodes is 11, and the number of nodes in each of the final subdomains is 2060.

#### 17.4.1.1 Example 2

A finite element model with an opening is considered as the second example shown in Fig. 17.5a. The model contains 4400 triangular elements and 2420 nodes. The graph theoretical approach resulted in dividing the model into three subdomains, two subdomains each having 1800 elements and 1178 nodes, and a two-piece subdomain with 800 elements and 462 nodes, Fig. 17.5b. The small subdomain shown in
